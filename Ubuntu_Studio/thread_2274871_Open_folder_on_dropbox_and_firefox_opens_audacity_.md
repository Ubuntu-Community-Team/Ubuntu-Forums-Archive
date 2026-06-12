---
title: "Open folder on dropbox and firefox opens audacity instead thunar"
date: 2015-04-23
forum: Ubuntu Studio
---

### Post by cjdg on 2015-04-23
hi i found a strange issue, every i use an application that opens folders to explore like firefox downloads or dropbox always opens audacity or anjuta if is installed, i found this on almost all ubuntustudio 14.10 installations

---

### Post by edelare on 2015-05-07
Hi,

I've not tested with Dropbox, but I'm facing the same behavior when opening the downloads directory from within Firefox download manager, except that it launches Audacious, but that's a detail.
I'm working on Ubuntu Studio 14.04 LTS.

This has never bothered me much, but when I saw your post, I thought I'd look into it, and I think I've found the culprit, although I don't know how to fix it yet.

[B]Looking inside system-wide MIME definitions (Applications menu / Settings Manager / MIME Type Editor), I found that all the "inode/*" MIME types that have their default application field non empty, have it defined to "Audacious" (in my case).
[/B]
Looks completely wrong to me !
Makes me wonder what else may be wrong in the MIME "database" and if someone else has seen some erratic behavior on other system components because of this.

It's to be noted that Chromium doesn't exhibit the same issue, and opens downloads directory without problem. It means that it uses another "method" than Firefox for directory opening.

Well, I'll try to look where this can be fixed, and if a Ubuntu bug needs to be open for it.

---

### Post by denungeherrholm on 2015-06-02
Firefox opened all folders in Audacious for me. But due to some other problem I installed Nautilus, and now Firefox opens folders in Nautilus instead, no matter if I have set Nautilus or Thunar as my default file-browser.

---

### Post by Nosphky on 2015-06-05
Whenever the file manager makes a default choice for a particular file type which does not suit you (and it happens often enough), it is fairly easily fixed.  Right click on the filename, and then hover on "Open with"  then you'll see a choice of application.  If you see the application you want, you can select it here but that probably won't fix the problem.  

A more permanent solution is to go right to the bottom of the list when you "right click/ Open with", and select "Open with other application" .  Scroll down and select the application, make sure the box "use as default for this type of file" is ticked and click "Open".

That usually fixes it for me for further instances of the same type of file.

---

