# TypeStats Analytics Setup Guide

## 현재 구현된 기능

### 1. Google Analytics 이벤트 추적
- **character_count**: 글자수 세기 이벤트 (언어별, 글자수, 텍스트 길이)
- **language_detected**: 언어 감지 이벤트
- **ui_language_used**: UI 언어 사용 이벤트
- **paste_button_clicked**: 붙여넣기 버튼 클릭
- **clear_button_clicked**: 지우기 버튼 클릭
- **language_changed**: 언어 변경 이벤트

### 2. 로컬 스토리지 통계
- 일별 세션 수
- 언어별 사용 통계
- UI 언어별 사용 통계
- 총 글자수 및 텍스트 수

### 3. 통계 대시보드
- 실시간 통계 표시
- 언어별 사용량 차트
- UI 언어 선호도 차트

## Google Analytics에서 확인할 수 있는 통계

### 1. 실시간 보고서
- 현재 활성 사용자 수
- 실시간 이벤트 발생

### 2. 이벤트 보고서
- **이벤트 > 이벤트 개요**: 전체 이벤트 통계
- **이벤트 > 이벤트 이름**: 특정 이벤트별 상세 통계
  - `character_count`: 글자수 세기 통계
  - `language_detected`: 언어 감지 통계
  - `ui_language_used`: UI 언어 사용 통계

### 3. 사용자 보고서
- **사용자 > 개요**: 총 사용자 수, 신규 사용자
- **사용자 > 기술**: 브라우저, OS, 디바이스 정보

### 4. 행동 보고서
- **행동 > 사이트 콘텐츠**: 페이지뷰 통계
- **행동 > 이벤트**: 이벤트별 상세 분석

## 고급 분석을 위한 Google Analytics Reporting API

### 1. API 설정
```javascript
// Google Analytics Reporting API v4 사용
// 서비스 계정 키 필요
// https://console.developers.google.com/apis/credentials
```

### 2. 주요 메트릭
- **사용자 수**: 총 방문자 수
- **세션 수**: 총 세션 수
- **이벤트 수**: 각 이벤트별 발생 횟수
- **언어별 통계**: 감지된 언어별 사용량
- **지역별 통계**: 사용자 지역 분포
- **디바이스별 통계**: 모바일/데스크톱 사용량

### 3. 커스텀 대시보드 구현
```javascript
// 예시: Google Analytics API 호출
function getAnalyticsData() {
  // API 호출하여 데이터 가져오기
  // 차트 라이브러리로 시각화
}
```

## 현재 수집되는 데이터

### 이벤트 데이터
1. **character_count**
   - event_category: "text_analysis"
   - event_label: 감지된 언어 (Korean, Chinese, etc.)
   - value: 총 글자수
   - custom_parameter_1: 감지된 언어
   - custom_parameter_2: 총 글자수
   - custom_parameter_3: 텍스트 길이

2. **language_detected**
   - event_category: "language_analysis"
   - event_label: 감지된 언어
   - value: 해당 언어 글자수

3. **ui_language_used**
   - event_category: "user_preference"
   - event_label: 선택된 UI 언어
   - value: 1

### 로컬 스토리지 데이터
```json
{
  "2025-01-27": {
    "totalSessions": 15,
    "languages": {
      "Korean": 8,
      "Chinese": 4,
      "Japanese": 2,
      "English": 1
    },
    "uiLanguages": {
      "ko": 10,
      "en": 3,
      "zh-CN": 2
    },
    "totalCharacters": 15420,
    "totalTexts": 15
  }
}
```

## 통계 확인 방법

### 1. 실시간 확인
- `/stats.html` 페이지에서 로컬 스토리지 기반 통계 확인

### 2. Google Analytics 확인
- Google Analytics 대시보드 접속
- 이벤트 보고서에서 상세 통계 확인
- 실시간 보고서에서 현재 사용자 확인

### 3. 고급 분석
- Google Analytics Reporting API 연동
- 커스텀 대시보드 구축
- 데이터 내보내기 및 추가 분석

## 다음 단계

1. **Google Analytics Reporting API 연동**
2. **실시간 통계 업데이트**
3. **지역별/디바이스별 분석**
4. **사용자 행동 패턴 분석**
5. **A/B 테스트 구현**
