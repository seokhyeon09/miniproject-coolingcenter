# miniproject-coolingcenter (무더위 쉼터 지도)

서울시 내 무더위 쉼터 위치를 시각적으로 제공하고, 원하는 장소를 검색 및 즐겨찾기 할 수 있는 지도 기반 웹 애플리케이션입니다. (개발 기간: 2026.02.27 ~ 2026.03.05)

## Links
- 배포 주소: https://miniproject-coolingcenter.vercel.app/map
- GitHub 저장소: https://github.com/seokhyeon09/miniproject-coolingcenter

## Tech Stack (사용 기술)
- Framework & Build Tool: React 19, Vite
- Language: JavaScript
- Routing: React Router DOM
- State Management: Context API
- Styling: Tailwind CSS
- API & Storage: Kakao Maps API, LocalStorage
- Security: Environment Variables (.env)

## Key Features (주요 기능)
- 카카오맵 API 연동 및 마커 제어: 카카오 지도 SDK를 커스텀 훅(useKakaoLoader)을 통해 비동기적으로 로드하여 지도를 렌더링하고, 좌표 데이터를 바탕으로 지도 위에 마커와 상세 정보창(InfoWindow)을 동적으로 표시합니다.
- 실시간 장소 검색 및 UI 업데이트: 사용자가 입력한 검색어에 따라 좌측의 쉼터 목록과 우측 지도 상의 마커가 useMemo를 통해 실시간으로 필터링되어 즉각적인 렌더링 결과를 제공합니다.
- 전역 상태 기반 즐겨찾기 (비휘발성): Context API를 도입하여 즐겨찾기 데이터 상태를 프로젝트 전역에서 관리합니다. 또한 LocalStorage와 연동하여 브라우저를 종료하거나 새로고침해도 사용자의 즐겨찾기 목록이 영구적으로 보존됩니다.
- 라우터 간 데이터 전달(State Transfer): 즐겨찾기 페이지에서 특정 쉼터의 '지도보기' 링크를 클릭하면, React Router의 state 속성을 이용해 해당 장소의 데이터를 Map 페이지로 전달합니다. 이를 통해 지도가 해당 위치를 중심으로 자동 이동하고 확대되도록 사용자 경험(UX)을 크게 향상시켰습니다.
- 환경 변수 관리를 통한 보안 강화: 카카오 앱 키와 같은 민감한 인증 정보는 Vite의 환경 변수(.env) 파일로 분리하여 외부 노출을 방지했습니다.

## 느낀점 / 개선할 점
- 느낀점: 외부 API인 카카오맵을 리액트에 맞추어 연동하는 과정에서 DOM이 렌더링되기 전에 외부 스크립트를 안전하게 불러오는 비동기 처리의 중요성을 배웠습니다.
- 개선할 점: 로컬에 저장된 JSON 파일을 데이터 소스로 사용하고 있습니다. 향후 서울시 공공데이터 포털 등에서 제공하는 Open API와 연결하여, 실시간으로 업데이트되는 무더위 쉼터 정보가 지도에 반영되도록 서비스로 만들어 보고 싶습니다.

## Getting Started (로컬 실행 방법)

1. 저장소 클론 (Clone the repository)
git clone https://github.com/seokhyeon09/miniproject-coolingcenter

2. 패키지 설치 (Install dependencies)
npm install

3. 환경 변수 설정 (Set up environment variables)
최상위 경로에 .env 파일을 생성하고 VITE_KAKAO_APP_KEY에 발급받은 카카오맵 API 키를 입력하세요.

4. 개발 서버 실행 (Run the dev server)
npm run dev
