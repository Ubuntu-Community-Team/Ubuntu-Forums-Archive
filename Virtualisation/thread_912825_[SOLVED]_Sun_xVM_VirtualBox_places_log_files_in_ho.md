---
title: "[SOLVED] Sun xVM VirtualBox places log files in home directory"
date: 2008-09-07
forum: Virtualisation
---

### Post by terrorsathan on 2008-09-07
-

---

### Post by rapolas on 2008-09-07
I have the same issue, didn't manage to solve it..

---

### Post by insane_alien on 2008-09-07
you could always set up a cron job to periodically wipe everything out your home folder with 'virtualbox' and 'log' in the file name.

---

### Post by Pom2122 on 2008-09-07
This was fixed in the 1.6.6 and 2.0.0 releases. (The 2.0.0 release also allows 64 bit guests, although it does have a few glitches. I currently have a 64 bit Ubuntu installed as a guest :))

---

### Post by terrorsathan on 2008-09-07
-

---

### Post by expatal on 2008-09-07
[QUOTE=terrorsathan;5742920]Hi,

I'm using Sun's xVM VirtualBox v1.6.4 on Ubuntu 7.10 and every time I start a virtual machine a log file similar to "2008-09-06-11-16-46.031-VirtualBox-6819.log" is created, placed in my home directory /home/username.

--->Please ignore above!!! (Newbie-related posting difficulties)

---

### Post by expatal on 2008-09-07
> **terrorsathan said:**
> Hi,

I'm using Sun's xVM VirtualBox v1.6.4 on Ubuntu 7.10 and every time I start a virtual machine a log file similar to "2008-09-06-11-16-46.031-VirtualBox-6819.log" is created, placed in my home directory /home/username.


The following solution (for those too lazy like myself to install a later version) seems to work for some. Apparently the bug (developer forgot to switch off debug logging in release version) can be worked around by inserting the following line in your shell startup script (e.g. ~/.bashrc):

```

export VBOX_LOG_DEST=nofile

```

I haven't yet had time to check it out yet. See post:
[http://forums.virtualbox.org/viewtopic.php?t=8917&highlight=log+files&sid=02134224457c3e50b4919aef9e197e3b]("http://forums.virtualbox.org/viewtopic.php?t=8917&highlight=log+files&sid=02134224457c3e50b4919aef9e197e3b")

---

