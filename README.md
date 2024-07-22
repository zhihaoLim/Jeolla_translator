# 📙 전라도 방언 - 표준어 번역기 📗
# 🥇도랑도랑 & 🥈싸게싸게
## 🧍 개발자
임지호(Jeeho Lim)
- Tsinghua University (Beijing, China, 2014)
- Language Researcher (Chinese, Korean, Endangered Language)
- Data Analyst (SQL, Python)
- AI Developer (DL, NLP)

## 🤖 모델 소개
- 도랑도랑 : KoBART 사전 학습 모델 기반 전라도 방언 - 표준어 양방향 번역 모델
- 싸게싸게 : Seq2seq + Attention 기반의 전라도 방언 - 표준어 양방향 번역 모델

## 📝 학습 환경 및 프로세스
- 도랑도랑
  - Pytorch/Transformers 환경에서 학습
  - 퍼스트 시퀀스에 dialect | standard 토큰을 넣어 번역 방향 사전 설정 후 학습
  - 사전 학습 모델(gogamza/kobart-base-v2)에 Seq2SeqTrainor를 임포트해 튜닝 후 학습
  - 주요 매개변수 :
      - max_length : 64
      - learning_late : 2e-5
      - batch_size : 32
      - epochs : 3
  
- 싸게싸게
  - Tensorflow/Keras 환경에서 학습
  - 퍼스트 시퀀스에 dialect | standard 토큰을 넣어 번역 방향 사전 설정 후 학습
  - Seq2Seq + Attention 메커니즘 모델링하여 튜닝 후 학습
  - 주요 매개변수 :
      - max_length : 64
      - learning_late : 2e-5
      - batch_size : 32
      - epochs : 50
  
## 📊 모델 평가
- BLEU(100) Score:
  - 도랑도랑:
      - 방언 > 표준어 : 0.76
      - 표준어 > 방언 : 0.62
  - 싸게싸게:
      - 방언 > 표준어 : 0.33
      - 표준어 > 방언 : 0.12
    
## 🫂 서비스 구현
- Django 기반 번역기 웹 서비스
- 'Service' 참조

## 📈 추후 발전 방향
- 총 3개의 대용량 데이터셋 중 1개만을 활용하였는데, 추후 3개 데이터를 모두 취합하여 재학습
- 전라도말 사전을 기반으로 하여 방언 데이터 전처리
- 전라도말 국어 음운론을 기반으로 신조어/전문용어 등에 대한 전라도식 표현 생성 매커니즘 연구
- (싸게싸게)두 언어 간 높은 유사성을 고려, 모델 경량화로 스코어 향상
- 저자원 언어(low-resource language)에 대한 번역 모델에 대해 지속적으로 연구 예정
- 개발자의 연구 분야인 '위기 언어(Endangered Language)' 보존 및 기획에 기여할 수 있는 방향 수립

### 📚 활용 데이터
- 중·노년층 한국어 방언 데이터 (AI-Hub)
- 한국어 방언 발화 데이터 (AI-Hub)
