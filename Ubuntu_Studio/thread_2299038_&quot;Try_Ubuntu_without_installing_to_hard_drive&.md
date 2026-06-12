---
title: "&quot;Try Ubuntu without installing to hard drive&quot; question"
date: 2015-10-15
forum: Ubuntu Studio
---

### Post by chris420 on 2015-10-15
Hi everyone,

I'm very new to Ubuntu, I've just moved from Windows to Ubuntu Studio 14.04.3 and it's amazing! I'm also a teacher and I want my students to be able to use Pd and Jack in a stable environment (hence Ubuntu Studio 14.04.3). However, at work I'm not allowed to do a dual boot (Windows/Ubuntu) or just Ubuntu Studio 14.04.3) on work machines. 

I've successfully installed Ubuntu Studio on a USB stick and it works (hence no need for the hard disk install), but it's really slow for booting and loading applications so pretty unusable. Therefore, I was wondering if there's a way I can use my Ubuntu ISO USB,  run it in "Try Ubuntu without installing to hard drive" install some extra applications that I need and then somehow save these applications for the next time I select the "Try Ubuntu without installing to hard drive" option? I know that when you select packages for install in the synaptic package manager that they won't be available next time round when in "Try Ubuntu without installing to hard drive" . Is there a way to make them available since the "Try Ubuntu without installing to hard drive" loads very quickly and this would solve my issue?

I've also tried making a new ISO image (with K3b) which includes my installed packages but it don't have sufficient file privileges for 'root' etc; even after loading K3b with sudo from terminal.

Any help/ solutions/workarounds for this problem would be very much appreciated

All the best

Chris

---

### Post by sudodus on 2015-10-15
Welcome to the Ubuntu Forums :-)

You have the 'middle of the road option between a live (live-only) session and an installed system': ***a persistent live system***, where an overlay file system will store saved files, tweaks and installed program packages (except the kernel and drivers). See this link (and links from it) for more details

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

I made the tool mkusb, which creates a partition with the label casper-rw, and it works with small as well as big drives (USB pendrives, but also hard disk drives and SSDs).

It is an advantage to connect via USB 3 or eSATA if available. Even if there is only USB 2 ports in the computer, a USB 3 pendrive is better than a USB 2 pendrive, because it has faster flash memory hardware. Otherwise the flash memory is limiting the speed. See this link

 [Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

-o-

With a fast connection, also installed systems work well from an external drive.

---

### Post by chris420 on 2015-10-15
Thank you very much for this quick reply ! It's great to know that there are some solutions to this problem Persistent live drive sounds the way to go. I'll have a go tonight. Thanks once again ! :) :)

---

### Post by sudodus on 2015-10-15
Good luck :-)

If/when you need help again, and I'm not at the keyboard, I think there are other people who can help you.

---

### Post by SeijiSensei on 2015-10-15
Are you also forbidden from creating a virtual machine?  You can install [VirtualBox]("http://virtualbox.org/") for Windows, then install an Ubuntu flavor into a new VM.  You can make the VM full screen, or even have both the host machine and the guest machine share the same display in "seamless" mode.  I wouldn't do this on a machine with less than 3 GB of memory though, so you can give 1 GB to the virtual machine and leave two for the more memory-hungry Windows.

---

