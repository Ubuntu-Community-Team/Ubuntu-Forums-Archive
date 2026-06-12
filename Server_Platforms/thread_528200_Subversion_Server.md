---
title: "Subversion Server"
date: 2007-08-17
forum: Server Platforms
---

### Post by infinitezero on 2007-08-17
I am trying to setup a subversion server without Apache (not looking for  http access). I want to have the server on my box and the client on the other users systems. Is there a easy howto on getting that setup?



Thanks,
iz

---

### Post by 10drill on 2007-08-19
This covers 5 access methods:

[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

---

### Post by PimpDaddyA on 2007-08-19
Follow-up question (I have a similar issue) - the information on the 5 access methods is part of it but there's one other thing:

I'm using Ubuntu Edgy server edition.  Is there a "correct" way to launch a svnserve daemon at boot time?  Something ubuntu-esque or debian-esque?

For instance, my system doesn't seem to have an inittab, or an xinetd.conf (assuming those would be relevant to my issue.)

I could:
1) emulate the apache2 setup, since _that's_ working OK
2) fiddle with stuff in /etc/rc5.d

Where might I find information about how best do this?

TIA for any help.

---

### Post by leefw on 2007-11-25
Hi

I'm in the situation. Did you find a good (tidy) solution for automatic subversion server start at boot time?

Regards
Lee Francis

---

### Post by crouton on 2007-11-29
update-rc.d will do what you want.  I suggest reading 'man update-rc.d' for details on the various options.

---

### Post by leefw on 2007-11-30
Thanks for the tip. I found a lot of what I needed at [http://eightpence.com/a-subversion-initd-script-for-ubuntu-linux/](http://eightpence.com/a-subversion-initd-script-for-ubuntu-linux/)

---

