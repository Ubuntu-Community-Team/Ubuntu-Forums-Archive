---
title: "I have Ubuntu 6.06 Installed, want to install Windows"
date: 2007-02-10
forum: Windows
---

### Post by Diffusio on 2007-02-10
(before I dive into this post, if there's a thread/guide that will help me, please post it)

Here's the deal:

**I have:** Ubuntu 6.06 installed on my laptop already. I used to have windows, but reformatted and erased it. 

**I want:** To install Windows XP Professional. I'd also like to dual boot these (with some kind of ease).
[B]
What would be the easiest route to do this? [/B]I've already began backing up important files.

I'm running an Acer Travelmate 2420 (laptop) in case this affects it.

---

### Post by housam on 2007-02-10
Install windows and then reinstall grub to get windows booting and have a dual boot.  

[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by Diffusio on 2007-02-10
Well how would I go about installing windows? Do I partition my Ubuntu's hard drive (it's 40gb)? What do I use to do this?

---

### Post by Vorian on 2007-02-10
[LEFT]*moved to windows forum*
[/LEFT]

---

### Post by Diffusio on 2007-02-10
Thanks, can anyone help?

---

### Post by housam on 2007-02-10
Use Gparted ( on the live cd ) to resize ubuntu partition to make room for windows ( 10 Gb ). This will leave an unallocated space which will be a new ntfs partition .

---

### Post by trondhuso on 2007-02-10
I have recently done what you want on my new Dell laptop. Here is the "log":

Installation of Ubuntu Edgy Edge Dual Boot on Dell Latitude D420
Facts: Dell D420 comes preinstalled with Windows XP Professional and also with some utilities in a hidden partition. 
Without the hidden partition the Dell rescue CD won't work, therefor it is of importance to save this one. The computes is also to be used with work so WinXP Pro had to be saved.

In some How Tos there is mentioned that you can use the Gnome Partition Manager-tool to resize the Windows Partition of NTFS-type. On my Dell this didn't work, so I had to do this in terminal.
Remember to "run" the utility with sudo.

The Dell D420 comes with a 80gb harddisk and so I put aside 20 gb for Windows. When most of the things I needed/wanted was installed. 8gb was used. So 12 GB more would make space for quite a lot. 
The command for resize is:
sudo ntfsresize -s G20 /dev/hda2

When ntfsresize is done you get the message below:
IMPORTANT: When recreating the partition, make sure you
  1)  create it with the same starting disk cylinder
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you may lose your data or can't boot your computer from the disk!

So you have to run fdisk. 
sudo fdisk -l /dev/hda (to list the partitions which is a good idea so you know which partition the one with NTFS is)
sudo fdisk /dev/hda (to enter fdisk)

**The commands below (From [http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html) so change the values to match your system)**

# fdisk /dev/hda

Command (m for help): p

Disk /dev/hda: 255 heads, 63 sectors, 2480 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/hda1   *         1      2479  19912536    7  HPFS/NTFS

Command (m for help): d
Partition number (1-4): 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-2480, default 1): 1
Last cylinder or +size or +sizeM or +sizeK (1-2480, default 2480): +11140M 

Command (m for help): t
Partition number (1-4): 1
Hex code (type L to list codes): 7
Changed system type of partition 1 to 7 (HPFS/NTFS)

Command (m for help): a
Partition number (1-4): 1

Command (m for help): p

Disk /dev/hda: 255 heads, 63 sectors, 2480 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/hda1   *         1      1355  10884006    7  HPFS/NTFS

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

I have followed most of what I found in guides at LinuxDevCenter ([www.linuxdevcenter.com/lpt/a/6554)](www.linuxdevcenter.com/lpt/a/6554)), The Dual Boot How To at [http://www.hezardastan.org/breezy_xp_dualboot/en/index.thml)](http://www.hezardastan.org/breezy_xp_dualboot/en/index.thml)).

2) Now you have resized the Windows Partition and the rest now is just installing Linux on the rest of the harddisk. You should now check to see if your Windows version is working. If it does, great. If it doesn't, you might have done something wrong, and I can't really say what that is. Search the web.

3) Installation of Ubuntu Edgy Edge (6.10)
Ran Live CD.
	When Ubuntu starts up you have to make sure your network is working. Nice to have it if you are unsure since you can surf the web while doing the installation. Also check that the keyboard-setup is correct (I am a Norwegian, so I use a Norwegian keyboard - I had to change). 

Installation is pretty much straight forward until you come to the part with partition. I tried a few times with different sizes and also with a fat32-partition (which is a good idea when you are creating the ubuntu.bin-file (more on that further down).

Finally I decided to use 55gb to linux and use the rest (think it was 1gb) for swap.
After the partition-part is done you must tell where to put Grub. Don't put it on hda0 because you will then ruin the mbr (master boot record). If that one is broken, you might not get your computer up at all.  
I ended up with the following partition table:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          10       80293+  de  Dell Utility
/dev/hda2   *          11        2443    19543072+   7  HPFS/NTFS
/dev/hda3            2444        9602    57504667+  83  Linux
/dev/hda4            9603        9729     1020127+  82  Linux swap / Solaris

When that is done the installation process is taking place with files being installed and installation-files being removed at the end. 
Before I rebooted I went into terminal/shell and created a ubuntu.bin file. You must put this on a partition that you can reach (therefor smart to have a FAT32-partition). Since I have a memory-stick I put it on that one.
You create the ubuntu.bin-file like this:
# dd if=/dev/hda2 of=/media/usbstick/ubuntu.bin bs=512 count=1

Now you can reboot from the Ubuntu LiveCD. You boot to Windows. 

When the computer starts up Windows it will run the check disk utility because the partition is being resized. Let it do so.

In Windows you open control panel, select System, and go to the Advanced Tab. Click the "Startup and Recovery" Setting button. Click the Edit button to edit the startup option file manually. This will fire up Notepad with the settings of boot.ini

Add a new line at the endof the file:
C:\UBUNTU.BIN="Ubuntu Linux"
And save the file. 


Also check that the two checkboxes are checked before you reboot again. 
When you do you will be asked if you want to boot windows or Linux. When you choose Linux you'll get Grub and you have to choose the latest kernel. And then you are in Ubuntu.

Hope this helps anyone.

Regards,
Trond

---

### Post by Diffusio on 2007-02-10
Says my filesystem is fat16, though it says ext3. Can I make this partition without erasing my hard drive?

---

### Post by trondhuso on 2007-02-10
If it is fat16 you can resize it with the Gnome Partition Manager that is in the system menu on the Ubuntu Live CD [http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#createditpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#createditpartgparted)
The link above will help you a lot with resizing that partition (as you don't have to use the ntsfresize tool).

trond

---

### Post by Starving.Wolf on 2007-02-14
Hi, there --

I have a similar problem, though it's a bit different in scope.  I had WinXP on my system, and wanted to move to Kubuntu.  I used the Live CD's, but I guess I screwed something up (I think the CD's themselves might have had bad ISO images) and my windows partition got all sorts of messed up.  I'm running it on an HP, so that means no rescue disk for me, but I still have my "D:\" drive in tact, and a big, open spot for WinXP to fit back into... does anyone know how to boot from the D: partition so I can re-install this damnable OS?

When GRUB loads up, I still have the Windows XP option down at the bottom, but when I select it, it gives me the following error:

No Sysyem Disk or
Disk I/O Error
[caps] disk boot failure, insert system disk & press enter

Now, I'd really like to insert that system disk, but it's buried under that stupid partition that HP uses... so am I stuck trying to get my hands on an XP boot CD? or can I sort this out on my own?

Thanks, much, everyone!  I'm sure I'll be having a blast with Kubuntu once I get my comp. back in order again...


~ Matt

---

### Post by erlyrisa on 2007-02-14
It's always a pain to work on a single partition (in the hope you actually get to keep your data)

I have read in intersting articles on the subject of Multibooting....

best bet is to start again and....

Partition - Root = Fat32 or 16 (your choice, if you especially want to use DOS v1 then fat16) , if you are planning on using some old OSes use about 20mb - 40mb (100+ if you plan to use win3.1 or other software which needs compatible dirve, or alternatively make another partition as fat32 for software)

Then it's time for your newer OS's

I like to install the MSoft stuff first and finish off with linux. - upto you on how you distribute your oses - just note the 1024the cylinder(or is it track) limit for some OSes.

WINXP should be able to install itself on the fat32 root partition, and then you need to DD a boot image to grub/lilo when you install that, then do a rescue for XP , redoing what XP does on install (I think it's the ntldr file that needs to get redone) then change your Boot.ini file to include your Linux BOOTSECT.lin file you just made.

Yess - as you can see I am bored by typing so much un-infarmative clutter, but there are alot of instructionals out there to guide you.
-The most important thing I wreckon though is haveing that fat32 root partition, it really helps being able to veiw it with a simple dos disk. and It's great for me favourite game... STUNTS!

---

### Post by Starving.Wolf on 2007-02-17
Thanks for the suggestion -- I'll have to try that if I can get my hands on a Windows disk at this point.

---

