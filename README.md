# ccbox

Claude Code with document-generation skills — PDF, XLSX, PPTX, DOCX, and more — in a Docker container.

## Quick start

```bash
curl -fsSL https://raw.githubusercontent.com/mk0e/ccbox/main/install.sh | bash
```

Close your terminal, open a new one, then from any directory:

```bash
ccbox
```

The installer walks you through authentication. The image is pulled automatically on first run.

To change auth, update, or uninstall — run the installer again:

```bash
curl -fsSL https://raw.githubusercontent.com/mk0e/ccbox/main/install.sh | bash
```

## Alternative: clone and install

```bash
git clone https://github.com/mk0e/ccbox.git
cd ccbox && ./install.sh
```

## Without the installer

```bash
mkdir -p ~/.ccbox
docker run -it --rm \
  -v "$(pwd)":/workspace \
  -v ~/.ccbox:/home/claude/.claude \
  ccbox
```

## Resume a session

```bash
ccbox claude --continue
```

To resume a specific session:

```bash
ccbox claude --resume <session-id>
```

## One-shot mode

```bash
ccbox claude --print "Create a PDF report summarizing Q1 sales"
```

## What's inside

### Built-in Skills

| Skill | Purpose |
|-------|---------|
| pdf | Create, edit, merge, split, OCR PDF documents |
| xlsx | Create and edit Excel spreadsheets with formulas |
| pptx | Create and edit PowerPoint presentations |
| docx | Create and edit Word documents with tracked changes |
| doc-coauthoring | Structured co-authoring workflow |
| internal-comms | Templates for status reports, newsletters |
| theme-factory | Apply consistent themes to documents |
| canvas-design | Create visual art, posters, infographics |
| brand-guidelines | Apply consistent brand identity |
| skill-creator | Create new custom skills |

### System Tools

LibreOffice, Pandoc, Tesseract OCR, qpdf, pdftk, ImageMagick

### Packages

**Python:** reportlab, pdfplumber, pypdf, python-pptx, python-docx, openpyxl, pandas, Pillow, and more

**Node:** pptxgenjs, docx, pdf-lib, pdfjs-dist

## Templates

Place company templates in one of two locations:

**Per-project** (in your workspace):
```
my-project/
├── templates/
│   ├── company.pptx
│   └── report.docx
```

**Shared** (available in all sessions):
```
~/.ccbox/templates/
├── company.pptx
└── report.docx
```

When you ask Claude to create a document, it checks both locations and uses matching templates to preserve your branding, layouts, and styles.

## Custom Skills

Add skills to your workspace (project-specific):

```
my-project/.claude/skills/my-skill/SKILL.md
```

Or to `~/.ccbox/skills/` (available in all sessions).

## Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` / `PGID` | `1000` | Match container user to your host UID/GID |
| `GIT_USER_NAME` | `Claude` | Git author name inside container |
| `GIT_USER_EMAIL` | `claude@ccbox` | Git author email inside container |

## License

MIT
