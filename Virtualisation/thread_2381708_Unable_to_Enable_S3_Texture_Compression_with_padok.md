---
title: "Unable to Enable S3 Texture Compression with padoka-ppa and driconf"
date: 2018-01-04
forum: Virtualisation
---

### Post by Neil_Sherin on 2018-01-04
Hi,

The other night I tried a fresh Ubuntu MATE 16.04 install onto a new SSD. I've found previously that the padoka-ppa drivers work well for 3D Acceleration with VMware Workstation installed running a Windows 7 guest for gaming, as long as you used driconf and on the Image Quality tab, set Enable S3TC Texture compression even if software support is not available to Yes.

In the past, the following worked - these are from my notes which worked fine a number of times:

Install Ubuntu MATE 16.04 - ticking the Download Updates while installing and Install third-party software options

Log in to the fresh install and do the following:

In Software & Updates - Other Software, tick Canoical Partners


From a terminal run:


sudo add-apt-repository ppa:paulo-miguel-dias/mesa
sudo apt-get update && sudo apt-get upgrade


Then reboot


From a terminal run:


sudo apt-get update && sudo apt dist-upgrade
sudo apt-get install driconf


Then go to System - Preferences - Hardware - 3D Acceleration to open the driconf panel


On the Image Quality tab, set Enable S3TC Texture compression even if software support is not available to Yes

Then reboot.

The problem is, when I run driconf, on the Image tab, there is no Enable S3TC Texture compression option at all. There are now very few options and most of them have a 0 or 1 setting.

This seems very strange - the version of driconf is still 0.91 - several years old, so it is not as if the software has been updated.

Is there another way to enable S3TC without driconf  so that it is set so that when the machine boots up and I am logged in that it is automatically enabled? Or is there a way to fix driconf to show the Enable S3TC Texture compression as it used to?

Any help is much appreciated, as I am rather stumped. given that this is a completely clean install, using steps that worked perfectly in the past.

Many thanks,
Neil

---

### Post by Yellow Pasque on 2018-01-04
> it's unconditionally enabled, and the previous "force_s3tc_enabled" tunables and related code is now dropped with the code always being present.

[https://www.phoronix.com/scan.php?page=news_item&px=S3TC-Lands-In-Mesa](https://www.phoronix.com/scan.php?page=news_item&px=S3TC-Lands-In-Mesa)

---

### Post by Neil_Sherin on 2018-01-04
Thanks for your reply.

It doesn't seem to work. Trying to run a VMware Workstation Windows 7 virtual machine with 3D acceleration seems to result in VMware saying that there is no acceleration available from the host. This worked fine before when I could change the setting in driconf - I think September time was the last time I tried this with success.

I tried running VMware via the terminal:

force_s3tc_enable=true /usr/bin/vmware %U

But it hasn't made any difference - the errors relating to acceleration still appear when I start the virtual machine up.

The card is an AMD R9 380.

---

### Post by Yellow Pasque on 2018-01-04
> Trying to run a VMware Workstation Windows 7 virtual machine with 3D acceleration seems to result in VMware saying that there is no acceleration available from the host.

Is VMWare complaining about S3TC specifically or 3D acceleration in general? Those are two very different problems. I'm not familiar with VMWare, but I believe it should have logs to give you more helpful/detailed error messages.

EDITL Oh, and obviously you need 3D to be working on the host:
```
glxinfo | grep string
```

---

### Post by Neil_Sherin on 2018-01-04
Thanks again for your quick reply.

It's complaining about a lack of 3D acceleration in general, not S3TC.

But enabling S3TC from driconf in the past has resolved the issue and stopped any 3D acceleration errors from VMware.

There's nothing in the logs in /var/log/vmware/host-d.log pointing to any 3D issues.

The output of glxinfo | grep string is:

neil@ubuntu:/var/log/vmware$ glxinfo | grep string
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: X.Org
OpenGL renderer string: AMD Radeon (TM) R9 380 Series (TONGA / DRM 3.9.0 / 4.10.0-42-generic, LLVM 6.0.0)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.4.0-devel - padoka PPA
OpenGL core profile shading language version string: 4.50
OpenGL version string: 3.0 Mesa 17.4.0-devel - padoka PPA
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 17.4.0-devel - padoka PPA
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
hen I run VMware form the terminal, I see:

neil@ubuntu:~$ force_s3tc_enable=true /usr/bin/vmware %U
Fail to open executable: No such file or directory

But VMware starts anyway.

---

### Post by howefield on 2018-01-04
Thread moved to the "*Virtualisation*" forum.

---

