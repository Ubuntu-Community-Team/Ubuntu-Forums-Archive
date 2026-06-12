---
title: "Intrepid Server Crashes on mount"
date: 2009-03-21
forum: Server Platforms
---

### Post by louvann on 2009-03-21
I have a Intrepid installation on a single drive computer which does a 'hard' crash on boot. Not being able to see is going wrong, I built on another single HD with a clean install of Intrepid. Then a physical install of the suspect HD as a ATA-slave HD, it shows in the device list as sdb and each of its partitions.
Mounting the suspect ext3 partition on this virgin server install also causes an instant crash of machine.

mount /dev/sdb5 /mnt/badHD

History on the suspect drive: I have been slowly adding functionality to a Intrepid install as a LAMP server over the last week. The last configuration was to add an external USB-HD and it's mount points. I had moved a large amount of data from the USB to internal so I could reformat the external USB-HD from FAT32 to ext3.  A reboot was the first evidence of problems. And the start of all my trouble.

How do I get data off this drive if I can't mount it?

---

### Post by cariboo on 2009-03-21
You may want to try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover your files. Testdisk is in the repositories and you can install it this way, at the prompt type:

```
sudo apt-get install testdisk
```

Jim

---

### Post by louvann on 2009-03-21
Here is some of the log lines,

I would guess that the time of the crash is at 15:15:44.

from     /dev/log/auth.log

 Mar 21 15:15:44 server3 sudo:     louv : TTY=tty1 ; PWD=/home/louv ; USER=root ; COMMAND=/bin/mount /dev/sdb5 /mnt/sys2

The next entries in any of the logs is 18:xx.yy when I rebooted to the new HD again.

None of the other log files I have looked at have any timestamp closer than a few minutes earlier. 

How do I get data off the drive, if I cant't mount it?

---

### Post by louvann on 2009-03-21
Thanks for the input on testdisk.
Your reply came in while I was composing.

I am running the application from a ssh login.

What is the partition type created by the installer for Ubuntu server?

---

### Post by louvann on 2009-03-21
I have found a corrupt partition table. But I can see the needed partition and it's directory structure. I have two choices, 1) fix the table and/or 2) pull off the contents. My first choice is 2) While I can see the directory structure, I am going for a backup. and then I'll try to fix the partition table in place.

It looks as though the 'testdisk' does not recover ext3 partition contents.  
--- from their site ---
TestDisk can undelete

    * files from ext2 filesystem,
    * files from NTFS partition since version 6.11,
    * files and directory from FAT12, FAT16 and FAT32 filesystem. 

If a lost file is still missing, give PhotoRec a try. PhotoRec is a signature based file recovery utility and may be able to recover your data where other methods failed. Note that it can recover deleted files from ext3 and ext4 filesystem. 


I will be trying PhotoRec next in my backup effort.

---

### Post by louvann on 2009-03-25
I need a different data recovery tool.
1) testdisk allows me to attempt tofix the partition table, but as yet without successful repair.
2) photorec attempts to recover the files but crashes after hours of manipulations prior to re-assembling the parts into anything useful.

Each of the other rescue software I have attempted has issues but with one common impairment. They all will crash the upon, what I assume is an attempt to mount the bad HD parts. 

 I have downloaded the following without any value, each boots and late in the startup crashes , I suspect due to the bad HD, unlike testdisk or photorec which must work in a different fashion. 
 I need a tool which, like testdisk or photorec does not attempt a mount anything  but can pull off data.


Gparted-Live
Ubuntu Rescue
Sysrescuecd 

I need a tool which, like testdisk or photorec does not attempt a mount anything  but can pull off data!

---

### Post by cariboo on 2009-03-25
The only thing I can suggest is try running fsck manually on the partition. Use the LiveCD.

Jim

---

