---
title: "Installing Elementary OS, cannot find os"
date: 2015-04-13
forum: Ubuntu/Debian BASED
---

### Post by 00101 on 2015-04-13
So I've tried several times now to get elementary os freya to install onto my Vaio pro 13 (svp132190X). I'm very new to linux, so there's a strong possibility I've ****ed something up somewhere. So the first few installations I attempted were in uefi mode and ended in getting a grub installation error and subsequently not being able to boot. I messed around with ways to get grub to install from a live usb, but was unsuccessful. I attempted an installation in legacy bios mode, which seemed to go through completely but then upon rebooting I was told that the operating system could not be found. I attempted to use boot repair to to fix the issue, but that just told me to reinstall in uefi mode. 

Which I did again, this time adding a /boot partition, which seemed to have allowed the installer to complete successfully. However, upon rebooting I was once again treated to 'no operating system found'. I tried running boot repair again grabbing the log files [before]("http://paste.ubuntu.com/10818250/") and [after]("http://paste.ubuntu.com/10818380/") running it. Still nothing. I am unsure of how to proceed, and any help would be greatly appreciated.

Thanks

---

### Post by Vladlenin5000 on 2015-04-13
I would start over...

1. If you intend to dual boot you must install the second OS (Ubuntu) in the same mode of the factory installed one (Windows 8.x). It means UEFI in your case.
2. Select "Something else" and remove all Linux partitions; create new partitions. Usually only / and *swap* are needed (the latter is now controverse) but redo as you wish.

---

### Post by oldrocker99 on 2015-04-13
If it's a new installation, do select "Something else." Then create two partitions, one / (root), and one /home. The / partition needn't be too big, 64 GB is probably enough. Tell the partition editor to mount that partition as /. Then create a partition from the remaining space and tell the partition editor to mount that partition as /home. If you do this, you can reinstall a system without restoring /home from a backup every time. What you do is select "Something else" again, and select the / partition to format, install, and mount as /. Then select the /home partition and tell it to mount as /home. Then all the programs you'll install will have all their settings intact.

BTW, /swap is usually automatically created in a first installation, and there's no need to reformat it at new installation time.

---

### Post by oldfred on 2015-04-13
Moved to other OS.

It looks like you changed sda1 from the ESP or efi system partition to sda8. You can only have one efi partition per drive.
Better to have sda1 as efi partition. You need to move boot flag from sda8 to sda1. 
Ubuntu/grub will install another folder for its boot files next to the Windows folder, so from UEFI you should be able to boot either system. 
But some vendors make it difficult. What brand & model system?

---

### Post by 00101 on 2015-04-13
I guess I should mention that there is no other OS present. The only reason I didn't select for it to overwrite the entire disk is because I have a recovery partition I'd like to keep (its a long story, but the partition isn't functional without a lot of developer software). 


I'll attempt to reinstall with just a root directory and try using the efi partiton at sda1.

---

### Post by 00101 on 2015-04-13
Well for some reason after installing with just a root and swap directories and using the efi partition at sda1 I get the error "A required device isn't connected or can't be accessed."

Literally no idea why I'd get an error like this, but yeah... 

Any other thoughts?

---

### Post by oldfred on 2015-04-13
That does not sound like Linux?

Is that from your UEFI?
And do you have secure boot still on, but installed with secure boot off?
Or booting in CSM mode, but install is UEFI?
Is drive set for AHCI?

What brand/model system?
Many brands have modified UEFI to only boot an efi entry that says "Windows".
If nothing else post Summary report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some of the fixes for vendor's who modify UEFI are in link in my signature.

---

### Post by 00101 on 2015-04-14
Its most probably from my uefi. The error from when I installed in uefi mode was also probably from my uefi as well. I've tried just about every combination of uefi legacy and secure boot, but I get the same errors each time, at least until this last one. As for the AHCI or not, I have no idea, my bios settings are absoultely pitiful, all I can really do is turn on/off a few ports and change boot order and uefi or legacy.

My model as I said before is the Vaio Pro 13 (SVP132190X). I'll try boot repair again and try to generate some logs again.

Thanks for the help so far

Edit: Here's the [log]("http://paste.ubuntu.com/10820153/") before running boot repair and here's the [log ]("http://paste.ubuntu.com/10820160/")after running boot repair again. Still getting the required device error.

---

### Post by oldfred on 2015-04-14
Sony is definitely one that only boots "Windows".

If you only have Linux, you change the name from ubuntu.
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
**d2**:  Disable Windows in UEFI and only boot from rEFInd or grub. If Windows is #1
sudo efibootmgr -A -b 0001

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
To restore Windows entry for dual boot - assumes sda1  add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

Others with Sony and dual booting have to copy grub and/or shim into a /EFI/Boot folder or create it and rename it to the hard drive boot entry file that is bootx64.efi. Instructions for that also in link in my signature.

---

### Post by 00101 on 2015-04-14
I'm sorry I really have absolutely no idea what I'm doing here. Would it be possible for a more detailed explanation of what I'm doing? Also, looking around my efi partition at sda1 is sony's vaio assist thing, rather than the boot loader that windows once used, which appears to have been at sda3. Should I remake the second efi partition and edit the boot loader there?

---

### Post by oldfred on 2015-04-14
You can only have one efi partition per hard drive.

Just run this:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by 00101 on 2015-04-14
Well I tried the command you provided, and it doesn't seem to have changed much as far as function of the computer goes. I still get the required device is missing error. I took a [picture]("http://i.imgur.com/jrPuUqM.jpg") of the terminal before closing out of the live disk so as to save the output if it was needed. 

As for only one efi partition, the laptop was indeed originally set up with two. One at sda1 and one at sda3. sda1 was called SONYSYS and the one at sda3 was the windows boot manager. 

Would it help if I made an image of the ssd as a back up and just wiped the whole thing clean and let elementary do everything automatically?

---

### Post by oldfred on 2015-04-15
Was one of the efi partitions hidden?
Did update to Windows description not work because one already existed?
Back up entire efi partition. (or both?)
If you do not have Windows delete Windows efi folder in efi partition.
Delete UEFI entry for Windows.
And then run command to create new Windows entry in UEFI that really uses shim.

Post this:
sudo efibootmgr -v

To delete Windows entry in UEFI:
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by 00101 on 2015-04-15
[Here's]("http://imgur.com/mDjX6SU") the output. I'll get working on the back up and then with deleting stuff.

---

### Post by oldfred on 2015-04-15
Just post text, no need for screen shot.

You are showing two Windows entries. Do not know if that creates issues or not.
But one is grub's shim and one is Windows boot file bootmgfw.efi file.

Does the one with shim work?

---

### Post by 00101 on 2015-04-15
Thank you so much. Deleting the previous windows entry now allows GRUB to load. Everything is working well. You are literally my favorite person right now.

---

### Post by oldfred on 2015-04-15
Glad you got it working. :)

---

### Post by assus on 2015-10-04
hi, i am new to linux and i have the same problem,if anyone could help ....??
[http://paste2.org/c4ww6kyU](http://paste2.org/c4ww6kyU)

---

### Post by oldfred on 2015-10-04
@assus
Did you go thru thread and run the changes needed. 
Particularly adding the "Windows" entry that really boots grub as in post #9.

You can also copy files from /EFI/ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi. You may also need a UEFI entry for UEFI: hard drive. 
Details of those changes are in link in my signature.

What brand & model system?

---

