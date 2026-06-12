---
title: "Networking XP MCE guest with an Xbox 360"
date: 2007-11-10
forum: Virtualisation
---

### Post by nutz on 2007-11-10
I have also posted this over in the Virtualbox forums but I wanted to post it here too. I am trying to network my MCE guest VM with an Xbox 360 so I can take advantage of it's media extender capabilities. Any help would be highly appreciated...


[http://forums.virtualbox.org/viewtopic.php?p=9717#9717](http://forums.virtualbox.org/viewtopic.php?p=9717#9717)

---

### Post by Runamok on 2007-11-12
Definitely interested in this, since I have similar possibilities.  Let me know if you find a link that works, but I would suggest seeing if Media Center will work behind a NAT.

---

### Post by nutz on 2007-11-12
I know it will work if I can get the right ports forwarded from the host to the guest XP MCE instance. But for the life of me I can't figure out the command syntax for doing this...

These are the ports that it needs...
[http://www.microsoft.com/windowsxp/mediacenter/extender/setup/firewall/config.mspx](http://www.microsoft.com/windowsxp/mediacenter/extender/setup/firewall/config.mspx)

---

### Post by ohzopants on 2008-02-06
Have you made any breakthroughs? I'm in the same situation (although I'm using qemu, but whatever)...

Are you using the official xbox wireless adapter?  I am using my laptop as a bridge, so I'm not sure if that's my problem.  I don't want to spend 100$ on the adaptor until I know it works to my liking.

---

### Post by nutz on 2008-02-06
I ended up using the host networking feature. So far it has worked flawlessly but with one drawback. I have not been able to get it working with a wireless NIC. So right now I am using a wired connection on my PC and the wireless adapter on the 360. But it works flawlessly...

[http://ubuntuforums.org/showthread.php?p=4191629](http://ubuntuforums.org/showthread.php?p=4191629)

[http://ubuntuforums.org/showthread.php?p=2062234](http://ubuntuforums.org/showthread.php?p=2062234)

[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

This is what I have in /etc/network/interfaces


```

auto lo
iface lo inet loopback

iface eth0 inet manual

auto tap0
iface tap0 inet manual
  tunctl_user nutz

auto br0
iface br0 inet dhcp
  bridge_ports eth0 tap0
  bridge_maxwait 0
```

---

