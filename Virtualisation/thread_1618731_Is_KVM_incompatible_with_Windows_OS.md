---
title: "Is KVM incompatible with Windows OS?"
date: 2010-11-11
forum: Virtualisation
---

### Post by tkman26 on 2010-11-11
Hi all.
I have been reading the forums trying to figure out a solution for my needs.
I want to be able to run Ubuntu Desktop, Windows XP, Windows 7 as a minimum.
I will use the Ubuntu Desktop as my main user OS, but I support clients who are Windows XP and Windows 7 based so need these as well.  I will also experiment with other Linux server configurations.
After reading, I decided on a Linux server as the host for the Virtual OS's.  I like Ubuntu so I chose it and installed 10.10 64 bit.  During the install I noticed the option for Virtualization support so I selected that.
However I am now reading the forums on virtualization and I see recommendations that KVM is not good for gui based OS's.  Is this correct?
If yes I expect I need to uninstall the KVM, and install something like VirtualBox which does support gui based OS's.
Any thoughts, corrections, or confirmation of what I have found would be appreciated.
Thanks in advance.

---

### Post by darkhelmetchris on 2010-11-11
> **tkman26 said:**
> Hi all. I have been reading the forums trying to figure out a solution for my needs.
I want to be able to run Ubuntu Desktop, Windows XP, Windows 7 as a minimum.

Hi tkman,

I am a little "green" when it comes to KVM under Ubuntu.  I am afraid I just don't know much about it.  However ... I have used both VMware and VirtualBox for running Windows and have had very good results with it - both for speed and compatibility.  I use Linux servers regularly, and use VMware player or VMware server as a Linux host to support Windows as a guest OS.  I think you'll find that very easy to do, especially with VirtualBox.  I find VMware to be faster/better generally, but VirtualBox is still excellent, and is certainly easy to configure.  That's my 2 cents.

---

### Post by gdahlm on 2010-11-12
It really depends on what you want but I have fully migrated off virtualbox to KVM on my workstation at work.

I need to run windows 7 for some management tools and outlook.

KVM will serve out the virtual machines display as a VNC display but I found that limiting due to the low resolution of the default video configuration.

Luckily if you are running windows 7 pro you can use RDP to access your host.  Unfortunately Windows 7 (starter|home|home premium) don't support allow you to use RDP except in a support situation.

XP will allow you to but I haven't tested it.

If you just need to have minimal Windows access try the following in a shell prompt.

sudo apt-get install virt-manager

Virt manager greatly simplifies the configuration of qemu-KVM if you are not that familiar with libvirt.

If you do want to use RDP I highly recomend installing remmina and remmina-plugin-rdp

It also has a gnome applet called remmina-gnome that will allow you to have quick connects from your gnome panel.

It has good functional shared clipboard that unlike virtualbox does not require drivers on your host.

I usualy make the machine full screen then I use the default gnome hot keys of <ctl><alt><arrow key> to move between workspaces.

This allows me to cut and paste between ubuntu and windows very quickly and it feels like your are on a pure windows host while you are in the workspace occupied by the windows RDP session.

It also allows me to run at the full native resolution of my monitor which is very nice.


If you want the best performance out of windows on KVM you will want to set up your host to use the "virtio" driver model

You can download a floppy image and a CD image from fedora that works during the install

Either give your host a second CD or a floppy drives and when windows can't find a disk to install on it should ask you for additional drivers

You can download them here

[http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/bin/](http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/bin/)

If you have already installed windows 7 with another device model (IDE or SCSI)

you can present a small additional disk to Windows 7 and when it asks for drivers use those disk images to add them.

if you then shut down the machine and either remove and re-add your boot disk as a virtio disk in virt-manager and start the machine you should be running on a the paravirt drivers, they will speed up your machine significantly.

Best of luck,

Greg

---

