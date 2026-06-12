---
title: "Duplicate device icons on desktop?"
date: 2012-09-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mips on 2012-09-05
I did a netinstall of 12.10 amd64 + xfce4.

Problem is I have multiple instances of the same devices (hdds/partitions) displayed on the desktop.

Secondly these devices appear under /media/<username>/ which I'm not sure is correct? I can't browse them under that folder either as I get "permission denied"

```
<username>@obelix:~$ ls -l /media/
total 8
lrwxrwxrwx   1 root root    7 Sep  4 23:33 floppy -> floppy0
drwxr-xr-x   2 root root 4096 Sep  4 23:33 floppy0
drwxr-x---+ 16 root root 4096 Sep  5 17:10 <username>

```

```
<username>@obelix:~$ ls -l /media/<username>
total 56
drwx------ 2 root root 4096 Sep  5 10:55 160GB_WD
drwx------ 2 root root 4096 Sep  5 13:23 160GB_WD1
drwx------ 2 root root 4096 Sep  5 14:29 160GB_WD2
drwx------ 2 root root 4096 Sep  5 02:43 500GB_SG
drwx------ 2 root root 4096 Sep  5 10:55 500GB_SG1
drwx------ 2 root root 4096 Sep  5 13:23 500GB_SG2
drwx------ 2 root root 4096 Sep  5 14:29 500GB_SG3
drwx------ 2 root root 4096 Sep  5 02:44 500GB_WD
drwx------ 2 root root 4096 Sep  5 10:55 500GB_WD1
drwx------ 2 root root 4096 Sep  5 13:23 500GB_WD2
drwx------ 2 root root 4096 Sep  5 14:28 500GB_WD3
drwx------ 2 root root 4096 Sep  5 15:25 500GB_WD4
drwx------ 2 root root 4096 Sep  5 17:10 500GB_WD5
drwx------ 2 root root 4096 Sep  5 14:29 A4AE5922AE58EE74

```

Image, click for larger version,
[[img]http://ompldr.org/tZmRoMQ[/img]](http://ompldr.org/vZmRoMQ)

---

### Post by dino99 on 2012-09-05
have you made some cleaning ?
(autoremove, gtkorphan, bleachit)

or rename (delete) : .gconf, .local, .gnome2, .config
(they will be recreated cleanly on next reboot)

---

### Post by Elfy on 2012-09-05
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375)

[https://bugs.launchpad.net/ubuntu/+source/xfce4/+bug/1044896](https://bugs.launchpad.net/ubuntu/+source/xfce4/+bug/1044896)

Got the same here.

This appeared a while ago and has not been seen to.

---

### Post by mips on 2012-09-05
> **dino99 said:**
> 
or rename (delete) : .gconf, .local, .gnome2, .config
(they will be recreated cleanly on next reboot)

First thing I tried was deleting config files for xfce, thunar etc. No go, still the same on a reboot.


> **Elfy said:**
> [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375)

[https://bugs.launchpad.net/ubuntu/+source/xfce4/+bug/1044896](https://bugs.launchpad.net/ubuntu/+source/xfce4/+bug/1044896)

Got the same here.

This appeared a while ago and has not been seen to.

At least now I know I'm not alone and it's not something I did. Thanks for the links.

---

### Post by mc4man on 2012-09-05
While there is no [love lost between dev's of FM's other than nautilus & udisks2]("http://igurublog.wordpress.com/2012/04/06/spacefm-udev/") in this case likely a change in gvfs* between 1.13.3-0ubuntu2 & 1.13.7*
I'm using gnome/nautilus but have pcmanfm installed for root browsing  where the duped icons are seen in the sidebar with the current gvfs source. A relatively quick test shows that downgrading to the 1.13.3 source packages removes the duped icons. The whole process is a bit of a pita but it could be narrowed down by trying the package sets between there & current - there are 7 in total

=======================================================================
Currently there is an issue in udisks2 that causes mount dir.'s to be left behind when restarting with volumes still mounted, not related to non nautilus FM duping but accounts for all the dir.'s mentioned in one of the bug reports

---

### Post by mips on 2012-09-05
mc4man hope you don't mind but I updated [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375) with the info you posted.

---

### Post by mc4man on 2012-09-05
As it turns out the very next release of gvfs produces the duped icons - gvfs_1.13.4-0ubuntu1

It is a 'new upstream' release so nothing too visible in the change log.
Could turn out that the various Fm dev's will have to adjust or maybe something in gvfs though it doesn't occur in nautilus (not unexpected

Edit: worth noting that the bug Elfy files was on 08/21 which certainly predates the upgrade to 1.13.4 on 09/02 so thunar may have other issues than seen here with pcmanfm

Re-edit
While installing/running thunar on my install can't totally reflect a Xubuntu install, (thunar seems confused as to my theme, ect. & running it in gnome) see single sidebar items with 1.13.3 & doubled with 1.13.4
This is with the current udisks2 packages

---

### Post by ventrical on 2012-09-08
Got the same here with current updated xubuntu desktop. Floppydisk, floppydisk,floppy disk .. etc..

---

### Post by fedleo on 2012-09-12
> **ventrical said:**
> Got the same here with current updated xubuntu desktop. Floppydisk, floppydisk,floppy disk .. etc..Little crossposting: [http://ubuntuforums.org/newreply.php?do=newreply&p=12233686](http://ubuntuforums.org/newreply.php?do=newreply&p=12233686)

Same problem. Already subscribed for this bug in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375").

---

