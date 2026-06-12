---
title: "CentOS On Meerkat NetTop"
date: 2010-07-14
forum: System76 Support
---

### Post by wrightjmf on 2010-07-14
I was wondering if anyone has tried running CentOS 5.4 on a Meerkat NetTop. If so, were there any issues?

Thanks,

Jeremy

---

### Post by thomasaaron on 2010-07-15
Hey 76ers, I asked Jeremy to post here. Are there any CentOS users out there on the Meerkat or Meerkat ION?

---

### Post by jml on 2010-07-15
I have not tried CentOS on a Meerkat, but I have tried it on several other computers.  A first generation Darter, an old IBM ThinkPad and an HP NX6110.  The basic install went well, however I had several 'issues." 

1.  I could not get wireless networking to function properly with either Broadcom, Atheros or Intel based wireless cards.  Wired networking worked out of the box.  Since CentOS is a distro focused on the enterprise/server environment, this should not be surprising.

2.  2D graphics worked out of the box, but I was not able to get accelerated 3D graphics to work.

3.  It's very difficult to find and install any "restricted" codecs you may need.  Unlike Ubuntu, there are no readily available repositories for them.

I would suggest that you download a copy of the CentOS live CD and try it out before you install it.  Here is a link.

[https://projects.centos.org/trac/livecd/](https://projects.centos.org/trac/livecd/)  

Hope that this helps.

Joe

---

### Post by wrightjmf on 2010-08-06
Just a quick report in case anybody else has a reason to run CentOS on a Meerkat:

Everything installed fine with CentOS 5.4 doing a network (PXE) boot and install. According to what CentOS is telling me, all of the hardware was detected and the proper modules were loaded. Everything seems to work normally and I haven't had any problems with it. The model of Meerkat that I purchased does not have WiFi built in though, so I was not able to test that.

Jeremy

---

