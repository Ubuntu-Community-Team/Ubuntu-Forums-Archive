---
title: "Plymouth discovering network message"
date: 2011-10-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2011-10-21
now we have this kind of regression on every boot:
on the plymouth splahscreen bottom, a message saying "trying to discover network" and sometimes "allowing 60 more seconds to discover network".

Why do we have such weirdness now ? Can it be tweaked ? Is it about wan/lan/samba/... ?

---

### Post by lucazade on 2011-10-21
> **dino99 said:**
> now we have this kind of regression on every boot:
on the plymouth splahscreen bottom, a message saying "trying to discover network" and sometimes "allowing 60 more seconds to discover network".

Why do we have such weirdness now ? Can it be tweaked ? Is it about wan/lan/samba/... ?

I saw it also in oneiric at it was due to a misconfig in /etc/network/interfaces
I had to remove the 2 entries about eth0 and rebooted.. (network-manager-gnome handles eth0 without any entries in that file)

---

### Post by dino99 on 2011-10-21
ah thanks, i will try your solution.

how it is right now:
auto eth0
iface eth0 inet dhcp

dont see what is wrong here.

---

### Post by lucazade on 2011-10-21
> **dino99 said:**
> ah thanks, i will try your solution.

how it is right now:
auto eth0
iface eth0 inet dhcp

dont see what is wrong here.

these 2 lines should not exist in this file, you can comment  them with a # because network-manager-gnome handles ethX without using this file.

---

### Post by dino99 on 2011-10-21
> **lucazade said:**
> these 2 lines should not exist in this file, you can comment  them with a # because network-manager-gnome handles ethX without using this file.

i did not know that, and i see some old files (2009) into /etc/network/if*/

Thanks, will see on next boot then.

---

### Post by dino99 on 2011-10-23
since a  day , now the config is:

# auto eth0
# iface eth0 inet dhcp

so it lets the system directly dealing , but still get the message time to time

---

### Post by tghe-retford on 2011-10-23
I found this to be a problem leftover from a bug(?) introduced during the last weeks of Oneiric. A full reinstall of Kubuntu and the problem did not resurface.

---

### Post by lucazade on 2011-10-27
upstart (1.3-0ubuntu11) oneiric-proposed; urgency=low

  * debian/conf/failsafe.conf: stop on static-network-up, so that a slow
    runlevel switch doesn't leave a confusing message on screen about
    starting up without networking.  LP: #881079.

[https://lists.ubuntu.com/archives/oneiric-changes/2011-October/011318.html](https://lists.ubuntu.com/archives/oneiric-changes/2011-October/011318.html)

---

### Post by dino99 on 2011-10-27
not a big deal, but its a good news, thanks :)

---

