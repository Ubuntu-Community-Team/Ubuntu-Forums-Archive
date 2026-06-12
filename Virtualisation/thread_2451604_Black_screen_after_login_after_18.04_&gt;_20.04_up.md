---
title: "Black screen after login after 18.04 &gt; 20.04 upgrade (on virtualbox)"
date: 2020-10-07
forum: Virtualisation
---

### Post by phormion on 2020-10-07
Hi,

I was happily running Ubuntu 18.04 (64 bit) in a VirtualBox VM (Windows 10 being the host), and today I decided to upgrade to 20.04. So after an upgrade check, when Ubuntu told me I could upgrade, I decided to do it, and after the upgrade was done and a reboot, I got the login screen. After logging in, the screen went black. Yay!

I tried to reinstall the VirtualBox guest additions CD. Unfortunately, inserting the drive from VirtualBox doesn't work; shared folders worked, however, so I unpacked the ISO in a shared folder and ran VBoxLinuxAdditions.run from there. After a reboot, I still get the black screen.

In Xorg.0.log I see this error:

```

[    26.488] (EE) Failed to load module "vboxvideo" (module does not exist, 0)

```

Then later:
```

[    26.656] (EE) modeset(0): glamor initialization failed

```

With 'ps axf', I see this process tree for the X server:

```

   1941 ?        SLsl   0:00 /usr/sbin/lightdm
   1974 tty7     Ssl+   0:02  \_ /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
   2204 ?        Sl     0:00  \_ lightdm --session-child 12 19
   2274 ?        Ss     0:00      \_ /bin/bash /usr/sbin/lightdm-session /usr/lib/gnome-flashback/gnome-flashback-metacity
   2383 ?        S      0:00          \_ xhost +si:localuser:stefan

```
Maybe xhost is hanging there? If I try to strace the process, it seems to be blocked reading something. 

I was using gnome-flashback previously, maybe that can lead to problems?

EDIT: I can get to X if I boot the previous kernel, the one from 18.04 (from the grub menu I went to Advanced and selected the second kernel).

---

### Post by phormion on 2020-10-08
The problem seems to have fixed itself after a very usual VirtualBox workaround: power off the VM and power it back on. This always seems to act differently than a restart, and maybe it makes sense - the power off and on sequence probably starts a new VM process. Now I can boot the latest kernel fine (though I'm somewhat reluctant to reboot again :) ). I'll monitor this and mark the problem as fixed if all goes well.

---

### Post by slickymaster on 2020-10-08
*Thread moved to **Virtualisation**.*

---

