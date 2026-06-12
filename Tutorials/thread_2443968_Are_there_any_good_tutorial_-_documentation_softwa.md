---
title: "Are there any good tutorial - documentation software that meets my needs?"
date: 2020-05-22
forum: Tutorials
---

### Post by LHammonds on 2020-05-22
I'm looking for a better way to maintain my tutorials and ensure they are easy to read/follow which can present complex steps in an easy-to-grasp manner from an organizational manner.  Suggestions would be appreciated.

I currently use phpBB bulletin board software and requires breaking a tutorial into multiple posts/replies, does not allow easy organization (e.g. collapsible sections).   The benefit however is that I can easily copy/paste a tutorial to this  site with minimal changes in format.

For internal access only, I tend to prefer wiki sites but it can be a  bit off-putting to others that don't know wiki code. The rigid rules  around title names are enough to scare off potential contributors.

Here are some features I'm looking for:

[LIST=1]
[*]Web-based, browser agnostic and work well on desktop or mobile.
[*]Ability to self-host the system and not rely on 3rd party.
[*]Collapsible sections to hide content that may not need to be read.  [Example]("https://www.w3schools.com/howto/howto_js_collapsible.asp")
[*]Ability to use text, images and video (local or external such as YouTube, imgur).
[*]Ability for end-users to view changes over time (like wiki history comparisons)
[*]Ability to use templates to help with maintaining consistent design (but not require it)
[*]Ability to organize just a few tutorials or thousands of them and the version-specific variants over time.
[*]Ability to get feedback even from anonymous users such as view totals, thumbs up votes, comments, etc.
[*]Allow tutorial status to stated explicitly and potentially hide tutorials (or make harder to find) based on status. (e.g. in progress, finished, out-dated)
[*]Permission management to ensure some articles are protected from change.
[*]Does not require a PhD to use and allow editing later to be "cleaned up" if it was sloppy or incorrectly organized, titled, etc.
[*]As a bonus, would be awesome if a tutorial could be "exported" into standard formats such as .PDF, .ODT, .DOCX, etc.
[*]As a bonus, having certain content locked behind a wall would also be great for company Intranet areas, etc.
[/LIST]

Wiki sites tend to be wide-open where people can register and make changes everywhere (which might not be a good thing for maintaining quality).

Any web app that allows registration tends to get slammed with spambot registrations which is why I disable registration on my forum (or enable it with manual approval)...so if there is to be public registration, it needs a good mechanism (that changes over time) to prevent spambots.

The ubuntu.com/tutorials site has no datestamp per article making it difficult to determine relevancy or if edited recently or what changed. Organization seems limited to a single category.  Search will include links outside of the tutorial area.  The ToC on the left is great and even better to see the entire tutorial on a single page if you click the "Suggest changes" link...which makes it possible to export as a single file (e.g. print to pdf).

Thanks,
LHammonds

---

### Post by LHammonds on 2020-11-24
Potential candidate: [MoinMoin]("http://moinmo.in/") wiki

1. Seems to work with all browsers except Safari.
2. Can host internally.
3. [CollapsibleSection]("http://moinmo.in/MacroMarket/CollapsibleSection")
4. [EmbedObject]("http://moinmo.in/HelpOnMacros/EmbedObject")
5. Info tab -> Revision history
6. [Templates]("http://moinmo.in/HelpOnTemplates")
7. Categorization using backlinks, groups (users/pages), versioning, searching (full text, reg expr, boolean)
8. [Ratings]("https://moinmo.in/RatingSystemForMoin"), [Comments]("http://moinmo.in/HelpOnComments")
9. Plugin: [TaskPlanner]("http://moinmo.in/TaskPlanner")
10. [Access Control Lists (ACL)]("http://moinmo.in/HelpOnAccessControlLists"), Page
11. [WYSIWYG editor]("https://moinmo.in/HelpOnGraphicalEditor")
12. via plugin: [ExportPDF]("http://moinmo.in/ActionMarket/ExportPDF"), [static HTML dump]("http://moinmo.in/MoinDump")
13. [SecurityPolicy]("https://moinmo.in/SecurityPolicy"), [Access Control Lists (ACL)]("https://moinmo.in/HelpOnAccessControlLists")

[Comparison to other wiki software]("https://www.wikimatrix.org/compare/moinmoin+dokuwiki+mediawiki+tiddlywiki+twiki+oddmuse")

---

