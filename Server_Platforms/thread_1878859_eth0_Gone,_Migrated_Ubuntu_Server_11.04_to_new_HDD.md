---
title: "eth0 Gone, Migrated Ubuntu Server 11.04 to new HDD"
date: 2011-11-10
forum: Server Platforms
---

### Post by flamadiddle on 2011-11-10
I cloned my Ubuntu server installation to a new hard-drive using Clonezilla live.  It's running with the exact same hardware as before except for the HDD.  The new HDD is even plugged into the same SATA port.

Everything worked fine except eth0 disappeared from ifconfig.

I searched around and found info about the file: /etc/udev/rules.d/70-persistent-net.rules

It did have an eth0 entry originally that apparently wasn't working.  I've deleted that file and rebooted several times.  Every time, the file re-appears without eth0.

I hope I'm just missing something simple.  Everything worked fine with the previous HDD.  Any help is appreciated.

---

### Post by darkod on 2011-11-10
I guess the connection is now called eth1 or eth2, etc. I don't have much experience with servers, but I noticed when cloning the desktop version to IDENTICAL hardware, that the connection eth0 and eth1 from the first machine did not exist on the second, instead new connections eth2 and eth3 did.

I don't know how using a device with another name might influence your server role, if it depended on the device being named eth0.

---

### Post by flamadiddle on 2011-11-10
I would be so happy if it were as simple as renaming it to eth1, but I don't have any eth* adapters listed in the newly-generated /etc/udev/rules.d/70-persistent-net.rules file.

---

### Post by CharlesA on 2011-11-10
What does this return?

```
sudo ifconfig -a
```

---

### Post by flamadiddle on 2011-11-10
Well, until 1 reboot ago, it only showed the loopback and wlan0 NICs, but about 30 minutes ago, as mysteriously as it disappeared, my eth0 adapter reappeared.

I suspect my hardware may be flaking out, which makes me less than happy.  For now though, it's working.  Thank you for your help.

---

