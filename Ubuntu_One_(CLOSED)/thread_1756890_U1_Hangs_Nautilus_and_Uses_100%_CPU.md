---
title: "U1 Hangs Nautilus and Uses 100% CPU"
date: 2011-05-12
forum: Ubuntu One (CLOSED)
---

### Post by tekstr1der on 2011-05-12
As the title suggests, U1 client hangs with:

```
File Sync error. (org.freedesktop.DBus.Error.NoReply:
Message did not receive a reply (timeout by message bus))
```


Apparently, I am suffering from this bug:
[https://bugs.launchpad.net/ubuntuone-client/+bug/776386](https://bugs.launchpad.net/ubuntuone-client/+bug/776386)

What I find particularly strange is there has been no update recently related to the U1 client. I am guessing this may be a server issue, but it seems that only a few of us are affected currently

Until this is resolved, I can no longer use ubuntu one. Pretty much a show-stopper as I rely on it regularly. 

Anyone else affected by this?

---

### Post by tekstr1der on 2011-05-16
After following joshuahoover's U1 reinstallation instructions here:
[http://ubuntuforums.org/showpost.php?p=8146023&postcount=2](http://ubuntuforums.org/showpost.php?p=8146023&postcount=2)

...I still have the same issue as soon as I sign in. Nautilus hangs and CPU is 100% until session terminates. There's been no activity on the bug report and no response here. 

Ubuntuone is completely unusable.

Anyone else having this issue?

Any suggestions?

---

### Post by tekstr1der on 2011-05-18
Simply deleting all ubuntuone local folders from my ~/ has resolved this for me.

```

$ rm -rf ~/.local/share/ubuntuone
$ rm -rf ~/.cache/ubuntuone
$ rm -rf ~/.config/ubuntuone
$ mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/
```

---

### Post by hamiljf on 2012-03-13
No idea if this is the same problem, or solution, or whether I've permanently damaged my system.  But finding nautilus consuming 100% CPU for minutes on end I used it to rename 'Ubuntu One' and cut and paste the other three directories (with appropriate new names) into the renamed directory.  If there's nothing further from me, it worked.  Using 11.10 with Gnome Classic, but also Kontact (too much stuff to migrate out I'm afraid).

---

### Post by screaminj3sus on 2013-01-29
I have this problem too, at random ubuntu one stops being able to sync, and rapes my nautilus cpu usage whenever I try to open the home folder. When this happens if I open U1 I get "IPCError". If I reboot it starts working again, for a time.

---

