---
title: "Rotate all pages in a pdf"
date: 2013-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by foberle on 2013-04-27
Hi:

Not sure if this is the right place to ask this, but here goes anyway ...

I have several pdf documents and I would like to regenerate them with all of the pages rotated 90 degrees (and of course with the page aspect ratio changed as well). Can anyone recommend any free utility (either command line or GUI is ok) that will allow me to accomplish this?

Thanks much.

---

### Post by entropy1 on 2013-04-27
I like pdftk.  It's in the repositories.  See also [http://www.pdflabs.com/docs/pdftk-cli-examples/]("http://www.pdflabs.com/docs/pdftk-cli-examples/")

---

### Post by foberle on 2013-04-29
Thanks much; pdftk did the trick (and quite quickly I might add), although I should point out that the syntax for doing page rotations seems to have changed from what's shown on the page you provided the link for - specifically capital letters are required for the direction of rotation (e.g. I had to use "1-endE" rather than "1-endeast"). Luckily the man file seems to have been updated. (I haven't yet tried any other commands, by the way).

In the software center, there is also a GUI called pdfChain that's a front end for pdftk; it had sort of mixed reviews, but it didn't have any facility for supporting page rotation and appears to be for just the basics of pdftk. I mention this just in case others are looking for pdf manipulation tools.

Frank

---

