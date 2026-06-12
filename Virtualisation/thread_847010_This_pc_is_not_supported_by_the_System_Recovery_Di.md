---
title: "This pc is not supported by the System Recovery Disks"
date: 2008-07-02
forum: Virtualisation
---

### Post by svk on 2008-07-02
Hello,

I'm interested in getting Vista to run as a guest in VirtualBox.  I have an HP dv6000 laptop, and I made a set of recovery discs under Vista.  However, the recovery discs refuse to install Vista under the virtual machine.  VirtualBox is able to boot Vista from the recovery discs, but it fails before the installation begins with this error message:

				 				[B]This pc is not supported by the System Recovery Disks
You will not be able to continue to recover this system with these discs.
[/B] 
This is a little silly -- it probably does that because it thinks I'm trying to copy Vista illegally or something.  The discs were probably expecting to find my exact hardware configuration that I had when I created the recovery discs, but of course, they won't find it under VirtualBox.  But my Vista is entirely legal, and I'm pretty determined to get this to work (there are some applications available for Windows only that I still need to run).

What are my options?

Vista did create a recovery partition (seen as the D:\ drive under Vista).  Is there anything I could with that (given that the recovery discs probably won't run)?

Is it possible to use my existing Vista installation and somehow configure VirtualBox to boot into that?

Please help!  This would be greatly appreciated!

---

### Post by bigken on 2008-07-02
thats because your recovery disc are bootable and need to install directly to the hhd from boot your recovery discs arnt the same as a normal windows install disc

---

### Post by svk on 2008-07-02
Ooh, I think I understand what you mean... Thanks for the explanation.

Well, I already have Vista installed on the hard drive, but I want to be able to run it using a virtual machine (Ubuntu as host, Vista as guest).  Is there any way I can do that?

---

### Post by bigken on 2008-07-02
the only way I can you doing this is with a normal install cd

---

### Post by bluefrog on 2008-07-02
Do you have the right to run your vista in a virtual machine? If premium for example, you do not have that right (read the EULA)

---

### Post by svk on 2008-07-02
I have the basic edition, so I guess I don't really have the right.

I guess it would be much easier to just boot into Windows and run Ubuntu from a virtual machine.  That's a bummer -- I've grown so used to Ubuntu that I pretty much live in it.  I only need Windows for a couple applications, that's all.

---

### Post by Keithel on 2008-07-03
Well, if you're careful, give [Sand Lee's great howto/post]("http://ubuntuforums.org/showthread.php?t=769883") a try.

Before you do that, MAKE A FULL BACKUP including boot sectors, etc -- try booting with a LiveCD and dd-ing the entire disk to a large removable drive -- like: dd if=/dev/sda of=/media/usbdisk/file bs=1M -- that way if you screw up, you can restore your system entirely.  No doubt this will take a long time -- so, I'd recommend doing it overnight (that's what I do :)

---

