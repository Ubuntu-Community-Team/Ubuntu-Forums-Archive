---
title: "x206M support"
date: 2006-06-27
forum: Server Platforms
---

### Post by mr_lars on 2006-06-27
hi everybody
I'm a long time newbie, :), thanks to debian first and now ubuntu i'm a quite happy linux  user from '99.

Now i've a server question for you: I'm following a art-multimedia project and we need a server. So a friend propose me an IBM x206M with RAID controller.
[http://www-03.ibm.com/servers/it/eserver/xseries/hardware/tower/x206m/index.html](http://www-03.ibm.com/servers/it/eserver/xseries/hardware/tower/x206m/index.html)
Don't really need a RAID installation but the price is good so I'm interested. 
Now, i never user a RAID and i really don't know if the raid controller is supported or not by ubuntu and /or debian...
someone have some experience on this machine? suggests?

---

### Post by mr_lars on 2006-06-27
The machine use ServeRAID-8e but i can't find nothing around about compatibility...

---

### Post by zaf on 2006-07-14
The x206m is a nice server. It still has that IBM ease of use when it comes to opening it up.

Getting it working under Linux isn't too hard. I have posted a  [Debian on x206M Howto]("http://zaf.geek.nz/projects/deb-on-x206m.html"). Its specific to Debian, but it can be easily adapted to any other distro.

The secret is to boot to knoppix, which can detect the onboard SATA RAID.

The howto has the required Kernel config options that need to be set.

[Zaf]("http://zaf.geek.nz/")

---

### Post by PicaEspuelas on 2006-07-20
Which Knoppix? Version 5.1 can not detect the onboard SATA RAID?

---

### Post by motin on 2008-07-16
> **zaf said:**
> The x206m is a nice server. It still has that IBM ease of use when it comes to opening it up.

Getting it working under Linux isn't too hard. I have posted a  [Debian on x206M Howto]("http://zaf.geek.nz/projects/deb-on-x206m.html"). Its specific to Debian, but it can be easily adapted to any other distro.

The secret is to boot to knoppix, which can detect the onboard SATA RAID.

The howto has the required Kernel config options that need to be set.

[Zaf]("http://zaf.geek.nz/")

But that guide explains how to set-up software raid, thus not using the FakeRAID Serveraid-8e controller or drivers... Do you know any way to use the third party drivers to set-up raid?

Also, check this for more about software vs fake raid: [Re: FakeRAID vs. Software RAID]("http://ubuntuforums.org/showthread.php?p=5396000#post5396000")

---

