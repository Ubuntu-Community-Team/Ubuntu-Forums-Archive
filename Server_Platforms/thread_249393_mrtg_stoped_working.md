---
title: "mrtg stoped working"
date: 2006-09-02
forum: Server Platforms
---

### Post by narrowband on 2006-09-02
MRTG stoped graphing at 12:00 after a rebbot.  I'm now getting the following error:- ERROR: Creating templock /var/lock/mrtg/_etc_mrtg.cfg_l_3922: No such file or directory at /usr/bin/mrtg line 1645. Can anyone help?

---

### Post by narrowband on 2006-09-02
Fixed using the following steps:-

1) sudo apt-get remove mrtg
2) sudo apt-get install mrtg
3) sudo env LANG=C /usr/bin/mrtg /etc/mrtg.cfg

But will I have to do this everytime I reboot the server?

---

### Post by Fabio Pedretti on 2006-09-07
I am having the same problem: seems that directory /var/lock/mrtg got removed when the server reboot.
I added a mkdir /var/lock/mrtg in a boot script and that worked.

Edit: a bug has been already filed and fixed here:
[https://launchpad.net/distros/ubuntu/+source/mrtg/+bug/30428](https://launchpad.net/distros/ubuntu/+source/mrtg/+bug/30428)
However current mrtg is yet not fixed.

---

### Post by narrowband on 2006-09-07
Thanks, I'll read the page you've linked when I have the time.  I haven't rebooted my server since so I hadn't discovered that the directory would dissapear every reboot.

---

