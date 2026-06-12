---
title: "How to get image of Server"
date: 2011-02-23
forum: Server Platforms
---

### Post by Farrukhjon on 2011-02-23
Hi! guro of Ubuntu Server, Who can recomend me how to get image of server with  all configuration files and data. Without  data loss.
Thanks in advance!

---

### Post by HermanAB on 2011-02-23
Well, clonezilla, dd or even cat can do that easily, but usually there is not much point in doing so.

On Linux systems, it is sufficient to backup your data only and when disaster strikes, you simply re-install the latest and greatest version of Linux, since re-installing is much easier and faster (20 minutes or so) than copying a gigantic whole disk image from backup (hours).

---

### Post by mnerobi15 on 2011-02-23
Hi,

Use Flyback, I do it's great and in the repositories. Use the link below  to access a tutorial and install it exactly as they say and you are  away. It even copes with saving to external drives and only saves  changed files top save on space.

---

### Post by Farrukhjon on 2011-02-23
Thanks!!!

---

### Post by Farrukhjon on 2011-02-23
[SIZE=3]How about SystemRescueCd do any try it,  is this the best way [http://martybugs.net/linux/image.cgi](http://martybugs.net/linux/image.cgi) ?[/SIZE]

---

### Post by HermanAB on 2011-02-23
If you just want backups, then rsync is your friend and almost all backup programs use rsync down below, ferinstance:
Deja Dup
Back in Time
Grsync
Rbackup
Dervish
Flyback
...
They all do basically the same thing.

...or you can make your very own one line rsync backup script like everybody else does.

---

