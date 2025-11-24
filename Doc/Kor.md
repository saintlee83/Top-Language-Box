# Top-Language-Box

결과

![Ex](/Ex.png)

자신이 가장 많이 사용한 언어를 pin에 고정할 수 있도록 하는 프로젝트입니다.

## 설정

### 단계 1: 저장소 포크하기
이 저장소를 포크하고 Actions 탭에서 GitHub Actions을 활성화하세요.

### 단계 2: Gist 생성하기
1. [gist.github.com](https://gist.github.com/)으로 이동
2. 새 gist를 생성하고 임의의 파일명 입력 (예: `top-language-usage.txt`)
3. 초기 내용을 추가
4. gist 생성 (공개 또는 비공개 가능)
5. URL에서 gist ID를 복사

예시: `https://gist.github.com/username/`**`f5ebdde2b6a31849520797f9f4e49831`** ← 이 부분 사용

### 단계 3: GitHub Personal Access Token 생성하기
1. [GitHub 설정 → Tokens](https://github.com/settings/tokens)으로 이동
2. **"Generate new token"** → **"Generate new token (classic)"** 클릭
3. 설명 추가 (예: "Top-Language-Box")
4. 다음 권한 선택:
   - ✅ **`gist`** - Gist 생성 권한
   - ✅ **`repo`** - 저장소 전체 접근 권한 (저장소 읽기에 필요)
5. **"Generate token"** 클릭
6. **토큰을 즉시 복사** (다시 볼 수 없습니다!)

### 단계 4: Repository Secrets 추가하기
1. 포크한 저장소로 이동
2. **Settings** → **Secrets and variables** → **Actions**로 이동
3. **"New repository secret"** 클릭
4. 다음 secrets를 추가:
   - **이름:** `GH_TOKEN`  
     **값:** 단계 3에서 생성한 Personal Access Token
   - **이름:** `GH_GISTID`  
     **값:** 단계 2에서 복사한 Gist ID

### 단계 5: Action 테스트하기
1. 저장소의 **Actions** 탭으로 이동
2. **"Build"** workflow 선택
3. **"Run workflow"** → **"Run workflow"** 클릭
4. workflow가 완료될 때까지 대기
5. gist를 확인하여 업데이트 되었는지 확인!

## 로컬 테스트

로컬에서 테스트하려면:

```bash
# 의존성 설치
npm install

# 환경 변수 설정
export USER_NAME=your-github-username
export GH_TOKEN=your-github-token
export GH_GISTID=your-gist-id

# 스크립트 실행
npm start
```

## 문제 해결

### "Bad credentials" 에러

이 에러는 GitHub 토큰이 유효하지 않거나 올바르게 설정되지 않았음을 의미합니다:

1. **Secrets가 올바르게 설정되었는지 확인**
   - 저장소 Settings → Secrets and variables → Actions로 이동
   - `GH_TOKEN`과 `GH_GISTID`가 있는지 확인
   - Secrets에 여분의 공백이나 따옴표가 없어야 합니다

2. **토큰 재생성**
   - 토큰이 만료되었을 수 있습니다
   - [GitHub 설정 → Tokens](https://github.com/settings/tokens)로 이동
   - 이전 토큰을 삭제하고 새로 생성
   - `repo`와 `gist` 권한을 모두 선택했는지 확인
   - 저장소의 `GH_TOKEN` secret을 업데이트

3. **수동 workflow 트리거로 테스트**
   - Actions 탭 → Build workflow로 이동
   - "Run workflow"를 클릭하여 즉시 테스트
   - 로그에서 자세한 에러 메시지 확인

### "Failed to calculate language usage" 에러

일반적으로 다음을 의미합니다:
- GitHub 사용자 이름이 올바르지 않음
- 저장소가 모두 비어있음
- API rate limit 초과

### Gist가 업데이트되지 않음

1. Actions 탭에서 에러 로그 확인
2. Gist ID가 올바른지 확인 (전체 URL이 아닌 ID 부분만)
3. Gist가 존재하고 편집 권한이 있는지 확인

---

[github_readme_state](https://github.com/anuraghazra/github-readme-stats#top-languages-card) 와 [productive-box](https://github.com/maxam2017/productive-box) 에서 영감을 받았습니다.
