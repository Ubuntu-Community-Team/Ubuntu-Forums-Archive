---
title: "Server 18.04 LTS on ESXi 6.0 - GUI function issues"
date: 2019-06-14
forum: Server Platforms
---

### Post by tallguy2402 on 2019-06-14
Hello All

I am new to the forum so forgive me if this has been covered. I searched but did not find anything that could help with my issue. I have installed Ubuntu Server 18.04 LTS 64bit on a virtual machine in ESXi 6.0.  I cannot get the GUI to function and I have tried every setting that I know of and even some suggestions from the web. Configuration is as follows:

VM Hardware

CPU - 2 Virtual CPU's
RAM - 4GB
Hard Disk - 50GB
Network - single adapter
1 CD Drive
Video Card -  Number of Displays - 1, Total Video Memory - 8MB, 3D Graphics(enable 3D support checked), 3D Renderer - Automatic, 3d Memory - 256MB.

The install works perfectly and I can get to my login screen and login without issue. I have tried several ways to get a GUI installed based on what I have found on the web but essentially what happens after the GUI is installed and I reboot is I get the purple splash screen and then I am unable to type or input anything on the screen. I have tried installing open-vm-tools as well which did nothing. I am stuck on how to get the GUI to function so that I can move forward. Not sure what other information anyone will need to assist though. Thank you!

---

### Post by SeijiSensei on 2019-06-14
If you want a GUI, install a desktop version, then add any missing server software.  Ubuntu Server is designed to be used from the command line.

---

### Post by TheFu on 2019-06-14
A agree 100% with SeijiSensei above, but if you must have a GUI on a server, it needs to be as small and lite as possible.  Definitely NOT bloated gnome3 which demands GPU access.

Some people coming from Windows often make the mistake of thinking that there is huge differences in the underlying code between the server and desktop versions. There isn't, at least not with Ubuntu.  All server packages can be installed on the desktop release.  If you work from the Server install as the base, many desktop conveniences won't be there.  That's perfect if you are a "server guy" already and don't want all the DE bloat.  But if you are relatively new, it isn't so good.

With ESXi, there won't be any local GUI, so you are connecting from a remote system, which means you are using a virtual desktop from the VM guest. The gnome3 desktop doesn't like not having direct access to the GPU. In a virtual environment, it is highly unlikely that direct GPU access is available, so we need to compensate by using a DE like XFCE, LXDE or Mate.

But, really, if you need a server OS, you don't want the bloat and security issues that running a GUI brings to that OS.  Learn the CLI and love it.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  ssh is all we need ... unless we need a serial console.

---

