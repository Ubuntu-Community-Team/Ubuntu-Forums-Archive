---
title: "CD Rom drives and virtualization"
date: 2008-03-20
forum: Virtualisation
---

### Post by VeeDubb on 2008-03-20
I have a perfectly valid WinMe disk and I'd like to install it in a virtualized environment.

I have tried the free version of VMware, virtualbox, and the 15 day tril of parallels.

No matter what I do, I cannot get any of them to reccognize that there is in fact a bootable CD rom in the drive.  I've done everything I can think of, and I have rebooted my computer to make sure the disk really is functionaing and bootable.

No dice.

What very basic setup step have I missed? 

I'm using Ubuntu 7.10

Thanks

---

### Post by fjgaude on 2008-03-20
The only thing I can suggest is trying using a <ctrl-c> when you are starting the install of Windows after you have of course installed the vm console.

I'm not sure if any vm works with WinME... there might be a way, but I don't know it. Does it show as an option in say, vmware server? I answer my own question regarding vmware server: Yes. Okay.

---

### Post by VeeDubb on 2008-03-20
All three officially support Windows ME.  So, that's not the issue.

As for hitting ctrl-c while installing windows, that's not an option.  I CAN'T install windows unless I can get virtualbox, vmware or parallels to reccognize that there is in fact a CD with an OS install on it waiting in the drive.

---

### Post by fjgaude on 2008-03-20
I understand, but when do you actually put the CD in the drive? I remember putting it in just as I was in the middle of creating the vm, after I had selected all the options for the virtual machine. That's when you put the CD in the drive and then if necessary hit <ctrl-c>. It worked for me... I've only had to do it on my main box, as since then I've kept the vmx and used it over and over again.

Just thinking out loud. If Ubuntu sees the CD, unmount it in Ubuntu. Then try again, taking it out of the drive and putting it back in while in the console of the vm server.

---

### Post by VeeDubb on 2008-03-21
For lack of a better idea, I have deleted the VM, and recreated it about 20 times, randomly inserting the CD at different points in the creation process.

As for hitting ctrl-c, I've tried that at various points, though I can't see that point.

I have also tried unmounting the the CD, or running vmware/virtualbox/parallels as root, and that didn't help either.


If anyone has encountered this problem, I'd love some help.  It CAN:T be that rare of a problem.  I have not done anything to my Gutsy install that should effect CDROM access, so everyone here must have had to do 'something' to create a working vm.

Oh, and for the record, I have now taken 3 or 4 different bootable CD's, and gone so far as to make ISO's out of them, and pointing vmware/virtualbox/parallels at the ISO's for a cd drive, and I STILL get the same error messages about there not being any bootable media.

---

### Post by fjgaude on 2008-03-21
All I can say is that there is nothing special I did to create a vm for WinXP... I've done it in VBox twice and done it for VMware server three or four times.

There must be something about your CD drive that none of the programs like, but I can't say what.

The drive is recognized by Ubuntu, eh?

---

### Post by siepo on 2008-03-21
Try an iso image of the cd rather than the cd itself.

---

### Post by VeeDubb on 2008-03-21
As I said, I have already tried 4 different bootable CD IMAGES.  Not just the CD's.  I've created 4 different ISOs from 4 different bootable disks, and pointed my various vmware-type programs at those images instead of the actual drive, and for every single program and ever CD, and every CD image, I get the exact same response- "No bootable media detected."

---

### Post by Kiri on 2008-03-22
In virtualbox, try opening the log file (menu>machine>show log file) and see if it provides any more information or clues about what is going on...

---

### Post by Shazaam on 2008-03-22
VeeDubb.....
Do you know how to edit the vmware bios settings? Here's how to do it with VMware Player (should work with Server and Workstation too).........
1. Put your bootable cd in the cdrom drive.
2. Find your vm.
3. Double-click the vmx file.
4. When Vmware Player is booting the vmx you will see a boot screen.
5. With your mouse cursor click on a blank portion of the black screen so vmware can grab focus and as soon as you do that hit F2. This happens pretty quickly so don't hesitate with the mouse & keyboard.
6. If done quickly enough you will be presented with a bios screen.
7. Using your right/left keyboard arrow keys go to where it says "Boot"
8. Using the up/down arrow key highlight "CDRom Drive"
9. Hold down "Shift" and the + keys and move "CDRom Drive" to the top of the list. (instructions are on the right under "Item Specific Help")
10. Using the right/left arrow keys again move to "Exit" and choose "Exit saving changes".
VMWare will reboot and the cdrom should now boot.

---

