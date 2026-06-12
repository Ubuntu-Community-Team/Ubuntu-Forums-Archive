---
title: "&quot;TIP&quot; GNOME not loading after VMWare Tools Install"
date: 2011-02-15
forum: Virtualisation
---

### Post by krisarmstrong on 2011-02-15
I did an easy install via VMWare Workstation 7.1 on a Windows 7 64bit host.  The install completed however the following message appears at each login.

Please Wait Vmware tools is being installed on your system Depending on the version of ubuntu you are installing you may log in below and use the system during the installation.  Otherwise please wait for the graphical environment to launch. Thank You.

So I log in and the graphical environment never loads.  I can however do a startx and I get gnome and everything works as expected.

So I did and uninstall via the vmware-uninstall-tools.pl script. Reboot the message was still there and X did not start.  So I went ahead and did a startx.  Interestingly enough it was like VMware tools was still installed as the mouse and everything worked between host and guest still.  confused.

So I rebooted once again and guess what X started without any issues and all worked fine.

Thought this might be helpful for someone out there.

---

