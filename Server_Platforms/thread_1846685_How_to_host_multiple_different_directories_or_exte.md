---
title: "How to host multiple different directories or external HDDs via FTP?"
date: 2011-09-19
forum: Server Platforms
---

### Post by ThunderKid Zero on 2011-09-19
Hi everyone, the title pretty much says it all.
I use proftpd server to host my files (Gadmin). I can set the directory which the user can access. But how can I set that the user can access a external hard drive/a completely different folder? I tried creating a "main" folder and adding links ("ln -s /media/myHDD /home/myuser/main/blabla") to the external drives, but I'm not able to cd into them from another computer... I haven't tried if it works with the folders yet though... 

Anyone knows what to do?
Thanks a lot!

---

### Post by zackwasa on 2011-09-19
Try this link:
[http://www.proftpd.org/docs/howto/Chroot.html](http://www.proftpd.org/docs/howto/Chroot.html)

It explains how to use symlinks with chroot jails

---

### Post by ThunderKid Zero on 2011-09-19
hmm nice thought, but does this work with gadmin-proftpd (GUI of proftpd)? I use virtual users only. Any way to come around this? actually, I have never checked the GUI properly, maybe there is something that enables this...

---

### Post by zackwasa on 2011-09-20
Why use a GUI if you can just edit config files?

---

