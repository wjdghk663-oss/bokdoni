복돈이 v5 — 나만의 가족 저축 앱 설치 안내
1. GitHub 계정에서 새 공개 저장소 bokdoni 생성. ZIP 압축을 풀고 내부 파일과 icons 폴더를 저장소 루트에 업로드. Settings > Pages > Deploy from a branch > main / root > Save.
2. Firebase Console에서 별도 프로젝트 생성. 웹 앱 등록 후 firebaseConfig 객체를 복사하여 firebase-config.js의 null 대신 붙여넣기 (window.BOKDONI_FIREBASE = {...}; 형태). 수정 파일을 GitHub에 업로드.
3. Authentication > Sign-in method > Email/Password 활성화. Settings > Authorized domains에 본인의 GitHub Pages 호스트 추가 (예: username.github.io).
4. Firestore Database 생성 (프로덕션 모드). Rules 탭에 firestore.rules 전체 내용을 붙여넣고 게시.
5. 앱 주소 https://username.github.io/bokdoni/ 에 접속하여 본인 이메일로 첫 가입, 이메일 인증 후 로그아웃. Authentication > Users에서 본인 UID 복사.
6. Firestore Data에서 settings 컬렉션, access 문서 생성. ownerUid (string)에 본인 UID, invitedEmails (array)에 초대할 이메일을 소문자로 추가. 초대자가 없다면 빈 배열. 저장.
7. 본인 재로그인. 기존 HTML 기록은 설정 > 데이터 백업 후 새 앱에서 데이터 복원. 빈 공유 기록에 복원하는 것을 권장. 복원은 기존 공유 기록을 교체하므로 먼저 백업.
8. 가족에게 앱 주소 전달. 초대 이메일로 첫 가입, 이메일 인증, 재로그인. 가족은 조회 전용. 관리자만 기록 수정 가능. 별도 가족 추가는 invitedEmails 수정.
9. 아이폰 Safari에서 앱 접속 > 공유 > 홈 화면에 추가. 다른 사람은 자신의 GitHub/Firebase 프로젝트로 1~9를 반복하면 완전히 별도 앱을 운영 가능.
10. 금리 탐색소는 금융감독원 API 인증키 또는 신뢰할 수 있는 중계 서버 설정 필요. 키를 공개 저장소에 넣지 말 것. CORS로 직접 호출이 실패할 수 있음.
주의: 공개 GitHub에는 소스만 올리고 백업 JSON, 개인 기록, 비밀번호는 올리지 마세요. Firebase 웹 설정은 공개 식별 정보이며 접근 제어는 Firestore 규칙이 담당합니다. 실제 Firebase 연결 및 iPhone 동작은 설치 후 확인 필요. 공유 기록은 단일 문서에 저장되므로 동시 관리자 편집 및 대용량 기록에 적합하지 않습니다.
