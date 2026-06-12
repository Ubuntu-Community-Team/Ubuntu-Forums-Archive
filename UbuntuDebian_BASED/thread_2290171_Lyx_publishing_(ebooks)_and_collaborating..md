---
title: "Lyx publishing (ebooks) and collaborating."
date: 2015-08-10
forum: Ubuntu/Debian BASED
---

### Post by ski_phreak on 2015-08-10
I love Lyx because it separates the formatting necessities from the actual writing process.  This tutorial doesn't attempt to guide you through all the capabilities of Lyx since their sample documents (Help menu) are far more thorough than I could ever be. Instead, this is my outline (a checklist for myself, really) in how to get my writing in formats that others can collaborate with me, and then published in some **non**-PDF formats.

Sadly, I couldn't find much help online about publishing other formats. Lots of help for math figures, and dense scientific formulae, but very little about export formats.  Half of that is obsolete and unworkable, and all of it heavily viewed.

Here's what I want to do, what I'm working with, and what's worked best for me.  (Let's convince the literary world that Lyx ain't just for Math/Science publications!)

**Equipment/OS**
Laptop Dell Dimension D530 SolydX x32 / TDE (a lightweight KDE)
Desktop Dell Dimension  E521 SolydK x64 / KDE & TDE

**Software**:
Lyx 2.1.2 (Document class: "Book with extra fonts," Page style: "Fancy," LaTeX preamble:\let\cleardoublepage\clearpage )
LibreOffice 4.3.3.2
Calibre 4.3.3
elyxer 1.2.5
Firefox ESR 38.1.0
Chrome [COLOR=#303942][FONT=Clear Sans]44.0.2403.89 x64[/FONT][/COLOR]

**Project**:
A novel with lots of dialog and thought processes (italicized.) I wanted a hyperlinked Table Of Contents (TOC), an occasional footnote, and a lot of index and nomenclature references (mostly for my own use while writing it.) I didn't want to fight some other word processor for the privilege of formatting it consistently and the way I want it.

**Complication**:
Several advance readers whose feedback I value have no intention of installing or learning Lyx.  Pity. For ease of reading, I wanted ePub and Mobi output, and for collaboration I need MSWord, OpenOffice, and GoogleDoc formatting.  The exports that retained hyperlinks seemed to foul up my paragraphs and indentation and vice-versa.  It was a two-part solution involving "line length" and a search-and-replace within Libre/OpenOffice.

   **Instructions to Publish Online**

  
[LIST]
[*]Save final changes in Lyx 
[*]Clean up working notes
[LIST]
[*]Change end outline (stuff I haven't yet written) into “notes” 
[*]Move index outside of “comment” area, if desired. 
[/LIST]
  
[*]PDF export (I prefer the pdflatex results)
[LIST]
[*]Tools –> Preferences –> Output –> General: Set "line length" to 0 
[*]verify export in okular/Adobe 
[/LIST]
  
[*]HTML export
[LIST]
[*]export –> HTML (not the HTMLs in More Formats) 
[*] verify export in Firefox/Chrome 
[/LIST]
  
[*]Make an Open- or  Libre/OpenOffice Writer doc (ODT)
[LIST]
[*]open the HTML as in Chrome (Firefox doesn't copy hyperlinks right) [(b)]("http://ubuntuforums.org/#enu_verify_HTML"). 
[*]copy all <ctrl>a, then <ctrl>c 
[*]open a new Libre/OpenOffice Writer document 
[*]paste <ctrl>v into the new ODT. 
[*]test hyperlinks (index/TOC) 
[*]replace the paragraph indent formatting (<ctrl>h)
[LIST]
[*]choose “other options” 
[*]choose “search paragraph styles” 
[*]replace “text body” (from the 1[SUP]st[/SUP] drop down list) 
[*]with “first line indent” (2[SUP]nd[/SUP] drop list) 
[*]replace all 
[/LIST]
  
[*]close “Replace” window & test hyperlinks (again) 
[*]carefully verify font consistency (Chrome ain't consistent when pasted into Writer) 
[*]fix paragraph fonts if needed (find/replace)
[LIST]
[*]choose “other options” 
[*]choose “search paragraph styles” 
[*]find “first line indent” (from the 1[SUP]st[/SUP] drop down list) 
[*](2[SUP]nd[/SUP] drop list doesn't matter) 
[*]find all (and leave all “1[SUP]st[/SUP] line indent” paragraphs selected) 
[*]change font name and size to be consistent 
[*]replace all 
[/LIST]
  
[*]save. 
[/LIST]
  
[*]MSWord
[LIST]
[*]open the document from 5 
[*]save as whatever version of MSWord they need (and hope that they have any clue about word versions and intercompatibility…<sigh>) 
[/LIST]
  
[*]GoogleDocs
[LIST]
[*]upload the ODT from 5 to GoogleDocs (1st time) 
[*]or paste all text from ODT into the previous GoogleDoc
[LIST]
[*]select all in ODT <ctrl>a. copy all of ODT <ctrl>c 
[*]select all (previous text) in GoogleDoc <ctrl>a. paste new text in its place <ctrl>v 
[*]pasting long Writer docs into GoogleDocs takes a while. go fix dinner or something. it is, however, potentially faster than re-doing all the shares with your advance readers if you upload the “new” file. (Cut/Paste HTML --> GoogleDoc is faster, but loses more formatting than ODT --> GoogleDoc.) 
[/LIST]
    
[/LIST]
  
[*]Create eBooks
[LIST]
[*]open Calibre 
[*]add booktitle.odt from 5 to the library 
[*]make ePub (Nook, Google, Moon+, iBooks & most other readers)
[LIST]
[*]select the book and click convert individually (right click works too) 
[*]make sure the format choice (upper right) shows EPUB 
[*]verify changes in Google, Nook, Moon+ and iBooks 
[/LIST]
  
[*]convert to Mobi.
[LIST]
[*]select the book and click convert individually (right click works too) 
[*]make sure the format choice (upper right) shows MOBI 
[*]verify changes in Kindle. 
[/LIST]
    
[/LIST]
    
[/LIST]

---

### Post by howefield on 2015-08-10
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by ski_phreak on 2015-08-11
I found text font/size inconsistencies after the ODT find/replace step.  Wow, I miss WordPerfect's powerful reveal- and replace-code features.

The 2nd find-all let's you set a standard format.

I did notice that index hyperlinks don't work as perfectly as I'd like.  I'll keep experimenting till a find a perfect replacement for my dearly departed WordPerfect.

---

