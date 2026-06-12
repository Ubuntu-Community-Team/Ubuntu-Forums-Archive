---
title: "qemu windows 10 blue screen"
date: 2019-10-18
forum: Virtualisation
---

### Post by jkiem43 on 2019-10-18
When I start qemu windows blue screens most of the time. My command in the terminal is sudo qemu-system-x86_64 -hda /home/jake/VM/windows10.qcow2 -m 6G -cpu host,kvm=off -enable-kvm -smp cores=6,threads=2. It seems when I delete -cpu -smp and -enable-kvm options it starts but is very slow. I want to be able to enable kvm and -smp options. I've tried a bunch of different variants of the options but nothing really seems to work. I got it to work a couple times with the options that I want but it just seemed like luck and it crashed a couple times.

---

### Post by Skaperen on 2019-10-18
how many cores on your real hardware?  can Ubuntu run in the same setup and show the same number of core?  can you try it without [COLOR=#800080][FONT=courier new]**-enable-kvm**[/FONT][/COLOR] (and without [COLOR=#800080][FONT=courier new]**sudo**[/FONT][/COLOR])?

---

### Post by TheFu on 2019-10-18
People seem to want to do things the hard way. I never understand that.

First, verify that your CPU and BIOS are setup to support KVM.  There's a program - kvm-ok
```
$ kvm-ok 
INFO: /dev/kvm exists
KVM acceleration can be used

```
Until you see something like that result, you cannot use KVM.  Until that is possible, all virtual machines will be terribly slow.

Next, load up **kvm**, **libvirt** and **virt-manager** packages.  Then use virt-manager to create a fresh VM with 2 vCPUs and 4GB of RAM.  Do not use EFI BIOS for the install. Use Legacy BIOS.  Use "reasonable" options for disk controller (SATA is probably the best "sure thing" choice), network controller (Intel PRO/1000) and do a fresh install of Win10.  If the virtual disk is placed on an SSD, then using qcow2 is fine.  If it is put on a spinning HDD, then you'll want to use a raw image that is fully pre-allocated, pre-sized, to avoid terrible performance.

By default, libvirt controlled VM storage is placed in /var/lib/libvirt/ ... so ensure you either mount any needed storage there or provide symbolic links from that area to somewhere with a Unix file system that has sufficient storage available.  How to handle storage can be an enterprise discussion, but those are the easy answers for someone new. 

If you want more control over the networking of client VMs, you might want to install bridge-utils.  I learned long ago not to use the built-in virtual networking when performance was terrible. Hopefully, that has been fixed, but a manual configured bridge has never shown any performance problems, at least not since 2010.

Do not give the VM too much RAM or more than 2 vCPUs to begin.  You can add more later, if needed, but I doubt more will be needed. 

Virt-manager is like virtualbox or VMware Workstation or VMware vSphere's interface into ESXi.

Run that VM for a few days to see that it all works.  The graphics will be a little slow. There are fixes for that, but those are best handled after you are better acquainted with the system.  Come back with kvm video questions later and I'll try to help. There are many, many, many, options, but those all depend on how you will access the VM and many don't use any of the virtual machine video settings at all.

Virt-manager and libvirt can be installed on other systems and used to connect to the VM host system over an ssh-tunnel.

Oh - and with libvirt, you don't need/shouldn't be using sudo to run VMs.  Just use your normal account and let libvirt + KVM handle stuff.  Your userid should be added to the libvirtd group, if that doesn't happen, manually add it.

There must be 500 youtube videos on how to do the basic KVM + libvirt stuff.

---

### Post by jkiem43 on 2019-10-19
Thank you for the reply Shaperen. My real hardware has 6 cores and 12 threads. I quickly tried to boot linux mint but after I clicked on start linux mint in the boot loader it it goes to a screen with blue and red lines. Back to windows 10, when I run it without -enable-kvm it gives me "qemu-system-x86_64: CPU model 'host' requires KVM." Without sudo it tells me I dont have permission. I added my user to the root group but I still dont have permission. Im still new to qemu so I might be missing something simple.

---

### Post by jkiem43 on 2019-10-19
Thank you TheFu for the reply. I ran kvm-ok and acceleration can be used. I prefer not to use virt-manager. I like to know what my machine is doing and how it works at its core. Qemu seems pretty easy to use at the terminal Im just not sure what im missing.

---

### Post by jkiem43 on 2019-10-19
I am able to run it without sudo since I added my user to the kvm group. I still get a windows 10 blue screen. Im getting stop code: system thread exception not handled

---

### Post by jkiem43 on 2019-10-19
when I took off the -cpu host,kvm=off I was able to boot but got alot of "warning: host doesn't support requested feature". I dont think kvm is enabled when I do this

---

### Post by jkiem43 on 2019-10-19
Windows seems to be booting now with my original configuration. It did this before so I'm not really sure what's happening. Windows isn't displaying my current cpu though. In the last few days it has done this before but has also displayed my cpu model.

---

### Post by jkiem43 on 2019-10-19
Windows is now crashing again

---

### Post by usernamenotvalid on 2019-10-30
For what it's worth, I've bene having the same problem as the initial poster. The work around was to use a RAW format disk image. I did not test exhaustively, but every successful attempt had a RAW disk. The same source ISO installed and ran fine on Debian, and a VM that I installed on Ubunutu with a RAW disk, which I later converted to QCOW2, also worked on Debian. So something's up with Ubunutu 19.04 and it's released packages, far as I can tell.

---

### Post by jkiem43 on 2019-10-30
Thanks for posting. I'll have to try the raw format.

---

