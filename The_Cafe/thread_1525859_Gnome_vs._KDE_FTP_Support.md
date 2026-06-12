---
title: "Gnome vs. KDE: FTP Support"
date: 2010-07-07
forum: The Cafe
---

### Post by aaaantoine on 2010-07-07
So I'm running two platforms at the moment: my desktop runs Ubuntu 10.04, and my laptop runs Arch Linux & KDEmod.

One of the things that I remember pushing me over the edge and trying out Arch for the first time -- back when I only had one computer that I could tinker with -- was that in 8.04 and 8.10, out-of-the-box FTP support was crap in Ubuntu.  Trying it now, it's gotten better.  Before, if I opened files in gedit over FTP, they would open in read-only mode.  Now, I can edit files in place using gedit, which is handy.

The reason I had switched to KDE was not only because of how Kate could handle editing FTP files in place, but the whole FTP experience was less of a hassle.  Some problems still persist in the Gnome desktop environment, which is why I write this post.

- I just tried opening a site in Nautilus, and kept getting an error about the directory not existing.  So I installed Dolphin, and using that I opened the directory just fine.  
- Numerous times while trying to open files I get some error about how the file could not be opened.  Kate isn't perfect in this regard as it also sometimes fails to load, but at least it doesn't immediately close the document window without allowing you a quick refresh.
- Kate rarely has a problem saving files, while gEdit almost always fails if the connection is idle for more than a few minutes.  But, it works when you try a second or third time afterward.

Without knowing any of the details, the behavior is as if gvfs is trying to keep the connection alive at all times, while KDE's file system only connects when prompted.

Thoughts?

(Put this in Recurring Discussions if you want, but I'm trying to at least focus on a single aspect of the G v. K debate.)

---

### Post by RiceMonster on 2010-07-07
Interestingly enough I found network browsing via SSH was a lot better in Nautilus than in Dolphin (inwhich it kept erroring out). The only way I could get it to work properly with Dolphin was to mount the remote directory with sshfs and then browse to it in Dolphin.

---

### Post by Paqman on 2010-07-07
I actually almost always use Nautilus for FTP access these days. The only thing i've found that annoys me about it is that it won't do permissions.

---

### Post by nrs on 2010-07-07
I think a lot of it has to do with the fact that Qt/KDE libraries are tightly integrated. A lot of GNOME/GTK+ stuff is third party + optional. 

As an example I think if you're using KDElibs you automatically have KIO/kParts (which is what enables this) support, but if you're developing a GNOME application you specifically have to include GVFS and design your app around it. It's the same with spell checking AFAIK. 

It isn't just limited to this. Certain functionality is available across ***ALL*** KDE applications. Like the ability to customize shortcuts, toolbars, switch application language, etc. Whereas with GNOME / GTK+ these are all individual.

---

### Post by Johnsie on 2010-07-07
ftp is an outdated and insecure protocol. People should really be using encrypted protocols like scp.

---

### Post by aaaantoine on 2010-07-07
Good point.  But how does SCP or SFTP work over Gnome and KDE apps compared to FTP?

---

### Post by YeOK on 2010-07-07
I use Gnome and nautilus to connect to servers all the time, I dropped FTP ages ago and simply use the ssh server. 

Works perfectly well for me. One of my favorite features in Linux / Gnome.

---

### Post by aaaantoine on 2010-07-09
Using KDE at the moment, I notice that it sends login info every time I visit a new folder in Dolphin.  Hence there is a noticeable tradeoff between the Gnome method and the KDE method.

In Gnome, if you visit a new folder, and your session is still alive, opening that folder is near instantaneous.  The tradeoff, however, is that it will fail more frequently.  Whereas in KDE, if you visit a new folder, it takes a second to reconnect, *then* downloads the listing.  This approach is more cumbersome, but more stable.

---

