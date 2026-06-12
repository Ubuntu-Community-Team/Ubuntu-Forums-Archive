---
title: "How I moved my /(root) to a raid 5 space."
date: 2008-12-18
forum: Server Platforms
---

### Post by yldouright on 2008-12-18
To Krupski, fjgaude and all the others who have helped me along the way in [[COLOR="DarkOrange"][COLOR="Lime"][COLOR="Blue"]this thread[/COLOR][/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?p=6386428#post6386428"), this is the culmination of all your efforts on my behalf. I will document the step by step I used to move my Ubuntu installation and ask all my questions here. I will consider the other thread resolved because my fstab was fixed.

---

### Post by yldouright on 2008-12-18
I am providing the summary below for those not inclined to review the previous thread.
My desired partition scheme is:
/dev/sda5 /boot (64MB at the beginning of the media on the drive)
/dev/sdb5 /boot (64MB mirror at the beginning of the media on the drive)
/dev/sda6 swap (384MB partition part of a raid 5 swap) md0
/dev/sdb6 swap (384MB partition part of a raid 5 swap) md0
/dev/sdc5 swap (384MB partition part of a raid 5 swap) md0
/dev/sdd5 swap (384MB partition part of a raid 5 swap) md0
/dev/sda7 / (4GB partition part of a raid 5) md2
/dev/sdb7 / (4GB partition part of a raid 5) md2
/dev/sdc6 / (4GB partition part of a raid 5) md2
/dev/sdd6 / (4GB partition part of a raid 5) md2
/dev/sda8 /home (remaining space part of raid 5) md1
/dev/sdb8 /home (remaining space part of raid 5) md1
/dev/sdc7 /home (remaining space part of raid 5) md1
/dev/sdd7 /home (remaining space part of raid 5) md1

My method will be:
1. boot from a live cd
2. move the entire installation to the new partition
3. make a /boot partition at the beginning of your disk (mirrored after)
4. edit fstab and my boot loader configuration to reflect the new location.

The unanswered questions from that thread are:
Do I need to stop the current arrays or will booting from a live cd ignore the arrays until I mount them?
Will booting from a live cd enable me to edit the necessary files (ie:will there be an access/permissions issue)?
Am I required to make a primary partition or have an MBR if I am solely using linux on this box?
Does anyone see potential problems with this configuration?

---

### Post by yldouright on 2008-12-19
C'mon guys. I'm really uncomfortable proceeding without at least SOME feedback on the questions above. I read that any changes to a working array are not safe to do and so I want to be certain before I start disassembling my md0. My suspicion is, if I start from a live CD the kernel will not have the information required to start and build the arrays so I shouldn't have to stop it manually to disassemble it but I don't know this for sure. I also would like to avoid a situation where all the files don't move because of permission/security issues and if I can avoid using the MBR altogether.

---

### Post by fjgaude on 2008-12-19
Hello! Will you answer a few questions before we start, as it seems you and I are bonded together. <smile>

I take it you have only four drives at present and these are the ones you are presently using, for that's whats on sd[abcd][1234] partitions?

What is the present array or arrays like?

Can you give us what a **df -h** presently shows?

Have you understood what it takes to even make a mirror, a raid1 array? Have you read, studied this link:

```
http://radu.rendec.ines.ro/howto/raid1.html
```

What you have suggested you wish to do seems somewhat off the wall, if you get my drift. So please give us more detail as to what you presently have. We know where you wish to get but there are many ways, and likely only one that will satisfy your needs considering where you presently are with your system.

I'll do the best I can if you answer the questions. Your questions don't make sense until we get to the bottom of where you presently are. <grin>

---

### Post by yldouright on 2008-12-19
This is my current drive state as per df -h:```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.1G  447M  88% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-16-generic/volatile
/dev/md1              191G  188M  181G   1% /Data

```My /(root) is mounted on a 4GB partition of the first drive (sda). The level 5 array (md1) was built on the last cylinders of all four drives. I was planning to move the /(root) to md1 long enough to build another smaller level 5 array (md2) for it afterwards. I was going to get around potential problems with my pre2K bios by making two small /boot partitions on the very first cylinders of sda and sdb. I read that there are certain instances when a machine improperly reboots and corrupts the filesystem from the swap space and that is the reason for the level 5 swap space. Once Here is my plan after moving my /(root) to md1:
1. Use  sdb5 to mount the /boot directory. I will need to configure GRUB to point to it and make the necessary entries in /etc/fstab and /etc/mdmadm/mdmadm.conf to successfully boot my new configuration. If I am successful,
2. Create the identical size partition with the same cylinders on sda5 and create a raid 1 mirror. I am still studying the link you provided but it seems like that method may be outdated for newer versions of GRUB. I will test the mirror set for failure and if I am successful,
3. Create the final resting place for my /(root), the level 5 array of md2. Then move my /home to md1 and test. Voila :)

---

### Post by fjgaude on 2008-12-19
What version of Ubuntu are you using? A server?

Your pre2K BIOS? You mean an eight-year old BIOS?

You don't wish to lose any data you have on /dev/md1?

When you mention MBR you know that grub is there? And from there a pointer to the partition that has the stages to boot the kernel?

I've never done what you are trying to do. I always think of reliability first. If your desired setup can be made to work a loss of one drive should permit you to still function, still boot. I'll have to do some research on making sure grub in on both mirrors in case of either of the drives failing. This has been an issue with many who have tried booting from software raid1 arrays.

If you have a working raid5 now and the data on it cannot be backed up, then all those partitions on the four drives will have to do. There is nothing wrong with having raid1 on the same drives that have raid5.

If you use a liveCD, Ubuntu one, then when it comes up you actually have to install mdadm, but you likely already know this. From memory I don't think any arrays that exist are auto mounted. The real issue is to get the grub on at least one of the boot drives in the mirror and then make the mirror in the partitions setup previously for them. It's easy to put grub into the MRB, really creating a new one, with this command:

```
sudo grub-install /dev/sda
```

and then by using the **grub** command you can place the pointer to the boot partition anyway you wish. I have done that many times, easy.

Here's another link that might be useful:

[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

I have always had a fast boot drive with the OS and then use raid5 for all data. Drive failures are the issue. If an OS drive goes down takes just an hour or so to reinstall the OS. It's just a philosophy. Always have multiple backups, online, near-line, off-line of all important data if you wish **never** to get burned.

---

### Post by yldouright on 2008-12-19
fjgaude
This is just experimentation for me so don't worry too much. Yes, the platform is an ancient Dual Pentium Server which runs quite spritely with its SCSI disk subsystem and Radeon GPU. I read the IDE port does not do as well since libata so went SCSI. The only thing worth keeping on this box so far are the links I've accumulated. Everything else can be trashed. I started with the Ubuntu 7.10 desktop cd. Naturally, the file system has had many updates since then but the base should still be 7.10. I can type winver on the Windows command line and find out exactly what version and build I am running; what is the equivalent function in Linux? 

No, I didn't know GRUB was there. I thought it was in the boot sector, ran like LILO and could be placed on the first few cylinders of the formatted media. Does GRUB support GPT? I'd like to avoid using an MBR if I can.
BTW, thanks for suffering through my newbieness. I hope my answers are sufficiently clear and responsive.

---

### Post by fjgaude on 2008-12-19
Okay, I sure would start with 8.04 or 8.10... things have been improving so fast the last few years. You are using the 7.10 server?

The MBR is the first 512 bytes on a drive. About 444 of that 512 is grub.

Yes, no problem usig GPT. The only program I know that putting it onto a drive or an array is **parted**, partition editor. Don't know if others do, certainly not **Gparted**.

After using **grub-install** you would use this series to find and then point to the boot area of the drive:

```
# grub
grub>find /boot/grub/stage1
grub>root (hd0,0)
grub>setup (hd0)
grub>quit
```

How did you put the existing 7.10 system onto the boot drive?

The way I would start this whole project is clean the drives, using 

```
sudo mdadm --zero-superblock /dev/sd[nn]
```

for each partition. Create the partitions one by one using cfdisk or gparted. Use parted to put the GPT filesystem on, then use the install liveCD to create the raid1 on the two drives setup for that. Then boot up. From there I'd create the raid5 on all four drives. The swap partition will be created from the install process when it askes what drives to use. It will not be that easy but if you understand what is needed you can get through the process. This is not for beginners, usually! 

The command **uname -a** gets the version of the kernel plus more you are running.

I've not used **lilo** since about 1996 and have forgotten anything about it.

The **man** pages gives much about all the commands of Linux. Try **man grub** and see.

---

### Post by yldouright on 2008-12-20
fjgaude
The command uname -a returns:```
Linux p2bds-ubuntu 2.6.22-16-generic #1 SMP Mon Nov 24 18:28:27 GMT 2008 i686 GNU/Linux

```I used the Desktop Ubuntu 7.10 CD for the install and have allowed every update. The Update Manager still displays "New distribution release '8.04' is available" so I am assuming I'm still using the same release. GParted 0.3.3 has GPT listed in the disklabel options so it may be supported. I was not aware that GPT was a file system. I thought it just another boot method similar to LILO and GRUB. Will I have to chose between GPT and EXT3? Is your suggestion to break md1 a step in the process to use GPT, if it isn't, what is the purpose of disabling a perfectly functional array that is located exactly where i want it on the media? Please recall that I am planning to initially move my /(root) there for testing before placing it on md2. Upon review of the GRUB manpages I see that I am able to interrupt the boot process and edit the grubmenu.lst if i get into trouble. Do I need and MBR if I use GPT? I'm gaining confidence but I am troubled that no one has stepped in and answered the previous questions definitively.

---

### Post by fjgaude on 2008-12-20
Okay, GPT is a type of partition table and can be used with any filesystem as far as I know. GPT doesn't have anything directly to do with MBR and grub or lilo. Too much to remember here. A link:

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Creating a GPT on a drive will delete any data that is there, yes.

You are using 7.10 with all updates, which is why the kernel is still what it is. I'm using 2.6.27-9.

I recommend what I think I could do if I was doing the installation myself. You said nothing is important with the data, so...

Start doing what you wish. You can always back out of things that are not working. Remember the filesystem starts at /, then boot then grub: /boot/grub. Just do some testing to find out what is going to work. Take a look at /boot/grub/menu.lst and notice what is in boot and in grub, remembering that the MBR points to menu.lst to offer a boot selection.

From the liveCD you can always get permission as needed with the **chmod**, **chown** commands. You might try the man pages for them, and the **mv** also.

A thought, you are on the Server Forum and most of the folks here simply don't have the time to go through such a detailed procedure with you. There are lots of very experienced people on the General Forum, lots more than on the Server one. You might try posting there with your issues and see what happens.

At present I can't mentally break the filesystem and move from one array to another and expect it to work. I would have to try and see, step-by-step.

> The unanswered questions from that thread are:
Do I need to stop the current arrays or will booting from a live cd ignore the arrays until I mount them?

[COLOR="Navy"]No stopping of the arrays. Just use the liveCD to boot.
[/COLOR]
Will booting from a live cd enable me to edit the necessary files (ie:will there be an access/permissions issue)?

[COLOR="Navy"]Likely no issues... you can edit anything you wish. If permissions are needed you can use chmod and chown to get them.[/COLOR]

Am I required to make a primary partition or have an MBR if I am solely using linux on this box?

[COLOR="Navy"]You have to have grub on the MBR, so yes you need a bootable partition.[/COLOR]

Does anyone see potential problems with this configuration?

[COLOR="Navy"]Can't say, have to try it, step-by-step.[/COLOR]


---

### Post by yldouright on 2008-12-20
fjgaude
Okay, I'm ready to jump now. The mv command appears to need a directory and since it is going to a blank space, how do I make it move the entire directory? Do I mount the new location as /(root) before moving it or is there some way to use a device designation to direct the move. How can I insure that none of the files will be skipped?

---

### Post by fjgaude on 2008-12-20
You copy directories, one or more all at once, by using **cp** and its -R option, for recursively, to the new directory. In your case you have made a directory called "/", the root.

```
sudo mkdir /
```

Do that after you **cd** to the new drive.

```
cp -R /dev/sda1 / /dev/sdb6 /
```

as an example. Please study the man pages for all these commands.

You can try using **mv** instead of cp but I have no knowledge of how that would go. With cp, after the copy over, you can delete what's on the source using the **rm** command along with its -R parameter.

You might try a test case before you go for the whole banana. I've never used cp to copy root to root. <smile>

All I can do is hope you get what you wish for. Doing this from a liveCD will work, I think. You might have to use the **chmod** and **chown** commands to get around permissions, but maybe not.

---

### Post by fjgaude on 2008-12-22
I ran across this link and how to use **chroot** in placing, editing certain files, directories. I think you might need chroot in what you are doing from the liveCD.

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

Also here's a link about MBR and **grub**, about all we will ever wish to know:

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

---

