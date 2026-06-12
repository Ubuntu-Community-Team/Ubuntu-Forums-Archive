---
title: "XEN installation on Ubuntu 7.04"
date: 2008-03-25
forum: Virtualisation
---

### Post by stephanbde19 on 2008-03-25
Hi all,

I'm almost desperate and gone mad with Ubuntu.
I had to take a Linux-OS for performance-studies and am now struggling for 2 weeks with several problems.
Today I tried to install XEN on Ubuntu. First I downloaded the package from the XEN-homepage, but the install.sh-script didn't work (I'm getting used to it).

With Google I found, that I can install XEN easily via apt-get.
I did that, and everything worked well. I also used the tutorial linked here:

[http://www.howtoforge.com/ubuntu_7.04_xen_from_repositories](http://www.howtoforge.com/ubuntu_7.04_xen_from_repositories)

When the tutorial instructed me to reboot, I rebooted the system.
Now I doesn't start anymore!!! :-(

I'm now getting shown different terminal outputs during boot, which might be normal after XEN-installation.
But the boot stops with an alert:

[26.870359] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Done.
         Check  root=bootarg cat /proc/cmdline
         or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/[*crypticnumber*] does not exist. Dropping to a shell!

BusyBox v1.1.3 (debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

I also tried a fresh installation of Ubuntu, but the problem is the same... Do you have some advice??

Thanks a lot in advance!

Regards

Stephan

---

### Post by stephanbde19 on 2008-03-27
Doesn't somebody have a hint for me?

Who has already installed XEN on Ubuntu 7.04? Used to package or downloaded from XEN-homepage?

Regards

Stephan

---

### Post by tpeelen on 2008-05-05
Hi Stephan,

I do not know whether this will help you with your particular problem but I recommend looking [https://help.ubuntu.com/community/Xen?highlight=(xen](https://help.ubuntu.com/community/Xen?highlight=(xen))
&#376;ou will find some very handy information about Xen on ubuntu. I followed the instructions you refer to but found it will only work for a edgy distro but not the later ones. At this link you will find a instruction on later dists under "Ubuntu Guest is Gutsy 7.10 or newer".

I think the instruction is OK for hardy as well. However I find myself confronted with some peculiar network-behaviour. I can't get the bridge working properly. I think I will post on the xen forum. :(

Success!

Tom

---

### Post by generic_idea_machine on 2008-05-05
I've ran into some serious problems after installing Xen on my Amd64 as well.

[LIST]
[*]# 1 - After installing Xen, seems like it takes over the kernel and overwrites the Kernel from the original install 
[*]# 2 - system goes into a read-only mode. You cannot remove the Xen installation. Even if you boot into the recovery mode
[*]# 3 - Since Xen has completely taken over the system, X does not load up. Trying to manually start X results in failure and all sorts of jargon error messages are spit on the screen.
[/LIST]

I did not expect this behaviour from Xen. My perception was that it was going to be a fairly simple change the likes of installating VirtualBox or any other utility on the host. Guess not. 

I could not locate pertinent instructions to uninstall Xen. So myself I am left with no other option but to reinstall the the OS. Guess I should have done a bit more research before deciding to install Xen...

If anyone has any instructions for a complete uninstall for Xen and restoring the system to a previous state. Then please let me know

thx!

---

