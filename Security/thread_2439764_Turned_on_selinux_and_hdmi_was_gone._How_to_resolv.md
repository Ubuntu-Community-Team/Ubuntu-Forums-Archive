---
title: "Turned on selinux and hdmi was gone. How to resolve?"
date: 2020-04-01
forum: Security
---

### Post by placidchat on 2020-04-01
I've enabled selinux, but when booting into the desktop, the hdmi connectivity was gone. xrandr couldn't find the external monitor at all. There was an entry in syslog to the effect of - hdmi needs to bind to gfx driver.

To return back to the original configuration, i had to alter the kernel boot line by removing the security=selinux entry. What i think is the driver needs to be bound with the hdmi driver early during the boot process, but it cannot do so. Even with selinux=disabled, after bootup, hdmi is still disabled. It seems the gfx driver needs to be bound during the initrd phase. 

How can i solve this?

---

### Post by TheFu on 2020-04-01
Ubuntu doesn't normally use SELinux, so you are in untraveled waters. Good luck.
If you want SELinux, best to use a RHEL-based distro.

Ubuntu has other techniques for program-level security. Apparmor is the main one. 
[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)
[https://help.ubuntu.com/lts/serverguide/apparmor.html](https://help.ubuntu.com/lts/serverguide/apparmor.html)

[https://linuxconfig.org/how-to-disable-enable-selinux-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-disable-enable-selinux-on-ubuntu-20-04-focal-fossa-linux) says:
> Make sure that you know what you are doing! Ubuntu offers an AppArmor as an alternative to SELinux. While SELinux is available on Ubuntu, it is rather in an experimental stage and most likely will beak your system if set to enforcing mode. In case you must use SELinux, make sure to disable AppArmor first. Also set SELinux first to permissive mode and check your logs for potential issues before you enable enforcing mode.

---

### Post by placidchat on 2020-04-01
I was looking for X11 sandboxing of some sort, and selinux popped up. Yes initially if the user boots up with selinux set to enforcing, the system will halt on bootup. Permissive mode must be set first so ubuntu can relabel everything on boot. Apparmor doesn't seem to have any X11 protection, so that wouldn't work.

---

### Post by EuclideanCoffee on 2020-04-02
As you know, SELinux is incomplete on Debian derived machines. AppArmor is "easier" to use, and to have an apparmor profile, you'd likely need to generate one for x11.

If you're looking for x11 sandboxing, may I recommend wayland.

[https://en.wikipedia.org/wiki/Wayland_(display_server_protocol)#Wayland_Security_Module](https://en.wikipedia.org/wiki/Wayland_(display_server_protocol)#Wayland_Security_Module)

You can typically install this on most Ubuntu versions today.

As for SELinux, I don't think you'll find many experts on it here. Not to say this is a great resource generally. SELinux requires configuration found on Red Hat natively but not so on Debian. This simply has to do with the lack of QA coordination, I think. And since systemd caused such a problem, I don't think the Debian community would be happy if SELinux became the defacto norm. If you want containers on the desktop, go with CentOS. Obviously however you're trading privacy for security.

---

