---
title: "[IDEA] Firefox's GtkFileChooser's Lack of Image Thumbnails"
date: 2007-07-11
forum: Ubuntu Brainstorm
---

### Post by kadath on 2007-07-11
I know a lot of people have different issues with Firefox's open/save/upload dialog (aka "GtkFileChooser").

My particular issue with it, is its lack of a thumbnail preview when navigating folders with images in them. This issue often comes up when attempting to use FF's filechooser to upload images to sites like Imageshack, Photobucket, Flickr, etc. The lack of a thumbnail view causes a lot of wasted time, because one has to open their filemanager, locate the image they want, make note of its filename, and then select the image with FF's filechooser. This is not intuitive, and its a needless hassle.

Now I've heard some people say that this is in fact a problem caused by the GNOME devs, but I believe it's a problem caused by the Linux Firefox devs, because other GTK programs (GIMP, for example) provide an image preview pane using the same GtkFileChooser that Firefox does. Also, people using Firefox on KDE have the same problem. So it seems that Mozilla is at fault in this.

Is it possible for Ubuntu's Firefox package maintainers to patch FF's filechooser to include the thumbnail view option, or perhaps to pressure the Mozilla devs themselves to apply this patch to FF's source code so that everyone can have this feature?

---

### Post by aysiu on 2007-07-11
More info:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381)

---

### Post by kadath on 2007-07-11
> **aysiu said:**
> More info:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/89381)

Excellent, at least it appears to be being worked on. I hope this is fixed soon.

---

### Post by CarpKing on 2007-07-13
I hope so too.  Galeon already has this, if anyone wants to use this in a GTK browser.

---

### Post by aysiu on 2007-07-14
Galeon's pretty close. You have to click on each image to see its thumbnail preview.

In Konqueror, you can enable a thumbnail view that allows you to see previews of all the images in the folder.

---

### Post by kadath on 2007-07-14
> **aysiu said:**
> Galeon's pretty close. You have to click on each image to see its thumbnail preview.

In Konqueror, you can enable a thumbnail view that allows you to see previews of all the images in the folder.

So this is indeed a problem with Firefox itself then, and not GtkFileChooser?

---

### Post by aysiu on 2007-07-14
> **kadath said:**
> So this is indeed a problem with Firefox itself then, and not GtkFileChooser?
Yes... and Epiphany... and Opera (which is odd, since it is a QT application--why doesn't it use the same dialogue as Konqueror?).

---

### Post by GeneralZod on 2007-07-14
> **aysiu said:**
> Yes... and Epiphany... and Opera (which is odd, since it is a QT application--why doesn't it use the same dialogue as Konqueror?).

KDE's file dialogue (the one used by Konqueror) is very different to the stock Qt one.  Presumably, the Opera devs didn't want to add a dependency on kdelibs, so just stuck with the Qt dialogue.

Edit: VVV

No problem :)

---

### Post by aysiu on 2007-07-14
Thanks for the clarification, GeneralZod.

---

### Post by rabid9797 on 2007-09-10
would it be possible for someone to make a small patch for gnome, allowing thumbnail views of photos to be shown in upload windows?(like, uploading a picture to photobucket, i have to find the individual filename in a list instead of just being able to scroll through a list of thumbnails)

ive seen it done before(a makeshift patch for gnome using kde code), and i know its possible since there is obviously a thumbnail view in nautilus, but could it be done?

---

### Post by 23meg on 2007-09-10
Merged.

---

### Post by Nano Geek on 2007-09-10
I think that showing the pic next to the file browser is just the GNOME way of doing it.

---

### Post by rabid9797 on 2007-09-24
> **asjdfwejqrfjcvm msz34rq33 said:**
> I think that showing the pic next to the file browser is just the GNOME way of doing it.


yeah, an incredibly cumbersome and inefficient way of doing it,

bump

---

### Post by yelo3 on 2007-09-24
I think instead that the best way is to implement "icon view" in gtk-filechooser. (a copy-paste from nautilus code?)

---

### Post by rabid9797 on 2007-09-30
bump

---

### Post by 23meg on 2008-01-12
This is fixed in Hardy's Firefox 3.

---

### Post by Jan-Nik on 2008-01-13
[http://bugzilla.gnome.org/show_bug.cgi?id=315207](http://bugzilla.gnome.org/show_bug.cgi?id=315207)

---

