---
title: "vmware won't boot after i add a hard drive"
date: 2008-08-27
forum: Virtualisation
---

### Post by beaver29 on 2008-08-27
i have a serious problem and i'm desperate to find a solution.

i'm running Ubuntu 7.10 as a guest under VMWare player 2.0.1 on a Windows XP host.  i ran a poorly written install package and it nuked something in my Ubuntu install.  now i can't boot the virtual machine.  unfortunately that machine has most of my work files and i haven't backed it up for over four months.  (i know, i know, what an idiot!!!)

i'm trying to recover the data in my .vmdk disk image without booting from it.  i tried several ways to mount the corrupted .vmdk on my Windows host, all without success.  then i found this cool post:

  [http://ubuntuforums.org/showthread.php?t=803411&highlight=vmdk](http://ubuntuforums.org/showthread.php?t=803411&highlight=vmdk)

which seems like my best shot at recovering this data.  i installed VMWare server 1.0.6 on another machine with a windows XP host and then installed a new Ubuntu virtual machine.  that boots just fine.  then i tried adding my corrupted .vmdk file as a second hard drive.  VMWare configures it to be a SCSI (0:1).  when i start the new virtual machine with the second hard drive, it won't boot.  it goes thru the grub loader OK, i see the Ubuntu logo page and then it freezes with a blank orange screen. 

the only other possible approach i've found is to convert the .vmdk file to a VHD file but i haven't found any free, downloadable software that would be able to mount or read a VHD file.

i will continue scrambling for answers but i'm in way over my head.  it's taken me two long days just to get to this point and it would be good if i could fix this before my boss finds out what happened!  i'm hoping someone has an idea or can point me to a prior post in the forum.  thanks!

---

### Post by Shazaam on 2008-08-27
If you run out of ways to get the files from the Ubuntu guest try this....
Try to boot the failed 7.10 guest. As VMware first starts make sure it has captured the mouse/keyboard; hit F2 (quickly click inside the blank window) to get to the VMware Setup screen (similar to a bios setup screen). Go to BOOT, use your - (dash) keyboard key to move CD-ROM DRIVE to the top. This sets the cd/rom as the first boot device on the vm. Then go to EXIT, EXIT Saving Changes. Put a Ubuntu Livecd in your drive then click enter (the vm will reboot). This should get you a livecd virtual machine. Once you get to the desktop see if you can get to the files you need. Depending or not on if you have internet access from the virtual Ubuntu Livecd you can either try to copy/paste (or drag/drop) the files to your host or set up Evolution and e-mail the files to yourself.

---

