---
title: "Benefits of updating server kernel?"
date: 2010-04-24
forum: Server Platforms
---

### Post by wesg on 2010-04-24
My server is currently sitting at 180 days of uptime, but I'll be taking it down shortly to make some hardware upgrades. It's also running kernel 2.6.28-11-generic. Is the kernel version independent of Ubuntu version? ie. 9.04 will support the latest kernel available

How often does everyone update their kernel?

---

### Post by P4man on 2010-04-24
no, ubuntu versions are tied to kernel versions. That said, if it aint broke, dont fix it. Install relevant security patches, keep your kernel.

---

### Post by wesg on 2010-04-24
How about updating to newest Ubuntu versions? 9.04 works fine for me, but is it worthwhile to upgrade (especially with 10.04 coming out)?

---

### Post by P4man on 2010-04-24
like I said, generally, if it aint broken, dont fix it. *Especially *for a server. 

Only problem is that support for 9.04 will be EOL'd in october. Id wait a until this summer, then upgrade to lucid as its an LTS release that you can keep until 2015 for the server version.

---

### Post by tgalati4 on 2010-04-24
Some kernel updates are security and/or performance fixes.  If you are bringing your machine down, then you might as well update the kernel as well.  GRUB keeps at least 7 of your previous kernels listed.  So if there is breakage, you can always reboot to the previous kernel.  I have found breakage rare with kernel upgrades--especially with servers.  Xorg upgrades can break video, but usually that is not a problem on a server.

I tend to do my updates in 6 month intervals as well.  You may find several hundred updates.  So prepare for at least some breakage.  Test all of your services after rebooting to make sure everything works as expected.

The biggest risk is the hard disks not spinning up right away.  The bearing oil becomes like glue when the drives cool down.  So don't let your disks get cold before rebooting, otherwise you will be scratching your head.

---

### Post by lukeiamyourfather on 2010-04-24
Sounds like others already have the bases covered. I was going to say if it ain't broke don't fix it which was already said. Also Ubuntu 9.04 is not a long term support release (LTS) so you'll want to upgrade to a LTS version of Ubuntu soon (like 10.04 LTS). Already mentioned as well. Cheers!

---

### Post by cdenley on 2010-04-24
> **P4man said:**
> Only problem is that support for 9.04 will be EOL'd in october. Id wait a until this summer, then upgrade to lucid as its an LTS release that you can keep until 2015 for the server version.

Don't upgrade from 9.04 to 10.04. Either upgrade to 9.10 then 10.04, or do a fresh install of 10.04. Going from 9.04 to 10.04 may work, but it is not supported and not tested, so you may have problems. Another reason to stick with LTS, since upgrading between LTS version (such as 8.04 to 10.04) is supported.

---

### Post by uberlinuxnerd on 2010-04-25
If uptimes are your `kick` then ksplice may be worth having a look at. 

We use it in work to patch and update Ubuntu servers without having to bring them down and works really well! 

[http://www.ksplice.com/](http://www.ksplice.com/)

Its is free for Ubuntu and always will be.

---

### Post by sh1ny on 2010-04-25
> **uberlinuxnerd said:**
> If uptimes are your `kick` then ksplice may be worth having a look at. 

We use it in work to patch and update Ubuntu servers without having to bring them down and works really well! 

[http://www.ksplice.com/](http://www.ksplice.com/)

Its is free for Ubuntu and always will be.

As far as i can read it's free for ubuntu desktop edition ? Does it work properly with the -server kernel ?

[http://www.ksplice.com/pricing](http://www.ksplice.com/pricing) shows that you have to pay for the sever version of ubuntu, well i guess unless you run a generic kernel on your server.

---

### Post by sh1ny on 2010-04-25
> **wesg said:**
> My server is currently sitting at 180 days of uptime, but I'll be taking it down shortly to make some hardware upgrades. It's also running kernel 2.6.28-11-generic. Is the kernel version independent of Ubuntu version? ie. 9.04 will support the latest kernel available

How often does everyone update their kernel?


I prefer to reboot every now and then ( scheduled ). Many hardware problems, mostly tied to HDD's show up only when rebooting, and i like to have a scheduled downtime that can get rough, than to have an unexpected power down only to discover that 2 out of the 3 disks in that RAID5 have failed mechanically after running for 200 days. But to each his own :)

---

### Post by CharlesA on 2010-04-25
> **sh1ny said:**
> As far as i can read it's free for ubuntu desktop edition ? Does it work properly with the -server kernel ?

[http://www.ksplice.com/pricing](http://www.ksplice.com/pricing) shows that you have to pay for the sever version of ubuntu, well i guess unless you run a generic kernel on your server.

Probably only works for the desktop kernel. I guess if you want, you could run a server using the desktop kernel.

On my server, I take it down during the off-hours to do updates, since when I upgrade to a new kernel, I need to build the RAID driver from source, but that isn't a huge deal, and it's done in 5-10 minutes after doing a reboot.

The major benefit on updating to a new kernel is fixes and security updates.

---

### Post by uberlinuxnerd on 2010-04-25
> **sh1ny said:**
> [http://www.ksplice.com/pricing](http://www.ksplice.com/pricing) shows that you have to pay for the sever version of ubuntu

Thats a bummer... use to be free. Even at $3.95 a system I can't really grumble (for the servers that are mission critical, so to speak).

---

