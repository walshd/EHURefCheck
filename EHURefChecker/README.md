# EHU Reference Checker

A client-side web application for checking academic references and in-text citations in student submissions. All processing happens entirely in the browser — no document data is ever transmitted to a server.

## Purpose

Students frequently lose marks for incorrectly formatted references or for mismatches between in-text citations and their reference list. This tool automates those checks, flagging issues reference by reference so students can correct them before submission.

## Features

**Document support**
- Microsoft Word (.docx)
- PDF (.pdf)

**Checks performed**

1. **Format validation** — each reference is assessed against the rules for the chosen style (author format, required fields, punctuation, year placement, [online] tags, Available from: and Accessed date for online sources, volume/issue/page numbers for journals, etc.).

2. **Cross-referencing — citations to references** — every in-text citation is matched to a corresponding entry in the reference list. Unmatched citations are flagged, with a hint if a surname match exists but the year differs.

3. **Cross-referencing — references to citations** — every reference list entry is checked for at least one corresponding in-text citation. Entries that appear only in the list (and never in the body text) are flagged.

4. **Alphabetical order** — for author-date styles, the reference list is checked for correct alphabetical ordering.

**Supported reference styles**

| Style | Level of validation |
|---|---|
| British Standard Harvard 2014 (EHU Default) | Full — based on EHU Learning Services guide |
| APA 7th Edition | Good |
| IEEE | Good |
| MLA 9th Edition | Good |
| Chicago / Turabian (Author-Date) | Good |
| Harvard (Generic) | Good |
| Vancouver | Good |
| MHRA | Basic |
| OSCOLA | Basic |

The EHU Harvard 2014 style is validated against the Edge Hill University Learning Services style guide and covers all reference types documented therein: books, edited books, book chapters, journal articles (print and online), websites, eBooks, Kindle editions, theses, blogs, YouTube/online video, conference papers, reports, newspapers, podcasts, broadcast TV/radio, Acts of Parliament, statutory instruments, Hansard, law reports, films, Facebook/X posts, apps, pre-prints, Cochrane Library entries, and more.

## Usage

Open `index.html` in any modern web browser. No installation, server, or internet connection is required for operation (the PDF.js and Mammoth.js libraries load from CDN on first use).

1. Select the reference style from the dropdown (default: EHU Harvard 2014).
2. Upload a .docx or .pdf file using the upload area.
3. Click **Check Work**.
4. Review the results — each reference is listed with a pass/fail indicator and, where issues are found, specific guidance on what needs correcting.

The filter bar lets you view all references, only those with issues, or only those that passed.

## Privacy

No data leaves the browser. Documents are processed entirely client-side using [PDF.js](https://mozilla.github.io/pdf.js/) and [Mammoth.js](https://github.com/mwilliamson/mammoth.js). Nothing is stored, logged, or transmitted.

## Deployment

The app is a single HTML file with no build step. It can be deployed to:

- **GitHub Pages** — push to a `gh-pages` branch or configure Pages in repository settings.
- **Cloudflare Pages** — connect the repository; build command: none, output directory: `.` (or `/`).
- **Any static host** — upload `index.html` directly.

## Limitations

Automated reference checking is a supplement to, not a replacement for, manual review. The checker may:

- Produce false positives for unconventional but technically valid formatting.
- Miss issues that require semantic understanding (e.g. whether a title is correctly capitalised in sentence case).
- Struggle to extract text cleanly from PDFs with complex layouts, scanned pages, or non-standard encoding.
- Fail to detect in-text citations if the document uses footnotes rather than parenthetical citations (relevant for MHRA and OSCOLA).

Students should always verify flagged issues against their style guide before making changes.

## Roadmap

- **Existence verification** — a planned future feature will cross-check references against academic databases (Google Scholar, CrossRef, OpenAlex) to verify that cited sources actually exist and that the metadata (year, journal, volume) is accurate. This was the focus of an earlier prototype ([Refify](https://github.com/walshd/refify)) and will be integrated once reliable API access is confirmed.
- Footnote citation detection for MHRA and OSCOLA styles.
- Additional feedback on citation consistency (e.g. same source cited with different years or initials).

## Acknowledgements

- Style guide: Edge Hill University Learning Services, *Harvard Referencing Style Guide* (2014, v3).
- PDF text extraction: [PDF.js](https://mozilla.github.io/pdf.js/) (Mozilla).
- Word document extraction: [Mammoth.js](https://github.com/mwilliamson/mammoth.js).
