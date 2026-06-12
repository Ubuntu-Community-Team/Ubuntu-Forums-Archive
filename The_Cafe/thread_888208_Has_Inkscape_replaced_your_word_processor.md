---
title: "Has Inkscape replaced your word processor?"
date: 2008-08-12
forum: The Cafe
---

### Post by Mr. Picklesworth on 2008-08-12
This is disappointing and fascinating at the same time...
Today I was tasked with adding a raster image to a PDF file. We did not have the source files.

"Easy", I thought! Just download OpenOffice 3 since it has a PDF import extension, import it and edit it within OpenOffice. A long tale of half-missing 64-bit support led to deep frustration, (I admit the jury is still out there) at which point I switched to KWord. KWord imported the file... and it came out blank. This is normally a very colourful PDF with lots of writing.

Some muttering, mumbling and feeble attempts to get OO working somehow led me to Inkscape. It opened the PDF without stumbling. Everything looked exactly right, and all the structure was intact.

I did some more fiddling, this time with GIMP, to get the logo (a raster image with white background!) fitting into the PDF. Every attempt led to aliasing and resizing was hopeless.
...Then I remembered Inkscape's Trace Bitmap function. I dumped the image into that, set it to layer my vectors by colour (4 colours)... and it was done -- WORKING perfectly -- in seconds. White background was removed, flawlessly and with no aliasing because the lines making up the actual logo simply became traced green coloured paths. The logo went from looking awful to looking beautiful, all automatically.

The final output looked just like before and had a smaller file size.

This served as a powerful reminder to me that should enhance my future productivity by an order of magnitude: Big office suites with word processors are almost universally useless. For charts and tables, I can use a spreadsheet. For letters, a simple text editor with spell check never fails. Alternatively, something simpler than Microsoft Office, at least, like Abiword -- also an ideal candidate for big documents since it has a more streamlined interface, designed so that the user follows a single path towards producing a document instead of there being a million conflicting ways to do so. (One can argue that MS Office is better at making big documents organized, but one has to hunt deeper than its interface's obvious to find out how -- often the time he learns the correct way is too late). It can also be argued that LaTeX is superior to all of those, since it properly keeps formatting out of the way while still doing it...

For producing any kind of flashy printed document, what we need is clearly not a "word processor", but Inkscape with a publishing focus. (Eg: More prominent text tool and multiple pages).
It has clearly succeeded where all others have failed: It does the right thing without hesitation.

---

### Post by mrgnash on 2008-08-12
Uhhhh no... I don't use a 'word processor' as such, but that's because I use LaTeX. Inkscape is not an adequate replacement.

---

### Post by eilu on 2008-08-12
very nice, creative solution. Just a thought though, won't Scribus be a more appropriate word processor replacement (seems to fit the "Inkscape with a publishing focus" description)? But I guess it depends on your needs. In my case the OOo Writer + Bibus combo is adequate for thesis & research writing, and plain text files for quick notes.

would keep this method in mind though, should I face a similar problem in the future (which is quite likely)

---

### Post by cardinals_fan on 2008-08-13
Vim replaced my word processor a long time ago :)

---

### Post by mrgnash on 2008-08-13
> **cardinals_fan said:**
> Vim replaced my word processor a long time ago :)

As well it should have :P

Vim FTW.

---

### Post by brunovecchi on 2008-08-13
I agree with your general concept of de-bundling the office workflow. But here's my personal pick:

for quick-and-dirty data analysis: gnumeric
for serious data analysis: perl
for graphs: gnuplot
for presentations: LaTeX's beamer class
for non-collaborative reports: LaTeX
for collaborative reports: Google Docs.

---

