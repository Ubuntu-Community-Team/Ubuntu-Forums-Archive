---
title: "Best Virtualization"
date: 2010-05-01
forum: Virtualisation
---

### Post by SALOOMAN on 2010-05-01
Im new in UBUNTU and need run xp in it.
Which virtualization program is the best and easy for me?
And how can i install it?
please help me.
I have UBUNTU 10 now

---

### Post by xirrin on 2010-05-01
I was successful with exactly 0 problems using Sun VirtualBox. I believe its right in Synaptic. Good luck!

---

### Post by rliegh on 2010-05-01
none of them are easy, unless you're willing to learn and read the manuals and able to use google.

virtualbox-ose is probably the least-hard, however. 

sudo apt-get install virtualbox-ose

We'll see ya back here when you're frustrated... :rolleyes:

---

### Post by benderisgreat on 2010-05-02
If you have VT-x capable hardware, I'd suggest kvm.
should be as easy as:
```
# apt-get install kvm
# qemu-img create -f raw diskforwindows.img 10G
# kvm -m 256 -cdrom windowsinstallcd.iso -boot d -hda diskforwindows.img
```

after you have installed xp:
```
# kvm -m 256 diskforwindows.img
```

If that doesn't work right away these links should be enough to get you well on your way:
[http://www.ehow.com/how_4845092_xp-kvm-guest-ubuntu-desktop.html](http://www.ehow.com/how_4845092_xp-kvm-guest-ubuntu-desktop.html)
[http://www.howtoforge.com/installing-windows-xp-as-a-kvm-guest-on-ubuntu-8.10-desktop](http://www.howtoforge.com/installing-windows-xp-as-a-kvm-guest-on-ubuntu-8.10-desktop)
[http://www.wand.net.nz/~smr26/wordpress/2008/08/28/kvm-the-hard-way/](http://www.wand.net.nz/~smr26/wordpress/2008/08/28/kvm-the-hard-way/)

---

### Post by mkvnmtr on 2010-05-02
I found it very easy to run XP in Virtual Box. Whether it is the best is indeed open to question.

---

### Post by Paulplex on 2010-05-02
VirtualBox for me; I've got my 'Windows' hard drive image on an external drive so I can free up space on my laptop for Ubuntu proper.

Oddly, Windows through Sun's VirtualBox runs faster and more efficiently than it did when directly installed on the computer.  How can *that* work?!:confused:

---

### Post by rliegh on 2010-05-02
> **Paulplex said:**
>  How can *that* work?!:confused:
I'm just guessing, but things such as disk writes are faster when the "disk" is actually just a file and doesn't actually involve any platters, lasers or other physical hardware. I say that because it's the most pronounced with cd-roms (try installing from a physical cdrom and then try installing from an iso file and you'll see what I mean).

It's true too for hard disks though maybe not as dramatically.

---

### Post by SALOOMAN on 2010-05-06
Thanx to all
I tried to install Vmware but I could not
The I install Virtualbox and when I want run my virtual machine it fail :
" Failed to start the virtual machine XP.
 VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE)."
What is the meaning of that?

---

### Post by TheFu on 2010-05-06
It appears you've installed both VirtualBox AND KVM on the same system. KVM is a kernel module, so you could just disable it, but for you, being new to Linux, I think you should remove the kvm package.

Then give VirtualBox a try again. It really is the easiest virtualization for desktop Linux users.

Whether VirtualBox is the "best" in virtualization is a completely different question that only you can answer.

---

### Post by dcstar on 2010-05-07
> **rliegh said:**
> none of them are easy, unless you're willing to learn and read the manuals and able to use google.
.........

Rubbish.

VMware Player 3.10 is 10.04 compatible and installs with a GUI interface and basically "works out of the box".

When installing things like XP the VMware tools install automatically, and there is a free tool to convert an existing Windows installation into a VM.

---

### Post by KdotJ on 2010-05-07
Just as a side note, if you do choose to go for virtualbox, if you want USB functionality you wil need to get the versions from Sun's website. Not the ubuntu repos

---

### Post by rliegh on 2010-05-08
> **dcstar said:**
> Rubbish.

VMware Player 3.1 is 10.04 compatible and installs with a GUI interface and basically "works out of the box".

When installing things like XP the VMware tools install automatically, and there is a free tool to convert an existing Windows installation into a VM.

Not rubbish at all. As a matter of fact, the fact that two posts above yours the OP came back and said "I tried to install vmware but I could not" (his words) proves my point.

---

### Post by SALOOMAN on 2010-05-08
> **rliegh said:**
> Not rubbish at all. As a matter of fact, the fact that two posts above yours the OP came back and said "I tried to install vmware but I could not" (his words) proves my point.
I love Vmware because I used to work with it.
How can I install that?

---

### Post by fjgaude on 2010-05-08
I think that people have trouble with VMware Player because of having installed, or tried to install, other versions of either VBox or VMware Server.

Player 3.0.1 is flat solid with Ubuntu, since about 9.04, and auto upgrades itself as kernels get updated.

---

### Post by manzdagratiano on 2010-05-08
> **benderisgreat said:**
> If you have VT-x capable hardware, I'd suggest kvm.
should be as easy as:
```
# apt-get install kvm
# qemu-img create -f raw diskforwindows.img 10G
# kvm -m 256 -cdrom windowsinstallcd.iso -boot d -hda diskforwindows.img
```after you have installed xp:
```
# kvm -m 256 diskforwindows.img
```If that doesn't work right away these links should be enough to get you well on your way:
[http://www.ehow.com/how_4845092_xp-kvm-guest-ubuntu-desktop.html](http://www.ehow.com/how_4845092_xp-kvm-guest-ubuntu-desktop.html)
[http://www.howtoforge.com/installing-windows-xp-as-a-kvm-guest-on-ubuntu-8.10-desktop](http://www.howtoforge.com/installing-windows-xp-as-a-kvm-guest-on-ubuntu-8.10-desktop)
[http://www.wand.net.nz/~smr26/wordpress/2008/08/28/kvm-the-hard-way/]("http://www.wand.net.nz/%7Esmr26/wordpress/2008/08/28/kvm-the-hard-way/")

Here I am looking at all these arcane manuals where I see I would have to do a truckload of configuration to set up kvm, and here you give me a three line easy solution which I just implemented successfully!!! THANK YOU SO MUCH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by manzdagratiano on 2010-05-08
Just a side note - by NO means would I run Windows :) - I just used the technique to run sidux in kvm. Now to play around with arch (and maybe subsequently an attempt with the very painful gentoo - I have previously gotten bored while the installation snails along and have aborted it; maybe this time will be different).

---

### Post by manzdagratiano on 2010-05-09
Just a quick important note:

```
# qemu-img create -f raw <harddrive>.img 5G 
```does create the image, but an installer would find it unusable since this occupies 256KB on the drive and reports it thus to the installer, because of the 'raw' formatting. Instead, therefore, use the following command:

```
# qemu-img create -f qcow2 <harddrive>.qcow2 5G
```This creates a filesystem of growing size, and works just fine. It will also be of size like 256KB but it shall report the full 5G to the installer, and will grow as data is written the filesystem becomes larger. Of course, one should then just do a 100G instead of 5G!

---

### Post by dcstar on 2010-05-09
> **rliegh said:**
> Not rubbish at all. As a matter of fact, the fact that two posts above yours the OP came back and said "I tried to install vmware but I could not" (his words) proves my point.

It is absolute rubbish because people try to install old versions of VMware products that are not 10.04 compatible.

I have already stated what version of VMware Player installs simply in 10.04, anyone is able to go to the VMware site, download and install it to find out for themselves.

---

