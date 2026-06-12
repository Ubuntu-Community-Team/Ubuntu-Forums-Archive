---
title: "RECYCLER virus"
date: 2009-08-05
forum: Security
---

### Post by Angel Villablanca Luoni on 2009-08-05
I have two HDs in my PC, one with Windows XP and the other with Ubuntu 9.04.
Generally I have no problems deleting Windows viruses from Ubuntu, including the famous RECYCLER, but recently one of my pen-drives was infected with this virus, putting a not writing permission, so I can not delete nothing in this device, not even format it.
I have tried with many commands, like rm -rf; used gparted, and I  can do nothing to obtain a solution, because I can not change the permissions of nothing.
¿Somebody has experience with this extreme situation?

Greetings,
Angel

---

### Post by lensman3 on 2009-08-05
You can always try:

dd of=/dev/<pendrive> if=/dev/urandom

This should write to the hardware random bytes.  It skips the file system layer and writes bytes to the device.  This should scrub whatever is on there.  (Make sure that it is not mounted when you do this.  You might have to be in single user mode so that a bare Linux is running).

After that you will have to do a mkfs.dos on the device to put a file system back on.


You have nothing to loose.  Hope this helps.

---

### Post by cdenley on 2009-08-06
Are you sure you didn't flip the write-protect switch by accident?

---

### Post by Angel Villablanca Luoni on 2009-08-07
> **lensman3 said:**
> You can always try:

dd of=/dev/<pendrive> if=/dev/urandom

This should write to the hardware random bytes.  It skips the file system layer and writes bytes to the device.  This should scrub whatever is on there.  (Make sure that it is not mounted when you do this.  You might have to be in single user mode so that a bare Linux is running).

After that you will have to do a mkfs.dos on the device to put a file system back on.


You have nothing to loose.  Hope this helps.



Dear fellows:
Unfortunately the system do not acept the instruction:

dd of=/dev/<pendrive> if=/dev/urandom

With the reply: "Folder or directory does not exist..."

And the device has not any flip blocked. Indeed since many years I have not seen a pendrive with any flip system.

Maybe I must operate from root? Well, I shall continue trying to solve the problem...

Thanks a lot,

Angel

---

### Post by Agent ME on 2009-08-07
Right-click the recycler folder. Click properties. Click permissions tab. In Owner section, set folder access to "Create and delete files" and file access to "Read and write". Near the bottom, click "Apply permissions to enclosed files". Close the window, and now you can delete the folder holding the virus.

---

### Post by arashiko28 on 2009-08-07
This happened to me once and though the operation was successful, the pen drive died...:(
Anyway, I got my way into the pen drive trough terminal and copied all that I needed before trying anything.
Next I did was looking for the forum note that says dangerous commands, and then the rm -rf... had many troubles to do so, and in the end I had an empty useless drive, so I went to gparted and after unmount tried to format it... anyway I learned a lot...
PS: When windows has a virus and passes it to the pendrive, you can't remove it, not even on the safe remove step, some people just click and pull out without waiting the message, outcome: an useless drive.

---

### Post by ikt on 2009-08-08
> **Angel Villablanca Luoni said:**
> Dear fellows:
Unfortunately the system do not acept the instruction:

dd of=/dev/<pendrive> if=/dev/urandom

With the reply: "Folder or directory does not exist..."


Did you replace **<pendrive>** with the correct value?

---

### Post by garikaib on 2009-08-08
Try
sudo mkfs.vfat /dev/<pendrive> in the terminal.

---

### Post by juancarlospaco on 2009-08-08
Use **sudo **

And please send the Virus to ClamAV
:)

---

### Post by Angel Villablanca Luoni on 2009-08-10
> **Agent ME said:**
> Right-click the recycler folder. Click properties. Click permissions tab. In Owner section, set folder access to "Create and delete files" and file access to "Read and write". Near the bottom, click "Apply permissions to enclosed files". Close the window, and now you can delete the folder holding the virus.

-------------------------------------
Thanks for the advise, but that was the first thing I did, with no positive ressults.

Geetings,

Angel

---

### Post by Angel Villablanca Luoni on 2009-08-10
> **arashiko28 said:**
> This happened to me once and though the operation was successful, the pen drive died...:(
Anyway, I got my way into the pen drive trough terminal and copied all that I needed before trying anything.
Next I did was looking for the forum note that says dangerous commands, and then the rm -rf... had many troubles to do so, and in the end I had an empty useless drive, so I went to gparted and after unmount tried to format it... anyway I learned a lot...
PS: When windows has a virus and passes it to the pendrive, you can't remove it, not even on the safe remove step, some people just click and pull out without waiting the message, outcome: an useless drive.

------------------------------
Arashiko, almost weekly I must remove RECYCLER from my pendrives or fiends, with no problems from Ubuntu, Nautilus and directly deletion. This is the reason why I am very angry with my only "rebel pendrive".

Greetings,
Angel

---

### Post by Angel Villablanca Luoni on 2009-08-10
> **ikt said:**
> Did you replace **<pendrive>** with the correct value?

-----------------------------------
Yes, I wrote /media/VILLABLANCA_ instead of pendrive. Or I must write sdc1 instead /VILLABLANCA_ ?

Regards,

Angel

---

### Post by Angel Villablanca Luoni on 2009-08-10
> **garikaib said:**
> Try
sudo mkfs.vfat /dev/<pendrive> in the terminal.

-------------------------
Garikaib, I wrote the instruction with mkfs.fat and the reply was: "command not found".
Then, I wrote only with mkfs and the reply was: "Read only command while adjusting the superblock". 

Regards,
Angel

---

### Post by cdenley on 2009-08-11
> **Angel Villablanca Luoni said:**
> -----------------------------------
Yes, I wrote /media/VILLABLANCA_ instead of pendrive. Or I must write sdc1 instead /VILLABLANCA_ ?

Regards,

Angel

You want to write to the drive directly (/dev/sd??), not the mount point (/media/???), and the drive SHOULD NOT be mounted when you do that.

You could try erasing the partition table of the drive
```

sudo dd if=/dev/zero of=/dev/sdc

```

or you could try simply re-formatting the fat filesystem
```

sudo mkfs.vfat /dev/sdc1

```

---

