---
title: "Creating AppImages"
date: 2016-07-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Chanath on 2016-07-09
Hope I am not hijacking this thread.
I was trying to understand the philosophy behind snaps and was trying to learn how to create a snap. I also didn't want the snap package to be larger than the original package, well maybe just a bit. I couldn't (much) understand how to create the snap, so for quite a while, I stopped thinking of having portable apps.

Few days ago, I thought of learning again how to create portable apps, and found AppImage. Created the Libreoffice 5.2.0.1 portable app from downloaded straight from the Libreoffice deb.tar.gz file. The resultant file is 256.8MB. Tried it in Ubuntu (2 flavours), Debian (Jessie, Testing) and Devuan (Jessie and Testing). Works without a problem. Have it also is in a USB stick. Works from that too. [IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Edit: The screeny below is with 3 portable apps, Firefox 47, Leafpad and Libreoffice on a ubuntu 16..04 based live iso.

[ATTACH=CONFIG]270030[/ATTACH]

---

### Post by vasa1 on 2016-07-09
Split off from [Testing deb apps converted to snap apps on Ubuntu & flavours]("http://ubuntuforums.org/showthread.php?t=2327088") so that that thread can stay focused on snaps.

---

### Post by grahammechanical on 2016-07-09
If this is to be a discussion on the technical differences between Appimages, Flatpak and Snap packaging, then leave me out. Likewise, if it is to be a "which is best" kind of discussion.

There is a snap of Libreoffice 5.2 beta. It is 287 MB in size. I have it working on Ubuntu. Things will get better for each of these candidates for a different way of delivering applications. What is important is that there is no locking out or locking in.

Do Appimage applications run in containment? I Think that running apps in containers of some sort a necessary precaution against malware that will become more important as Linux becomes more popular and the traditional sources of revenue for malware writers becomes less & less.

Regards.

---

### Post by user1397 on 2016-07-10
I haven't yet tried to package anything into a snap, flatpak, or appimage, but so far from what I read about AppImage it seems pretty awesome.  Says so right on its homepage how sandboxing can be implemented with other tools like firejail so that seems to not be a disadvantage of AppImages.  The only thing that remains unclear to me is how they are updated exactly.  Snaps have the advantage of transactional/atomic upgrades but I'm not sure (yet) how AppImages upgrade themselves (if at all).  No clue how flatpak does upgrades but I imagine they're similar to snaps?

Either way, I think all the hype is dumb.  Way too early to tell about any of these (though AppImage has been around far longer than the other 2).  Interesting though to find out and discuss the technical differences between them (probably the only constructive thing to do at this point when it comes to these "debates").  Facts, people, facts!

Cheers!

---

### Post by Chanath on 2016-07-10
> **grahammechanical said:**
> If this is to be a discussion on the technical differences between Appimages, Flatpak and Snap packaging, then leave me out. Likewise, if it is to be a "which is best" kind of discussion. 

No!

> There is a snap of Libreoffice 5.2 beta. It is 287 MB in size. I have it working on Ubuntu. Things will get better for each of these candidates for a different way of delivering applications. What is important is that there is no locking out or locking in.

I am interested in creating self-contained apps, so I be trying to find out how to do snaps. If you (anyone) do, could you please write about in the other thread? Would be appreciated!

---

