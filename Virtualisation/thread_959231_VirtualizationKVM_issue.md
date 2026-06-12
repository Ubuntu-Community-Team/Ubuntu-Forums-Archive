---
title: "Virtualization/KVM issue"
date: 2008-10-26
forum: Virtualisation
---

### Post by strange_cathect on 2008-10-26
Hello,

I'm following the advice I found [here]("http://tombuntu.com/index.php/2008/04/14/virtualization-with-virt-manager-and-kvm-in-ubuntu-804/") and [here]("http://www.greenhughes.com/content/virtualisation-with-kvm-and-virtmanager-kubuntu-804") to set up a virtual Windows XP on my system. Everything works fine until I actually begin the installation of the virtual XP.

As my attached screenshot indicates, I am getting a persistent message that "Setup cannot read the CD you inserted."

This is a genuine copy that I used before I converted to Ubuntu. I've searched high and low but cannot find anyone describing this problem or a workaround.

Any ideas?

---

### Post by strange_cathect on 2008-10-27
Please?

---

### Post by strange_cathect on 2008-10-29
Ok, I found something. This is a bug in the GUI for Qemu. A bug description may be found [here]("https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/238692"). However, there is a command-line workaround described there to fix the problem:
> 
qemu -no-kqemu -no-acpi -m 512 -cdrom /dev/cdrom -boot d XP.img


However, I can't seem to get it to work. Qemu tells me it "could not open disk image Xp.img.

Is this because I need to tell it where the image lives on my machine? It resides at /home/XP/Xp.img.

Can someone help me with the command-line?

---

### Post by bodhi.zazen on 2008-10-29
```
qemu -no-kqemu -no-acpi -m 512 -cdrom /dev/cdrom -boot d /home/XP/XP.img &
```

qemu will be slow, can you try KVM ?


```
kvm -no-acpi -m 512 -cdrom /dev/cdrom -boot d /home/XP/XP.img &
```

Also see this link :

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

The wiki page is a bit of a mess, but there is a section on running kvm from the command line and a script for networking.

Also use the man pages.

```
man qemu
```

The man page is well written and one of the best sources of information for options and fixes. Most qemu commands work for KVM.

---

### Post by strange_cathect on 2008-10-29
Hi thanks for your reply.

I tried the following command:

> qemu -no-kqemu -no-acpi -m 512 -cdrom /dev/cdrom -boot d

And now I have a set-up screen for Windows XP. My question: based on this command, where is this going to be installed? Should I continue?

How will I access the XP machine later?

Thanks for your help.

---

### Post by bodhi.zazen on 2008-10-29
With the command you listed it will not be installed anywhere as there is no hard drive.

If you include a physical partition or the Windows XP.img it would be installed there.

KVM can boot / install to physical partitions or if you use the XP.img a file.

---

### Post by strange_cathect on 2008-10-29
Ok, so I used the Virtual Machine manager to create an image called XP.img that is in a folder called XP within my home folder. But then, of course, the bug prevents the install. So I need to use the terminal.

Basically, what is the appropriate command line command to start the installation to that image file?

I tried:

> kvm -no-acpi -m 384 -cdrom /dev/cdrom -boot d XP.img

But I get:

> qemu: could not open disk image XP.img

I guess I need to tell qemu where the image is? I tried to add the following:
> 
 kvm -no-acpi -m 384 -cdrom /dev/cdrom -boot d /home/username/XP/Xp.img 

but it didn't work either.


Sorry for all the questions!

---

### Post by bodhi.zazen on 2008-10-29
No, that command will not create the XP.img file

You create the XP.img file with qemu-img

```
qemu-img create XP.img 10G
```

---

### Post by strange_cathect on 2008-10-29
Please note that I edited my prior remarks. And thanks for your help thusfar!

I was finally able to get the command to work. I had accidentally capitalized something.

> kvm -no-acpi -m 384 -cdrom /dev/cdrom -boot d /home/alan/XP/xp.img 

The installation began but it again gets hung up by not recognizing my CD Rom. Screenshot attached.

---

### Post by bodhi.zazen on 2008-10-29
I do not know about that one. I suggest you try :

1. Running the command as root

sudo kvm ....

It may be you need to be root to access your physical CDROM

2. Google search qemu install windows XP.

---

### Post by strange_cathect on 2008-10-29
Ok, thanks for all your help. Incidentally, using sudo did not help matters...

---

### Post by redbrain on 2008-10-30
What i would do is scrap using the ubuntu kvm package, its too old to be that reliable:

Follow my tutorials on my blog:
[http://redbrain.co.uk/?page_id=29]("http://redbrain.co.uk/?page_id=29")

[http://redbrain.co.uk/?page_id=35]("http://redbrain.co.uk/?page_id=35")

The only thing i havent put up there is decent documentation of virtio and more mem and newwer features and such.

I just find the qemu package in ubuntu is great but the kvm implementation is much much easier doing it as root and compiled from scratch :)

Remember you need to sudo your qemu-system-x86_64 commands, also check qemu monitor vvia ctrl-alt-f2 and do info kvm to make sure kvm support is loaded.

If there is an iso reading problem it will be on qemu's behalf because kvm is just a project like kqemu but much better :)

---

### Post by Weissbier on 2008-10-31
> **redbrain said:**
> What i would do is scrap using the ubuntu kvm package, its too old to be that reliable:

Follow my tutorials on my blog:
[http://redbrain.co.uk/?page_id=29]("http://redbrain.co.uk/?page_id=29")

[http://redbrain.co.uk/?page_id=35]("http://redbrain.co.uk/?page_id=35")

The only thing i havent put up there is decent documentation of virtio and more mem and newwer features and such.

I just find the qemu package in ubuntu is great but the kvm implementation is much much easier doing it as root and compiled from scratch :)


I second this!

BTW, can you maybe help me with some Networking Problems Redbrain? I used your tutorial and i would like to "open" a few ports to be able to access windows file-sharing's and other stuff from my guest system (Win-XP).
Topic is here: [http://ubuntuforums.org/showthread.php?t=965589](http://ubuntuforums.org/showthread.php?t=965589)

---

### Post by carfield on 2008-12-06
Hihi, I get the same "setup could not read the cd you inserted" issue, but using kvm doesn't solve the problem....


Will anyone have any idea?

---

### Post by strange_cathect on 2009-05-07
Carfield,

Is your XP disc really old? Like the first release w/o any updates? I'm beginning to think that this might have to do with it somehow...

---

