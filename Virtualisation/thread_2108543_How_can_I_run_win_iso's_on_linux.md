---
title: "How can I run win iso's on linux?"
date: 2013-01-24
forum: Virtualisation
---

### Post by PcMojo on 2013-01-24
I've gone to linux as my sole OS but still have an old XP disk that I assume I can virtualize. My question is: what do I need to do to play CD's/DVD's and ISO's that were meant to be installed on Windows? I don't mean movie DVD's or music CD's, I mean the type that would have a setup.exe or similar file on them for installation on a Windows system. Can I do this in Virtualbox? Do I need to setup some sort of persistence option so I won't have to keep reinstalling it?


Thanks in advance!

---

### Post by SeijiSensei on 2013-01-24
If you have a Windows CD and a valid license key, you can just install VirtualBox, then install Windows from the CD into a virtual machine.  It will operate just as if you had only Windows.  You can install software from CDs by the usual method of running setup.exe on the CD.

Once you install VB, create a New machine in the VirtualBox manager and follow the steps.  It's really quite simple.  For XP I'd allocate at least 512 MB of memory; 768 if you have a lot of physical memory available.

---

### Post by PcMojo on 2013-01-24
Thanks! When I set up the size of the virtual machine can I direct the path to my portable usb hard drive? I'm using a laptop and running out of HDD space.

---

### Post by alexii on 2013-01-25
Yeah, you can use your thumb drive. Unless you always want to run off the disk, you'll only need the iso once, after which you'll boot off your virtual hard drive (vdi or vmdk), which you can have on your thumb drive.

---

### Post by SeijiSensei on 2013-01-25
You can, but it will be a lot slower than using the internal hard drive.  I'd move some rarely-used large files to the external drive to free up space and install the virtual machine on the internal drive.

---

### Post by PcMojo on 2013-01-31
I think what I want to do is to take my external hard drive and direct an XP virtual machine to reside there and play win-based ISO's off my CD if necessary.  I fully switched to Linux and can't foresee me using windows that much. I understand it will be slow, as long as it doesn't take 5 minutes to load, I should be okay. I seem to have QtEmu installed. I'm running Cinnamon as a DE and I'm not sure if I should be running that or QEMU. After researching my issue, others that wanted to do the same thing said that I needed to use Virtualbox and download some extensions. Has anyone else run virtual machines from an external HDD (not a thumbdrive). My main concern is my external usb HDD is my backup and has many old files from previous crashed HDDs. I don't want virtualbox changing my NTFS drive to ext3 and/or formatting over all of my data. I played with Virtualbox before in linux and it put the virtual machine inside it's own partition (of the linux host OS). Does that mean virtualbox will want to put an ext3/4 partition on my NTFS drive? If it will allow using a NTFS as is, will it just put the vm in a folder or will it reformat or repartition my drive?  Sorry for all the questions but this is my backup of files I've had for years and I can't take any chances of wiping it out!

---

