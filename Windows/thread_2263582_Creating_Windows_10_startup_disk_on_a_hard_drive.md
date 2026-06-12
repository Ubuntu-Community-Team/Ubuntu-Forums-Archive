---
title: "Creating Windows 10 startup disk on a hard drive?"
date: 2015-02-01
forum: Windows
---

### Post by TriforceOfKirby on 2015-02-01
I want to install Windows 10, then later dual boot it with Ubuntu.

Currently I have Ubuntu 14.10.

My USB drive that I have is only 4GB, which is .2GB too small for creating a Windows 10 64-bit installation disk, but I do have a spare 320GB blank hard drive that I'm hoping I can use as an alternative installation media.

So is this possible?

---

### Post by Bucky Ball on 2015-02-01
*Thread moved to **Windows**.*

I can't see why not. Guess you would boot from the Windows install disk and select a partition on the 320Gb drive, or create one with the Windows installer. 

When you've finished, boot Ubuntu and:

```
sudo update-grub
```

... in a terminal. That should pick up the Windows install.

---

### Post by TriforceOfKirby on 2015-02-02
I don't actually have a Windows install disk, I have the .iso file, I want to make the 320GB hard drive a Windows install disk and boot off that. I can't seem to find a tool that can create a Windows install disk on a hard drive though. Unless, can GRUB boot a .iso directly?

---

### Post by Bucky Ball on 2015-02-02
> **TriforceOfKirby said:**
> ... can GRUB boot a .iso directly?

Not that I know of, you might want to research that, but Virtualbox (in the repos) and other virtualisation software can. That is another alternative. Install Virtualbox, or the virtualisation software of choice, and run the Win10 as a virtual machine 'guest' with Ubuntu as the 'host'. If you just want to try it out for now, that would probably be the best way to go.

---

### Post by yancek on 2015-02-02
>  Unless, can GRUB boot a .iso directly?         

Yes and no.  Grub2 can boot pretty much any Ubuntu or derivative iso and a number of other Linux systems or tools but not the proprietary windows.

I did this a few weeks ago, put the extracted windows tech preview iso on an external drive and started the install process.  Didn't install because the installer stopped saying it could not install to a usb drive and I had no where else to put it.  I'll post the notes I have on how it was done and after reading them, you will probably go with the suggestion by Bucky Ball to use VirtualBox.  Much easier.

 First create a partition on the external large enough to hold the iso files.  You can do this in 
GParted.  Open GParted and click the Partition tab, then click New and in the window which opens, 
select the size you want for the partition and ntfs for File system and Create as Primary partition.  Click Add then 
go to the check mark tab at the top and click it.  This is Apply operations.  It will create the partition and do the format.  
When it finishes, right click the new ntfs partition in the main window of GParted and select Manage Flags from 
the drop down menu and click the check box next to boot.  Again, right click the new ntfs partition 
and select Information.  You will see details about the partition.  Near the bottom is UUID and to 
the right of it a series of letters/numbers which is your UUID for that partition.  Write it down.   

Next you need to extract the windows iso files and copy them to this partition.  If you have your 
windows tech preview iso in your Downloads folder, first create a mount point for it.
I tried using the Disk Image Mounter and got a message the file was too large so I used this process.
I created a mount point in the Downloads folder:  
```
mkdir windows10
``` (Note that if you are doing this outside your /home/user directory, you will need to use sudo)
Then mount the file with:  

```
mount -o loop WindowsTechnicalPreview-x86-EN-US.iso windows10 
```

After doing the above mount command (and again, if done outside to /home/user directory you need sudo)
You need to create a mount point for the external drive partition and then mount it before copying files.
If the partition you created on the external is sdb1 create the mount point for it:

```
sudo mkdir /mnt/sdb1
``` (you don't need to use sdb1, it's just simpler and you need to be consistent)
Next do the actual mount: 

```
sudo mount -t ntfs /dev/sdb1 /mnt/sdb1
``` 

Then either use the terminal or a filemanager as root, using sudo, to copy all the files from the Downloads/windows10 
directory to the /mnt/sdb1 directory.  This will take a while.  When finished go to /mnt/sdb1 to verify 
the files/folders are there.  They should be similar to the below:

> autorun.inf  boot/  bootmgr  setup.exe  sources/  support/

Then as root on your Ubuntu, put the entry below either in the grub.cfg file and save it if you are only going to use it once
If you do this do NOT run update-grub, or put it in the /etc/grub.d/40_custom file and save it and do run:  sudo update-grub.  It should show in the boot menu 
when you reboot.  Before saving the change to the grub menu, you need to change the uuid number shown below to the one you got earlier.  I

menuentry "Start Windows Installation" {
 insmod ntfs
 search --no-floppy --fs-uuid 459532DE5D8D5C3A --set root 
 chainloader +1 
 boot
}

---

### Post by TriforceOfKirby on 2015-02-02
I already tried it out with VirtualBox, I would like to actually install it. I'll try the steps above, thanks. Also I should probably mention that it is an internal hard drive and not an external one, I assume the steps are the same?

---

### Post by yancek on 2015-02-02
> Also I should probably mention that it is an internal hard drive and not an external one, I assume the steps are the same? 		

Yes.  Make sure the partition you create on which to put the extracted iso file is formatted ntfs and is marked active/bootable as explained above.  That should not be a problem if all you have installed now is Ubuntu as Linux partitions do not need a boot flag which windows systems do.  Are you installing to the same hard drive you are installing to?  If you do that, I'm sure the windows 10 will overwrite your Ubuntu Grub.  It will be a lot less problem if you are installing to a second drive.  Make sure you have your Ubuntu installation medium handy so you can re-install Grub.  When you get it installed you will need to the partition you installed to as active.  Maybe that happens during the install, I don't know as I haven't installed any windows in over ten years.

---

### Post by TriforceOfKirby on 2015-02-03
Yes I'm going to overwrite Ubuntu with Windows 10. After Windows 10 is installed I'm going to dual boot with Ubuntu, thankfully Ubuntu fits on the 4GB USB drive.

Also quick question about partitioning, Can I use the whole drive space or do I have to make a small partition?

---

### Post by yancek on 2015-02-03
> Also quick question about partitioning, Can I use the whole drive space or do I have to make a small partition? 		

If you put the windows 10 installation files on a hard drive and install it to another hard drive, I would just let it create whatever partitions the installer wants.  Usually, the newer windows versions have a separate boot partition if pre-installed but I doubt that is necessary.  If you have UEFI and intend to use it, the installer should create the EFI partition and insert the correct files.  If you don't use UEFI, I would expect you could just create one partition to install.  I only installed it in VirtualBox so I guess the only way to find out is to give a try.  Make sure before you try booting the installed system that you said the new windows 10 partition to active.  Maybe the installer will take care of that for you as it will be the only system installed.

When you go to install Ubuntu, use the windows 10 Disk Management tool to shrink its partition before trying to install.  Just a note, if you do use UEFI with the windows install, you must use UEFI with Ubuntu.

---

### Post by TriforceOfKirby on 2015-02-03
I have UEFI as the PC originally came with Windows 8, does Ubuntu have any problems with it? I currently have it disabled.

---

### Post by yancek on 2015-02-03
I don't use UEFI but if you use the search function here at the forums, you should find a lot of posts relating to it.

---

### Post by TriforceOfKirby on 2015-02-03
Ok so I followed your instructions, everything seemed to work except on trying to boot "Start Windows Installation", it gives this:
```

error: no such device: 747E6617133E982D.
error: invalid EFI file path.
error: you need to load the kernal first.

Press any key to continue...

```
I know that UUID is correct for that partition, so I'm not sure what's wrong.
Should I use the volume name instead? (J_CCSA_X64FRE_EN-US_DV5)

---

### Post by TriforceOfKirby on 2015-02-03
Nevermind, I got it. Just had to select "System Setup" and select "Windows Boot Loader" as the boot device. Thanks for the help!

---

### Post by Bucky Ball on 2015-02-03
Good news. If you feel your original problem is solved, please mark the thread solved to help future travelers. See the second link in my signature for how. Good luck. ;)

PS: Marking the thread won't close it, just alerts others.

---

### Post by yancek on 2015-02-04
> Nevermind, I got it. Just had to select "System Setup" and select "Windows Boot Loader" as the boot device

I expect that is because of UEFI as I use MBR boot and didn't need that.  Congrats.

---

