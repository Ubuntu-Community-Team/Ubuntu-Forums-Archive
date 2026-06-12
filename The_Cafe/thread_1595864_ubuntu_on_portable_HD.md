---
title: "ubuntu on portable HD"
date: 2010-10-13
forum: The Cafe
---

### Post by losthawken on 2010-10-13
Hey all,
 

 I'm new here, but I wanted to throw this out there to get feedback and discuss how I created my portable ubuntu system.  I'm really a novice at all of this and there may have been better methods (which I would love to hear) and there may also be problems I have not yet encountered that others may be able to predict.
 

 Essentially what I have done is created a personal portable operating system configuration on a portable hard drive.  It allows me to work in a consistent environment with all of my personal files, software, and settings by plugging into any computer that will boot from a USB.  In addition the system is designed to back-up both my work computer (on which which I cannot install Ubuntu due to policy) and my home computer and have all of the files from both available to me wherever I am.
 

 **Tools used:**
 

 Computer capable of booting from USB
 

 320 GB Iomega eGo (Nicknamed DataFlask)
 

 Ubuntu 10.04.1 Live CD (downloaded and burned .iso to CD)
 

 **Additional Software:**
 

 GParted
 

 Unison
 

 [Truecrypt]("http://www.truecrypt.org/downloads")
 

 **Step 1:  Partitioning**
 

 This was done using GParted on the Live CD.  The first thing to do was to create the partition set-up on the portable drive.  In order to keep my backed-up/synced folders accessible to the windows systems the first partition is left as a ~300 GB NTFS formatted partition.  Next next comes the boot partition; a 512 MB ext2 partition flagged as 'boot'.  And finally the ~20 GB extended partition with the ext4 section and the swap area.
 

   | 300 GB NTFS | 512 MB ext2 *boot || < extended | ~20 GB ext4 | swap | /extended > ||
 

 **Step 2:  Ubuntu install**
 

 From the Ubuntu Live CD I installed Ubuntu.  Using manual partitioning, I selected the portable drive and designated the ext2 partition to mount from /boot and the ext4 partition as the root ' / '.  IMPORTANT on the last page of the install wizard I selected the 'Advanced' option and designated the ext2 partition (sdc3 in my case) to be where the boot loader (Grub) is installed.   
 

 On restart I was able to log into Ubuntu on the portable drive with no problem.  Also, and most importantly, I did not erase the MBR on the HD of the computer I was working on (at least not on the second try).  Had I not selected the advanced option and designated where the boot loader would be, I would not be able to load Windows, or any system, without having the portable drive plugged in.
 

 **Step 3:  Setting up Security**
 

 Because this portable drive (which I will refer to as 'DataFlask') was going to contain all of my personal files and information the first thing I did was install Truecrypt.  Using Truecrypt I created a 100 GB encrypted file on the NTFS partition (FYI: this took several hours).  Because truecrypt works across platforms (i.e. works on windows and macs) and the file is located on the NTFS partition, all of my files are securely encrypted but still accessible when I'm not running Ubuntu.  I can just plug the DataFlask in while running windows and it functions like a regular external HD.
 

 **Step 4:  Setting up file syncing**
 

 To sync my files between computers and the DataFlask I chose to use Unison ('sudo aptitude install unison-gtk') because again, it is a cross platform software, and because it will sync both ways between folders.  Using Unison I synced my user folder under windows (C:/Documents and Settings/usrname) to a file I called 'Work' within the truecrypt volume.  I then went home and synced my home user folder to a separate folder in the truecrypt volume called 'Home'.
 

 At this point I had a mountable, portable Ubuntu system with access to all of my personal files on whatever computer I boot into into.   Also, the files are still accessible when plugging the DataFlask into a system already running Windows or MacOS (although I haven't tested it on a Mac).
 

 As an added benefit the DataFlask and Hard Disks of each computer serve as back-ups for one another; protecting my files should one of the drives fail.
 

 **Step 5:  Making it easier on myself**
 

 I found it most efficient to save files to the truecrypt volume while operating in Ubuntu and then sync to the 'real' HD before shutting down.  I put two folders on the Ubuntu desktop labeled 'Work' and 'Home' respectively.  Within each I put links to the 'Desktop' and 'MyDocuments' folders on the synced  folders for each windows computer within the truecrypt volume.  This allows quick access to the files I care about in an organized way.
 

 **Drawbacks/problems I've found:**
 

 Obviosuly, start-up is not as fast as it would be if install on the computers own HD.  There is a scary blank screen that stares at you in between choosing the OS in grub and visibly seeing Ubuntu load. However, being used to older computers running WindowsXP, I've actually been impressed by how quickly Ubuntu gets up and running and once up everything zips along as would be expected.
 

 The Ubuntu system itself is not encrypted, therefore files saved anywhere other than the encrypted volume are vulnerable should the drive get stolen.  I'd love to hear ideas on how to retro-encrypt the Linux  system.   
 

 GParted seems to cause errors in the disk, even when not touching the partitions on the DataFlask.  This results in unstable mounting of all media drives while using Ubuntu and failure to load Ubuntu on restart.  Running fsck on the system drive either before rebooting using -force or using the Live CD seems to fix the problem when it crops up.  I'm considering scripting fsck to run on every boot since it is so quick and easy.
 

 Because the boot set-up is arranged in a sort of awkward way (at least to me) I once ran into trouble when I tried to update to maverick 10.10.  Doing this broke Grub and would drop me at the grub rescue command line instead of loading.  Someone with more experience with grub and boot loaders probably could have fixed it, but despite my best efforts I couldn't and ended up reinstalling everything.
 

 Unison sometimes runs into trouble with permissions discrepancies, probably due to the differences between how Windows and Lynux deal with them (?).  Running Unison from the command line using unison syncfile -perms=0 fixes the problem.


I've been using this tool for the past 3 months or so and its been absolutely amazing.  Everything I want is at my fingertips whenever and wherever I want it.  Very useful for a graduates student that often brings work home.

Let me know your thoughts and how something similar could be done more simply or flaws and problems I haven't spotted yet.  Thanks!

~JG

---

