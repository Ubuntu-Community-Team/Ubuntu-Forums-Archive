---
title: "[SOLVED] How does pdftotext work?"
date: 2015-02-21
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-02-21
I've used **pdftotext** from the software center quite a few times. I think it's a great asset. I'm curious to know how it works its magic. I use it with "regular" pdf files such as bank statements with the **-layout** option. Then, getting the data into a spreadsheet needs a little work but not much.

---

### Post by TheFu on 2015-02-21
Well created PDF has text and standard fonts inside it. Provided that the PDF isn't based on images or Adobe Type-3 fonts, it doesn't take that much to dump the text out.  Adobe has published the PDF standards for many years - with those, it is possible to create a file parser.  In the mid-90s, I worked on a team that did exactly that.  If you look at postscript files, you'll see that PDF and PS are closely related - they are both page layout languages.

---

### Post by vasa1 on 2015-02-21
Thanks for explaining :)

Now it makes sense why ghostscript can be used to manipulate pdf files.

---

