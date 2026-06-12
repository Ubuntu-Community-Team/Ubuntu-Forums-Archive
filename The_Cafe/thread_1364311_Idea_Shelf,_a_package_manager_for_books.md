---
title: "Idea: Shelf, a package manager for books"
date: 2009-12-25
forum: The Cafe
---

### Post by PacSci on 2009-12-25
There's a bunch of nice "open source" (CC, GFDL, etc.) books out there, like Dive Into Python, the Mercurial book, and of course various documentation. Downloading them could be kind of annoying, so I came up with an idea - Shelf, a package manager for books. The basic idea is that a book maintainer would write a "card catalog" file for a book, maybe something like this:

```
identifier: diveintopython
title: "Dive Into Python"
author: "Mark Pilgrim"
description: "A Python book for experienced programmers."
synopsis: >
  ...some text...
available in: [pdf, html]
pdf:
  url: "http://diveintopython.org/download/diveintopython-pdf-5.4.zip"
  archive file: diveintopython5.4/diveintopython.pdf
# and so on...

```

Then, you would run a command like 'shelf-get --card diveintopython.card' to download the book and extract the zip file. Then, when you wanted to read it, 'shelf-read diveintopython' would open the book in the PDF reader, or the Web browser if you downloaded the HTML edition.

---

### Post by Bachstelze on 2009-12-25
```
sudo apt-get install diveintopython
```

It installs the HTML version IIRC. Feel free to make a [font=monospace]diveintopython-pdf[/font] package and submit it.

---

### Post by Mr. Picklesworth on 2009-12-25
The new Software Centre runs as a normal user, with installation handled with PolicyKit and APT daemon. I don't think anyone has really pondered it, but you're right: we already have a lot of content packages like books, artwork and code documentation that should be handled differently since they are things individual users may be immediately interested in. Since the relevant tools for finding those packages are now running as the current user, that seems like something fairly reasonable to implement :)

It could either go ahead downloading the package to the system-wide place in the root directory and then add a link to it in some kind of content manager (or just the user's Documents folder), or it could go a bit further by actually unpacking the package to a place of the user's own choosing (although that may need some changes to the format / packaging guidelines).

---

