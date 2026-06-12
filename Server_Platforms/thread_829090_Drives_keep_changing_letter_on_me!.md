---
title: "Drives keep changing letter on me!"
date: 2008-06-14
forum: Server Platforms
---

### Post by batty on 2008-06-14
I am setting up a server at home. With the help of these forums and Google I have it almost working!

My server consists of 1 80Gb IDE drive which I have installed the OS on.
I have set up 4x500Gb SATA drives as Raid5 using the Mdadm command.
All seemed fine but I've noticed after a reboot my OS drive which is /dev/sda and one of the raid5 drives /dev/sde keep swapping so Fdisk sees sde as having the OS not sda.
What am I missing so I can stop this from happening?

Dave

---

### Post by batty on 2008-06-15
Just out of interest why is my IDE drive showing up as /dev/sda and not as /dev/hda ?

I thought sda were for SATA drive and hda for IDE.

---

### Post by shad0w_walker on 2008-06-15
They changed the IDE library a couple of releases ago, the new one uses sd for IDE devices as well.

---

### Post by batty on 2008-06-15
Well I got fed up with trying to sort this out!

I have now installed Debian Server and no longer have this problem.

Debian does still use hda for the IDE drive, don't know if that is the reason it works or not.

---

### Post by nix4me on 2008-06-15
This is a common problem.  To fix it, use UUID entries in /etc/fstab instead of drive letters.  This will ensure they wont change.

Search UUID on the wiki for instuctions on how to do this.

---

### Post by fjgaude on 2008-06-16
The command **blkid** shows all the UUIDs on the system.

---

### Post by batty on 2008-06-16
I seem to remember that my boot drive sda was setup in fstab using the UUID method by default,that's why I was surprised to see drive change.

Should I have tried setting raid using UUID instead of /dev/md0 in Fstab as well?

I may reinstall using Ubuntu server again later.

I noticed in the original Fstab that the boot drive had # at the start of the line,does # mean the line is commented out or is the # for another reason?

Cheers for help

Dave

---

### Post by fjgaude on 2008-06-16
In fstab # means comment. In menu.lst it can mean other things, especially in two certain lines of the file.

It seems that the naming and the UUID generation is different. Name change but the UUID is associated with a specific device, drive, and that never changes... it's embedded in the header of the device by serial number notation.

When it comes to mdadm raid UUIDs take on another task. The UUID made by mdadm is not the same as the one made by the kernel and which shows with **blkid**. All this is strange but needs to be learned and honored.

---

### Post by batty on 2008-06-16
> **fjgaude said:**
> In fstab # means comment. 

So I would need to remove the # from the Fstab file then?

Dave

---

### Post by fjgaude on 2008-06-16
I don't think so, unless you wish to mount to /dev/sd[nn]. The UUID= is just below the drive name?

For your /dev/mo0 array use its name, not its UUID... that should work. Leave all the other UUIDs in the fstab as they are. mdadm doesn't use the drive names to assemble but the superblocks and the array UUID that it uses internal to each of the drives.

If you wish to mount the md0 array using its UUID, use the command **blkid** to get it.

---

### Post by batty on 2008-06-16
fjgaude, Thanks for your help.

I have reinstalled Ubuntu server 8.04.
I have looked at Fstab and it only comments out #/dev/sda1 and underneath mounts using UUID.The # is obviously there to just to inform you what it's doing. I looked too quickly and didn't pay attention. :oops:

I believe my problem may be related to incorrectly building my raid array using mdadm.

I used sudo mdadm -Cv -l5 -c64 -n4 -pls /dev/md0 /dev/sd{b,c,d,e}1
I thought this would give me a 4 disk raid5 array. What it actually did was try create a raid5 4 disk array with a spare disk,which I obviously didn't have installed!
So when I used mdadm -examine it shows my array as have 1 disk faulty and sde1 as spare!!

I have since recreated the array using :- 
sudo mdadm -Cv -l5 -c64 -f -n4 -pls /dev/md0 /dev/sd{b,c,d,e}1
Note the -f forces all 4 disks to be used,no spare allocated.

Hopefully once array is rebuilt problem will go away :rolleyes:

I have to say this has been a long and painful process!
But I have learned lots and lots and made huge great piles of handwritten notes.

For anyone new reading this,stick with the server edition and keep banging away at the command line prompt.It will be worth it in the end. 
Don't give in!!

Dave

---

