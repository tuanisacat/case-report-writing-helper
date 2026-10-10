# case-report-writer v.0.1

An open-source agent skill that turns scattered clinical materials — history, labs, imaging, pathology, treatment course, follow-up — into a **publication-ready medical case report** compliant with international reporting guidelines (CARE 2013 / SCARE 2023).

## Features

- **Guideline-compliant by default** — [CARE 2013](https://www.care-statement.org/) (13 items) for general case reports; [SCARE 2023](https://www.scareguideline.com/) for surgical cases, with the mandatory guideline-citation sentence and Clavien–Dindo complication grading.
- **Structured workflow** — intake → structured data extraction (confirmed with the user) → drafting → item-by-item compliance self-check (✅/⚠️/❌) → export.
- **Safety rails** — strict fidelity to source data, a de-identification checklist, and a hard rule against fabricated references.
- **Bilingual manuscripts** — supports English- and Chinese-language case reports, with per-language style rules (terminology, tense, title conventions).
- **Format-adaptive** — feed it published example articles and it distills a journal style note (`references/journal-style-<name>.md`) before writing.
- **Environment-agnostic** — works with any agent runtime that supports skills (Kimi Work, Claude Code, Codex, …). Uses local search tools (PubMed, web) when available; leaves `[citation needed]` placeholders otherwise.

## Quick start

1. Copy this folder into your agent's skills directory, e.g.:
   - Kimi Work / Kimi Code CLI: `~/.config/agents/skills/`
   - Claude Code: `~/.claude/skills/`
   - Project level: `.agents/skills/`
2. Start a conversation and ask, e.g.:

   > Write a CARE-compliant case report from these records: a 45-year-old male presenting with … (attach history, labs, imaging)

   or

   > Turn these surgical notes into a SCARE-compliant case report for submission to [journal name].

3. The agent will extract and confirm the structured data with you, draft the manuscript, run the CARE/SCARE self-check, and export Markdown (or `.docx` where document tooling exists).

## Repository layout

```
case-report-writer/
├── SKILL.md                          # skill entry: principles + 6-step workflow
├── references/
│   ├── care-2013-checklist.md        # CARE 13 items with self-check usage
│   ├── scare-2023-checklist.md       # SCARE 2023, 18 topics for surgical cases
│   └── writing-guide.md              # per-section style, de-identification, rejection traps
├── assets/
│   └── manuscript-template.md        # fill-in manuscript skeleton
└── examples/                         # your published reference articles go here
```

## Built on

- Gagnier JJ, et al. The CARE guidelines: consensus-based clinical case reporting guideline development. *J Clin Epidemiol* / *J Med Case Rep*, 2013.
- Sohrabi C, et al. The SCARE 2023 guideline: updating consensus Surgical CAse REport (SCARE) guidelines. *Int J Surg*. 2023;109(5):1136–1140.
- CARE-radiology statement. *BMJ Evidence-Based Medicine*, 2024.

## Roadmap

- Journal-specific style packs (`references/journal-style-*.md`) distilled from real published examples
- `.docx` / LaTeX export templates
- Case-series (PROCESS 2023) support

Contributions welcome — see issues and pull requests. Please never commit identifiable patient data.

## Disclaimer

**This tool is intended solely as an academic research aid. It is not a medical device, does not provide medical advice, and must never be used for clinical diagnosis, treatment, or any decision affecting patient care.**

By using this tool, you acknowledge and agree that:

1. **No accuracy is guaranteed.** All content is produced by an AI system and may contain errors, omissions, or fabricated statements. Every value, citation, and conclusion must be independently verified against primary sources by a qualified professional before any use.
2. **You bear full responsibility.** The user assumes sole academic, ethical, and legal responsibility for the authenticity and lawfulness of all input data, for the complete de-identification of patient information, for obtaining informed consent and ethics-committee approval where required, and for the final content of any manuscript submitted or published.
3. **Prohibited uses.** Using this tool to fabricate, falsify, or manipulate clinical data or references; to input, process, or output patient-identifiable information; or to violate any applicable law, regulation, or institutional policy is strictly prohibited.
4. **No liability.** To the fullest extent permitted by applicable law, the authors and contributors shall not be liable for any direct, indirect, incidental, or consequential damages — including, without limitation, manuscript rejection or retraction, findings of academic misconduct, legal claims, or harm to any third party — arising from the use or misuse of this tool.
5. **No warranty.** This tool is provided "as is" and "as available", without warranty of any kind, express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, and non-infringement.

If you do not agree to these terms, do not use this tool.

## License

[MIT](LICENSE)
