![0001](https://user-images.githubusercontent.com/63702924/127151995-7d71be4d-41a9-44e2-afd4-1d6161be1be2.jpg)

![0002](https://user-images.githubusercontent.com/63702924/127151997-8ff4c487-4114-47d6-9947-946a7b86f840.jpg)
프로젝트 개요입니다. 유튜브의 인기 동영상을 보면, 하단 댓글 창에 많은 사람들이 자신의 생각을 표현하는 댓글을 답니다. 영상과 관련 있는 느낌이나 정보를 남기는 사람들도 있지만, 자신의 유튜브 채널을 홍보하거나 영상과 관련 없는 광고 댓글을 남기는 스패머들도 많이 존재합니다. 그래서 유튜브에서는 자체적으로 스팸 댓글을 차단하기도 하지만, 제대로 탐지하지 못한 댓글 또한 많이 존재합니다.
그래서 저는 유튜브 영상에 달린 댓글 데이터를 학습하여 댓글이 스팸 댓글인지 아닌지의 여부를 판별하는 모델을 만들어 보았고, 이를 Flask를 통해 간단한 웹서비스의 형태로 제작해 보았습니다.

![0003](https://user-images.githubusercontent.com/63702924/127151999-525aa21c-b60e-44be-b483-9edb6fe0980a.jpg)
사용한 데이터의 정보입니다. UCI 머신러닝 연구소에서 제작한 데이터셋을 사용하였고, 유명 가수들의 뮤직비디오 5개에서 크롤링한 댓글 데이터입니다.

![0004](https://user-images.githubusercontent.com/63702924/127152004-21a402de-7e9f-444c-89d7-ade20136fc24.jpg)
전처리 과정입니다. 데이터셋이 5개로 나누어져 있기 때문에 Concat을 통해 병합을 해 주었습니다. 그리고 학습에 불필요한 정보들을 삭제해 주었고, Count Vectorizer를 통해 문장 데이터를 벡터로 변환해 주었습니다. Count Vectorizer를 사용하면 문서를 먼저 토큰 리스트로 변환하게되고, 각 문서에서 토큰의 출현 빈도를 센 뒤 그 빈도수를 통해 인코딩 벡터로 변환하는 과정을 거치게 됩니다. 

![0005](https://user-images.githubusercontent.com/63702924/127152009-554c95a0-e189-47d9-8da2-aa6ba84f4df1.jpg)
모델 학습 과정입니다. 저는 나이브 베이즈 분류기를 사용하여 학습을 시켰습니다. 그 중에서도 MultinomialNB를 사용하였는데, 주로 문장에 나타난 단어의 횟수 등 정수 카운트에 적용되는 모델이기 때문에 이번 프로젝트에 적합한 모델이라고 생각했습니다. 정확도는 0.91 이상으로 꽤 높게 나타났습니다. 이 모델을 파이썬의 Pickle 모듈을 사용하여 저장하였습니다.

![0006](https://user-images.githubusercontent.com/63702924/127152014-579cecb6-eba1-4f6e-9056-554cf1355a7b.jpg)
앞에서 구현한 모델을 통해 댓글 내용이 스팸인지 아닌지를 판별하는 웹페이지를 제작했습니다. 상자에 스팸인지 아닌지 예측하고자 하는 댓글 내용을 입력하고, predict를 눌러줍니다. 그러면 내용에 따라 영상에 관계없는 댓글, 즉 스팸 댓글인지 영상과 관계있는 내용의 댓글인지 여부를 알려줍니다.  
