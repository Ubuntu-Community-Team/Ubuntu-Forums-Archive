---
title: "Virtual machine says Starting up ... and hangs forever, why?"
date: 2011-01-27
forum: Virtualisation
---

### Post by EmreSevinc on 2011-01-27
Hello,

I'm a KVM newbie and I'm trying to create a virtual machine on my Ubuntu system (10.10 maverick). I have given the following command to create my first virtual server:

```
sudo vmbuilder kvm ubuntu -v --libvirt qemu:///system --ip 192.168.0.100 --hostname myvm --part vmbuilder.partition
```And the contents of my vmbuilder.partition is:

```
root 4000
swap 100
---
/var 2000
```When the command finished I had the following files in a ubuntu-kvm directory:

```
-rwx---r-x 1 emre emre   95 2011-01-27 11:23 run.sh
-rw-r--r-- 1 root root 116M 2011-01-27 11:23 tmpca9BaI.qcow2
-rw-r--r-- 1 root root 262M 2011-01-27 11:23 tmpVGAPyc.qcow2
```And I was able to list the machine:

```
$ virsh list --all
 Id Name                 State
----------------------------------
  - myvm                 shut off

```However when I run the machine via:

```
$ virsh start myvm
Domain myvm started

```and then try to connect to it via GUI-based Virtual Machine Manager it says (in the black boot screen): 

Starting up ...

and it is waiting forever (and my laptop's CPU hits %50 constantly):

[IMG]http://farm6.static.flickr.com/5094/5392188279_e9546c06f2_z.jpg[/IMG]


So, where did I go wrong, what am I missing? Doesn't vmbuilder build a bootable virtual machine by default, e.g. should I specify some packages at the vmbuilder command line?

---

### Post by sh1ny on 2011-01-27
As much as i like ubuntu stuff, i never got vmbuilder working the way i wanted. I'd suggest using either virt-manager to create the virtual machine or virt-install. Never had a problem with those. You will have to actually "install" the machine ( boot from the cd , etc ) just like you would install a real machine, but it works just fine.

---

### Post by EmreSevinc on 2011-01-27
Well, I tried the following:

```
$ virt-install --prompt
What is the name of your virtual machine? myvm2
 How much RAM should be allocated (in megabytes)? 128
 What would you like to use as the disk (file path)? myvm2.img
 How large would you like the disk (myvm2.img) to be (in gigabytes)? 4
 What is the install CD-ROM/ISO or URL? ubuntu-10.10-server-i386.iso
 

Starting install...
Creating storage file myv 100% |=========================| 4.0 GB    00:00     
Creating domain...                                                 0 B 00:00 
Guest installation complete... restarting guest.
```It opened a window and inside the window the installation began. Then it rebooted and I saw the GRUB screen for a 1-2 seconds then I don't know what happened, the screen within the window turned black and stayed so. I exited that window and now I'm trying to reach that virtual machine:

$ virt-viewer myvm2

and it opens a black screen within a window and nothing else (see screen-shot). I also tried to Send Keys, again no response from the black screen.

The file that is created by the virt-install is:

```
-rwxr-xr-x  1 emre emre 4.0G 2011-01-27 13:57 myvm2.img
```I also cannot see that virtual machine with virsh:

```
$ virsh list --all
 Id Name                 State
----------------------------------
  - myvm                 shut off

emre@emre-laptop:~/virtual-machine$ virsh list --inactive --all
 Id Name                 State
----------------------------------
  - myvm                 shut off

```What am I missing now? :-(

---

### Post by EmreSevinc on 2011-01-27
I realised that I had to use qemu:///session instead of qemu:///system so now I can do the following:

```
$ virsh -c qemu:///session list --all
 Id Name                 State
----------------------------------
  - myvm2                shut off

$ virsh -c qemu:///session start myvm2
Domain myvm2 started

```And when I do:

```
$ virt-viewer myvm2
```I can see the GRUB screen, I select the Linux kernel to boot and I press ENTER, the screen goes black again forever.

---

### Post by Jeruvy on 2011-01-31
> **sh1ny said:**
> As much as i like ubuntu stuff, i never got vmbuilder working the way i wanted. I'd suggest using either virt-manager to create the virtual machine or virt-install. Never had a problem with those. You will have to actually "install" the machine ( boot from the cd , etc ) just like you would install a real machine, but it works just fine.

Funny, I have had nothing but issues with virt-manager.

I can use qemu from the terminal no problem.
I can create machines using virt-manager no problem
They will not boot from (guest) hard disk.  
They will boot from qemu from the terminal.

---

