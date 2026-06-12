---
title: "USB device in Wine, patch applicable ?"
date: 2010-09-14
forum: Wine
---

### Post by bdutta on 2010-09-14
Hi,

My intent is to use a certain USB device in a Windows application, via Wine. I am running Ubuntu 9.10, and got the stock Wine via PPA, installed thru the Ubuntu Software Manager. 

$ wine --version
wine-1.0.1

Now, that version of Wine seems pretty old, given that we have active development on 1.2 and 1.3 ! Could someone confirm this ?

On searching, found this link [http://wiki.winehq.org/USB](http://wiki.winehq.org/USB) on the support of USB in Wine, which looked quite promising. What I am unable to find is information on whether this patch (originally made for 1.1 and later someone ported it to 1.2) is already rolled into the version I am running, or may be able to upgrade to. Will it help to move to 1.2/1.3 ? My interest is USB support, as barring that, most other things that I run on Wine, seem to work fine.

I've added, the Wine PPA to apt.sources, and run "apt-get update", but wasn't offered to upgrade Wine. If I need to go to 1.2/1.3, would I have to do "apt-get install wine1.2" ? Can Wine-1.2 coexist with Wine-1.0.1, s.t. if certain other things are broken on 1.2, I can quickly fallback on 1.0.1 ?

Help / pointers are appreciated.

regards,
BD

---

