# BUL:C 제품 소개서 · Product Brochure

BUL:C(불씨) GPU 화재·피난 시뮬레이션 제품 소개서입니다. (주)메테오시뮬레이션, 2026년 11월판.
Product brochure for BUL:C, GPU fire and evacuation simulation by Meteor Simulation Inc. (November 2026 edition).

| | PDF | HTML (editable booklet) |
|---|---|---|
| 한국어 (Korean) | [BULC_Product_Brochure_KO.pdf](BULC_Product_Brochure_KO.pdf) | [BULC_Product_Brochure_KO.html](BULC_Product_Brochure_KO.html) |
| English | [BULC_Product_Brochure_EN.pdf](BULC_Product_Brochure_EN.pdf) | [BULC_Product_Brochure_EN.html](BULC_Product_Brochure_EN.html) |

A4, 17 pages. The HTML files are self-contained (fonts and images embedded); download and open them in a browser to view, edit, or print to PDF.
최신 판 다운로드 / Latest downloads: [Releases](../../releases/latest)

제품 안내 / Product: <https://bulc.msimul.com> · 사용 설명서 / Docs: <https://docs.msimul.com/bulc> · 검증 결과 / V&V: <https://docs.msimul.com/bulc/vv>

---

## BUL:C V&V 보고서 · V&V Report (2026.11, 초안 · Draft)

BUL:C의 화재 해석 엔진(BUL:C GPU 코어)은 FDS 입력 파일을 그대로 읽어 GPU에서 계산합니다. 이 보고서는 NIST가 공개한 FDS 공식 Verification·Validation 가이드(FDS 6.11.1판)의 케이스를 공식 입력 파일 그대로 BUL:C GPU 코어로 다시 계산하고, 같은 입력의 CPU FDS 결과, 해석해, 실험 측정값과 비교한 기록입니다. 잘 맞는 결과와 함께 차이가 남은 케이스, 계산을 끝내지 못한 케이스, 알려진 편차를 같은 무게로 실었습니다.

The BUL:C fire engine (the BUL:C GPU core) reads FDS input files as they are and runs them on the GPU. This report recomputes the cases of the official FDS Verification and Validation Guides (FDS 6.11.1 edition, NIST) with the BUL:C GPU core from the official input files, unchanged, and compares them with CPU FDS runs of the same input, analytical solutions, and experimental measurements. Cases that agree well are reported with the same weight as cases where differences remain, runs that did not finish, and known deviations.

| | 화면용 (표지 + 본문) · Screen | 인쇄용 · Print (A4 body + cover spread) |
|---|---|---|
| 한국어 (Korean) | [BULC_VV_Report_2026.11_Draft_KO.pdf](vv-report/BULC_VV_Report_2026.11_Draft_KO.pdf) | [본문 Body](vv-report/print/BULC_VV_Report_2026.11_Draft_KO_Body_A4.pdf) · [표지 Cover](vv-report/print/BULC_VV_Report_2026.11_Draft_KO_Cover_Spread.pdf) |
| English | [BULC_VV_Report_2026.11_Draft_EN.pdf](vv-report/BULC_VV_Report_2026.11_Draft_EN.pdf) | [Body](vv-report/print/BULC_VV_Report_2026.11_Draft_EN_Body_A4.pdf) · [Cover](vv-report/print/BULC_VV_Report_2026.11_Draft_EN_Cover_Spread.pdf) |

A4, 한국어판 84쪽 · English edition 88 pages. 영문판은 한국어판의 번역입니다 / The English edition is a translation of the Korean edition.

### 구성 · Contents

| | 한국어 | English |
|---|---|---|
| 1장 · Ch. 1 | V&V의 뜻, 문서 범위, 비교 방식, 결과 한눈에 | What V&V means, scope, how the comparison is made, results at a glance |
| 1부 · Part 1 (2–6장) | **Verification** — 해석해가 있는 문제에서 CPU FDS와 같은 답을 내는지 | **Verification** — does the GPU core reproduce CPU FDS on problems with analytical solutions? |
| 2부 · Part 2 (7–10장) | **Validation** — 실험에 대해 FDS와 비교해 어느 정도의 정확도를 보이는지 | **Validation** — how accurate is it against experiments, compared with FDS? |
| 부록 · Appendices | 덱별 결과, 판정 식, 판 이력, 계산 환경과 자료 출처 | Results by deck, verdict formulas, version history, computing environment and data sources |

실험 장치·측정 방법과 기존 FDS 결과는 옮겨 적지 않고 가이드의 절과 쪽을 밝혔습니다.
Experimental setups, measurement methods, and existing FDS results are not reproduced; the report cites the relevant Guide sections and pages.

### 이번 판의 결과 · Results of this edition

**Verification (1부 · Part 1)** — FDS Verification Guide 해석해 비교 92절, 입력 파일(덱) 704개 · 92 Guide sections, 704 input files (decks)

| 항목 · Item | 결과 · Result |
|---|---|
| GPU 정상 종료 · GPU runs completed normally | 667 / 704 (중단 · aborted 19, 계산 전 · not yet run 18) |
| CPU FDS 6.11.1과 비교 완료 · Decks compared with CPU FDS 6.11.1 | 439 |
| CPU 대비 에러 ≤ 20 % · CPU-relative error ≤ 20 % | **371 / 439 (84.5 %)** |
| CPU 대비 에러 > 100 % · CPU-relative error > 100 % | 6 |
| 절 판정 · Section verdicts (92) | 잘 맞음 Good 74 · 차이 Differs 5 · 패치 중 Patching 3 · 비교 전 Pending 10 |

CPU 대비 에러는 같은 입력의 CPU FDS 결과에 대한 GPU 결과의 열별 상대 RMS 차이입니다. 정확해와의 직접 비교(수렴 차수 등)는 가이드 후처리를 옮긴 5절부터 싣고 있습니다(4장).
The CPU-relative error is the column-wise relative RMS difference of the GPU result from the CPU FDS result for the same input. Direct comparisons with exact solutions (orders of convergence, etc.) are given for the first 5 sections whose Guide post-processing has been ported (Chapter 4).

**Validation (2부 · Part 2)** — 15 케이스 · 15 cases (실험 · experiment 6, 다중 메시 파생 · multi-mesh derived 5, 엔진 회귀 · engine regression 4), fds_gpu 0.104.0 vs CPU FDS 6.10.1

| 항목 · Item | 결과 · Result |
|---|---|
| Phase 1 케이스 판정 (FDS 대비) · Case verdicts against FDS (13) | NOTE 8 · WARNING 2 · FAIL 3 |
| GPU 계산 미완료 · GPU run did not finish | 2 |
| Phase 2 실험 측정점 · Experimental measurement points | 17 — 가이드 2σ̃ 대역 안 · within the Guide's 2σ̃ band: GPU 14, FDS 15 |
| 4분면 · Quadrants | 둘 다 실험과 일치 Both agree 12 · GPU만 차이 Only GPU differs 2 · 둘 다 차이 Both differ 1 · GPU가 더 가까움 GPU closer 2 |
| 알려진 편차 · Known deviations | 18 (열림 · open 17) |

Phase 1의 기준은 참값이 아니라 FDS입니다. FAIL은 "FDS와의 차이가 가이드의 모델 불확도 σ̃<sub>M</sub>의 두 배를 넘는다"는 뜻이지 계산 실패가 아닙니다. 어느 쪽이 실험에 더 가까운지는 Phase 2가 보여 줍니다.
The Phase 1 reference is FDS, not the true value. FAIL means "the difference from FDS exceeds twice the Guide's model uncertainty σ̃<sub>M</sub>", not a failed run. Phase 2 shows which of the two is closer to the experiment.

### 이 판의 계산 조건 · Run conditions of this edition

| | Verification (1부 · Part 1) | Validation (2부 · Part 2) |
|---|---|---|
| BUL:C GPU | 0.100.0-r5-3b2a559c (덱마다 판 사슬의 가장 새 결과 · newest result in the version chain per deck) | fds_gpu 0.104.0 (2bcd868) |
| 기준 · Reference | CPU FDS 6.11.1 | CPU FDS 6.10.1 · 실험 측정값 · experimental data |
| 장비 · Hardware | NVIDIA GeForce RTX 5070 Ti (16 GB) · AMD Ryzen 9 7950X | NVIDIA GeForce RTX 5060 |
| 자료 시각 · Data as of | 2026-11-02 | 2026-11-12 |

이 판은 **초안**입니다. 수치는 자료 시각 기준이며 정식 판에서 바뀔 수 있습니다. 보고서는 엔진 판이 바뀔 때마다 같은 틀로 다시 만듭니다. 결과를 인용할 때는 판(2026.11 초안)과 엔진 판을 함께 적어 주십시오.
This edition is a **draft**. Values are as of the data date and may change in the final edition. The report is regenerated in the same format whenever the engine version changes; when citing results, please state the edition (2026.11 draft) and the engine version.

FDS(Fire Dynamics Simulator)는 미국 표준기술연구소(NIST)가 개발해 공개한 프로그램이며, 입력 파일과 실험값은 firemodels 공개 저장소의 것을 고치지 않고 썼습니다.
FDS (Fire Dynamics Simulator) is developed and distributed by NIST; input files and experimental data were taken unmodified from the public firemodels repositories.
