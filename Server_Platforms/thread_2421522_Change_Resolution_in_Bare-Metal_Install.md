---
title: "Change Resolution in Bare-Metal Install"
date: 2019-06-23
forum: Server Platforms
---

### Post by grandta13 on 2019-06-23
I have an 18.04 amd64 install on bare-metal that I use as a home server. I wanted to configure it such that the terminal resolution when booting locally would default to 800x600 or 640x480 for maximised compatibility. Currently, GRUB boots in the desired resolution, but while the terminal is loading, it changes to a higher resolution that my current monitor can't properly display. I've tried editing [FONT=lucida console]etc/default/grub[/FONT] as per the advice I've seen in several forum posts, but the most I've been able to acheive is the get the initial GRUB menu to display the desired resolution, but the resolution changes while the OS is booting. It is also worth noting that when booting in recovery mode, I do get a usable image. My monitor displays it as 720x400, though I suspect that it's receiving a lower resolution and scaling it based on a bit of research.

When I initially set up the server, it was over HDMI with an attached graphics card. I've sinced removed the graphics card and am now relying on the built-in VGA port.

Below is my current [FONT=lucida console]etc/default/grub[/FONT] conifg:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="maybe-ubiquity"
GRUB_CMDLINE_LINUX=""

GRUB_GFXPAYLOAD_LINUX=800x600x16
```

Any assistance would be appreciated.

Regards,
grandta18

---

### Post by cruzer001 on 2019-06-23
You can use xprofile to set by session.

[https://wiki.ubuntu.com/X/Config/Resolution#By_Session_with_.xprofile](https://wiki.ubuntu.com/X/Config/Resolution#By_Session_with_.xprofile)

Or xrandr to set dynamically.

[https://wiki.ubuntu.com/X/Config/Resolution#Dynamic_setup_with_xrandr](https://wiki.ubuntu.com/X/Config/Resolution#Dynamic_setup_with_xrandr)

And welcome to the forums :)

---

### Post by grandta13 on 2019-06-26
> **cruzer001 said:**
> You can use xprofile to set by session.

[https://wiki.ubuntu.com/X/Config/Resolution#By_Session_with_.xprofile](https://wiki.ubuntu.com/X/Config/Resolution#By_Session_with_.xprofile)

Or xrandr to set dynamically.

[https://wiki.ubuntu.com/X/Config/Resolution#Dynamic_setup_with_xrandr](https://wiki.ubuntu.com/X/Config/Resolution#Dynamic_setup_with_xrandr)

And welcome to the forums :)

 Thank you for that information; I'll look into that. Though I would like to know if it is possible to change the resolution without installing X Server. The system is obviously capable of changing it by itself, which would lead me to believe that there would be some way for the end-user to change it with inbuilt functionality.

---

### Post by cruzer001 on 2019-06-27
Ok, sounds like x-window settings.

X-windows (xinit) could be used to change the position/size using -geometry.

[https://www.x.org/archive/X11R6.8.1/doc/xinit.1.html](https://www.x.org/archive/X11R6.8.1/doc/xinit.1.html)

Xinit can be installed without bringing in xserver.
```
sudo apt install --no-install-recommends xinit
```
[https://packages.ubuntu.com/bionic/xinit](https://packages.ubuntu.com/bionic/xinit)

I run xserver and have not tried this without, but looks doable.

Hope it works, thats all I have.  Good luck

---

### Post by #&amp;thj^% on 2019-06-27
Here is a method i use:[ https://linuxconfig.org/how-to-increase-tty-console-resolution-on-ubuntu-18-04-server]( https://linuxconfig.org/how-to-increase-tty-console-resolution-on-ubuntu-18-04-server)

---

### Post by cruzer001 on 2019-06-27
Is that a voice from the woods I hear :)

His title says resolution, but the post to reads geometry to me :confused:

---

### Post by dmnur on 2019-06-27
> **grandta13 said:**
> the resolution changes while the OS is booting

This is done by Kernel Mode Setting (KMS). The easiest way to keep the resolution set by GRUB is to disable KMS. You can do this by adding **nomodeset** to the kernel command line:
```
GRUB_CMDLINE_LINUX="nomodeset"
```

---

### Post by #&amp;thj^% on 2019-06-27
> **cruzer001 said:**
> Is that a voice from the woods I hear :)

His title says resolution, but the post to reads geometry to me :confused:

Hello from the Woods :)
I read as "_wanted to configure it such that the **terminal** resolution _when booting locally would default to 800x600"
I guess we will just have to wait and see for sure then.;)

---

### Post by cruzer001 on 2019-06-27
And with the addition of nomodeset I think all bases are now covered.

---

