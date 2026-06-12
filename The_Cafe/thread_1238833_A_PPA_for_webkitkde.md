---
title: "A PPA for webkitkde?"
date: 2009-08-12
forum: The Cafe
---

### Post by Ranax on 2009-08-12
I am trying the Webkit backend for Konqueror and generally it works great, except for that it renders some pages like Google searches in a minute font. This appears to be a bug with the webkitkde package that Jaunty has in the repo, so can someone please point me to the appropriate PPA so I can update?

---

### Post by Ranax on 2009-08-13
Bump.

---

### Post by loell on 2009-08-13
probably install kde 4.3 PPA , which may have the latest konqueror?

[http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html]("http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html")

---

### Post by Ranax on 2009-08-13
> **loell said:**
> probably install kde 4.3 PPA , which may have the latest konqueror?

[http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html]("http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html")

Yes I am running 4.3 already :)

The problem is that the webkitkde backend in the repos is an early alpha.

---

### Post by Starlight on 2009-08-13
I'm curious, how did you enable webkit in Konqueror? I've installed all the webkit KDE packages, but I can't find any options related to it in Konqueror :(

---

### Post by Ranax on 2009-08-13
> **Starlight said:**
> I'm curious, how did you enable webkit in Konqueror? I've installed all the webkit KDE packages, but I can't find any options related to it in Konqueror :(

Search for webkitkde in KPackageKit and install it. Then open up Konqueror and goto View >> View More >> Webkit.

---

### Post by Starlight on 2009-08-13
> **Ranax said:**
> Search for webkitkde in KPackageKit and install it. Then open up Konqueror and goto View >> View More >> Webkit.

Thanks for the reply! But it's strange, I installed that package, but there's no "View More" in my Konqueror :( I have KDE 4.3


EDIT: It's ok now, I had to restart KDE and now it's there :)

---

### Post by Ranax on 2009-08-13
> **Starlight said:**
> Thanks for the reply! But it's strange, I installed that package, but there's no "View More" in my Konqueror :( I have KDE 4.3


EDIT: It's ok now, I had to restart KDE and now it's there :)

I didn't have to restart KDE for it to appear :confused:

Are you using 4.2 or 4.3?

---

### Post by Starlight on 2009-08-13
> **Ranax said:**
> I didn't have to restart KDE for it to appear :confused:

Are you using 4.2 or 4.3?
I'm using KDE 4.3 :)

It seems that it wasn't restarting KDE that helped, but going to a different website. For some reason, that option in the menu doesn't appear when I'm looking at the default home page.

---

### Post by Ranax on 2009-08-13
> **Starlight said:**
> I'm using KDE 4.3 :)

It seems that it wasn't restarting KDE that helped, but going to a different website. For some reason, that option in the menu doesn't appear when I'm looking at the default home page.

I see :D

But it still has this issue....

**.::KHTML::.**
[IMG]http://img246.imageshack.us/img246/4580/snapshot31.png[/IMG]

**.::Webkit::.**
[IMG]http://img134.imageshack.us/img134/8999/snapshot30.png[/IMG]

:(

---

### Post by Starlight on 2009-08-13
It's like that on my computer too, but I don't really mind it. :) However, Konqueror seems to switch back to KHTML every time I go to a different website. And with Webkit enabled, it crashes with a segfault quite often. :(

---

### Post by Ranax on 2009-08-13
> **Starlight said:**
> It's like that on my computer too, but I don't really mind it. :) However, Konqueror seems to switch back to KHTML every time I go to a different website. And with Webkit enabled, it crashes with a segfault quite often. :(

That's why I'm trying to find a more up to date version from a PPA! :P

---

### Post by Starlight on 2009-08-13
> **Ranax said:**
> That's why I'm trying to find a more up to date version from a PPA! :P
Maybe there's no newer version yet :P

---

### Post by Ranax on 2009-08-13
> **Starlight said:**
> Maybe there's no newer version yet :P

Don't say that! :(

---

### Post by Starlight on 2009-08-13
> **Ranax said:**
> Don't say that! :(

Well, I hope they are working on it so that it gets better soon. :) It would be good to have a good KDE browser. I love KDE 4.3, but unfortunately the best browsers at the moment are GTK ones, like Firefox and Chromium. It would be nice to have a really good KDE browser. Konqueror is still rather behind these two, but it's getting better and better. Arora also looks promising, but it's still a very early version, without many features...

---

### Post by sertse on 2009-08-13
Opera 10 Beta, Qt4 version. 

It's a full featured proper web browser and integrates with Qt4 (which Kde also uses) nicely.

---

### Post by Ranax on 2009-08-13
> **sertse said:**
> Opera 10 Beta, Qt4 version. 

It's a full featured proper web browser and integrates with Qt4 (which Kde also uses) nicely.

I have already tried it and it didn't work very well, infact I found it worse than Konqueror.

---

### Post by Changturkey on 2009-08-13
I really hope KDE devs give Konqueror some attention for 4.4.

---

### Post by Skripka on 2009-08-13
> **Changturkey said:**
> I really hope KDE devs give Konqueror some attention for 4.4.

They really just need to drop KHTML and use Webkit as the default backend...MOST of Konqueror's web-browsing problems come from the continued default KHTML.

---

### Post by Starlight on 2009-08-14
> **sertse said:**
> Opera 10 Beta, Qt4 version. 

It's a full featured proper web browser and integrates with Qt4 (which Kde also uses) nicely.
I agree, Opera 10 Qt4 version is very good, I use it sometimes. :) But its KDE integration isn't very good. It ignores KDE's color scheme (like the menu bar and selection colors) and its Qt Native skin is unusable and full of weird glitches (the default Opera skin is really good, but it would be nice to be able to make Opera look like other KDE applications). And Opera's file dialogs are different than KDE file dialogs. They have less features, and more bugs (I was just trying to import Firefox's bookmarks to Opera from a HTML file, and Opera's file selection dialog showed the directory with that file as empty, even though that file was there, and the file dialog was set to look for HTML files. What's interesting, when I manually entered "bookmarks.html" in that file dialog, it imported all the bookmarks correctly).


> **Skripka said:**
> They really just need to drop KHTML and use Webkit as the default backend...MOST of Konqueror's web-browsing problems come from the continued default KHTML.

That would be cool :) Some other good things for Konqueror would be to have something like Firefox's Awesomebar, and to fix favicons in bookmarks (in bookmarks imported from Firefox, all their icons are generic HTML icons instead of each site's favicon, even after I open that site).

---

### Post by Ranax on 2009-08-14
> **Starlight said:**
>  That would be cool :) Some other good things for Konqueror would be to have something like Firefox's Awesomebar, and to fix favicons in bookmarks (in bookmarks imported from Firefox, all their icons are generic HTML icons instead of each site's favicon, even after I open that site).

Agreed. :P

---

### Post by dlenmn on 2009-10-09
> **Ranax said:**
> can someone please point me to the appropriate PPA so I can update?

There may have been some updates to the webkitkde package since this was posted, but -- for my own amusment -- I've made a package for karmic from the latest source and put it in [my PPA]("https://launchpad.net/~leon-n-maurer/+archive/ppa"). This is the first time I've made a package, and I don't know the state of the source code (I am in no way associated with the development of the WebKit KPart), so there's the off chance that installing this package will blow up Pittsburgh. However, I followed the [instructions]("https://wiki.ubuntu.com/PackagingGuide/Complete") and the package works on my computer. If there's interest, I can keep this package up to date since no one close to the project is regularly providing new packages.

---

