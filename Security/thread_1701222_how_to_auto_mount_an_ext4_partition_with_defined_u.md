---
title: "how to auto mount an ext4 partition with defined user group and mask using fstab?"
date: 2011-03-06
forum: Security
---

### Post by tanoloco on 2011-03-06
Hello,

sorry to bother you with this problem with for many of you gurus might be silly, but I'm still a newbie of linux and I'm completely lost because googling I got so many things but nothing working.

What I have is a device ext4 formatted and I would like to auto mount it at boot.

What I've done is modify fstab adding this line:
```
UUID=c5f7175d-8ebd-498f-aaa2-d8f6dfaecded	/mnt/home	ext4	defaults,users,errors=remount-ro	0	1
```

what I obtain is
```
drwxr-xr-x 3 root root  4096 2011-03-06 13:34 home

```

what I would like to have is
```
drwxrwx--- 3 root users  4096 2011-03-06 13:34 home
```

But how? 
I tried using option like uid, gid, umash, fmask, dmask .. it answers with errors and it seems ext4 doesn't support such options.

I tried changing /etc/profile and /root/.bash_profile but with no luck

Anyone so kind to explain me the right path please?
Thanks in advance for any help

---

### Post by wacky_sung on 2011-03-06
If you are gonna use it on ISO , perhap **[COLOR="Red"][Unetbootin]("http://unetbootin.sourceforge.net/")[/COLOR]** is for you.

FYI: It is a bit buggy that at time you do it a few times before successful.

---

### Post by vanadium on 2011-03-06
Permissions and ownerships are not set through options in /etc/fstab, except for file systems that do not support file permissions, such as ntfs and fat.
Masks are not set on a per directory level. The umask setting determines the default permissions of new files. Only for file systems not supporting file permissions an umask can be specified in /etc/fstab.

---

