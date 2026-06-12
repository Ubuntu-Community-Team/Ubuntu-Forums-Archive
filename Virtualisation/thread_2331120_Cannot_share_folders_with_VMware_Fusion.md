---
title: "Cannot share folders with VMware Fusion"
date: 2016-07-18
forum: Virtualisation
---

### Post by tjrob137 on 2016-07-18
I am new to Ubuntu, but have used Red Hat and its derived Scientific Linux for ~20 years. I am a very experienced software developer, and have written Linux kernel drivers for custom hardware.

I have installed Ubuntu 16.04 into a VMware Fusion virtual machine. But the two versions of VMware tools are fighting -- there is a package open-vm-tools and the version that VMware Fusion provides. Neither works to share folders with my Mac. This basically makes it useless for me.

On the new system, open-vm-tools was installed. In the VMware Fusion settings I removed and re-added the folders I need to share. But /mnt is still empty (no hgfs directory). Some of the VMware tools seem to be running, in that I can re-size the window, and can cut-and-paste between guest and host, but no shared folders. So I Google the problem...

I did "sudo apt-get remove open-vm-tools open-vm-tools-desktop" And then installed the VMware tools from the CD-ROM that VMware Fusion provides. It tried to compile the kernel modules, but the compilation failed in the vmhgfs module with dozens of errors. In addition, the ability to cut-and-paste between guest and host has been lost, so I cannot show you the errors.

How can I get this to work? -- I need to share folders on the host Mac to the guest Ubuntu. (I have many VMs running Red-Hat-derived Scientific Linux, and they all share folders just fine.)

---

### Post by howefield on 2016-07-18
Thread moved to the "*Virtualisation*" forum.

---

### Post by MAFoElffen on 2016-07-18
There is a problem with the package open-vm-tools at the moment when trying to use it with 16.04. Both VMware Support and "us'" have found that of you uninstall open-vm-tool (remove --purge), then use VMware tools, then everythiign works with that.

Personally, I think open-vm-tools is just a little behind on support for the new release and will take a little time to catchup... but VMware, since that toolset is basically the same for most of their product line, paid products have a lot more resources to be able to keep their code up to date.

---

### Post by tjrob137 on 2016-07-19
That's what I found via Google, and what I tried (removing open-vm-tools and using the VMware tools; but I didn't use "--purge"). Building the VMware tools failed with dozens of compile errors. I'm away from that system today, but tomorrow I'll try again.

---

### Post by MAFoElffen on 2016-07-20
>>"Building the VM Tools failed" ???

VM Tools is in an iso form, that downloads and installs from within VMware programs itself right? At least that is the way it works from within VMwarte's Player, Workstation, Workstation Pro, and vSphere Client. I do not have a Mac, so have not used Fusion, but I would assume since that is how it is with all their other products, that it would be the same for it.

I just select "Install VM Tools from within those programs, and it gives a message as "Installing VM Tools to  guest". From what I can see in vSphere, is that it is not just 1 tools, but is based several(?), which I assume it picks which flavor, based on the environment it needs for the OS of the guest.

---

### Post by tjrob137 on 2016-07-20
Yes, building the VMware tools fails. Badly. I did "sudo apt-get remove --purge open-vm-tools open-vm-tools-desktop", and then "sudo rm -fr /etc/vmware-tools /usr/bin/vmware-tools" (because those seemed to get left behind). I got the VMware tools from the CD-ROM that VMware Fusion mounted in Ubuntu when I said "Install VMware Tools". I unpacked the tarball into $HOME/vmware-tools-distrib, did "cd $HOME/vmware-tools-distrib", and did "sudo ./vmware-install.pl". I accepted all the defaults. I have attached the relevant portion of the Terminal window to this thread as "zap.txt". These errors look like there is a major disconnect between Ubuntu and VMware.

This is CRAZY -- the only way I could get the output from the compile into this thread was to mount a USB stick into Ubuntu, copy the file, eject it, pause the Ubuntu VM (otherwise the stick is always mounted into the Ubuntu VM), and then re-insert the stick so my Mac can see it and upload it into this thread.

Ubuntu is useless for me until I can get folder sharing from the host in VMware Fusion. I support a scientific simulation program, and have been supporting Linux for more than a decade. Recently my builds on Scientific Linux (derived from Red Hat Enterprise) have been failing for users using Ubuntu (even when I have them copy in the system .so-s), and I would like to support Ubuntu for my users. I thought that would be easy, given that I already support it on another Linux distribution -- it seems not :(.

---

