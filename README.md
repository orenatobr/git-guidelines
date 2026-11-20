# git-guidelines

Produces a branch name, commit message, PR title and PR description that follow Conventional Commits, in EN-US. It carries the branch format (`<type>/[<ticket>-]<kebab-description>`), the commit format with a mandatory scope and a 72 character limit, a full PR description template and a short list of PR best practices.

## Install

For Claude Code, copy the skill folders into your personal skills directory:

```bash
git clone https://github.com/orenatobr/git-guidelines.git
mkdir -p ~/.claude/skills
cp -R git-guidelines/skills/* ~/.claude/skills/
```

Start a new Claude Code session. Skills load from the `description` in each `SKILL.md`, so they trigger on their own and can also be called by name.

Other agents: each skill is a folder with a `SKILL.md` (YAML frontmatter plus Markdown). Tools that read the Agent Skills format can load `skills/` as it is. For the rest, paste the body of the `SKILL.md` into the agent's instruction file.

## Usage

Invoke `/git-guidelines` with a diff, ticket or summary to fill the templates, or with nothing to see the blank ones. It also triggers on "commit message", "branch name" and "PR description".

## Requirements

Nothing beyond an agent that loads skills.

## Related skills

`prs-fixes` and `prs-reviews` (included here) follow these conventions.

## What is in this repo

| Path | Purpose |
|------|---------|
| `skills/git-guidelines/` | The `git-guidelines` skill. |
| `skills/prs-fixes/` | PR helper: apply review feedback and resolve threads. |
| `skills/prs-reviews/` | PR helper: post a Requested Changes review. |
| `AGENTS.md` | Rules for AI agents that edit this repo. |

The two PR helpers ship in every repo of this family:

- `prs-fixes`: Applies the suggested fixes on one or more GitHub PRs, pushes them, replies to every review comment and resolves each thread. Example: `/prs-fixes 12, 15`.
- `prs-reviews`: Reviews one or more GitHub PRs and posts a Requested Changes review, one inline comment per finding, each with an exact location and a suggested change. Example: `/prs-reviews 12, 15`.

They need the `gh` CLI, and they call `git-guidelines`, `humanizer`, `programming-best-practices` and `attack-protection` when those skills are installed.

## Contributing

`main` is protected: changes land through a pull request with one approval. See [AGENTS.md](AGENTS.md) for the conventions.

## License

MIT, see [LICENSE](LICENSE).
