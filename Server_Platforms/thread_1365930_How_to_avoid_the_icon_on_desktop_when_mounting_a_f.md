---
title: "How to avoid the icon on desktop when mounting a file"
date: 2009-12-27
forum: Server Platforms
---

### Post by jocampo on 2009-12-27
This is a portion of my fstab

```

#Music on guanabana
guanabana:/home/jocampo/Music	/home/jocampo/Music	nfs	rw	0	0
#Videos on guanabana
guanabana:/home/jocampo/Videos /remote	nfs	rw	0	0

```

So far.. so good... I can see the nfs folders on my local drive(laptop) but for the last 1st one, Music, an Icon on desktop appears; I do not want that icon indicating a mounted file. How can I avoid this behavior and why it is not happening to 2nd one, the one mounted at /remote , because is under root?

Thanks in advance,

PS: forgot to mention, the nfs resides on an Ubuntu server but my laptop or client is running Jaunty with gnome/GUI ...

---

### Post by jocampo on 2009-12-28
Answering myself ..

Found the explanation, posting this links so maybe will help someone else...

[http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/]("http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/")

Also, I forgot that to hide partitions mounted in fstab, I just need to mount them under /mnt/ . If they are mounted elsewhere, the icons show on the desktop.

---

