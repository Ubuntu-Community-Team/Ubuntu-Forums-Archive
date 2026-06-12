---
title: "KVM switch + gnome-screensaver bug?"
date: 2012-08-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-08-03
This effects both Precise and Quantal:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290)

I'm Erick there so no need to repeat everything I said - I hope :)

I'm hoping that some of the gnome-smart folks can help me here :)

Maybe Jeremy Bicha?

I'm a bit in over my head :D

---

### Post by kansasnoob on 2012-08-03
BTW I waited until the latest X-stack was built to make sure this was not just an X bug :)

---

### Post by ventrical on 2012-08-03
I have a 4 port KVM and do not have the problem in Unity 2D. I 'll keep testing.

How do I duplicate?

---

### Post by kansasnoob on 2012-08-03
> **ventrical said:**
> I have a 4 port KVM and do not have the problem in Unity 2D. I 'll keep testing.

How do I duplicate?

It's easy to duplicate, just set 'gnome-screensaver' to activate after a given number of minutes, then switch to a different machine and wait for that time to pass. When you try to go back to that box you'll get the expected blank screen but when you move the mouse or press a key you get an improper resolution.

---

### Post by ventrical on 2012-08-03
Nope.. resolution is OK here.

---

### Post by kansasnoob on 2012-08-03
> **ventrical said:**
> Nope.. resolution is OK here.

There is certainly a hardware component involved (maybe hardware detection), I'm not smart enough to understand it all but based on the users effected so far it's mostly Intel graphics. There is at least one with nvidia graphics though.

In my case I know that xscreensaver works OK but gnome-screensaver does not. And only Precise and Quantal are effected, Oneiric was OK.

---

### Post by ventrical on 2012-08-03
> **kansasnoob said:**
> There is certainly a hardware component involved (maybe hardware detection), I'm not smart enough to understand it all but based on the users effected so far it's mostly Intel graphics. There is at least one with nvidia graphics though.

In my case I know that xscreensaver works OK but gnome-screensaver does not. And only Precise and Quantal are effected, Oneiric was OK.


I think I  mixed up my testing here. It keeps saying  gnome screensaver <ok> then pops up xscreensaver and I have to press ok otherwise it will hang .. so I must be using xscreensaver daemon then.

I think the hardware component is EFI which transfers BIOS data from the monitor across the KVM.  I talked to effenberg about this during precise testing. I'll see if I can dig up olde Precise topic.

---

### Post by ventrical on 2012-08-03
here is link..

[http://ubuntuforums.org/showthread.php?t=1886049&highlight=KVM](http://ubuntuforums.org/showthread.php?t=1886049&highlight=KVM)

---

### Post by ronacc on 2012-08-03
I don't know if this is related but I have been getting a warning during boot about KVM disabled in bios . I have just been ignoring it because I don't use a KVM switch .

---

