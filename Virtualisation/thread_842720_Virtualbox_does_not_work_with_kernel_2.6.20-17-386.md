---
title: "Virtualbox does not work with kernel 2.6.20-17-386"
date: 2008-06-27
forum: Virtualisation
---

### Post by madelman on 2008-06-27
Hi:

I started to have problems with VirtualBox on Ubuntu 7.04 using kernel 2.6.20-17-386.

Before you think in upgrading, I do not want to upgrade yet after being upgrading other machine to 7.10 and was a nightmare then I upgraded recently other machine to 8.04 and other nightmare, so 7.04 at the moment in my machine is all set and no problems, until today when I tried to use Virtualbox 1.5.4

I started to get this error when I tried to start any virtual machine:
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

So I tried uninstalling and reinstalling but there is no DEB file available in Sun servers for 7.04, so I found it somewhere in virtualbox.org and reinstalled it, nothing changed same error. 

So I ran sudo /etc/init.d/vboxdrv setup. And some errors where found when I execute dmesg:  vboxdrv: disagrees about version of symbol struct_module

So at some point I found something where recommended to run:
modprobe vboxdrv then I got to this link: 
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/226753](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/226753)

Where it says : 
>>>>>>>>>>>>>>>>>>>
no module built for 2.6.24-17-generic

I upgraded the kernel and found that virtual box does not work anymore because "vboxdrv" was still 2.6.24.16 and there was no package available for 2.6.24.17.
>>>>>>>>>>>>>>>>>>>


Thinking that I have 2.6.20-17-386 and it says that there is no package for 24.17 I assumed was something similar, so still having the kernel 2.6.20-16-386 in my machine I execute some of the commands suggested in that bug report and VirtualBox worked:

sudo depmod
sudo insmod /lib/modules/2.6.20-16-386/misc/vboxdrv.ko

Obviously when I rebooted it did not work and I need to do this manually, which sucks, so my questions are, is there any patch for this problem on 7.04 as mentioned in the bug report? or can you tell me why the kernel was upgraded in 7.04 when this web page does not talk anything about the new release?([http://packages.ubuntu.com/feisty/linux-generic](http://packages.ubuntu.com/feisty/linux-generic))

How do I go back to kernel 2.6.20-16-386?

** This is one of the issues I discussed today about switching from Windows to Ubuntu and why people without too much knowledge cannot switch, since this simple issue can become a nightmare every time you upgrade or ubuntu upgrades something. Why is that Sun Microsystems have to screw everything and stop allowing downloads for previous versions?. 
When someone asks me switching from Windows to Ubuntu I do not recommend it at all since the release of 7.10 and believe me, the very first question I asked is, do you know how to list files in command mode in Linux? or have you worked on the command prompt in windows? if the answer is, no, then I suggest to stick with Windows. Really these issues suck and for me there is no problem trying to figure out the solution but if Linux really wants to get more minds working in  this OS they should think how to improve  these "tiny" problems.

---

### Post by starcannon on 2008-06-27
When you first boot up there is a "Grub" menu that appears for about 3 seconds.

Press an arrow key, this will stop the timer.

In this menu you will see a list of available kernels.

Choose the one that worked for your needs in the past.

You can make it the default by editing your /boot/grub/menu.lst file.

GL

oh and as far as upgrading goes, imo the best way to do that is with clean install of the version your upgrading to, but this is only practical if you set up /home on its own partition. Its been my experience that regardless of operating system, windows, mac, linux, that "upgrade installs" are never as trouble free as fresh clean installs.

---

