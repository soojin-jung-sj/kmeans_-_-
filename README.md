# kmeans_-_-
# 📊 인프런 이벤트 댓글 군집 분석 (TF-IDF & K-Means Clustering)

## 📝 프로젝트 개요
이 프로젝트는 인프런(Inflearn) 이벤트 참여자들의 댓글 데이터를 바탕으로 자연어 처리(NLP) 및 비지도 학습(Unsupervised Learning) 기법을 활용하여 주요 주제와 유저들의 관심사를 도출하는 텍스트 마이닝 프로젝트입니다. 
텍스트 데이터를 **TF-IDF** 기법으로 벡터화하고, **K-Means** 알고리즘을 사용하여 유사한 성격을 가진 댓글들을 군집화(Clustering)하였습니다.

## 🛠 기술 스택 (Tech Stack)
- **Language:** Python
- **Environment:** Jupyter Notebook
- **Libraries:** Pandas, Numpy, Scikit-learn (`TfidfVectorizer`, `KMeans`, `silhouette_score`), Matplotlib, Seaborn 등 (형태소 분석기 등 사용 시 추가 기재)

## 🔍 분석 프로세스 (Workflow)
1. **데이터 전처리 (Data Preprocessing):**
   - 댓글 텍스트 정제 및 형태소 추출
   - 분석에 불필요한 불용어(Stopwords) 제거
2. **특성 추출 (Feature Extraction):**
   - `TfidfVectorizer`를 이용해 텍스트 데이터를 고차원 수치 벡터로 변환
3. **군집화 모델링 (Clustering):**
   - K-Means 알고리즘 적용 (초기 실험 $K=30$으로 진행)
4. **모델 평가 및 시각화 (Evaluation):**
   - 실루엣 스코어(Silhouette Analysis)를 통한 군집 응집도 및 분리도 시각화 검증

## 💡 분석 결과 및 시사점 (Results & Insights)
- **텍스트 데이터의 군집화 특성:** TF-IDF로 벡터화된 텍스트 데이터의 고차원/희소(Sparse)한 특성 때문에, 전체 평균 실루엣 스코어는 수치형 데이터에 비해 다소 낮게(0 근처) 도출되었습니다.
- **특화 군집 도출 (Cluster 1~29):** 특정 강의명, 강사명, 이벤트 목적 등 핵심 키워드를 포함한 댓글들은 높은 실루엣 계수를 보이며 매우 뚜렷하고 단단한 의미 있는 군집을 형성했습니다.
- **거대 잡동사니 군집 (Cluster 0):** 특징이 모호하거나 여러 주제가 섞인 일반적인 댓글들이 하나의 큰 군집(Cluster 0)으로 묶이는 현상을 확인했습니다.

## 🚀 향후 개선 계획 (Action Plan)
현재 결과를 바탕으로 모델의 성능을 향상시키고 더 깊이 있는 인사이트를 도출하기 위해 다음 4단계의 고도화 작업을 계획하고 있습니다.

1. **불용어(Stopwords) 사전 업데이트:** 여러 군집에 걸쳐 무의미하게 반복되는 단어를 찾아 제거.
2. **최적의 K값 탐색:** 너무 잘게 쪼개진 군집들을 통합하기 위해 K값을 15~20 범위로 줄여서 재학습 진행.
3. **계층적 클러스터링(Sub-clustering) 적용:** 의미가 뚜렷한 군집은 확정 짓고, 모호한 데이터가 뭉친 **Cluster 0** 데이터만 따로 추출하여 2차 KMeans 군집화를 통해 숨겨진 소주제 발굴.
4. **노이즈 필터링:** 실루엣 계수가 0 이하인(잘못 분류된) 데이터는 분석 대상에서 제외하여 최종 결과의 신뢰도 향상.

## ⚙️ 실행 방법 (How to Run)
1. 이 저장소를 로컬 환경에 클론(Clone)합니다.
2. `requirements.txt`가 있다면 필요한 라이브러리를 설치합니다. (`pip install -r requirements.txt`)
3. `ch08.1.인프런_이벤트 댓글 분석_TFIDF_KMeans_0312.ipynb` 파일을 Jupyter Notebook 또는 Jupyter Lab 환경에서 엽니다.
4. 위에서부터 순차적으로 셀을 실행하며 분석 과정과 시각화 결과를 확인합니다.
