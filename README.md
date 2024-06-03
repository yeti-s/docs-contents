👀 [Yeti Docs](https://yeti-s.github.io/)
📦 [Docs Repo](https://github.com/yeti-s/yeti-s.github.io)

# 📚 Docs Contents

개발의 진행 상황이나, 고민한 과정, 그리고 공부한 내용들을 기록하기 위한 Docs를 만들었습니다.
하지만 Docs의 구조와 콘텐츠를 분리하여 관리하고 싶었어요.
따라서 Docs의 저장소와 콘텐츠의 저장소를 분리하고, 콘텐츠의 저장소를 Docs의 Submodule로 사용하려 합니다.

# 📜 메타데이터 규칙

각 컨텐츠의 메인에 해당하는 index.mdx 파일은 아래와 같은 메타데이터를 가집니다.
```
---
title: 문서의 제목 (필수!)
description: 문서에 대한 설명
date: 문서 최종 수정 날짜
category: 문서의 카테고리 (필수!)
visible: 문서 공개 여부
order: 문서 정렬 순서
---

...
...
```

해당 컨텐츠의 페이지는 `/{title}`의 URL을 가집니다.

컨텐츠의 하위 항목에 해당하는 *.mdx 파일은 아래와 같은 메타데이터를 가집니다.
```
---
title: 문서의 제목 (필수!)
description: 문서에 대한 설명
date: 문서 최종 수정 날짜
subject: 문서의 주제 (필수!)
visible: 문서 공개 여부
order: 문서 정렬 순서
---

...
...
```

해당 하위 컨텐츠의 페이지는 `/{subject}/{title}`의 URL을 가집니다.

# 🏗️ 폴더 구조

문서를 구성하는 컨텐츠는 아래와 같은 폴더 구조를 따라야 합니다.

```
|-- contents
|     |-- category1
|           |-- subject1
|                 |-- index
|                       |-- index.mdx
|                       |-- img1.png
|                       |-- img2.png
|                       |-- ...
|                 |-- title1
|                       |-- title1.mdx
|                       |-- img1.png
|                 |-- ...
|           |-- subject2
|                 |-- ...
|           |-- ...
|     |-- ...
|-- elems
|     |-- index.ts
|     |-- elem1.tsx
|     |-- elem2.tsx
|     |-- ...
|-- index
|     |-- index.mdx
```

* contents/index 폴더에 존재하는 index.mdx 파일은 문서의 첫 페이지에 대한 내용을 나타냅니다.
* subject 폴더에 존재하는 index.mdx 파일은 해당 주제에 대한 기본 페이지 내용을 나타냅니다.
* subject 폴더에 존재하는 index.mdx 제외한 나머지 .mdx 파일은 해당 주제의 하위 항목으로 표시됩니다.
* 각 페이지에 들어갈 이미지와 같은 데이터는 해당 페이지를 구성하는 .mdx 파일과 동일한 위치에 존재합니다.
* elems 폴더에 .tsx 파일은 컨텐츠에서 사용할 ReactNode들을 나타냅니다.