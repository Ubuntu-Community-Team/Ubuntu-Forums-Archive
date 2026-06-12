---
title: "[Resolved] VMware Server 2.0 with Ubuntu 6.06LTS guest network issues"
date: 2008-09-27
forum: Virtualisation
---

### Post by LinuxETC on 2008-09-27
[FONT="Arial"]I figured I would post this since it is listed elsewhere in the forums, but similar issues.  On a side note, do the items below via the VMware Server Console **NOT** via an ssh terminal since you will be bringing the network interfaces up/down.[/FONT]

[FONT="Arial"]The story goes that we upgraded the host (CentOS v5.2) VMware Server to 2.0 recently.  Accordingly we started upgrading the VMware Tools in various guest systems too, including an Ubuntu 6.06LTS server and K/Ubuntu 8.04LTS desktop.[/FONT]

[FONT="Arial"]**First item/issue, having [FONT="Courier New"]vmxnet[/FONT] module loading properly:**
What occurs here in particular with the "vmxnet" module is that one needs do the following (noted from a few VMware Server v1.0.x postings across the net as well):[/FONT]

[FONT="Arial"]Edit the */etc/modprobe.d/blacklist* file to include the following line:[/FONT]

[FONT="Courier New"]blacklist pcnet32[/FONT]

[FONT="Arial"]which is what a typical guest system install will auto detect in VMware Server v1.0.x and v2.0 installs.  This will blacklist the [FONT="Courier New"]pcnet32[/FONT] modules from loading and letting the [FONT="Courier New"]vmxnet[/FONT] to properly load for the guest.  After this change is made, reboot the guest system, and you will note things should come up properly.[/FONT]


[FONT="Arial"]**Second items/issue, having the network come up properly:**
What occurred differently for us with the upgrade of VMware Tools to v2.0 is after a system (the guest here) reboot, the network interface would not come online.  The results of [FONT="Courier New"]/etc/init.d/networking start[/FONT] showed the following:[/FONT]

[FONT="Courier New"]SIOCSIFADDR: No such device eth0
eth0: ERROR while getting interface flags: No such device
[/FONT]

[FONT="Arial"]Further inspection via [FONT="Courier New"]lsmod|grep vmxnet[/FONT] did show the module was loaded.  Via another posting on the Ubuntu Forums:[/FONT]

[FONT="Arial"]*[http://ubuntuforums.org/showthread.php?t=221768]("http://ubuntuforums.org/showthread.php?t=221768")*[/FONT]

[FONT="Arial"]showed that by doing an [FONT="Courier New"]ifconfig -a[/FONT] showed that the MAC address was swapped from eth0 to eth1.  Editing the [FONT="Courier New"]/etc/iftab[/FONT] with this little swap, then a system reboot, things came up fine.[/FONT]

[FONT="Arial"]HTH for others down the road.[/FONT]

[FONT="Arial"]LinuxETC[/FONT]

---

