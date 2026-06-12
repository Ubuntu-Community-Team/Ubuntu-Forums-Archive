---
title: "Use apt cache as repository"
date: 2007-02-22
forum: Repositories &amp; Backports
---

### Post by ugarth on 2007-02-22
Hi.
My current installation has many apps I use and updates, and almost all of these were installed with apt.
I want to install ubuntu on another pc, and I'd like to use the packages my pc has downloaded, as a repository for the other pc, besides the regular ones.

How can I do this ? Copy over files from one place to another or what ?

---

### Post by zvacet on 2007-02-28
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by mertle on 2007-03-16
I recently (just last night, actually!) used my previous apt cache when doing a fresh install of Kubuntu and didn't need any software or tools, but it's pretty much a low tech workaround. Yes, you can simply copy the files back over to the new apt cache **BUT** for it to work, you need to make sure that all of the repositories you used to get those packages are added to your sources list. Furthermore, do not copy over the 'lock' file nor the 'partial' folder. Just the .deb files.

For example, I had a MUD client package in my apt-cache that I got from a repository other than Ubuntu's, but forgot to add that repository to my sources list after a fresh install... so basically, apt didn't recognize it existed. After I copied all the files over, I tried to run Adept/apt-get and it said there was an error and it closed. All I had to do was make sure that everything in my cache was available when I apt-get update'ed.

If your sources match your packages (and you did an apt-get update), you can then just install as if you were installing a program directly from a repository... just instead of it DLing from the 'net, it picks up the local copy.

Hope this helps. :)

- mertle

---

