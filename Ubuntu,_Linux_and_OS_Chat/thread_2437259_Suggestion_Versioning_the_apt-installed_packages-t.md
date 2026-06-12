---
title: "Suggestion: Versioning the apt-installed packages-tree"
date: 2020-02-20
forum: Ubuntu, Linux and OS Chat
---

### Post by nehrhardt88 on 2020-02-20
Hi Guys, in days of fast and also slow disk-drives, i want to make a suggestion:

Wouldnt it be great to have versioning tool for all the dep-packages you have downloaded, and when you broke your package-manager you just switch branch or restore any "commit"?
Maybe its enough to git init in certain folder?

---

### Post by wildmanne39 on 2020-02-20
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

You may be able to contact the [Ubuntu Developers ]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel")

---

### Post by TheFu on 2020-02-22
> **nehrhardt88 said:**
> Hi Guys, in days of fast and also slow disk-drives, i want to make a suggestion:

Wouldnt it be great to have versioning tool for all the dep-packages you have downloaded, and when you broke your package-manager you just switch branch or restore any "commit"?
Maybe its enough to git init in certain folder?

Don't think git works automatically.

I have that.  It is called "a versioned backup." Very handy for all sorts of things, not just accidentally removed, corrupted, files.

People want to invent some slick new tool that accomplishes the same things that proper backups accomplish.  My backups include a list of the currently installed software packages on the machine.  Just run **dpkg -l** to see yours. Redirect that output to a file and include that data in your daily backups.  Refresh the list as part of the backup cron-job and it wll always be there for you.

Some other files created daily just before backups run:
```
/root/backup# ls
apt-mark.auto    blkid.txt     df.txt       log.rereinstall  pvdisplay.txt
apt-mark.manual  crontab.tf    dpkg.list    lshw.list        vgdisplay.txt
auto.list        crontab.root  dpkg-l.list  lvdisplay.txt
```

---

