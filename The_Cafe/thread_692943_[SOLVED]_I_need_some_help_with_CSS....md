---
title: "[SOLVED] I need some help with CSS..."
date: 2008-02-10
forum: The Cafe
---

### Post by diablo75 on 2008-02-10
I am currently building a website based upon this template:

[http://www.oswd.org/design/preview/id/3559](http://www.oswd.org/design/preview/id/3559)

The website I'm making is here:

[http://www.davestechsupport.com/habitatdraft](http://www.davestechsupport.com/habitatdraft)

I know enough HTML to be able to find some problems in the code if there is one, but I know almost nothing about CSS.

All I want to do is be able to insert an image without the CSS automatically adding a 1 pixel thick brown border.  I like the border on most images, but for some things (like a gif of a button with rounded corners), I don't want an added border.  Thanks for the help in advanced!!

---

### Post by ~LoKe on 2008-02-10
.nopx { border: 0; }

<img class="nopx" src="path/to/image.gif" />

---

### Post by diablo75 on 2008-02-10
Excellent help!  Thank you very much!

---

### Post by mmiller73 on 2008-02-10
The following style will remove any borders around images:

img {
  border: 0;
}

---

### Post by Washer on 2008-02-10
I divide my website making experience into two parts. The period before I discovered firebug & the period after I discovered firebug.

---

