# Plan

Two plans in one file: one for the HW #4.3 project itself, one for how the repo gets set up and maintained.

---

## Part 1 — Project Plan (HW #4.3)

### Goals

- Produce one Quarto document that covers all three required sections (airports, Monte Carlo, calcium GenAI comparison).
- Render it to a clean PDF with a proper table of contents, numbered sections, cross-references, and a code appendix.
- Make the analysis reproducible so anyone with the repo can re-render the PDF without edits.

### Needs

**Things:**
- Laptop, R, RStudio, Quarto, TinyTeX (for PDF rendering).
- R packages: `tidyverse`, `knitr`, `kableExtra`.
- `calcium.csv` from the instructor.
- `generic_group_means.png` and `generic_individual_lines.png` from the instructor.
- Airport passenger numbers typed into a tibble (sourced from Wikipedia and public airport stats).

**Actions:**
- Build the airport tibble, pivot wide, render the table with `kable` + `kableExtra`.
- Plot six-airport line chart with Brewer colors and labeled breaks.
- Write `generate_mcPoints()` and `make_mc_plot()` helpers for Section 2.
- Use a Quarto layout div to put four Monte Carlo plots in a 2×2 grid.
- Read `calcium.csv`, split into two groups, rename columns, drop the empty row, pivot longer, bind together.
- Draft the plan-informed prompt for Claude, save the exact text in Appendix A.
- Compare plan-informed vs. generic output in Section 3.
- Add reflection and GenAI usage appendix.
- Auto-generate the code appendix with `ref-label: !expr knitr::all_labels()`.

### Steps

1. Sketch the three sections on paper before opening RStudio.
2. Write the YAML header (title, author, date, `format: pdf`, execute defaults).
3. Build Section 1 — airport tibble, table, line chart, analysis paragraphs.
4. Build Section 2 — Monte Carlo helpers, four plots in the layout div, analysis paragraphs.
5. Build Section 3 — tidy `calcium.csv`, write the plan-informed prompt, paste Claude's output code, drop in the two generic PNGs, write the comparison.
6. Write the reflection and both appendices.
7. Render to PDF. Fix any LaTeX errors that show up.
8. Read through the rendered PDF end to end to catch typos and broken cross-references.
9. Push the final version and tag the commit.

---

## Part 2 — Repo Plan

### Goals

- Keep `main` stable and only update it through reviewed pull requests.
- Do all active writing and editing on a `dev` branch.
- Use issues to track anything that needs fixing instead of keeping a mental list.
- Leave enough commit history that a grader can see how the project came together.

### Needs

**Things:**
- GitHub account, Git installed locally, SSH or HTTPS access to the repo.
- A public repository named something like `stat184-hw43`.
- A `.gitignore` that ignores `*_files/`, `*_cache/`, `.Rproj.user/`, and `.DS_Store`.

**Actions:**
- Create the public repo on GitHub.
- Initialize locally, set the remote, push the first commit to `main`.
- Branch off into `dev` for all follow-up work.
- Open issues for each concrete task (README, YAML fix, missing data labels, etc.).
- Close issues through commits using `Closes #N` so the link shows up on the issue page.
- Open a PR from `dev` into `main` when a chunk of work is ready for review.

### Steps

1. Create a public repo on GitHub with a README stub and an MIT license.
2. Clone locally, drop in the QMD, PDF, `calcium.csv`, and the two PNGs.
3. Make the first real commit to `main` with the baseline files.
4. `git checkout -b dev` and push the dev branch.
5. Open the first few issues: README content, plan document, YAML header, reproducibility check, code appendix.
6. Work each issue on `dev`, one commit per issue when possible, referencing the issue number in the commit message.
7. When a batch of issues is done, push `dev` and open a PR into `main` with a short description of what changed and which issues it closes.
8. Merge the PR. Pull `main` locally so it stays in sync.
9. Before submission, double-check that `main` has the final PDF, final QMD, README, and PLAN, and that most issues are closed.
