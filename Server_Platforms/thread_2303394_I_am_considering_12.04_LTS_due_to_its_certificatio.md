---
title: "I am considering 12.04 LTS due to its certification for HP Pro Liant DL360 G5 server"
date: 2015-11-18
forum: Server Platforms
---

### Post by bbiandov on 2015-11-18
Hi everyone,

I am considering 12.04 LTS due to its certification for HP Pro Liant DL360 G5 server. Here's the link to the certification:

[http://www.ubuntu.com/certification/hardware/200810-1111/](http://www.ubuntu.com/certification/hardware/200810-1111/)

My question is this: since this will NOT be a Smart Start assisted install but rather just boot off that ISO and use native LTS install what happens next?

I mean are there HP tools for 12.04 such as Array Controller management? This DL360 comes with Smart Array P400i -- how do I manage logical drives, etc from within Ubutu CLI?

Thank you!
~B

---

### Post by Bucky Ball on 2015-11-18
*Thread moved to **Server Platforms**.*

You'll probably have better luck here with those questions. Good luck.

---

### Post by darkod on 2015-11-18
First of all, I am sure you can use 14.04 LTS too, even if it's not officially on the list. These things take time and effort and I guess sometimes simply no one does it, so it remains not included on certified list.

As for array management, I'm not sure what you can expect. The controller will have it's own utility/BIOS that you can enter before it starts booting, and usually you can set all arrays there, and do the management you need. After that, the OS simply sees each array/logical disk as a simple disk, so you can partition it and use it to your liking. It will not be very aware that it's a logical disk on an array.

You can investigate which tools there are in ubuntu for that controller. There are probably some...

---

### Post by lukeiamyourfather on 2015-11-18
Ubuntu Server 14.04 LTS will work just fine on the machine. Worst case scenario you might have to configure disks through the controller BIOS instead of on a running system.

---

### Post by bbiandov on 2015-11-18
Thanks guys, yes I can most certainly configure the array controller parameters using HP's BIOS -- the only downside to that is that I have to reboot the box. I was hoping I can use Ubuntu HP tools where I can make controller changes while the OS is functioning -- same capabilities exist for Windows OS using HP's array management tools.

Thanks

---

### Post by tgalati4 on 2015-11-18
Send an email to HP asking for a 14.04 build of the tools.  If they are open source, you can build them yourself.  If they are only available for RedHat, then perhaps you can use *alien* to convert to a 14.04 Debian package, which you can then install.  I used this method to get Dell PowerEdge system tools to run on a newer version of Ubuntu.

Post the results of your efforts.

---

