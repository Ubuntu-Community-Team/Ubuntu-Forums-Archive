---
title: "Mozilla Firefox bug in Linux?"
date: 2005-05-22
forum: The Cafe
---

### Post by jiyuu0 on 2005-05-22
Mozilla Firefox in Windows
[img]http://myosc.org/jiyuu0/firefox_windows.jpg[/img] 

Mozilla Firefox in Linux
[img]http://myosc.org/jiyuu0/firefox_linux.jpg[/img] 

In Firefox Linux, the bottom part seems to be white. It is suppose to be brownish (see the correct colour of the page in Firefox Windows)

Temporary solution: Firefox Linux will show the correct colour if I press the arrow key up and then down

I thought this is a coding problem of the page, but after some testing, I've found out that Firefox Linux seems to have limitation in page length or something. If I shorten the page... then the colour would appear ok.

This problem only occur in Firefox Linux but not Firefox Windows.

Is this bug?

---

### Post by SparkyDawg on 2005-05-22
No, not a bug, your theme is just white.

---

### Post by jiyuu0 on 2005-05-22
[QUOTE=SparkyDawg]No, not a bug, your theme is just white.[/QUOTE]

but why is firefox in windows showing correctly?

---

### Post by HungSquirrel on 2005-05-22
[QUOTE=SparkyDawg]No, not a bug, your theme is just white.[/QUOTE]
 If you scroll up from the area in question using the arrow keys (as the post said), the area is redrawn in the correct color.  I think it's a rendering engine bug.  The page passes W3C's markup checks, so it's probably not a case of bad page design.  Besides, the poster notices different behavior in Linux and Windows.

---

### Post by jiyuu0 on 2005-05-22
reported to bugzilla

[https://bugzilla.mozilla.org/show_bug.cgi?id=295102](https://bugzilla.mozilla.org/show_bug.cgi?id=295102)

---

