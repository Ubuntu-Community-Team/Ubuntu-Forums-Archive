---
title: "Experiences with KVM/QEMU, VMWare Server and VirtualBox on karmic"
date: 2009-11-08
forum: Virtualisation
---

### Post by ajaym on 2009-11-08
Hmm. This got complex but had a happy ending. Wanted to set up a virtualised set of machines, starting with XP on Karmic. Didn't go according to plan.

QEMU/KVM. (with latest 0.11 qemu-kvm package installed and Karmic completely up to date with patches) Installing XP SP2 guest, fails to format partition to NTFS during install and reports error. Will format to FAT and then complete installation but then after complete host OS restart, the VM reported a missing NTLDR. Deleted all images and did a fresh VM create and reproduced the NTFS formatting error, at which point gave up on it, filed a bug with QEMU, and tried VMWare Server

VMWare Server. Will not install unless a series of patches applied (posted elsewhere and thanks to contributor - really appreciated the info). Once installed, able to create XP guest but midway through installation at locale customisation point i.e choose English US etc, machine locked up and you could only regain control of the host OS at approximately 1 minute intervals for around 10 seconds before it would lock up again. Some kind of kernel locking issue I suspect, performance monitor (when it would run) did not show any CPU consumption. 

Restarted host OS and then VMWare would no longer connect via the web interface. Have found some suggestion that (going back to 2006) this is due to dynamically-created devices at boot time which VMWare doesn't handle. Gave up.

VirtualBox. I'm embarrassed to say I've never used this before.  Installed with a warning about dbus device, but appeared to complete OK. Installed guest XP flawlessly. And did so much more quickly than either of the other two products. I am very impressed, so much so that I am now back in my primary host XP partition (machine dual boots Windows/Linux) and am installing VirtualBox for Windows. If it works as well as it does in Linux, I'm abandoning VMWare entirely.

---

### Post by fjgaude on 2009-11-08
With Ubuntu 9.10 I went through much the same things we report. But, but with VMware Player 3.0 all issues went away. Install and creation of VMs are fast, fast. I tried Player with 9.04, the same.

If you don't have to access VMs remotely Player 3.0 is a complete solution, AFAICS.

Until someone comes up with an easy way to use VMware Server 2.0 and 1.0, Player 3.0 is one way to go.

---

### Post by sdowney717 on 2009-11-09
the web page is unusable to me

---

### Post by sdowney717 on 2009-11-09
the web page is unusable to me totally broken.

ok, i got it installed and it is much better i think than the server.
i have been using this for tversity podcast video to a dsm 320 media player and it has been a pain to get it working.
tversity media server would keep stopping or not responding with the vmware server
right now it is working well with vmware 3 player. everything except for hulu which gives me 
"Off screen browser is not updating, reloading page"
i wonder if the networking has better support with the version 3 player?

how about a snapshot feature? does it have this?

what is the 'Enter Unity' on the menu, i tried it and it gave me a tiny screen and i had to reboot the pc.

---

