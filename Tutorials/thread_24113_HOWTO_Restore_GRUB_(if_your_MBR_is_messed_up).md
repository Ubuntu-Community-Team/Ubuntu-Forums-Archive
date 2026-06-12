---
title: "HOWTO: Restore GRUB (if your MBR is messed up)"
date: 2005-04-05
forum: Tutorials
---

### Post by vnbuddy2002 on 2005-04-05
Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

---

### Post by remmelt on 2005-04-06
Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)

[QUOTE=vnbuddy2002]Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.[/QUOTE]

---

### Post by vnbuddy2002 on 2005-04-06
:) Your way is definately faster, but for newbies, many of them try to avoid command line as much as possible. That is why I brought up an alternative.

---

### Post by Tomy on 2005-04-06
[QUOTE=vnbuddy2002]:) Your way is definately faster, but for newbies, many of them try to avoid command line as much as possible. That is why I brought up an alternative.[/QUOTE]
Hey thanks, I never thought of doing this. It worked great for me today.

Last time I messed up grub I used the Live CD method but did not write anything down so today I searched for "grub" and found this post. But I couldn't find a Live CD so I used your method with the Install CD.

Thanks
Tomy

---

### Post by wernst on 2005-04-08
Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.

If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different.  Here's are the instructions that I have for my system:

How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps. Since I use Norton Ghost to make regular backups and restores (I do a lot of testing), I do this all the time...

-Warr

---

### Post by rpakdel on 2005-05-12
Here is another way:

1. Boot with any live CD (I've done it with Knoppix 3.x and Ubuntu)
2. Get a root shell and make a folder (mkdir ubuntu)
3. mount the root (/) partition of ubuntu (e.g. mount /dev/hdb ubuntu if you have two disks)
4. chroot the mounted partition (chroot ubuntu)
5. grub-install /dev/hda [1]
5. Exit the shell
6. Reboot

[1] Important: If you are multi-booting with Windows, make sure you do NOT install the MBR on the active partition (say /dev/hda1) but on the drive (/dev/hda). At least with Windows XP, you will have to re-install it (FIXMBR/FIXBOOT won't work).

---

### Post by Heliode on 2005-05-12
Since all you need for these fixes is a command prompt, you don't need to load the GUI. For Knoppix I believe you type something like 'knoppix 3'. For the Ubuntu Live-cd I don't know. I'll edit this post when I figure it out.

---

### Post by H3AsO4 on 2005-06-10
at step 10, I encountered a problem: it asks you if you want to proceed when you click the Install Grub, and in all the previous steps, "yes" or "continue" was the correct response, at step 10, if you select "yes" the ubuntu disk will proceed and attempt to install ubuntu.... which will ruined my current install...   ah well....  :(

[QUOTE=vnbuddy2002]Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.[/QUOTE]

---

### Post by jsimmons on 2005-06-24
I currently have a mobile rack so that I can have Ubuntu on one drive, and Windows on another. When I need to change OS's, I turn off the system, swap drives, and turn it back on again.  I've decided this is too much of a hassle (and not necessarily easy on the electronics).

I am going to install another SATA drive and I want to move my current Ubuntu install over to that drive (without having to reinstall Ubuntu), and then setup GRUB on my Windows drive so I can dual boot.  

Will I experience any problems doing this? The reason I ask is because I'll be moving Ubuntu from /dev/hda to /dev/sdb, and I'm wondering if any OS-specific stuff cares about that kind of thing.


Should I just throw in the towel and reinstall Ubuntu from scratch on the new drive, or is what I want to do doable?

---

### Post by Rikko on 2005-08-24
Hi guys,
The problem I'm having is that Ubuntu installed GRUB onto /hdb1, but my primary partition (as far as my BIOS is concerned) is /sda1
I can run 'grub' and reinstall grub like described by remmelt, but I don't know what the ID of /sda1 is. (hd1,0)? (hd2,1)? What command can I use to get the mapping?
I'm able to boot off the Live CD only at the moment.

---

### Post by Tomy on 2005-08-25
[QUOTE=Rikko]Hi guys,
The problem I'm having is that Ubuntu installed GRUB onto /hdb1, but my primary partition (as far as my BIOS is concerned) is /sda1
I can run 'grub' and reinstall grub like described by remmelt, but I don't know what the ID of /sda1 is. (hd1,0)? (hd2,1)? What command can I use to get the mapping?
I'm able to boot off the Live CD only at the moment.[/QUOTE]

From the grub prompt trying using the <tab> key to see what choices you have.

grub> root (<tab>

Tomy

---

### Post by Rikko on 2005-08-26
[QUOTE=Tomy]From the grub prompt trying using the <tab> key to see what choices you have.

grub> root (<tab>

Tomy[/QUOTE]
 Thanks Tomy, that got me a little farther.. Now I'm getting a "Partition type is 0x7" (or something very similar - I've since booted back into Windows)... Maybe I'm misunderstanding Grub but I thought it could just be placed into the MBR without needing any partition space.
Or can I mix up the setup() and root() commands to install Grub into sda1's MBR but store the actual files needed on /hdb1?

Geez, just when you thought you know something about computers... :)

---

### Post by j.hill on 2005-08-26
[QUOTE=Tomy]Hey thanks, I never thought of doing this. It worked great for me today.

Last time I messed up grub I used the Live CD method but did not write anything down so today I searched for "grub" and found this post. But I couldn't find a Live CD so I used your method with the Install CD.

Thanks
Tomy[/QUOTE]

For some reason the Live CD method doesn't work for me.  I boot from the Live CD and open a terminal, which tells me "command not found" when I type "grub."

Anyone know what this is about?

---

### Post by Rikko on 2005-08-27
[QUOTE=j.hill]For some reason the Live CD method doesn't work for me.  I boot from the Live CD and open a terminal, which tells me "command not found" when I type "grub."

Anyone know what this is about?[/QUOTE]
 I had that as well - the Live CD doesn't seem to actually have the grub command available.. 
Do you already have Ubuntu installed on a physical drive and just want to reinstall Grub? If so, you just need to mount it. My steps:
Drop to a root terminal
mkdir hda1
mount /dev/hda1 hda1 (mounts that device into ./hda1)
cd hda1/sbin
./grub

Replace hda1 with whatever the physical drive that Ubuntu is installed on happens to be.
Worked for me - I'm just stuck trying to actually install Grub on my NTFS partition somewhere.

---

### Post by j.hill on 2005-08-28
[QUOTE=Rikko]I had that as well - the Live CD doesn't seem to actually have the grub command available.. 
Do you already have Ubuntu installed on a physical drive and just want to reinstall Grub? If so, you just need to mount it. My steps:
Drop to a root terminal
mkdir hda1
mount /dev/hda1 hda1 (mounts that device into ./hda1)
cd hda1/sbin
./grub

Replace hda1 with whatever the physical drive that Ubuntu is installed on happens to be.
Worked for me - I'm just stuck trying to actually install Grub on my NTFS partition somewhere.[/QUOTE]

So if my computer is using the notation "hd0" for this sort of thing, I would type
```
mkdir hd0
```
?

Seems almost too easy.

Will this conflict in any way with the current location of Grub?  And, if this works, will I still edit the Grub menu in /boot/grub/menu.lst?

And is there any danger of seriously screwing up my computer with this method?  I'm still an abject n00b, so I'm sort of reluctant to try anything risky.

---

### Post by j.hill on 2005-08-30
Can't I just reinstall Grub through Synaptic?

---

### Post by filemanager on 2005-08-31
[QUOTE=Rikko]I had that as well - the Live CD doesn't seem to actually have the grub command available.. 
Do you already have Ubuntu installed on a physical drive and just want to reinstall Grub? If so, you just need to mount it. My steps:
Drop to a root terminal
mkdir hda1
mount /dev/hda1 hda1 (mounts that device into ./hda1)
cd hda1/sbin
./grub

Replace hda1 with whatever the physical drive that Ubuntu is installed on happens to be.
Worked for me - I'm just stuck trying to actually install Grub on my NTFS partition somewhere.[/QUOTE]
 at the cd hda5/sbin step I'm getting this error:

> bash: cd: hda5/sbin: No such file or directory


---

### Post by j.hill on 2005-09-01
[QUOTE=rpakdel]Here is another way:

1. Boot with any live CD (I've done it with Knoppix 3.x and Ubuntu)
2. Get a root shell and make a folder (mkdir ubuntu)
3. mount the root (/) partition of ubuntu (e.g. mount /dev/hdb ubuntu if you have two disks)
4. chroot the mounted partition (chroot ubuntu)
5. grub-install /dev/hda [1]
5. Exit the shell
6. Reboot

[1] Important: If you are multi-booting with Windows, make sure you do NOT install the MBR on the active partition (say /dev/hda1) but on the drive (/dev/hda). At least with Windows XP, you will have to re-install it (FIXMBR/FIXBOOT won't work).[/QUOTE]

I'm stuck on steps 3 and 4.  For step 3, the computer gives me the following ambiguous message:  does this mean that I've successfully mounted what needed mounting?

```
root@ubuntu:/home/ubuntu # mount -t ext3 /dev/hda/ubuntu
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

Then, when I try to chroot, I get this:

```
chroot: cannot run command `/bin/bash': No such file or directory
```

This last bit really confuses me.  Obviously /bin/bash exists; I'm using a bash shell to give the chroot command.  

What does it all mean?

---

### Post by dragon slayer on 2005-09-18
you can use use ultimate boot cd to rewrite the mbr it's very easy.
download and burn as an iso at [http://ubcd.sourceforge.net/download.html](http://ubcd.sourceforge.net/download.html) .
 :) I wanted to get rid of lilo after I tried xandros. Xandros leaves lilo on your mbr, it worked great, it has a lot of tools to  :)

---

### Post by vnbuddy2002 on 2005-09-19
You had specified the wrong mount syntax. It should be

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda[0 .. whatever here ] /mnt/ubuntu

Make sure you know which partition you are trying to mount

sudo fdisk -l

-----


[QUOTE=j.hill]I'm stuck on steps 3 and 4.  For step 3, the computer gives me the following ambiguous message:  does this mean that I've successfully mounted what needed mounting?

```
root@ubuntu:/home/ubuntu # mount -t ext3 /dev/hda/ubuntu
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

Then, when I try to chroot, I get this:

```
chroot: cannot run command `/bin/bash': No such file or directory
```

This last bit really confuses me.  Obviously /bin/bash exists; I'm using a bash shell to give the chroot command.  

What does it all mean?[/QUOTE]

---

### Post by rj686 on 2005-09-19
how do u mount your appropriate partitions if u can't get past the manual partition screen?(install cd)  u just press enter and it doesnt go away.

---

### Post by Xian on 2005-09-19
[QUOTE=rj686]how do u mount your appropriate partitions if u can't get past the manual partition screen?(install cd)  u just press enter and it doesnt go away.[/QUOTE]
You set the mount points by highlighting partitions in the selection list.
Press the enter key and then edit the mount point.

Do this for each partition.
Then select "Finish partitioning...."

It will ask for confirmation.

---

### Post by ghostintheshell on 2005-09-22
Aaargh!! Thank you guys!! Very very very much!! You saved my virtual life!

I lost my Grub / MBR and YOU restored it!

After searching too much time on the web, I fell on this topic. I read it completely and applied a mix of your solutions.

Here's the steps I followed to restore GRUB / my initial MBR:

1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> [color=black]*mkdir /mnt/ubuntu*[/color]
4. Check the Ubuntu partition -> *fdisk -l* (Mine is /dev/hda4)
5. Mount the root partition of Ubuntu -> *mount -t ext3 /dev/hda4 /mnt/ubuntu* (replace /dev/hda4 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> *chroot /mnt/ubuntu*
7. Restore Grub / the initial MBR -> *grub-install /dev/hda*
8. Exit the shell
9. Reboot

That did the trick for me.

Thank you very much again to all of you! ( :bigsmack: )

---

### Post by TakisX on 2005-10-10
When i give fdisk -l nothing hapens
When i give grub-install /dev/sda it says that there is not exista such partition


And the other method
1 boot with live cd
2 give grub   ok
3 root (hd0,3)   and partition not found

what to do ?

---

### Post by lliseil on 2005-10-22
UP,

Anybody correct me if I'm wrong,
SATA hard drive where to install grub (MBR) might be (**sd0**) right ?

---

### Post by willalbro on 2005-10-23
Well...I run 2 SATA drives with Winblows on one and Ubuntu as my primary drive. I believe your SATA drive would be referred to by GRUB as /dev/sda for primary and /dev/sdb for slave. If you want the primary partition on your primary SATA drive then it would be /dev/sda1. The (hd0,0)  naming convention still holds true as well but I digress.

---

### Post by KrazyPenguin on 2005-10-30
I was having problems with my Wife's computer, which is the exact same setup as mine.

Both are an Asus Motherboard but hers is newer.

The problem she was experiencing was the Grub would lock for about 1 minute at stage 1.5.

I did what the dude said in the first post and tried the Install CD.

When I got to partitioning I changed Primary #1 (Breezy is on primary #2 but I don't think that matters).
Primary #1 was mounted as /media/hda1 so I changed it to /
Then I continued and then tried to reisntall grub.
The computer locked up.   :( 

I rebooted it and this is WEIRD.  It no longer gets stuck in GRUB Stage 1.5.

HAPPY HAPPY !!!!
But at the same time :confused: 

None of the grub reinstalled.  It was stuck at 0%.

I don't care about reasons.  It works.  That is all that matters.

;-)

---

### Post by rodent43 on 2005-11-04
this thread is great and i am hoping it will help me when i get home...but i just gonna post what i have done to my PC here as i am a noob and really done something great :confused: 

OK, i have Windows XP x64 on the SATA 1 (200Gb) and after using Ubuntu 5.04 at work i decided to try 5.10 at home...

so i purchased a cheap 80gb SATA and put it in as SATA 2...so far so good...

I installed 64 bit version of 5.10 on to the sata 2 (sdb) drive and all went on ok, grub then wanted to install mbr to hd0,0 and i let it...

once i rebooted i got no selection or grub, windows just booted up...

so i then tried the install again and this time at the grub stage i specified to install the mbr at /dev/sda and then rebooted...this time my screen just scrolled throuhg saying grub grub grub grub (you get the idea)

so i got the ultimate boot cd off the net and used something named cag or gag...that worked for booting the windows drive but not linux

so is there any way i can sort grub out?

i dont mind reinstalling the ubuntu system as i have not even got it to boot yet, so i still need to do the finishing install on that...

any help will be much appreciated...

---

### Post by rodent43 on 2005-11-07
ok thought i would update this but i am still having problems if anyone would care to help me out

i also have 2 IDE drives on a PCI ide card in removable drive bays...if i take those out and install ubunut, grub works fine but once i put those back on grub reports

error 17

any help?

---

### Post by daibak on 2005-11-09
After being struck by Ubuntu Breezy Install CD GRUB Error 21 this newbie will proceed more warily. Had to rebuild Windows XP from scratch on HP notebook with factory recovery disks that only took me two weary days incl. all the downloading of three years' computing on this machine. But hey, I'm not ready to give up!

Well now I've clobbered GRUB and MBR on Windows C: drive the original Ubuntu Breezy root and swap partitions I set up on external Firewire Seagate hard drive by Guided Partitioning are probably all that's left intact.

These two Linux partitions were formatted on external SCSI1 (sda) drive by Breezy install partitioner as:
  #1 of SCSI1 (0,0,0) (sda) ext3 - I understand this is root, so sda0
  #9 of SCSI1 (0,0,0) (sda) swap - logical drive in extended partition, so sda9 

Does this mean I can now boot with Ubuntu 5.10 LiveCD and follow the steps below, merely substituting my root partition of Ubuntu as /dev/sda0 in Step 5 (this is the active, primary partition on the external Seagate), and I'll then be back to a dual boot that works for Windows and Breezy off C (hda)?  Or not?

Or does someone know a Breezy cheatcode like Knoppix 4.0.2's LiveCD lets you type at first boot prompt
knoppix offhd=/dev/sdaX if you've dumped Knoppix LiveCD earlier on drive X?

Thanks to ghostintheshell for this post, the closest I found - I think - to what I'm seeking.    

[QUOTE=ghostintheshell]Aaargh!! Thank you guys!! Very very very much!! You saved my virtual life!

I lost my Grub / MBR and YOU restored it!

After searching too much time on the web, I fell on this topic. I read it completely and applied a mix of your solutions.

Here's the steps I followed to restore GRUB / my initial MBR:

1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> [color=black]*mkdir /mnt/ubuntu*[/color]
4. Check the Ubuntu partition -> *fdisk -l* (Mine is /dev/hda4)
5. Mount the root partition of Ubuntu -> *mount -t ext3 /dev/hda4 /mnt/ubuntu* (replace /dev/hda4 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> *chroot /mnt/ubuntu*
7. Restore Grub / the initial MBR -> *grub-install /dev/hda*
8. Exit the shell
9. Reboot

That did the trick for me.

Thank you very much again to all of you! ( :bigsmack: )[/QUOTE]

---

### Post by apps4apps on 2005-11-13
[QUOTE=ghostintheshell]Aaargh!! Thank you guys!! Very very very much!! You saved my virtual life!

I lost my Grub / MBR and YOU restored it!

After searching too much time on the web, I fell on this topic. I read it completely and applied a mix of your solutions.

Here's the steps I followed to restore GRUB / my initial MBR:

1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> [color=black]*mkdir /mnt/ubuntu*[/color]
4. Check the Ubuntu partition -> *fdisk -l* (Mine is /dev/hda4)
5. Mount the root partition of Ubuntu -> *mount -t ext3 /dev/hda4 /mnt/ubuntu* (replace /dev/hda4 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> *chroot /mnt/ubuntu*
7. Restore Grub / the initial MBR -> *grub-install /dev/hda*
8. Exit the shell
9. Reboot

That did the trick for me.

Thank you very much again to all of you! ( :bigsmack: )[/QUOTE]

Hi All, 

I ran out of space on my original HD and am trying to get a cloned version on a larger drive running but am hitting a large brick wall. The closest I seem to have come so far is to boot with the live CD and try the suggestion above. The problem that I'm running into however is that it won't seem to let me mount the partition. Using fdisk -l to get the partition info to mount I see /dev/hda5 as Linux LVM with an id of 8e. When I try and mount /dev/hda5 I get: [COLOR="Red"]/dev/hda5 already mounted or /mnt/ubuntu busy  [/COLOR]

Any suggestions would be greatly appreciated...

---

### Post by theswan on 2005-11-13
[QUOTE=vnbuddy2002]Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.[/QUOTE]


hello there!
at first time my GRUB works fine...but when i get back to Windows XP and use partitionmagic to do some partioning on some unused space (not the linux drive or swap), then my GRUB failed to work...=( at start i get an ERROR 22.

@vnbuddy2002: i think i'll better follow your instructions as the only LIVE cd i've got is the one that comes with OpenCD. also, i'm not yet really familiar with commandlines thingy in Linux.

just like to ask what do you mean by number 4 in your instructions above?
do you mean the error in number 8 is like 'cannot install because no root directory is found'?

thanks for any help. cheers!

---

### Post by mcrane on 2005-11-13
[QUOTE=rodent43]ok thought i would update this but i am still having problems if anyone would care to help me out

i also have 2 IDE drives on a PCI ide card in removable drive bays...if i take those out and install ubunut, grub works fine but once i put those back on grub reports

error 17

any help?[/QUOTE]

Sounds like the same problem I'm having. Unfortunately, I can't unplug the drives on the PCI IDE controller (Promise FastTrack66) because one of them contains my Ubuntu installation.

---

### Post by rodent43 on 2005-11-14
i dont want to uplug either as they contain my files and games etc...

i am kinda stuck now and either going to try another flavour of linux or just stay on windows :'(

---

### Post by ajgreeny on 2005-11-21
When I install ubuntu I do the default of putting grub in the MBR. Once that is up and running I make sure that my floppy drive is listed in /grub/boot/device.map as
(fd0)  /dev/fd0
and if it's not there I add it exactly as shown.  (If you don't do this the next bit will fail).

I then do a
sudo grub-install fd0
which gives me a floppy grub boot disk from which I can start up if the mbr gets messed up in some way.  Once you've started up you can put grub back on the mbr by doing a 
sudo grub-install /dev/hda

OK, I realise this is only any use for people with a floppy disk drive and it can get messed up if you update your linux version and that doesn't update grub for some reason, but so far, touch wood, it's always worked for me, and as long as you know what the linux version update was you should be able to edit the grub menu by highlighting the specific entry in the menu and hitting e, and then changing the numbers on the particular linux entry.

Hope this helps and that I have got things right.  Perhaps if my understanding of things is a bit flaky, someone can let me know.

---

### Post by jars_u on 2005-11-24
Ok, I know  I'm new at Linux - I've tried several of the different suggestions posted and still no luck dual booting.  From the install CD the only thing I can manage is a complete install - nothing with just install GRUB.  No luck with the various command line options from the live CD either - although I admit there is bound to be some user error there.  Any other suggestions to my specific circumstances will be appreciated.  Kubuntu is up and running no problem just can't get back to WinXP.

IDE1 Slave (hdb) (old salvaged HD currently NTFS but plan to reformat for FAT32 once I get dual boot working for file sharing)

SATA (0,0,0)(sda)
#1 Primary NTFS (my WinXP files)
#2 Primary NTFS (kind of an accidental partition but empty at the moment)
#3 Primary ext3  (Kubuntu)
#5 logical   SWAP

I've tried the default setting for GRUB at least 3 times during install with no luck, last try was to /dev/sda3 also nothing at boot I get no options and LILO comes up and Kubuntu starts no problem.

Have not tried correcting problem via WinXP re-install for fear of ruining my files (I did back up the key stuff prior to partition) and having a system that is totally dead.

Any help will be greatly appreciated.

---

### Post by jars_u on 2005-11-25
Here are the contents of my menu.lst if that will help:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by xristos on 2005-11-25
[QUOTE=remmelt]I may be missing your point though, if so, please forgive me :)[/QUOTE]

This way the user must know the correct hd(0,6) .
So I believe that this way is actually more complex

---

### Post by jars_u on 2005-11-25
Ok, sort of figured out my problem.  The offender was a 2nd PATA drive I had salvaged from an old computer and installed in my machine.  When I removed that and did a clean install of Kubuntu on the partition I had made previous on my SATA drive - the defaults for GRUB worked fine.  I can now get back into Windows (who ever thought I would be so happy to the see the Windows welcome screen...) and can also boot to Kubuntu.

Going to try and few other things and see if I can't get that old PATA working and remort it for FAT32 - should be able to use it to share files between Win/Linux right?

Now for the easy question - how do I extend the default time that GRUB gives you to make a selection?

---

### Post by ghostintheshell on 2005-11-25
[quote=jars_u][...]

Now for the easy question - how do I extend the default time that GRUB gives you to make a selection?[/quote]

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp
sudo gedit /boot/grub/menu.lst
```

and modify here:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        1
```

*timeout X* ==> X sec.

---

### Post by commodore on 2005-11-26
I have two grubs accidently. They are on different partitions. Someone sayd I should reinstall grub. I tried to install it on where it was first, but I get this: xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem

---

### Post by commodore on 2005-11-26
Ok I am going to tell everything now. I wanted to install a second Ubuntu for testing stuff on it so that I don't mess up my primary Ubuntu install. I wanted to do some partitioning with gparted. It gave me two errors and later it showed that I don't have partitions on my second harddrive (where both Ubuntus are now installed) just unpartitioned space. I didn't make a notice of it. I booted into windows (yes, I have windows too) and it worked (windows has a bit of that second harddrive too :D). Later I installed the second Ubuntu, but when I wanted to go to the primary Ubuntu (I hadn't done it for some time) it didn't work. It gave me an error similar to "can't start tty, job control turned off". I posted a thread to get help and someone said "have you tried reinstalling grub" and gave me a link to this thread. I tried to do that now, but I got the error I discriber in the last post. Is it because the gparted errors? Do I have to throw away both Ubuntus, format the whole harddrive and start installing again those thousands of stuff?

---

### Post by syklitengutt on 2005-11-26
have some difficulties with the two first suggestions.
When booting up my pc, I directly jump into windows.

I tried installing grub from cd and when its finished it jumps straight back to
selecting partitions. Dont know why.
So I then tried to install via live cd.
type su and try the password I have on my linux partition, and it doesnt work.
I also tried every other possible passw. but still it doesnt work.

fdisk:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3696    29688088+   7  HPFS/NTFS
/dev/hda2            3697       14593    87530152+   5  Extended
/dev/hda5            3697        6307    20972822+  83  Linux
/dev/hda6            6308        6361      433723+  82  Linux swap / Solaris
/dev/hda7            6362       14593    66123508+   7  HPFS/NTFS

where hda1 is parition C: on windows
hda2 is unknown, but I think its where hda5 and hda7 is written to.
hda 5 is my linux (used to be hda6 and hda7 is D: in windows (used to be hda5

so I really need help guys....

---

### Post by ajgreeny on 2005-11-28
Hi commodore.
What is the content of your /grub/boot/device.map file?

As far as I can make out, any disk on which you want to install grub with the "sudo grub-install" command must be listed in the device.map file or you will get the error mesage you mentioned.  Try adding an appropriate line to the file as in my first post to this thread, but also note the end of the error message (or at least this is what I see) telling you the error can be ignored and should not cause any problems, and then listing the content of your device.map file and telling you to amend it if needed.

Give it a try.

---

### Post by Carnwaj on 2005-11-28
Just thought I would share my experience of GRUB.

Windows on hda
Ubuntu on hdb
GRUB working fine

One day Windows just doesn't load - it just sits at the splash screen and goes nowhere.

Used XP CD to restore MBR using fixmbr.

I then used the "install CD" method at the top of this post to reinstall GRUB. When I got to the manual partitioning part I noticed that hdb was mounted as /media/hdb. I set this as '/'. I then jumped to the reinstall GRUB part of the install process and everything else worked as described.

Top post from vnbuddy2002

It wasn't all plain sailing - I tried the live CD method and got an error 21 when I tried to root (hd0,0). Tried seaching forums but couldn't get to the bottom of it.

---

### Post by dakota34 on 2005-12-23
very first post worked perfectly for me after a Norton ghost image hosed my grub/mbr.  

Couldn't get live cd methods to work.  

Have to say, it's a little scary when the install cd asks you if you really want to write the changes to the disk (no changes, you're really just mounting existing) .. but it works!!!!!!!!!!!  

Thanks a hell of a lot, this was causing me extreme stress, what with Xmas rolling around etc..

Real lesson: time to get rid of Windows.

TG.:razz:

---

### Post by Bitter Peace on 2005-12-28
Thank you, thank you, thank you, ghostintheshell! This did the trick for me.

Here is the problem I had: Two HDDs, just Ubuntu installed on them (so no dual-boot setup), yesterday it booted just fine, today it didn't. No updates or anything either, I shut the computer down like always and it gave me these mesages on startup today:

```
module minix not found
...
can't access tty; job control turned off
...
Target filesystem doesn't have /sbin/init
``` 

So thank you again, ghostintheshell and everybody else who worked toward this solution.

[QUOTE=ghostintheshell]Aaargh!! Thank you guys!! Very very very much!! You saved my virtual life!

I lost my Grub / MBR and YOU restored it!

After searching too much time on the web, I fell on this topic. I read it completely and applied a mix of your solutions.

Here's the steps I followed to restore GRUB / my initial MBR:

1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> [color=black]*mkdir /mnt/ubuntu*[/color]
4. Check the Ubuntu partition -> *fdisk -l* (Mine is /dev/hda4)
5. Mount the root partition of Ubuntu -> *mount -t ext3 /dev/hda4 /mnt/ubuntu* (replace /dev/hda4 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> *chroot /mnt/ubuntu*
7. Restore Grub / the initial MBR -> *grub-install /dev/hda*
8. Exit the shell
9. Reboot

That did the trick for me.

Thank you very much again to all of you! ( :bigsmack: )[/QUOTE]

---

### Post by Carwash on 2005-12-29
Ive completely messed up my system, cant get into Linux or Windows.

Had Windows installed for about 4 weeks on my new system and had left 10gb spare as a partition for linux, got round to installing it yesterday and it didnt go too well.  I got upto the bit where it asks if you want to install GRUB, i said "Yes" and it did its business, told me to take out the cd and reboot.  

After that it was trying to boot from the PXE-E53, i tried various things and couldnt get it working.  Put in the WinXP cd and went to recovery console and tried fixmbr/ fixboot which then gave me the error "ntldr is missing".  Tried copying ntldr and ntdetect from the winXP cd in i386 but got the same message.

So... i got told by a friends friend if i could get into linux (usin the live cd) and use GRUB, id be able to fix it and get the MBR / GRUB back.  Ive tried the various ways on here to get my system back, but none have worked (prolly my fault though).

My system:
Shuttle SN25P (nForce4 mobo)
AMD Athlon64 3700+ San Diego
2Gb RAM Geil
1 x 80Gb Maxtor SATA HDD (with 2 partitions, WinXP being the main one)
2 x 300Gb Maxtor SATA HDD (No o/s's on either of these)
ATi X1800XL


Now ... the way my hdd's are setup in the BIOS shows that the 80gb hdd is listed 3rd (which would mean its sdc).  
When i got into GRUB and did the search, it told me the boot was (HD2,1), so i changed what i needed to to that and on boot up it says :

> 
root (hd2,1)

Error 22: No such partition

Press any key to continue...


Pressing any key takes me back to the GRUB o/s selection screen where it gives me the same error for all the options accept windows which says the following :

> 
Booting 'Windows NT/2000/XP (loader)'

root (hd2,1)
Filesystem type unknown, partition type 0x42
savedefault
maleactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

NTLDR is missing
Peress Ctrl+Alt+Del to restart



Would really rather not have to format and start all over again, im surei dont have to ... its just im completely stuck now and dont know what else to try.

Please help !


--------
Edit:

Fdisk -l
> 
root@ubuntu:/root# sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      581463   293057320+  42  SFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      581463   293057320+  42  SFS

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        8688    69786328+   7  HPFS/NTFS
/dev/sdc2   *        8689        9907     9791617+  83  Linux
/dev/sdc3            9908        9964      457852+   5  Extended
/dev/sdc5            9908        9964      457821   82  Linux swap / Solaris

Disk /dev/sdf: 250.9 GB, 250999209984 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       30515   245111706    7  HPFS/NTFS


> 
grub> find /boot/grub/stage1
 (hd2,1)



Just read this though on the first page... and think it may be what ive done? :(
> 
[1] Important: If you are multi-booting with Windows, make sure you do NOT install the MBR on the active partition (say /dev/hda1) but on the drive (/dev/hda). At least with Windows XP, you will have to re-install it (FIXMBR/FIXBOOT won't work).


---

### Post by j-a-p on 2006-01-02
I may be missing the point here, but can't you just do:

```
dd if=/dev/hda of=hdambr bs=512 count=1
```

to restore the 1st stage loader and the reinstate a backup of the /boot partition?

---

### Post by viraldhimar on 2006-01-03
[QUOTE=rpakdel]Here is another way:

1. Boot with any live CD (I've done it with Knoppix 3.x and Ubuntu)
2. Get a root shell and make a folder (mkdir ubuntu)
3. mount the root (/) partition of ubuntu (e.g. mount /dev/hdb ubuntu if you have two disks)
4. chroot the mounted partition (chroot ubuntu)
5. grub-install /dev/hda [1]
5. Exit the shell
6. Reboot

[1] Important: If you are multi-booting with Windows, make sure you do NOT install the MBR on the active partition (say /dev/hda1) but on the drive (/dev/hda). At least with Windows XP, you will have to re-install it (FIXMBR/FIXBOOT won't work).[/QUOTE]


Thanks man, this worked great after I tried to reinstall Dell mediaDirect(apparently dell rewrites the bootloader..bad dell very bad...) If you have sata drives just use "sda" instead of hda.

---

### Post by rajaiskandarshah on 2006-01-07
hi guys,

running windows xp and ubuntu on my acer travelmate 2301 notebook for the last 6 months. my prefered os is ubuntu where all of my main documents are.

since last week, i had a small project using visual basic, so i had to run winxp. yesterday morning, i installed a windows update in the morning when prompted, and in the evening winxp eventually(!) crashed. grub works ok and i can get to ubuntu no problem and even browse the files under winxp. but winxp will only get up to the splash screen, then there is the blue screen of death and the computer will restart.

will the following work ?? and any advice ?
1. copy my documents to another computer on the network
2. restart the computer with winxp cd and select the recovery option
3. run the fixmbr command
4. restart the computer as normal to winxp
5. restart the computer with ubuntu install cd and reinstall grub as per the top post
6. restart the computer to grub

any other potential issues ?

---

### Post by adrian15 on 2006-01-11
If you do not want to mess up with commands...

**Note: This method works very well with system with only one Linux... if you have more than one Linux Super Grub Disk will restore the first Grub that it will find on your partitions.**

[LIST]
[*]Download [Super Grub Disk]("http://adrian15.raulete.net/grub")
[*]Burn into a cdrom (better) or a floppy
[*]Boot from it
[*][b]Select: your language
[*]Select: Restore Grub on MBR
[*]Select: Auto[/b]
[*]You see the message: SGD has done it!
[*]Reboot
[*]You're done.
[/LIST]

---

### Post by jonathansizz on 2006-02-05
Hi

I've looked through the posts but none of the methods described seems to be quite what I am looking for. I have Ubuntu 5.10 as my main distro. I installed this first. Later I installed 6.04 preview, and this installed its own GRUB. Now, I want to remove 6.04 altogether but when I tried this GRUB no longer booted my system (presumably as it was looking for the no-longer-existant GRUB from the deleted 6.04 partition). So I reinstalled 6.04 in order to be able to boot into 5.10. What I need is to be able to remove 6.04 but have GRUB boot 5.10 (from the 5.10 partition?). Here is the relevant info:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14797       19457    37439482+  83  Linux
/dev/sda2                   1       14216   114189988+  83  Linux
/dev/sda3           14217       14796     4658850    5  Extended
/dev/sda5           14217       14594     3036253+  82  Linux swap / Solaris
/dev/sda6           14595       14796     1622533+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

I think 6.04 is on sda1 and 5.10 is on sda2. So I think I need to have the asterisk next to sda2? sda5 is the swap for 5.10 and sda6 is the swap for 6.04

What is the best way of fixing this?

Thanks for your help!

---

### Post by jonathansizz on 2006-02-05
Sorry! I posted in the wrong section

---

### Post by Hawkeye501 on 2006-02-10
vnbuddy2002 im new to linux, my first install on a Compaq Proliant 3000 server, and I had that problem, GREAT NEWB document! :) helped me fix my prob :D

---

### Post by Hawkeye501 on 2006-02-10
ugh i did do something wrong, grub failed to load

---

### Post by phbc50 on 2006-02-11
Hello,
After installing another OS I lost the mbr on my HD (hda with ubuntu on hda7), here is the solution that I found to work :
- boot the ubuntu LIVE CD
- go in console, and change user to root with **su root**
- make a temp dir to mount the ubuntu partition :
**mkdir /mnt/hda7**
- mount the drive with :
**mount -t ext2 /dev/hda7 /hda7**
- chroot to the mounted system :
**chroot /dev/hda7**
- run grub at the promtp : **grub**
then :
**grub> root (<tab>**
where <tab> is an actual TAB which returns the hd that grub recognises, in my case **hd0 hd1 hd2**
then :
**grub> root (hd0,5)**   # in my case the hda7 partition is recognized by grub as (hd0,5)
**grub> setup (hd0,5)**
**grub> exit**
then reboot and it worked...
HTH
regards,
phbc50

---

### Post by charsiubao on 2006-02-15
i've used the live cd method to fix the error 17...but i get the error every so often.  i feel like that should definitely not be happening so often.  any suggestions/comments as to what the problem may be?...

---

### Post by jdpipe on 2006-02-16
If you need to restore your original Windows MBR / boot sector (for example if you messed up during your Ubuntu installation), see [this post]("http://www.ubuntuforums.org/showpost.php?p=733542&postcount=220").

---

### Post by SVFUSiON on 2006-03-05
i don't see /boot just ext and swap

---

### Post by SVFUSiON on 2006-03-05
here is my problem now, I reinstalled Ubuntu, I hit the "Install GRUB" it installed to the "MBR" or whatever the default is. For some reason, it is still booting to lilo, and I can not even get back to vista. here is my partition tables

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       30402   244204033+   7  HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
**Windows Vista is Install here**/dev/hdd1               3       79889    40262656    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
**Ubuntu is here **/dev/hdd2   *       79895      151933    36306900   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hdd3          151933      155056     1574370    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hdd5          151933      155056     1574338+  82  Linux swap / Solaris

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36138186    7  HPFS/NTFS

At this point i have no idea what is going on, 
I can't even find lilo anymore, where is it? where did grub go? How can I get my to normal lol. I use Ubuntu as a main OS but I still need vista to report bugs.

---

### Post by Scunizi on 2006-03-18
This thread was very helpful but I had a slightly different wrenkel that I discovered.  I lost my motherboard in a brown-out durning a thunderstorm.  After installing a new Asus P4v8x-mx I could boot into windows as normal but not Ubuntu.  So I deleted the Ubuntu partitions on my secondary SATA drive and proceeded to reinstall.  When finished and trying to reboot to Ubuntu I got the dreaded Error 22 and the previous error mentioned when trying to boot into windows.  After rebooting with the Ubuntu install disk and going through the install several times I started looking a the drive designations during the partion process.  What I discovered was my primary boot/windows drive was being listed as Sdb instead of Sda.  A quick swap of the cables on the motherboard and following the previous instructions fixed everything!  I couldn't have done it without reading this thread and a little investigation.  Thanks!:-D

---

### Post by armada on 2006-03-22
[QUOTE=remmelt]Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.
[/QUOTE]

This did work wonder in restoring the MBR of my Compaq Armada 1750 after I restored the laptop from Ghost. Yet the laptop's special partitition, where the BIOS tools are located, is no longer accessible through pressing F10 duing POST. 

I can live with this as I still can access the BIOS settings through using a floppy. Yet I wonder if there is a way to have both Grub and the easy F10 access to the BIOS tools.

I suspect that the original Compaq MBR is Windows-compatible. I may be able to Windows' boot.ini to access the Linux partitions and still keep the original BIOS access intact.

Thanks.

---

### Post by cellarguy on 2006-03-23
I'm missing one small piece.
When I boot to live CD, how do I become superuser?

---

### Post by Vlammetje on 2006-04-08
Just sudo I guess?


Here's my little problem.

Recently I installed Dapper flight 6 from a Live CD (via espresso) next to my XP install. It booted all fine and wonderful and both OS's worked well. After a while I have the brilliant thought of reinstalling dapper using the same Live CD as before, and this is something I wish I'd never done. During this install, it failed to install Grub. I've tried this over and over and over and over, and grub will not ever install to my PC at all.

Now I'm stuck with a PC that has (presumably) 2 working OS's on it, and no way to get to either of them.

I do have the Live CD. I have all my partitions mounted. Now how do I go about installing grub to the PC while I'm booted on the live disk?? :confused: 


Any help would be appreciated

---

### Post by PhilOSparta on 2006-05-05
I have followed all the steps on two identical laptops, one of which has the grub MBR messed up.  The messed up laptop is my daughter's and I am communicating via phone with her (I hate being a help desk! :sad: ).

We are stuck on step 4.
When we ***sudo chroot /mnt/ubuntu*** , we get this:

```
chroot: cannot run command `/bin/bash': No such file or directory
```

This really confuses me.  On my good laptop everything is fine.

The only difference in the setups is that I am using a Live Ubuntu CD burned from a downloaded ISO file.  My daughter is using a factory Ubuntu Live CD.

Any ideas?

---

### Post by Masterminds on 2006-05-27
thanks mate

---

### Post by StormWatcher on 2006-05-27
[QUOTE=remmelt]Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)[/QUOTE]


This method did bring back my grub, however I get an error when I boot.
My partition list is:
/dev/hda1 Windows NTFS (Has my XP Pro on it)
/dev/hda2 Extended 3 (Has my Ubuntu on it, and I can mount and look at all my data)
/dev/hda5 Swap
/dev/hda4 Unformatted

I opened a terminal window and did the following:

```

grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage_5" exisits... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded. succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.list"... succeeded
Done.
```

The first time I ran this command I did get errors, but it said they were not fatal.  I do not know what they where, but now it seems to succeed just fine.


But when I boot my screen looks like:
```
  Booting 'Ubuntu. kernel 2.6.12-10-386 '

root (hd0,2)
 Filesystem type unknow, partition type 0x5
kernel /boot/vmlinuz-2.6.12-10-386 root=dev/hda3 ro quiet splash

Error 17: Connot mount selected partition

Press any key to continue...
```

Also when I boot using the the rescue option and then type:

```
sh-3.00# grub-install /dev/hda2
```

I get:

```
The file /boot/grub/stage1 is not read correctly.
```

So now I am not sure what I should do....  My linux is on hda2.  I have very little knowledge of linux.  The menu still boot my Windows XP.  I wish it was there other way around.

Thanks for your help.  ](*,)

---

### Post by StormWatcher on 2006-05-28
If anyone caree, I was able to fix my problem by editing the menu.lst file in /boot/grub.  I changed the file to read:

root (hd0,2)
kernel /boot/vmlinuz-2.6.12-10-386 root=dev/hda3 ro quiet splash

to

root (hd0,1)
kernel /boot/vmlinuz-2.6.12-10-386 root=dev/hda2 ro quiet splash

and all works fine now.  This thread helped alot.  Thanks.

---

### Post by loko on 2006-06-02
I want to thank "remmelt" for his great tip, how to handle grub.

this helped me a lot.

---

### Post by BoomAM on 2006-06-18
Im having quite a few problems here.
All of the fixes that have been listed thus far dont work.

Basically, i booted into XP yesterday, set my TPs updator going, and it told me about a 1.3Gb update to the R&R Partition on my TP. So i DLed it & installed it. Anyway. I come to boot the laptop now, and it gets to a screen where it says 'GRUB' at the top, then does nothing. So now i cant access anything at all.

The only live CD/install CDs ive got to hand are the 5.04 ones, ive lost my 6.06 CD, and i havnt got anymore CDs to burn anymore.

Any ideas ppl?

---

### Post by HolyMurderer on 2006-06-18
To me it says:

grub> root (hd0,0)
 Filesystem type is fat, partition type 0xc

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/boot/grub/stage2" exists... no

Error 15: File not found


I have Windows at sda1. It's the first partition on the first hdd. I'm having a problem, I just changed default from 0 to 4, for windows becoming the default boot, and now, if in grub I select to boot windows, or wait for auto boot, It shows the grub menu again... :(

the only thing that's not booting is windows. The rest is booting...

The entry (windows part) in menu.lst is:

> title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
makeactive
chainloader    +1 


My fdisk -l
> Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1853    14884191    c  W95 FAT32 (LBA)
/dev/sda2            1854       19452   141363967+   f  W95 Ext'd (LBA)
/dev/sda5            1854        9416    60749766    b  W95 FAT32
/dev/sda6            9417        9622     1654663+  82  Linux swap / Solaris
/dev/sda7            9623       17476    63087223+  83  Linux
/dev/sda8           17477       19452    15872188+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        7297       24321   136753312+   c  W95 FAT32 (LBA)
/dev/sdb2               1        7296    58605088+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    7  HPFS/NTFS



I remembered now something. First I did grub-install /dev/sda1. I've tried fdisk /mbr and grub isn't removed. So I think grub is not on mbr, but on hdd itself. Is it possible that when I choose the windows option in grub, grub is loading grub again, because is on that hdd and partition?

I don't know if it's stupid, the question, or if it's possible... I'm just in despair, because i need my work on windows and I can't even boot into win xp cd to fixboot :(

Any help please?

---

### Post by airjunman on 2006-06-29
Hey,

I am an absolute beginner to Ubuntu and pretty much the same to Linux... Now I  tried playing with a couple of "unknown" type partitions during a session and forgot about it ...  some time later my system(which by the way, has happened  afew times before too, but thats off the point) ... I hard reset it and since then had a GRUB Error 17
very similar to this post...[http://www.ubuntuforums.org/showthread.php?t=199893](http://www.ubuntuforums.org/showthread.php?t=199893)

I did a > 
sudo mkdir /mnt/hda6
mount -t ext3 -o rw /dev/hda6 /mnt/hda6
grub-install --root-directory=/mnt/hda6 /dev/hda
Now I seemed to be able to fix the Error 17, but now it boots to a error 22 saying that No such partition hda(0,8) ... 
Why can't i just tell grub to boot off hda6 which is my bootable linux partition?
And a lot of people reply saying "reinstall grub", but i really don't have a clue as to how to do that..
Using the Install CD to do it failed.. the Installation just crashed and i didn't see anything about installing GRUB...
I'd really appreciate some help.. Thanks in advance

---

### Post by ericesque on 2006-07-01
Wow.  I just had the bought of the century with my MBR.  

I installed a fresh dapper a few days ago.  Not even considering the consequences, I installed with my external sata drive running.  There was an old install of some linux distro on there that I'd never wiped.

Come a few days later when I actually took my lappy away from my desk, I tried to boot and started getting errors from grub.  Something about my sata drive not being available and it mentioned superblocks.  

So it was on to searching the forums.

I found this thread and tried the live boot method... a couple times.  Once before removing the linux install on my sata drive, once with the drive off, and maybe once after I deleted the install.   No luck.

So I decided I'd had it and I'd try the first post-- if I fried my current install, so be it.  

I fought with the dapper text based installer some as well.  I had to abort the install 2 or 3 times before I figured out exactly how to make it reinstall grub.  It is a highly particular installer.  It even bothered to mention that one of the ext2 partitions that I'd formated with Acronis Disk Director had a... and I quote... "funny looking format".  Funny looking format? Is that the technical phrase for it?

Anyway, it finally worked.  This thread played a big part in getting there.  Big thanks to those who have contributed.

---

### Post by alejandrops on 2006-07-03
HELP!!!
i've tried everything on this thread but still cant reintall GRUB.
when I type grub-install /dev/sda the answer is:
could not find device for /boot: Not block found or not a block device.
aso when i tyoe inside grub find /boot/grub/stage1 says "error 15: file not found"
both commands after and before chroot my linux part. 
any ideas?
heeeelp!!!!

---

### Post by petern on 2006-07-12
Sorry you have had no replies. I have experienced exactly the same frustrations you have. Nobody seems able to explain the 're-install grub' suggestion, and I have been trying to do it with the Knoppix live cd without success.
The only way forward would seem to be to re-install the o/s, hopefully without losing everything in the process.
To access/boot your Windoze partition, use Knoppix (as root), or System Rescue or a Win 98 boot floppy/Win 2000 install cd, and type this:

   fdisk /mbr

Then at least Windows will boot, and you can do what needs to be done later.

---

### Post by Vostronius on 2006-07-17
ok, so this is my situation, I had windows XP and Ubuntu 6.06 both working perfectly with GRUB as the boot loader. But then I had to reinstall Windows, and then GRUB stopped showing up and letting me switch between the os at start up, after trying everything on this forum to no avail, I decided to try system commander, so I got that when I went to reboot, system commander wouldn't work, it just said "boot >>" and then it wouldn't do anything, so now I can't even get into Windows, so I am forced to use the live cd from an old ubuntu 5.10 to do anything. And it didn't work when I tried using the live mode or install mode on my ubuntu 6.06 cd. Please help, thx in advance.

---

### Post by Dural on 2006-07-27
GRUB is screwed up on my computer. I have two hard drives (both are ATA so they are called hdc (Windows XP) & hdd (Kubuntu Dapper Drake). I put each OS on its own hard drive so that (in theory) should one happen to get messed up, the other would be fine. Later on, I had a seperate problem with Kubuntu (it messed up my screen resolution) and after asking for help at various forums and having all solutions fail, I angrily decided to reinstall Kubuntu. Unfortunately, the graphical install froze as it was copying the files to the hard drive, so I restarted the system. The first time, I was greeted with GRUB Error 22, so I then tried to fix the Master Boot Record using a Windows XP CD (shown here: [http://www.neowin.net/forum/index.php?showtopic=292614]("http://www.neowin.net/forum/index.php?showtopic=292614")), only to realize that it would not work because GRUB could not load, giving me GRUB Error 15. I was about to try the suggestions on this thread, but rushing to solutions is what got me into various messes involving both Ubuntu ahd Kubuntu Dapper Drake so I want to wait and see what you guys have to say. 
System Specs:
Processor: AMD Sempron 3100+
Memory: 1 GB
Video Card: Nvidia GeForce 4Ti 4200 (128 MB)
boot order was:
Hard Drive 1: hdd (40 GB ATA /w the Kubuntu Dapper Drake install)
Hard Drive 2: hdc (80 GB ATA /w Windows XP SP2)

I would add my fdisk -l output, but I am typing this from a laptop (not the affected computer) running Windows XP SP2. 

Any help would be much appreciated.

---

### Post by akurashy on 2006-07-30
Okay guys, I really need a hand here 

I installed windows today in another partition, MBR took over , this is how I messed up 

Right now it's a miracle i'm logged in to my ubuntu partition, i've been playing with lady luck for a while

I installed GRUB again but the problem is 
root (hd0,1) gives me "can't mount" 
then i tried editing with (hd0,2) which worked 
then noticed that it didn't work , then noticed that the hda mounting said "2" and changed it to "3" and it started to boot

as you see i have a mess right now 

i want to install my GRUB correctly and flawless, knowing that my linux partition is safe i'm glad because i have a lot of data here 

my fstab
> david@akulinux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



and this is my menu.lst

> david@akulinux:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

splashimage=(hd0,1)/boot/grub/default-splash.xpm.gz

title           Ubuntu, kernel 2.6.17
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17
savedefault
boot

title           Ubuntu, kernel 2.6.17 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17
boot

title           Ubuntu, kernel 2.6.15-26-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-26-k7
boot

title           Ubuntu, kernel 2.6.15-23-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-k7 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-k7 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-23-k7
boot

title           Ubuntu, kernel 2.6.15-22-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-22-k7 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-22-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-22-k7 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-22-k7 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-22-k7
boot

title           Ubuntu, kernel 2.6.15.4
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15.4 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15.4
savedefault
boot

title           Ubuntu, kernel 2.6.15.4 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15.4 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15.4
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Arch Linux
root            (hd0,3)
kernel          /boot/vmlinuz26 root=/dev/hda4 ro
initrd          /boot/initrd26.img
savedefault
boot


i don't know how i did it but i had to edit this 

root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-k7
savedefault
boot

i'm actually very nervous right now , to be honest is my first time playing with GRUB and i don't want to make any mistakes  >_< 
anyway i hope anyone here can help me

---

### Post by KillrBuckeye on 2006-08-06
My MBR seems to be really screwed up after moving, deleting, and creating some partitions on my only hard drive.  I have tried rewriting Grub to the MBR many times (both via the Grub floppy, and within Ubuntu), but I keep getting an error message upon reboot:

DISK BOOT FAILURE, INSERT SYSTEM DISKA ND PRESS ENTER

(Yes, I know it is trying to boot from the HDD since I have tried disabling everything else in the boot order).  However, if I boot from a Grub floppy, I can specify the 'menu.lst' file and everything works fine.  Further, I can use a LiveCD and choose "Boot from first hard disk", and it works fine.  The problem is definitely with my MBR or something I'm doing wrong while writing to it... :(

My grub folder is on my /boot partition, which is hd0,0.  I have tried writing to the MBR in the following ways:

1) grub> root (hd0,0)
         setup (hd0,0)

2) grub> root(hd0,0)
         setup (hd0)

3) sudo grub-install /dev/hdb

(yes, my only hard drive is primary slave, or hdb)

Nothing works, and I have no idea what to try now.  Any suggestions?

---

### Post by xgravix on 2006-09-04
Um, could someone kindly delete the misinformation in the first post? Following the instructions results in your ubuntu installation on disk being partially wiped and replaced with garbage when the installer crashes. 6.06 LTS.

I was able to correctly restore my GRUB using the command line, but it is too late thanks to this HOWTO which has been posted all over the internet.

---

### Post by magnum2000 on 2006-09-23
Hi all.
I have reinstalled Winzozz and now grub isn't enabled.
I'm trying to restore GRUB but nothing to do...

This is my configuration:
```

/dev/hda1 WINDOWS
/dev/hda2 /
/dev/hda3 /swap

```
This is the log

```

root@ubuntu:/# grub-install --root-directory=/boot /dev/hda
Could not find device for /boot/boot: Not found or not a block device.

root@ubuntu:/# /sbin/grub
Probing devices to guess BIOS drives. This may take a long time.
root@ubuntu:/# /sbin/update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-26-k7
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Now no one MBR start :( 
Suggestions?

---

### Post by oscabat on 2006-09-24
My situation is a little different:
I have two hard drives - 1 Windows, 1 Ubuntu
I want to format both of them, so I first formatted my Ubuntu one.  Apparently, there must have been some GRUB files on my Windows hard drive as well, as it still attempts to load GRUB (and now I get error 17).  I can't really restore GRUB from either of my hard drives because both of them are NTFS, and so I can't mount them (at least, I assume that's why).
What can I do to boot back into Windows?

---

### Post by wolf202 on 2006-11-08
Ok so I reinstalled windows and it messed grub so i'm trying to reinstall it with a live cd. I've been trying all the methods on the master list.

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

The thing is when I type "root (hdX,X) or whatever I can never find one that works I don't know what to choose

This is the picture of my hdd setup can someone tell me what to type because find /boot/grub/stage1" does not work.

[IMG]http://img.photobucket.com/albums/v440/wolf202/a279e0b3.png[/IMG]

The 51GB partition is Windows the 40GB partition is Ubuntu, the others are just NTFS Data Storage

BTW, I'm using the Edgy Eft AMD64 live CD also I can boot my ubuntu with the [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php")

-wolf

---

### Post by venky80 on 2006-11-12
OK guys I think the thread basically lost the point after a while 
therefore I am listing the problem again and letting ppl know what solved it for me.
PROBLEM: RE INSTALLING WINDOWS IN A DUAL BOOT SYSTM WIPES THE MBR and HENCE U DONT HAVE GRUB NOW TO MULTIBOOT.
SOLUTION : BOOT WITH LIVE CD
OPEN TERMINAL WINDOW
$ sudo fdisk -l
this should list all ur Hard disk
my root was /dev/hda4
then
$ SUDO GRUB
grub> root (hd0,3)
I dont know why it was hd0,3 and not hd0,4 but it worked
then
grub> setup (hd0)
grub> quit
 problem fixed
always using SUDO works
hope it helps

---

### Post by dabotsonline on 2006-11-15
Hey guys,

I have a dual-boot setup of Win XP (hda1 / (hd0,0)) and Ubuntu Edgy ext3 (hda2 / (hd0,1)). extended is hda3 and linux-swap is hda5.

GRUB hung on "GRUB Loading stage1.5" a few weeks ago, with the menu never appearing, and I solved it by booting into Edgy Desktop CD and entering the following:

> 
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# cd /mnt
root@ubuntu:/mnt# ls
root@ubuntu:/mnt# cd
root@ubuntu:~# mkdir /mnt/ubuntu
root@ubuntu:~# mount -t ext3 /dev/hda2 /mnt/ubuntu
root@ubuntu:~# chroot /mnt/ubuntu
root@ubuntu:/# grub-install /dev/hda


This originally solved the problem.

However, I experienced the same problem today and, when I entered "grub-install /dev/hda", I was confronted with the following message:

> /dev/hda: Not found or not a block device.

So I tried replacing the last line with a suggestion I found elsewhere:

> grub-install /dev/hda --root-directory=/mnt/ubuntu/boot/grub

however, this was the response:
> mkdir: cannot create directory `/mnt/ubuntu/boot/grub/boot': No such file or directory
Why has it added an extra 'boot' at the end? There are no further subdirectories within /mnt/ubuntu/boot/grub .


I then tried the following:

> grub> root(hd0,1)
but I got this back:
> Error 27: Unrecognized command
and when I typed:
> grub> setup(hd0)
I got the same response. When I tried it in an attempt before this one, I think it said "Unrecognized drive" or something similar.

Incidentally, given my dual boot setup, should I have instead written, "setup(hd0,1)"? I have attached my menu.lst below.


I then tried the final suugestion I found on here.

The Edgy Alternate CD "Partition disks" sections indicates that:

> 
#1 primary   ntfs   /media/hda1   
Bootable flag: on

#2 primary   ext3   /media/hda2
Mount point: /media/hda2
Bootable flag: off

#5 logical   swap   swap


The suggestion on here seemed to say that I should change the mount point of /media/hda2 to /, and also set the bootable flag to on; but should I also leave the /media/hda1 bootable flag on as well?


Thanks,

Nick


Here is my /mnt/ubuntu/boot/grub/menu.lst:

> 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bfe5aabb-1181-4c09-8c06-25e4d70074c0 ro
# kopt_2_6=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Is this bit:

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

significant?

---

### Post by dabotsonline on 2006-11-17
I've fixed the problem: [http://ubuntuforums.org/showpost.php?p=1769691&postcount=5](http://ubuntuforums.org/showpost.php?p=1769691&postcount=5) :D

---

### Post by marx2k on 2006-11-29
> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)

Best instructions ever. I have now saved 2 systems with this method.

---

### Post by marx2k on 2006-11-29
Actually, scratch that...

When I use "Boot from first hard disk" from the liveCD, it works...

if I dont use a CD and try to boot from the first hard disk... it gives me Error 22: No Such Partition or something like that...


WHat gives??

---

### Post by marx2k on 2006-11-29
Ok looks like on this system:
```

Disk /dev/hda: 13.6 GB, 13676544000 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1662    13349983+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       38913   292085797+   f  W95 Ext'd (LBA)
/dev/sda5            2551       15298   102398278+   7  HPFS/NTFS
/dev/sda6           28047       38913    87289146    7  HPFS/NTFS
/dev/sda7           15299       16573    10241406   83  Linux
/dev/sda8           16574       27839    90494113+  83  Linux
/dev/sda9           27840       28046     1662696   82  Linux swap / Solaris

```

grub was trying to boot from (2,6)
I had to edit that at boot time to be (0,6)

Not sure why it set itself up that way.

---

### Post by Roberto Rosselli on 2006-12-01
Hi all, I have 

* Windows on hda (several partitions)
* /boot on hdb1
* / on hdb2

What should I type to restore grub?

Thanks in advance!

Roberto

---

### Post by zigot on 2006-12-12
I had the same problem. After playing arround with all the methods described without success, I've found that (for some reason) none of my partitions were active.

This is the way I've solved it:

- burned an iso of the Super Grub Disk (what a great tool)
- used the CD to activate my hd0
- I reseted and booted into fully operational Ubuntu installation via Super Grub Disk
- then I sudo-ed into grub, did the "root (hd0,x)" and "setup (hd0)" <-- just to be sure
- I restarted the system and that was it :)

---

### Post by intrepidus on 2006-12-12
I need to reinstall grub to get XP working, but I don't know what drive grub is on. I know it's my primary drive, but I don't know what sata it is.

Is there a way to find out what drive is sda, sdb, sdc, sdd, etc.? And which one hd(0,0) is?

---

### Post by shahin on 2006-12-27
wow I must say SGD, Super Grub Disk, is a life saver.  I foundout about it about an hour ago and burned the iso and was just able to recover my Windows XP stuff and erase the old mbr.  I am now reinstalling Ubuntu 6.10 and hope that will install a good copy of grub so I can double boot.  I'll keep you posted.  I think other ways would work also, but for absolute beginners like myself the software rocks.  The url where you can get it is posted in previous comments but here it is again:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by shahin on 2006-12-27
ok reinstalling ubuntu did not work.  I am able to log into xp when I remove the mbr grub enteries with SGD but I can not reinstall ubuntu with the desktop cd:-(.  I get error 18.  Since I am installing ubuntu on a 80 G drive I wonder, is the size of the drive really?  I think the last time the two (Ubuntu and XP) were working on this pc it was the same setup.  I changed the setings in bios also but did not get rid of the error.  
In previous posts there is mentione of live cd vs. Install CD.  Just making sure, by live you mean the desktop cd?  And install is the other one?  that one should give me more options?  I tried to change the /root to logical, but the desktop install did not allowe me to do this.

---

### Post by shahin on 2006-12-27
> **zigot said:**
> I had the same problem. After playing arround with all the methods described without success, I've found that (for some reason) none of my partitions were active.

This is the way I've solved it:

- burned an iso of the Super Grub Disk (what a great tool)
- used the CD to activate my hd0
- I reseted and booted into fully operational Ubuntu installation via Super Grub Disk
- then I sudo-ed into grub, did the "root (hd0,x)" and "setup (hd0)" <-- just to be sure
- I restarted the system and that was it :)

Would you please state ( as much as you recall ) how you did the following:
used the CD to activate hd0?  What options did you use from the CD?

reseted and booted into fully operational Ubuntu?  

setup hd0?  How?  I followed some of the procedures in previous post successfully but I still get the same error ie. error 18.  Do you recall what error you got?  I may just be having a different problem.  I admit I have to read some of the material about grub to findout exactly what it does.  The super grub disk page has some good advice.  But regarding error 18 it just briefly discusses some of the procedures stated here.

---

### Post by Cleric. on 2007-01-02
I recently installed Windows XP on a drive that shared a computer with one harboring Ubuntu Edgy. 

When I tried booting from Edgy, I got the same GRUB Error 21 message that most people seem to be getting.

So, I followed the majority of the instructions on the first and last few pages of this thread, but much to my dismay, nothing has worked yet. 

When I am under GRUB in the terminal and I type the "/boot/grub/stage1" command to attempt to find out my boot partition number, but "Error 15: File Not Found" is the only response I get. 

I used "sudo fdisk -l" in the terminal to get my hard drive info, and the boot path is "/dev/hda1" but the only thing that happens when I try "root (hd0,0)" under GRUB in the terminal is "Error 21: Selected disk does not exist."

Nothing else has worked so far, either.

Any hints on what might be wrong and what I can do?

---

### Post by ucsdrake on 2007-01-02
> **Cleric. said:**
> 

When I am under GRUB in the terminal and I type the "/boot/grub/stage1" command to attempt to find out my boot partition number, but "Error 15: File Not Found" is the only response I get. 


you need to type in the "find /boot/grub/stage1"

but personally i dont know how to actually change the location of my grub from its location on the internal HDD (which by following those instructions is (hd0,3) to my external HDD which i know is (hd1), has 4 partitions

1. Windows NTFS
2. Win/Lin Shared Fat32
3. Linux Swap (swap)
4. General Linux (Ext3)

would that mean that i want to change my location to (hd1,3) and if so where in the instructions of 

Quote:
Originally Posted by remmelt View Post
Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me

---

### Post by ajare on 2007-01-02
> **Cleric. said:**
> I recently installed Windows XP on a drive that shared a computer with one harboring Ubuntu Edgy. 

When I tried booting from Edgy, I got the same GRUB Error 21 message that most people seem to be getting.

So, I followed the majority of the instructions on the first and last few pages of this thread, but much to my dismay, nothing has worked yet. 

When I am under GRUB in the terminal and I type the "/boot/grub/stage1" command to attempt to find out my boot partition number, but "Error 15: File Not Found" is the only response I get. 

I used "sudo fdisk -l" in the terminal to get my hard drive info, and the boot path is "/dev/hda1" but the only thing that happens when I try "root (hd0,0)" under GRUB in the terminal is "Error 21: Selected disk does not exist."

Nothing else has worked so far, either.

Any hints on what might be wrong and what I can do?

---------------------------------------------------------------------------------------------------------

I might be barking up the wrong tree but the command in GRUB is

"find /boot/grub/stage1"

I recall getting the same error when I tried to save time by using the command line before  booting into the GUI. Once the live cd was into the GUI though I reinstalled GRUB without problems.
in a terminal...

> grub
grub> find /boot/grub/stage1
(hd0,1)
(hd0,2)
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

this installs grub to the MBR, note the issues raised in earlier posts if you have other boot programs installed.

---

### Post by ucsdrake on 2007-01-02
> **ajare said:**
> 
I recall getting the same error when I tried to save time by using the command line before  booting into the GUI. Once the live cd was into the GUI though I reinstalled GRUB without problems.
in a terminal...

> grub
grub> find /boot/grub/stage1
(hd0,1)
(hd0,2)
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

this installs grub to the MBR, note the issues raised in earlier posts if you have other boot programs installed.


you go from 
grub> root (hd0,1)
to
grub> setup (hd0) 

from my understanding the ,1 was avery important part of this fix ... do we need to add the ,1 or not?

sorry i just want to make sure i get all the steps right before i go forward seeing as i'm having problems as it is and i dont want to make it worse lol

---

### Post by ajare on 2007-01-03
> **ucsdrake said:**
> you go from 
grub> root (hd0,1)
to
grub> setup (hd0) 

from my understanding the ,1 was avery important part of this fix ... do we need to add the ,1 or not?

sorry i just want to make sure i get all the steps right before i go forward seeing as i'm having problems as it is and i dont want to make it worse lol

ucsdrake,
I can't see any typos in what I wrote and it worked for my amd64 3500+ installation of 6.10.

I can't say more then that. Now I just need to solve my wireless problems...

---

### Post by sblanzio on 2007-01-04
hi this can help anybody...

I substituted my HD with a larger one and used partimage to move linux partition to the new HD... but I had a continuos Grub Error 15 at boot (without any specified "file not found").

I tried to do anything suggested in this thread but i kept having this problem.

Then i understood it was a BIOS problem. In fact my bios allowes to select a priority in HD booting access. Even if i moved my last HD from master to slave it still was at the top of the bios hd boot priority.

So i changed properly this value and finally the correct grub has loaded.

hth

bye
sblanzio

---

### Post by pichalsi on 2007-01-11
This guide sure helped a lot of people :) I just messed with partitions a little bit so my grub did not boot. Solution? Fire up LiveCD, use Konqueror to Google "Ubuntu howto restore GRUB" and the solution is right there. I have to love this ! Thumbs up

---

### Post by bugz0r on 2007-01-12
The screen freezes at the splash screen.

---

### Post by bugz0r on 2007-01-12
and when I use the method in the first post there is never a root file system. see screenshot.

---

### Post by geezerone on 2007-01-16
Has anyone had problems using SATA drives in conjunction with IDE (PATA) drives? I ask this as I have had to physically unplug the power to any IDE drives otherwise GRUB installs to the MBR of the IDE drive. Have had this happen on all my machines so isn't a one off.

:KS

---

### Post by Foolishgrunt on 2007-01-21
OK, so here's my problem. I'm running a dual boot with Edgy and Windows XP. Recently I started having all sorts of trouble with getting GRUB to boot properly, and I eventually resorted to popping in the Windows XP CD and restoring the MBR from there. Now Windows works fine, but it bypasses GRUB entirely and I can't figure out how to get back to Ubuntu.

I've looked at a lot of the solutions offered here, and they all seem to involve booting from the linux CD. But for some insane reason which I still can't figure out, my CD drive will read practically any disc except the Ubuntu disc. (I've tried burning multiple copies from multiple computers. None of them work, so I'm quite sure it's a problem with my drive.) Can anyone help me restore GRUB *without* the use of a CD?

---

### Post by GeoPirate on 2007-02-17
Ok I am trying to get triple boot working.  I was running XP and xubuntu.  I installed ubuntu and the xubuntu dissapeared off my grub, how do I add xubuntu back to grub or edit the grub menu? FYI xp is hd0, xubuntu is hd4 and ubuntu is hd5
when I put in the command " find /boot/grub/stage1 " the output is " (hd0,5)"
thanks in advance!

---

### Post by irrational_e on 2007-03-06
I have been trying for a WEEK without any remote sniff of success to fix GRUB.
My setup:

Hda = WIndows XP. Master on IDE0 (Work drive)
Hdd = Windows XP. Slave on IDE1 (Occasional backup drive that I now wanted to remove)
Sda = Ubuntu Edgy on S-Ata (Hopefully new work drive)

The problem: 
Installed Edgy with all drives in the machine, removing the hdd cause GRUB error21 in Stage 1.5

I finally fixed the problem after thinking about it for a while and trying out some things.

There are 2 files in /boot/grub. device.map and menu.lst that make a difference. Basically they tell what shows up on the GRUB menu on bootup it seems.

steps:

1: Remove Hdd
2: Boot using Ubuntu Edgy install CD
3: Mount the Edgy drive as explained earlier like this:

[B]In the install CD gui open a  terminal or use ctrl+alt+f1 for a different term.
Changes as root user![/B]
> sudo bash **"""switch to root user"""**
> mkdir ubuntumnt** """make a mount point"""**
> mount -t ext3 /dev/sda1 ubuntumnt **"""Mount ubuntu drive. the '1' is a partition (s-ata drive, partition 1). In other words, mount the partition, not the drive"""**

4: Now that you have a point edit the device.map and menu/lst files

> vi ubuntumnt/boot/grub/device.map
**"""This shows the contents of the device.map file"""**
hd0 /dev/hda
hd1 /dev/hdd
hd2 /dev/sda

[B]"""
Edit above to remove the hdd. Since the IDE drive is read first by the system, by observation the s-ata drive will be hd(x) where x is the number after all ide drives (it seems to me), so 4 ides and an s-ata will result in hd4 being the sata drive.
Now we have:
"""[/B]

hd0 /dev/hda
hd1 /dev/sda

**"""save the file and edit the menu.lst""**
> vi ubuntumnt/boot/grub/menu.lst

**"""At the bottom you will have entries like this"""**

***********************************************************************
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd2,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd2,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd2,1)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
chainloader +1

*********************************************************************************

**"""Edit the file to change the drive numbers to correspond to the device.map and remove the hdd so it now look slike this:**
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

*********************************************************************************
**"""Save the file and enter the grub interface"""**

> grub

**Now we show where the root is. Since we mounted the edgy partition, we can see the grub folder. (Not mounting is the reason why "find /boot/grub/stage1" sometimes does not work as asked in above posts.**
 >find /boot/grub/stage1
hd (1,0) **"""This should be you edgy drive. In my case hd(1,0) after I removed hdd. 2nd Physical drive 2, partition 1. Meaning sda1 in my case"""**

**Now we follow previous steps in this HOW TO**
root (hd1,0) **"""Define the root partition on the drive**
setup (hd1) **"""Setup grub on the drive"""**

[B]"""At this point all previous posts said quit and restart, yet I still got the Error21. I eventually decided the MBR on the hda windows disk was messed up too.
Since I know the windows drive is hd0 I also did"""[/B]
setup (hd0)
quit

**"""Now we restart the machine and voila! IT works again**

---

### Post by RonKZ on 2007-03-23
avoid?  hell, for a newbie prior to actually being booted into whatever distro, commandline is virtually impossible, it's plain wilderness stuff.

---

### Post by SFHasan on 2007-04-30
Please please,

All my dear fellows in trouble, benefit from the excellent tool called Super GRUB at [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org) 

Download its ISO image, burn to an empty Floppy or CD. Boot from it and answer simple menu based question to get your GRUB working and enabling the access to Multi-Boot Windows XP/Vista again.

Regards,
S.F.Hasan

---

### Post by Hakunushi on 2007-05-20
guys u just shouldnt forget that to run grub and do something on it u actualy gota be root, so even if u boot grom the live cd u gota run grub as root so u should type $"sudo grub", the live cd wont ask for passwd and ull run grub with the permitions to do whatever u want to.

---

### Post by lilnerd on 2007-05-26
> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)

Hi! I'm trying this method but its not working. Well its just me. I dont know what my hardisk is  (i.e hd0.6) How can i find out. Help appreciated. Windows is driving me nuts. Thanks LilNerd

---

### Post by vyoufinder on 2007-05-27
I've been trying this for more than 2 days now.  I've tried every suggested method in here and several variations thereof.  None of them work for me.  Every time I try to boot, no matter which method I try, I get "Grub loading..."  Then the Ubuntu logo pops up with the progress indicator and it doesn't move.  I let it sit for more than an hour to make sure it was frozen and nothing.  I tried Norton Ghost too - didn't work, wouldn't even try it.  Now what?  Seriously, it should not take 20+ hours of trying, just to backup a hard drive!

---

### Post by RonKZ on 2007-05-27
> **SFHasan said:**
> Please please,

All my dear fellows in trouble, benefit from the excellent tool called Super GRUB at [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org) 

Download its ISO image, burn to an empty Floppy or CD. Boot from it and answer simple menu based question to get your GRUB working and enabling the access to Multi-Boot Windows XP/Vista again.

Regards,
S.F.Hasan

Sorry, folks, but the link to [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org) gets us nowhere.  It opens a webpage with nothing on it.  So I spend over 2 hours today Googling/etc for Supergrub, and can report only that apparently it is now vaporware, nowhere to be found.  Save yourself the time.

I have generally found solutions using BootIt-NG, Symantec/Norton Boot Magic module of PartitionMagic, and DOS MBR tools (buried within .../tools on windoze CD's).  I'm still rather a newbie to Linux but have tried most all the major distros, and in doing so have wiped out/corrupted my MBR countless times.  So we do need a better standard linux tool for Grub/Lilo, something straightforward rather than messing with all those mentioned!

---

### Post by vyoufinder on 2007-05-27
> **RonKZ said:**
> Sorry, folks, but the link to [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org) gets us nowhere.  It opens a webpage with nothing on it.  So I spend over 2 hours today Googling/etc for Supergrub, and can report only that apparently it is now vaporware, nowhere to be found.  Save yourself the time.

I have generally found solutions using BootIt-NG, Symantec/Norton Boot Magic module of PartitionMagic, and DOS MBR tools (buried within .../tools on windoze CD's).  I'm still rather a newbie to Linux but have tried most all the major distros, and in doing so have wiped out/corrupted my MBR countless times.  So we do need a better standard linux tool for Grub/Lilo, something straightforward rather than messing with all those mentioned!

You can download it here: [http://freshmeat.net/projects/supergrub/?branch_id=62132&release_id=251708](http://freshmeat.net/projects/supergrub/?branch_id=62132&release_id=251708)

A quick Google check found it on the 1st page.  I already tried using Super Grub Disk.  It didn't do anything for me that helped anything.  Exact same freeze-up after stage 1.5 of Grub and as soon as the Ubuntu logo shows it's frozen.  I'm coming up on my third day of trying to simply backup a disk.  I think I've tried about all the tools out there but any suggestions?  It's a default install.  The only reason I want to do this is to see if any of the methods actually work as posted.  So far they all have missing steps, expect you to know tons of computer terms that I don't know, or just don't work.  Some of the methods described here are impossible in 7.0.4 too.  What a mess.  Glad I don't actually have to back something up that's important!  I'd have destroyed it probably 10 times by now.

---

### Post by vyoufinder on 2007-05-27
I can't believe it.  I was about to leave and call it another wasted day and thought I'd try booting one more time.  Well, no change happened.  I got to the Ubuntu logo and as soon as the progress indicator loaded it just froze.  Same as it's been since I started the backup process more than 2 days ago... For no apparent reason, I decided to hit enter and bam!  The damn thing just started booting!  I didn't do anything or use any tools this attempt.  I used the simple tar method.  None of the backup tools did anything for me.  Half of them I either didn't understand how to use or they simply didn't work so I'd say don't waste your time on backup programs.  I'm just glad I can forget about this whole backup thing now and finally move on.  Only 2.5 days to make a backup, wow, now that's progress.

---

### Post by vyoufinder on 2007-05-31
I just realized my backup still did not boot.  I had the original drive in and didn't realize it.. So my mbr is still messed up.  I've tried re-installing it through the Synaptic package manager, tried reinstalling from command prompt.. Something screwy here going on.  When I use Super Grub Disk to boot, it boots right in and runs fine.  Ideas anyone?

---

### Post by dannyboy79 on 2007-05-31
i don't understand what you want here? Are you saying that you used some form of tool to backup your entire install and then you restored it to another drive or partition? You want to be able to boot into the backup to see if it worked? If all you want to do is install grub and have it boot this backup image that you untarred onto a partition, then you'll need to make sure that your menu.lst and your fstab files are correct, here is the guide to reinstall grub if you need it: 
[http://ubuntuforums.org/showthread.php?t=459257](http://ubuntuforums.org/showthread.php?t=459257)
when you get to that link, it's actually a link to help another user install 3 os's into his machine BUT the post number 4 is the one that you have to follow, all you do is copy and paste what the commands are that are within the little code boxes and that will reinstall grub into the mbr of the hard drive that you are booting from the bios. (NOTE: make sure you chose the correct device (hd0 or hd1 for your situation) Then the next step is to make sure that the menu.lst that it's going to look at and use for it's config is correct. You'll need to make sure that the boot line is correct. So, if you're unsure of how to make sure it's correct, I'll need to see the following info to help, after you chroot into your system, I neeed you to paste the output from these commands
```
sudo fdisk -l
```
and
```
cat /mnt/root/boot/grub/menu.lst
```
```
cat /mnt/root/etc/fstab
```
So you're saying that you never had this freezing problem before you did this backup and restore thingy? What does this show?
```
lspci
```
ALso, I have made a cool guide for checking SBACKUP backups (SBAACKUP is a GUI backup tool that I use and love and it VERY easy to use) so that you know you have a backup of your system once you have it the way you want it and can trust that the backup will save you one day if your system is unfixable. It's here: [http://ubuntuforums.org/showthread.php?t=401425](http://ubuntuforums.org/showthread.php?t=401425)

---

### Post by razeshkale on 2007-06-19
When i tried to restore with Live CD i got this?

With root file give me this?
How can i restore Ubuntu now
its on (hd0,1)

---

### Post by dannyboy79 on 2007-06-19
did you somehow overwrite your Ubuntu partition with your windows install? Where was you ubuntu installed to previously? What you can do is use the live cd and view the folders that contain your ubuntu installation, most likely in /media/ and if they aren't there, you can mount them yourself to any folder that you create anywhere and see if your ubuntu installation is still there. if not, then I am sorry to say but you overwrote it within windows. are you maybe chosing the wrong disk? do you have more than 1 disk?

---

### Post by jan on 2007-07-06
I guess this howto is no more valid for 6.10 and 7.04! Can anyone advise for these two?

---

### Post by dannyboy79 on 2007-07-09
> **jan said:**
> I guess this howto is no more valid for 6.10 and 7.04! Can anyone advise for these two?

if you read a few more posts in, you would see that they is more ways to skin the cat. I am not aware of how fiesty's live cd install works but you can reinstall grub from the live cd BUT WITHOUT doing the install and then quitting. Here's what works with any distribution:

Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.

If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different. Here's are the instructions that I have for my system:

How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps. Since I use Norton Ghost to make regular backups and restores (I do a lot of testing), I do this all the time...

---

### Post by drytear on 2007-07-16
small question: if i reinstall grub, will it still detect my "other" os ? or do i have to do something to tell him that ubuntu is not alone on my pc ?

---

### Post by Absorbed on 2007-07-16
It should detect I think. But don't take my word as gospel.

---

### Post by tomaasj on 2007-07-21
> **dannyboy79 said:**
> if you read a few more posts in, you would see that they is more ways to skin the cat. I am not aware of how fiesty's live cd install works but you can reinstall grub from the live cd BUT WITHOUT doing the install and then quitting. Here's what works with any distribution:

Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.

If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different. Here's are the instructions that I have for my system:

How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps. Since I use Norton Ghost to make regular backups and restores (I do a lot of testing), I do this all the time...


Output of terminal:

> grub> find /boot/grub/stage1

Error 15: File not found

grub> 


Checked the directory though, the file is there.  Where do I go wrong ?

>OK figured it out.  Did not go Superuser.

---

### Post by odin1965 on 2007-08-09
> **jan said:**
> I guess this howto is no more valid for 6.10 and 7.04! Can anyone advise for these two?

I know for 7.04, if you use the alternate install CD, you have the option to "Rescue a broken system". Pick this option and follow the language and keyboard prompts thru to the end. Then after the aoutodetection is thru, pick the partition that has your existing install on it. Then you get several rescue options, one of which is , TA DA, "reinstall GRUB bootloader". Pick where you had your old GRUB, hd0 for MBR (it has some explanatory material here to help you pick), and it's easy peasy from there. When you reboot, you're fixed.

---

### Post by cherry316316 on 2007-08-11
> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)



i dont have the live cd , i just downloaded installation cd , and my installation stop for some errors, now i am not able to boot into my win also , and its giving error "unable to boot operating system" :(

ps: how to open a terminal or tty , when i m using installation cd and i have just put the cd inside and  before starting my installation ??

---

### Post by dannyboy79 on 2007-08-13
> **cherry316316 said:**
> i dont have the live cd , i just downloaded installation cd , and my installation stop for some errors, now i am not able to boot into my win also , and its giving error "unable to boot operating system" :(

ps: how to open a terminal or tty , when i m using installation cd and i have just put the cd inside and  before starting my installation ??

unless you downloaded the "alternate" install cd than every install cd is a live cd. meaning you boot  it up, it gives you a menu, you click on the first choice which is to run in live cd mode or install it. When you pick the first choice you will be presented with a normal  looking desktop of ubuntu, there will be a icon on the desktop that says "Install" but just don't click on that yet. THen follow the instructions.

Otherwise the Super Grub Disk (SGD) can be downloaded and burned to a cd, then boot to that and it can get you into your Win install very easily.

---

### Post by lukon on 2007-08-17
Will restoring GRUB make it work consistently?

See, my dual boot computer boots up fine sometimes, but often hangs at the GRUB prompt. So GRUB works intermittently. So what I want to know is: will restoring grub according to the advice in this thread likely fix it?

And, since I can occasionally boot into Ubuntu, what commands do I use to restore GRUB from a normally booted session? Are these commands any different from those used from a live CD?

---

### Post by dannyboy79 on 2007-08-17
if you can boot into grub one time and then the next you can't, reinstalling grub will not solve this issue as it's not with grub. there's some other underlying issue with your current setup. what  is the error? when you say grub hangs, where does it hang? it only hangs when trying to boot to ubuntu but not windows? do you have a multiple drive setup or just 1 hard drive which both os's on it? these are some of the questions that need to be answered. but no matter what you have to think about it, if grub works one time, then it doesn't the next, then it does the next, than that means that all of grubs files are there and it's loading so i don't think the issue is with grub.

---

### Post by lukon on 2007-08-17
It hangs in GRUB at the GRUB prompt.

The computer is Windows98se on HD0 and Ubuntu Dapper Drake on HD1 with GRUB in the MBR on HD0.

---

### Post by petoro on 2007-08-29
> **dannyboy79 said:**
> if you can boot into grub one time and then the next you can't, reinstalling grub will not solve this issue as it's not with grub. there's some other underlying issue with your current setup. what  is the error? when you say grub hangs, where does it hang? it only hangs when trying to boot to ubuntu but not windows? do you have a multiple drive setup or just 1 hard drive which both os's on it? these are some of the questions that need to be answered. but no matter what you have to think about it, if grub works one time, then it doesn't the next, then it does the next, than that means that all of grubs files are there and it's loading so i don't think the issue is with grub.

I've restored the grub following the guide by dannyboy79, but without success.

My grub also works some of the times that I start the computer.

I have Tribe 5 and Vista Ultimate.  (Also the Vista Bios emulator Loader 2.2.0 installed for experimental purposes.)

But I think I have found a pattern and now I know when Grub is going to fail:

If the last system I run was Ubuntu then grub works fine in the next boot.

If the last system I run was Vista then grub fails in the next boot, and I have to switch off the computer or restart with the power button.

(In this last case, grub works fine again.)

So, it is a run of the Vista operating system what makes grub fail in the next boot, and grub "magically" works again in the following boot.


Any hint to solve the grub fail after a Vista run?


Petoro

---

### Post by dannyboy79 on 2007-08-30
> **petoro said:**
> I've restored the grub following the guide by dannyboy79, but without success.

My grub also works some of the times that I start the computer.

I have Tribe 5 and Vista Ultimate.  (Also the Vista Bios emulator Loader 2.2.0 installed for experimental purposes.)

But I think I have found a pattern and now I know when Grub is going to fail:

If the last system I run was Ubuntu then grub works fine in the next boot.

If the last system I run was Vista then grub fails in the next boot, and I have to switch off the computer or restart with the power button.

(In this last case, grub works fine again.)

So, it is a run of the Vista operating system what makes grub fail in the next boot, and grub "magically" works again in the following boot.


Any hint to solve the grub fail after a Vista run?


Petoro
here's a very similar problem and solution to yours. check it out
[http://ubuntuforums.org/showthread.php?t=391194&page=3](http://ubuntuforums.org/showthread.php?t=391194&page=3)

---

### Post by petoro on 2007-09-01
> **dannyboy79 said:**
> here's a very similar problem and solution to yours. check it out
[http://ubuntuforums.org/showthread.php?t=391194&page=3](http://ubuntuforums.org/showthread.php?t=391194&page=3)

I'm not sure that I can find there a solution for my problem. I only have a  hard disk with three partitions.

Anyway:

I've found that the grub error only happens after having closed Vista properly.

I've had the opportunity to see this after a Vista crash.  I've had to close Vista by turning the computer off and then on again.  And grub behaved well this time.

So, it is something that Vista makes at closing time what makes grub fail in the next boot.


Petoro

> **petoro said:**
> 
So, it is something that Vista makes at closing time what makes grub fail in the next boot.
Petoro

And it is something that grubs makes when it fails at the beginning what "magically" restores the proper grub functionallity again.

Very estrange.  Any clue to mend this?


Petoro

Well, I have found a solution at last.

I was tweaking the settings on Turbo Memory (or Robson Memory or whatever it's called).

I did two things at once (not sure which of them got the problem solved):

1. I disabled the AHCI setting in the BIOS of the computer.
2. I actualized the Intel controller for Turbo Memory.

I activated AHCI again and the problem kept solved. The Grub has never failed again.

And thumbs down for the Turbo Memory technology, I've had to painfully turn off and then on the computer scores of times to get it functioning. In spite of that, I haven't noticed any improvement with it.


Petoro

---

### Post by erusfatum on 2007-09-10
hey guys, i have some problems and cant figure out whats wrong :confused: i had problems with windows xp, and had to reinstall them. 
then i did as it was said, boot from the ubuntu cd, sudo grub, find /boot/grub/stage1, it gave me hd0.2 and hd1.5, so i did root (hd0.2), setup (hd0) and quit, restar but nothing, boots in to xp directly so i did it again but with root (hd1.5) but still the same, boots directly to xp :confused: how can this be solved? ive got 2 hds, one  with 2 windows partitions, and ubuntu, and the other drive (i took it out from another pc to backup before installing windows again) with one partition ext3 for backup stuff, and fedora
thanks in advice

Edit: silly me, when i did root (hd1.5) i had to do setup (hd1) now every thing works fine

---

### Post by mahasmb on 2007-09-11
> **vnbuddy2002 said:**
> Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.


I'm a little confused with this. Are you saying that we should boot with the CD and then click on "Install" ?? But the fact that we don't format any partitions means nothing but GRUB will be changed/installed?

Edit: And would it make a difference if I have Feisty installed, but use a Dapper Drake CD??

---

### Post by Czar on 2007-09-15
With the Feisty CD, this 'trick' doesn't seem to work.  Feisty fights with you until you format something, else it never allows you to finish.

---

### Post by carlosponti on 2007-10-01
What about a dual boot system with windows xp on partition and Ubuntu on the other? will installing grub the way described repair the loader to xp and Ubuntu or will it only work for a straight Ubuntu system.

---

### Post by flarkit on 2007-10-02
> **Czar said:**
> With the Feisty CD, this 'trick' doesn't seem to work.  Feisty fights with you until you format something, else it never allows you to finish.

Oh dear, this is worrying.

I have a 160Gb disk with 3 partitions, for XP (OS + Apps + Data). I added a 250Gb with 5 partitions (XP-pagefile + Linux swap + / + /home + Shared-data)

Now Grub has cleverly gone and installed itself on the 160Gb, instead of the 250Gb. I suppose this is due to the BIOS pointing to the 160Gb as the boot disk. I'd hoped to leave the 160Gb untouched by the Linux install, so I plan to use the XP CD to **fixmbr** and **fixmbr**, to return the XP mbr. Now, I'd hoped to be able to switch the BIOS's boot-disk setting and reinstall Grub to the 250Gb's MBR.

Is it still possible to boot from the Feisty LiveCD, then install Grub, following the suggestions in the thread ["How to install Grub from a live Ubuntu cd"](http://ubuntuforums.org/showthread.php?t=224351)?
:confused:

**edit:**
Definitely some confusion here. If I set the 250Gb as the boot-disk, then Grub has no idea where anything is. Booting into the LiveCD and running "find /boot/grub/stage1", finds the same details as already stated, even though the partitions are quite different. I'll have to delve a little deeper, so that I can correctly dual-boot, without having Grub installed on my XP disk's MBR

---

### Post by flarkit on 2007-10-03
My problem was solved as follows:

[LIST=1]
[*]Swap SATA cables, so my 250Gb (with Feisty) is the 1st drive
[*]Then, make that the boot-up disk (obviously, since I want Grub on there)
[*]Then I booted with the LiveCD and followed the instructions to setup Grub (from [How to Install Grub...](http://ubuntuforums.org/showthread.php?t=224351))
[*]I edited the menu.lst file, to ensure that Feisty is booted from 'hd0' and Feisty from 'hd1'
[/LIST]

All works happily!
:)

---

### Post by CRJeepin on 2007-10-19
Wow, read all this and it didn't address the problem I'm having, and some others on this thread had.  

Scenario:
-installed Ubuntu on secondary, 80 gb ATA HD
-Windows XP already existed on primary, 250 gb SATA HD

When I rebooted after install, it just went right into XP because GRUB installed onto the MBR of the secondary, 80 gb drive which did not have boot priority in my BIOS.

SOLUTION:  Switched my BIOS around to make the secondary drive have boot priority.  Now GRUB loads up, asks me if I want to run Ubuntu or Windows XP.  Yep, GRUB is smarter than XP.

Grub:1  XP:0

---

### Post by sutte on 2007-10-20
I am experiencing this problem, with only one partition on my laptop... I find I HAVE to format someting in order to proceed, so I tried resizing my partition and the formatter crashed... Even reinstalling Grub will not work. Ubuntu 7.10

---

### Post by rwheindl on 2007-11-19
I just tried the technique with the install CD for Ubuntu Studio 7.10 and it worked great! It even detected my Fedora 8 partition! WHOO HOO!!! There were a few extra "no" commands because it kept trying to go back to the BASE INSTALL, but the bootloader reinstalled anyway. Thanks for this great post!

---

### Post by danezeq on 2007-11-20
> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)


How can i tell if i need to type "root (hd0,6)" hd0,5 hd 0,4 or whatever?
i know i have on my main HD two partitions. C: and D:
this "hd0,x" still get me confused :confused:

---

### Post by Absorbed on 2007-11-20
> **danezeq said:**
> How can i tell if i need to type "root (hd0,6)" hd0,5 hd 0,4 or whatever?

You can type "sudo fdisk -l" (make sure you type it correctly) and that'll list your partitions like displayed before in this thread. You will then know where your linux partition is.

> i know i have on my main HD two partitions. C: and D:
this "hd0,x" still get me confused :confused:

As I understand it, if your linux partition is on /dev/hda or /dev/sda then that means you want root(hd0, blah). If the "a" is a "b" then "hd1", "c" hd2", etc.

If the partition is /dev/hda1, then you need root(hd0,0), /dev/hda2 would be root(hd0,1).

So to summerise:
1 = a = 0
2 = b = 1
3 = c = 2
etc.

Welcome to Computer Science.

---

### Post by danezeq on 2007-11-21
ok i did type on grub console "root (hd0,1) and i got "Error 21: Selected disk does not exist

on the fdisk list - the linux partition showed as /dev/hda2
What's wrong then?

i'm from the DOS generation :(

---

### Post by meierfra on 2007-11-21
>  i did type on grub console "root (hd0,1) and i got "Error 21: Selected disk does not exist

Make sure that you use "sudo grub" and not only "grub" 

Also you can find out  the correct (hdx,y)  via

```
sudo grub
find /boot/grub/stage1 
```

---

### Post by danezeq on 2007-11-21
Yes but when i write sudo he ask for admin password.
what password do i need to write?
rmember: i'm on the live cd. i never set any password. (tried my usual password i set when i installed ubuntu - and it's wrong)

so i just kept on doing the instructions without typing correct password. is that the reason i got the error message?

---

### Post by meierfra on 2007-11-21
> what password do i need to write?
Leave it blank. That is just press "enter".

---

### Post by dravidan on 2007-11-25
Here is my setup
hda0: windows
hda1: linux
hda2: swap

I had to reinstall windows because of obivious windows issues.  After the install I could not boot ubuntu.  I tried a few from this posts but none of them worked for me.  Finaly It worked when I used the following method.

1. Boot live cd of ubuntu (I used xubuntu)
2. Ran Gnome Partition editor
3. Changed the boot flag from windows partition to the linux partition

(I ran those grub root and setup commands to my linux partition before I changed the boot flag so I don't know if those commands had anything to do with it or not)

Hope it helps to some like me.

---

### Post by dolecannery on 2007-12-05
Super Grub Disk worked easily and well to reinstall (restored) GRUB which allowed my abiltiy to have either Ubuntu or Kubuntu session or the boot windows XP. 

I googled for Super Grub Disk, D/L ISO, burned CD, booted from CD and followed the simple guided directions.  It worked easily.

I tried using the live CD and the Grub command but it did not work for me (find /boot/grub/stage1 generated error message).

I tried the mkdir ubuntu method, mount /dev/hdb, chroot ubuntu method and it did not work (got stuck on grub-install /dev/hda step).

Super Grub Disk was elegantly simple and effective.

---

### Post by Nymphadora on 2007-12-07
Thanks for this, I'm gonna try it immediately ^_^

---

### Post by manemannen on 2007-12-12
Hi, I get the Error 22 from grub so as far as I understand it is my MBR that is incorrect. I tried the instructions below but they didn't solve my problem.

When I start with the live CD and check my devices I get the following:

sda (my SATA disk where the linux I want to boot is stored).
hdh (a PATA disk - primary on my 4th controller)
hdg (another PATA disk - secondary on my 4th controller)

Now I would assume that sda1 (containing the /boot) would translate to hd0,0. Is this correct? How do I check this?

If I try in grub:
"grub> find /boot/grub/stage1"
I get 
hd0,0 (sda1?)
hd2,0 (hdg1 - an old linux installation)

So, according to the instructions this would mean:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,0)"
5. Type "setup (hd0)"
6. Quit grub by typing "quit".
7. Reboot.

Won't work :confused: PLEASE - HELP NEEDED.

> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)

---

### Post by Tass on 2007-12-20
OK - I´ve read through this whole thread, tried everything, and I´m still stuck.  I probably have the same situation as several people here.  I´m now sitting my with case open, with a cd rom hang out, just to boot up - quite a mess.

Here´s where I am :

1. Using (and hard-powering off in the middle of) the GParted CD seemed to mess something up.  When booting after that I got the standard ¨DISK BOOT FAILURE.  INSERT....¨.

2.  If I continue to use the GParted CD, and scroll down the main menu and choose ¨Boot MBR on first hard drive¨, Ubuntu boots up fine.  This makes me think that there´s a boot record somewhere, it´s just been redirected somwhere.

3.  When I run Partition Editor from Ubuntu, the first partition (/dev/hda1 - mountpoint /, etx3) from my first drive (hda) is set as bootable.

4. I´ve tried using the sudo grub-install /dev/hda
    I´ve tried using the sudo grub-install /dev/hda1

5. I´ve tried going into sudo grub, running :
        find /boot/grub/stage1
        run (hd0,0)
        setup (hd0,0)
    and also :
        find /boot/grub/stage1
        run (hd0,0)
        setup (hd0)

With no effect - I keep coming up with DISK BOOT FAILURE.  So I´m not too sure what else I can do?

Any ideas would be great.  If you need me to run any diags on my system please let me know.

---

### Post by meierfra on 2007-12-20
The command is "root (hd0,0)" not "run (hd0,0)". So try 


```

sudo grub
root (hd0,0)
setup (hd0)
quit
```



If this did not work, post the output of 

```
sudo fdisk -lu
```

and 

```

cat /boot/grub/menu.lst

```

---

### Post by Tass on 2007-12-22
Hi

Sorry, typo there, I was using root, not run.

But I tried it again, and still no luck.  I have since downloaded SuperGrub, and tried using that, without any success.

I booted into SuberGrub, went through the SuperGrub (With Help).
I went to the first menu option - Gnu\Linux (Grub)
I choose the Fix MBR
It scrolled down, showing the response, and said :
¨SGD has succeeded!¨
I then went through to the next screen, where I choose to reboot the PC.

Phrases above might not be exact, I´m typing from memory, but I did what the Help suggested, and was receiving the successful responses.

Below is what I get from sudo fdisk -lu :

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe7ad9ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   150657569    75328753+  83  Linux
/dev/hda2       150657570   156296384     2819407+   5  Extended
/dev/hda5       150657633   156296384     2819376   82  Linux swap / Solaris

Disk /dev/hdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3efdc6f6

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1              63   781417664   390708801    7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x114cd256

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b786cc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   586067264   293033601    7  HPFS/NTFS


And the response to cat /boot/grub/menu.lst is :

# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e2ff3aca-6216-4599-8c82-9c05941ae402 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e2ff3aca-6216-4599-8c82-9c05941ae402 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e2ff3aca-6216-4599-8c82-9c05941ae402 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e2ff3aca-6216-4599-8c82-9c05941ae402 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e2ff3aca-6216-4599-8c82-9c05941ae402 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

(Not sure how much of this you need - sorry if it´s overkill??)


Thanks very much for your help - let me know if there´s anything else you need.

---

### Post by meierfra on 2007-12-22
I don't see anything wrong. Maybe you are trying to boot from the wrong hard drive. Make sure that the Bios are set to boot from the "ubuntu" drive.

If that did not help: Did you get any error messages after
 " sudo grub; root (hd0,0); setup (hd0)" ?  Try again and after "setup (hd0)" copy  the whole terminal and post it here.

---

### Post by Tass on 2007-12-22
No, it´s all successful.

:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit

---

### Post by meierfra on 2007-12-22
Did you check  the boot order in the bios?

---

### Post by Tass on 2007-12-22
:)  You know, some times I could kick myself.

Thank you very much for you help - it was driving me insane!!

---

### Post by nomorewin on 2008-01-10
> **Rikko said:**
> Hi guys,
The problem I'm having is that Ubuntu installed GRUB onto /hdb1, but my primary partition (as far as my BIOS is concerned) is /sda1
I can run 'grub' and reinstall grub like described by remmelt, but I don't know what the ID of /sda1 is. (hd1,0)? (hd2,1)? What command can I use to get the mapping?
I'm able to boot off the Live CD only at the moment.

Rikko, I think you want to execute the following:

[COLOR="Blue"][I]# sudo grub
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)

grub> quit[/I][/COLOR]


Regards.

---

### Post by shabuntu on 2008-01-11
I have fedora 8. I tried installing Ubuntu by formatting the partition used for fedora. Installation aborted saying grub-install failed and it's fatal error. Then I rebooted my laptop to see only "GRUB" without any menu option like before (fedora and vista). I again installed fedora 8 to restore it. Now I want to install ubuntu. What should I do get avoid this install issue?

---

### Post by BobSongs on 2008-01-18
[FONT=Verdana]> **dolecannery said:**
> Super Grub Disk worked easily and well to reinstall (restored) GRUB which allowed my abiltiy to have either Ubuntu or Kubuntu session or the boot windows XP. 

I googled for Super Grub Disk, D/L ISO, burned CD, booted from CD and followed the simple guided directions.  It worked easily.

I tried using the live CD and the Grub command but it did not work for me (find /boot/grub/stage1 generated error message).

I tried the mkdir ubuntu method, mount /dev/hdb, chroot ubuntu method and it did not work (got stuck on grub-install /dev/hda step).

Super Grub Disk was elegantly simple and effective.
I'm going to give [COLOR=DimGray]**Super Grub Disk**[/COLOR] a try.

[/FONT][FONT=Verdana][COLOR=Red]**VNBuddy2002 - FYI:**[/COLOR] The **Ubuntu Feisty Fawn 7.04 Live CD** and **Alternative** setup CDs do **not **comply with this tutorial. The Breezy Badger CD did the very thing you describe but Feisty does not.[/FONT]
[FONT=Verdana] 
I have some of suggestions:[/FONT][LIST=1]
[*][FONT=Verdana]Please keep your tutorial updated and accurate.
[/FONT]
[*][FONT=Verdana]Ensure this technique works with the various active Ubuntu versions (such as Gutsy, Feisty, Edgy and Dapper). This gives us an accurate picture. It avoids [COLOR=Purple]1)[/COLOR] the unnecessary slogging through 17-odd pages of questions and answers to tease out a solution; [COLOR=Purple]2) [/COLOR]ending up in a state where the user is unprepared to handle a crisis. (I have a 2nd PC so it's not urgent for me. But not everyone has this luxury.)
[/FONT]
[*][FONT=Verdana]Include links to useful utilities in your main post such as the **Super Grub Disk** mentioned in the text above. This appears to be (though not yet tested, it soon will be) an excellent way to get folks out of a bind if they don't have a setup CD that works with your described message. And for many Ubuntu users: a messed-up GrUB is a fairly serious problem.[/FONT]
[*][FONT=Verdana]If you'd rather not maintain this tutorial delegate it to someone else. I'm sure someone would be glad to put something together that's accurate and up-to-date.
[/FONT][/LIST][FONT=Verdana]I do thank you for the effort. But I must admit: my appreciation could be much higher. Forgive the obvious frustration, but the subject matter you've written about is very important. The lack of accuracy could be dealt with.
[/FONT]

---

### Post by BobSongs on 2008-01-20
[FONT="Verdana"]Well. **[Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")** worked just fine.

I used the [floppy disk .img file]("http://forjamari.linex.org/frs/download.php/844/super_grub_disk_english_floppy_0.9677.img"), but there's also a [CD-ROM ISO]("http://forjamari.linex.org/frs/download.php/832/supergrubdisk_0.9677.iso").

First I formatted the diskette. Then I used the **dd** command to move it to the diskette. Then I booted to the fd0 (diskette) drive.

When the menu came up I selected choice #2.

Within seconds my Grub boot menu appeared in color. Nice. Not how I remember it, but nice none-the-less.

I selected Ubuntu as a boot choice, shut down and removed the diskette. When I restarted Grub was completely restored and normal.

Thanks again, dolecannery, for the tip.[/FONT]

---

### Post by KingdomKid on 2008-02-12
Hey guys, I recently cloned my hard drive with Acronis. Every thing worked ok except that I can not boot into windows anymore on the new cloned drive. I have a dual boot system (Kubuntu / Windows XP Pro).
I can boot into Kubuntu fine and all is well. Just booting into XP is messed up.

When I choose to boot into XP it just sits there with "starting up" in the top left of the screen.

I was wondering if doing the steps at the beginning of this post is what I need to do?

Does anyone know what got messed up during the cloning process and how to fix it so I can get back into my XP side?

---

### Post by StGeorge on 2008-02-13
The more I read about grub the more my head gets messed up.
Why on earth does grub automatically install to the MBR?
I have not been able to fix  grub for 6 months now.
I have been here and there trying out Super Grub Disk, XUbuntu Restore, Live CD to mention just a few.
If it wasn't for PQ Boot Magic rescue disk my windows system would be unreachable.
Grub is a messy boot loader.
I have a simple problem but no one seems to have any idea how to solve it.
My 98se is on a dedidated 10gb drive. C
My Ubuntu is on the first section of a second HD
It is called hdb1.
So why will grub not install itself there?
I was going to enclose a copy of my Menu.lst.
I have just found out that EXPLORE2FS.EXE does not work now either.
Anyway just a vein hope someone will know what to do.

---

### Post by StGeorge on 2008-02-14
Oh well I deciced to re install instead.
That is another suprising thing.
I did have 6.06 installed.
Decided to re install with 7.10.
It would not keep any files or settings.
None of the previous programs either.
I had to format the old installation prior to re installation.
Luckily I had used [[COLOR="Red"]Explore2fs[/COLOR]]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs-old.htm#Download") to get any files or folders I wanted transfered to windows.

Right at the end of installation there is an advanced button.
On clicking it it gave me the option where to install grub.
I chose (hd1,1) on the second occassion.
So at long last I have grub installed where I want it.
[COLOR="YellowGreen"][COLOR="Sienna"]Personally I think that anyone not having much experience with Linux having trouble with grub should simply re install the OS.[/COLOR][/COLOR] 
I must have spent about 5 to 10 working days trying to fix grub over 6 months. Re installation, 2 hours. 
(I had to re install twice as my Ubuntu drive is called sdb1 or hd1,1. Why name a drive twice?).
I am all for a learning curve but a learning circle messes up my head.

---

### Post by rare HERO on 2008-02-23
> **vnbuddy2002 said:**
> Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

Doesn't work.
after step 5 i get this:
> The file system on /dev/hdb1 assigned to / has not been marked for formatting. File systems used by the system (/, /boot, /usr, /var) must be reformatted for use by this installer. Other file systems (/home, /media/*, /usr/local, etc.) may be used without reformatting. Won't allow me to continue.

---

### Post by rare HERO on 2008-02-23
> **Tomy said:**
> From the grub prompt trying using the <tab> key to see what choices you have.

grub> root (<tab>

Tomy

I get this:
> grub> root 
Error 1: Filename must be either an absolute pathname or blocklist

---

### Post by ultrageeky on 2008-03-11
Phew, this is a long thread...

Haven't read the lot so someone else may have pointed out some of this.

Have a look at 

[http://linuxmint.com/wiki/index.php/How_to_repair_your_grub](http://linuxmint.com/wiki/index.php/How_to_repair_your_grub)

Try supergrub it may help
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

The next alternative to a complete re-installation is the Ultimate Boot CD (UBCD).  There's both a Linux version and a Windows version.  Both can be useful if only to allow access to files.  [http://www.ultimatebootcd.com/download.html]("http://www.ultimatebootcd.com/download.html")

The last thing I would try is to install on another partition, sometimes this will fix the issues, and at least, will give access (possible access) to files on the system.

I've done all the above in the past.  When using SuperGrub, when you edit the "root" drive pointer details remember that you can alter the drive numbering more than once i.e if you change it and it doesn't work, change it again until you find the right drive details.  Try hd0,0 or hd0,1 or hd0,2 or hd1,0 or hd1,1 or hd1,2 and so forth.

If I've helped, drop me a thank you because I often post my solutions to problems I've had; and without feedback, I don't know how well I've helped others.  No feedback, no more help.

As a side note, set aside a separate drive (not partition) for all personal documents.  I used to do this in Windows and I've taken this to Linux too.  Remember that the "home" directory is only small (few GB) and is designed to make it easy for us to back-up our personal settings.  Just copy and paste it somewhere safe (like a DVD) and when you need to back-up your system, copy and paste it back!

Regards,
UltraGeeky

---

### Post by mikh on 2008-04-16
> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)

Hi,

I've reinstalled a WinXP and naturally my grub doesn't work anymore.
I've applied this method to restore the grub, with the following specific parameters:

1. livecd
2. terminal
3. ```
sudo grub
```
In the grub terminal:
4. ```
find /boot/grub/stage1
```
It returned ```
(hd0,5)
```
5. ```
root (hd0,5)
```
6. ```
setup (hd0)
```

At this point, the grub terminal displays this:

```
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested
```

Any help will be much appreciated!

---

### Post by joris1977 on 2008-04-21
Maybe i did something wrong, but i tried to reinstall grub with the hardy live cd as advised in this howto and ruined my install.

 I did chose not to format in the partitioner, but it started installing without formating in my root partition and screwed up my install. It was a fresh install so there was no data loss, but it still sucks to do another install. 

I am afraid this howto is outdated :(

---

### Post by ubromtoo on 2008-04-27
Try Super Grub Disk . I used the 0.9588 version just yesterday and

it worked very easily and quickly .

---

### Post by ubestim on 2008-04-30
I load the 8.04 desktop iso image from my hard disk 
It is just another install process,
I don't know how to get to the desktop.

I have 2 alternatives:
one is Install the grub4dos on windows and then copy the entry of loading
Unbuntu and then paste in the menu.lst file in your windows system drive
The other one is :
when booting ,choose the grub entry
and then choose the:
find and load linux with menu.lst installed

This way you can load Ubuntu
It works fine for me.

The original menu.lst on your /boot/grub dir may like this:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=c79d0c09-5538-43ac-8a16-b17a2e114809 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=c79d0c09-5538-43ac-8a16-b17a2e114809 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

---

### Post by uuser on 2008-04-30
I apologize if this link was posted earlier - I haven't read through this entire thread. In any case, I struggled with this Grub  problem after resizing my Ubuntu partitions until I found this link:

[http://www.linuxforums.org/forum/ubuntu-help/91017-grub-gone-2.html](http://www.linuxforums.org/forum/ubuntu-help/91017-grub-gone-2.html)

Worked perfectly for me...

---

### Post by VMC on 2008-05-15
> **mikh said:**
> Hi,

I've reinstalled a WinXP and naturally my grub doesn't work anymore.
I've applied this method to restore the grub, with the following specific parameters:

1. livecd
2. terminal
3. ```
sudo grub
```
In the grub terminal:
4. ```
find /boot/grub/stage1
```
It returned ```
(hd0,5)
```
5. ```
root (hd0,5)
```
6. ```
setup (hd0)
```

At this point, the grub terminal displays this:

```
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested
```

Any help will be much appreciated!

I think if root returned root (hd0,5), then setup should be setup (hd6) and not setup (hd0)

---

### Post by Rohen on 2008-05-21
> **VMC said:**
> I think if root returned root (hd0,5), then setup should be setup (hd6) and not setup (hd0)

LOL I have exactly the same problem!!!!!  Anyone knows what's going on here????

---

### Post by mx727 on 2008-07-19
> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)

Thank you.
I accidentally wiped out the MBR, reinstalled Vista and lost GRUB.

I followed remmelt's steps from Damn Small Linux in a pen drive(I didn't have the Ubuntu live cd with me when that happened) and it worked out perfectly. now I have Ubuntu 8.04 running again!

---

### Post by gordonngai on 2008-07-24
I have just updated to ver 20 and Ubuntu does not boot in ver 20 from MBR. It works OK when I boot it from ver 19. How do I fix this problem?

---

### Post by unutbu on 2008-07-24
Boot into ver 19, open a terminal and post the output to
```

sudo fdisk -l
cat /boot/grub/menu.lst
```
Also, can you tell us more detail about what happens when you try to boot ver 20? Do you see a GRUB error?

---

### Post by gordonngai on 2008-07-24
I have followed the instruction but I still have the problem. When I start my computer and select either ver 20 or ver 19, I have the following message:-
Starting up...
[0.000000]ACPI:BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI

In ver 19, I will see "Loading please wait". But in ver 20, nothing happens to the computer.

---

### Post by arpanaut on 2008-07-24
ver .20 is messed up right now, just continue using .19 until a fix comes down in updates.
If it really bothers you uninstall ver .20 kernel grub will re-write itself.
You may want to disable the proposed repositories until this is fixed.

---

### Post by gordonngai on 2008-07-25
Thanks. Can I delete ver 20 ref from the MBR?

---

### Post by geezerone on 2008-07-27
> **arpanaut said:**
> ...You may want to disable the proposed repositories until this is fixed.
  +1 to that.

---

### Post by HuntMike79 on 2008-08-07
> **wernst said:**
> Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.

If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different.  Here's are the instructions that I have for my system:

How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps. Since I use Norton Ghost to make regular backups and restores (I do a lot of testing), I do this all the time...

-Warr
Just tried this, worked fine in hardy. :)

---

### Post by tallpaul66 on 2008-09-09
> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)

I tried both options and neither worked. When I tried the terminal option I typed grub and hit enter. After a minute I had grub> on the screen. When I typed in "root (hd0,1)" and hit enter it said "selected disk does not exist". XP is on the master HD and Ubuntu is on the slave so wouldn't that be discs 0 and 1? Just for kicks I tried (hd1,2) but that did not work either.

I used supergrub which works so so but it keeps defaulting to discs 1 and 2 instead of 0 and 1. At least I can get into Ubuntu now.

---

### Post by unutbu on 2008-09-09
tallpaul66, (hd0,1) means the first drive, second partition. The 0 in (hd0,1) means the first drive, and the 1 in (hd0,1) means the second partition. GRUB starts numbering at 0.
So (hd0,1) is GRUB-talk for /dev/sda2. 

Similarly, (hd1,2) is /dev/sdb3, the second drive, third partition.

Perhaps try Catlett's instructions here: [http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1)

---

### Post by jwferk on 2008-09-09
This has saved me on more than one occasion.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I've used it for both Suse and Ubuntu.

---

### Post by tallpaul66 on 2008-09-09
> **unutbu said:**
> tallpaul66, (hd0,1) means the first drive, second partition. The 0 in (hd0,1) means the first drive, and the 1 in (hd0,1) means the second partition. GRUB starts numbering at 0.
So (hd0,1) is GRUB-talk for /dev/sda2. 

Similarly, (hd1,2) is /dev/sdb3, the second drive, third partition.

Perhaps try Catlett's instructions here: [http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1)

Thanks. The problem has been solved. I used supergrub to create a grub file then used gedit to change the hard disk info. Now I have a grub menu that works with both linux and windows.

---

### Post by rugbert on 2008-09-10
After following [this guide](http://ubuntuforums.org/showthread.php?t=35087) to back up and restore my system, and then running the following commands in the grub menu
> 
find /boot/grub/stage1 (optional)
root (hdX,Y)
setup (hd0)
quit 


I then get Error 15: File not found.

So I hit a key and it brings me to the grub menu (I guess it does rebuild the grub) but any option I choose I get the Error 15. When I choose E to edit an entry the kernel line is listed as follows:

> 
kernel /vmlinuz-26.20-16-server root=UUID=2d58187c-3077-4c41-9a07-10a35ce5b062 ro quiet splash


I dont know enough about the grub but it looks a little funky. I only have one HDD and the entire thing is dedicated to the install. Please help!

---

### Post by caljohnsmith on 2008-09-10
Rugbert, so on start up you get the Grub menu, but when you choose any of the Ubuntu entries it gives the error 15? Please boot your Live CD, open a terminal, and post the output of:
```
sudo fdisk -lu
```
From the above command, also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
That will probably give us enough info to fix your problem.

---

### Post by rugbert on 2008-09-10
Thank you caljohnsmith, here ya go:

```

fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89254f32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   470672369   235336153+  83  Linux
/dev/sda2       470672370   488392064     8859847+   5  Extended
/dev/sda5       470672433   488392064     8859816   82  Linux swap / Solaris

```

Mounting sda1
```

root@ubuntu:/home/ubuntu# cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2d58187c-3077-4c41-9a07-10a35ce5b062 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-server
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-server root=UUID=2d58187c-3077-4c41-9a07-10a35ce5b062 ro quiet splash
initrd		/initrd.img-2.6.20-16-server
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-server root=UUID=2d58187c-3077-4c41-9a07-10a35ce5b062 ro single
initrd		/initrd.img-2.6.20-16-server

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=2d58187c-3077-4c41-9a07-10a35ce5b062 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=2d58187c-3077-4c41-9a07-10a35ce5b062 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

huh so yea, that kenel line needs to be pointing to the partition that holds the kernel im guessing? and instead its looking at what, a symbolic link?

---

### Post by caljohnsmith on 2008-09-10
OK, while you still have your Ubuntu partition mounted, do:
```
gksudo gedit /mnt/boot/grub/menu.lst &
```
And change the following:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		[COLOR="Red"]10[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#[/COLOR]hiddenmenu
```
So give it a longer timeout, and comment-out the hiddenmenu. Next do:
```
sudo blkid
ls -l /mnt
ls -l /mnt/boot
```
So do you get the Grub menu on start up? Or do you get the error 15 before you get the Grub menu?

---

### Post by rugbert on 2008-09-10
> **caljohnsmith said:**
> OK, while you still have your Ubuntu partition mounted, do:
```
gksudo gedit /mnt/boot/grub/menu.lst &
```
And change the following:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		[COLOR="Red"]10[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#[/COLOR]hiddenmenu
```
So give it a longer timeout, and comment-out the hiddenmenu. Next do:
```
sudo blkid
ls -l /mnt
ls -l /mnt/boot
```
So do you get the Grub menu on start up? Or do you get the error 15 before you get the Grub menu?

I get the grub yes, but any entry I choose give me the error 15.

Im assuming I should edit the entries accordingly?

---

### Post by caljohnsmith on 2008-09-10
> **rugbert said:**
> I get the grub yes, but any entry I choose give me the error 15.

Im assuming I should edit the entries accordingly?
Yes, you will need to edit your Ubuntu entries in menu.lst, and if you can do it on your own, that's great. If you need help with it, then please post the output of those other commands I gave while your Ubuntu partition is still mounted on /mnt.

---

### Post by rugbert on 2008-09-11
> **caljohnsmith said:**
> Yes, you will need to edit your Ubuntu entries in menu.lst, and if you can do it on your own, that's great. If you need help with it, then please post the output of those other commands I gave while your Ubuntu partition is still mounted on /mnt.

Ok, so when I got in the grub menu and went to edit the entry I made it this
```

root (hd0,0)
kernel /vmlinuz-2.6.20-16-server root=UUID=6e69ca5e-3407-4afd-835d-2e1b7c019cb7
initrd /initrd.img-2.6.20-16-server
quiet
saveddefault

```

buuut I still get the Error 15. But I just noticed that even after I make changes, if I hit ESC to go back to the grub and then edit the entry again the changes werent saved. How do I save them?

---

### Post by unutbu on 2008-09-11
Perhaps try this:

Boot from LiveCD
```
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/boot/grub/menu.lst
```

Go down about 2/3 of the way through the menu.lst file.
Edit the first boot stanza:

```
root (hd0,0)
kernel [COLOR="Red"]/boot[/COLOR]/vmlinuz-2.6.20-16-server root=UUID=6e69ca5e-3407-4afd-835d-2e1b7c019cb7 [COLOR="Red"]ro quiet splash[/COLOR]
initrd [COLOR="Red"]/boot[/COLOR]/initrd.img-2.6.20-16-server
quiet
saveddefault

```
Save, exit, reboot.

---

### Post by caljohnsmith on 2008-09-11
> **rugbert said:**
> Ok, so when I got in the grub menu and went to edit the entry I made it this
```

root (hd0,0)
kernel /vmlinuz-2.6.20-16-server root=UUID=6e69ca5e-3407-4afd-835d-2e1b7c019cb7
initrd /initrd.img-2.6.20-16-server
quiet
saveddefault

```

buuut I still get the Error 15. But I just noticed that even after I make changes, if I hit ESC to go back to the grub and then edit the entry again the changes werent saved. How do I save them?
When you edit the Grub menu on start up by pressing "e", the changes are only temporary and not saved once you boot an OS or restart. You have to modify your menu.lst to make the changes permanent.

---

### Post by rugbert on 2008-09-11
> **unutbu said:**
> Perhaps try this:

Boot from LiveCD
```
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/boot/grub/menu.lst
```

Go down about 2/3 of the way through the menu.lst file.
Edit the first boot stanza:

```
root (hd0,0)
kernel [COLOR="Red"]/boot[/COLOR]/vmlinuz-2.6.20-16-server root=UUID=6e69ca5e-3407-4afd-835d-2e1b7c019cb7 [COLOR="Red"]ro quiet splash[/COLOR]
initrd [COLOR="Red"]/boot[/COLOR]/initrd.img-2.6.20-16-server
quiet
saveddefault

```
Save, exit, reboot.

THAT WORKED! THANKS!


So basically, the grub was referring to a block location on the previous HDD that no longer exists, so blkid finds the correct block on the current HDD? Just so I understand how it works. this is going to help me out SO MUCH in couple of weeks.

---

### Post by unutbu on 2008-09-11
rugbert, I'm glad it worked.

The "root (hd0,0)" grub command tells GRUB to mount /dev/sda1 and look for files there.

The command 
```
kernel /boot/vmlinuz-2.6.20-16-server root=UUID=6e69ca5e-3407-4afd-835d-2e1b7c019cb7 ro quiet splash
```

tells GRUB to look inside the filesystem on /dev/sda1 for a file whose path is /boot/vmlinuz-2.6.20-16-server. You were getting Error 15 (File not found) because vmlinuz-2.6.20-16-server is inside the /boot directory.

The next part I'm a bit shady about, but I'll tell you what I think is true. I'd appreciate it if anyone can confirm this or correct me:

The kernel needs other files to complete the boot. Some of those files might live in /etc for example. The "root=UUID=6e69ca5e-3407-4afd-835d-2e1b7c019cb7" tells the kernel to look for these other files on the partition whose UUID is "6e69ca5e-3407-4afd-835d-2e1b7c019cb7". You can find the UUID by running "blkid".

The "ro quiet splash" are kernel boot options sent to vmlinuz-2.6.20-16-server.
ro means "Mount root device read-only on boot". I find this a little strange, since the root filesystem is not read-only by the time the boot completes. I guess it is remounted later, but I'm unsure.
quiet means "Disable most log messages"
splash means display the orange progress bar instead of text messages

---

### Post by Rhyader on 2008-09-11
Quote: <<<
 Re: HOWTO: Restore GRUB (if your MBR is messed up)
at step 10, I encountered a problem: it asks you if you want to proceed when you click the Install Grub, and in all the previous steps, "yes" or "continue" was the correct response, at step 10, if you select "yes" the ubuntu disk will proceed and attempt to install ubuntu.... which will ruined my current install... ah well....
>>>

I feel for you.  8)  
I did soemthing quite similar myself. I selected "yes" and it said 
"installing base system". I thought - but this will wipe out my current 
installation - and with panic I hit the reset button. So far it seems to be OK,
I am running (the previously installed) Ubuntu as I type and nothing *seems*
to have changed. I guess it was still "reading" the CD and didn't have time 
to start writing yet. But in general the install CD tries to force you to
install. I'd rather avoid that and use the other methods people contributed
here. I'll have to download a "live" CD. Then after I have it, translate the
following for my computer...

Quote: <<<
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.
>>>

In my case, Windows is on the first drive on channel 1 and Ubuntu is on
partition 3 of the first drive on channel 2. Linux calls these /dev/hda 
with windows at /dev/hda1, and /dev/hdc with Ubuntu at /dev/hdc3. 
So, translating the above, what should I type?
"root (hd2,2)"  { assumming that /dev/hda hd0 and /dev/hdc is hd2 }
"setup (hd0)"   { to install in the MBR is the first drive /dev/hda }
Did I get this right?
I know this will install grub in the MBR of my first drive: this is what 
I want to do. (If you don't want to do that, you should do something else).

---

### Post by kushykush on 2008-09-19
These answers tell what is so basically wrong with Linux Pundits. How do we open a terminal? What do I do if I do not have a live CD?  What is tty?

Plus what about a two or more disk scenario? How about if you have Vista installed?  Here is my scenario:

The first PATA Harddisk (0) has three partitions. Ubuntu is installed in the third partition.

The second is a larger and newer SATA hard disk (1) which already has Vista installed in its partition one.  

In my BIOS I have designated my larger SATA disk (1) as the boot disk.

When I installed Ubuntu on the older and my first PATA hardrive, Ubuntu correctly installed GRUB on the PATA Disk (0). I changed my BIOS settings and designated the PATA Disk (0) as my first boot hard drive. GRUB came up and I was able to start Ubuntu and later "Windows longhorn" as well.

But the next day something happened and GRUB did not come up.  I used the Ubuntu in rescue mode and got my Ubuntu installation back.

Question and Problem: Where (and How) should I install GRUB?

P.S: Both, my Vista and Ubuntu (Intrepid beta), are properly installed and work fine when I do a manual boot through the SUPER GRUB DISK.  However, SuperGrub fails to install GRUB. The GRUB menu still comes up but gives a disk error when I attempt to start Intrepid.  However, when I use the same GRUB to start "windows longhorn" Vista boots fine.

---

### Post by caljohnsmith on 2008-09-19
Kushykush, since you can boot Ubuntu from Super Grub, go ahead and do that, and once you are in Ubuntu, open a terminal (Applications > Accessories > Terminal), and post the output of the following:
```
sudo fdisk -lu
cat /boot/grub/menu.lst

```
Also, I assume you want to keep Grub installed to your PATA Ubuntu drive, and not your SATA drive, is that right? In other words, do you want to keep the PATA drive first in the boot order, and have it load Grub on start up?

---

### Post by kushykush on 2008-09-19
I have no preference as to which hard drive the system boots from. Note that grub menu.lst rightly shows a Vista installation on Sda1 (hd0,0). However, this is an old Vista installation that does not work and Windows is not using it. I am using the new Vista installation on Sdb1 (hd1,0). This is currently the system boot.
Here is an ancilliary problem. When for some reason, my GRUB got messed up, I installed GRUB on the Ubuntu-Intrepid partition (/dev/Sda5). This GRUB installation works manually through SuperGrub disk, and Ubuntu-Intrepid starts. However, Intrepid had installed GRUB on the MBR of VISTA (/dev/Sdb1). It is this GRUB which does not work. GRUB menu comes up but it fails to connect with Ubuntu-Intrepid installationn on /dev/sda5). Will this be a problem? I mean should the GRUB installed inside Intrepid on /dev/sda5 pose a problem when GRUB is finally installed on /dev/sdb1 ? (I do not know how to install GRUB there and if that is where it should be installed.
Here is the output from fdisk -lu and cat /boot:
 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc518c518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    65239964    32619951    7  HPFS/NTFS
/dev/sda2        65241088   137517055    36137984    7  HPFS/NTFS
/dev/sda4       137532465   312576704    87522120    5  Extended
/dev/sda5       219447963   308672909    44612473+  83  Linux
/dev/sda6       308672973   312576704     1951866   82  Linux swap / Solaris
/dev/sda7       137532591   219367574    40917492   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce66706a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   204802047   102400000    7  HPFS/NTFS
/dev/sdb2       204802048   330860543    63029248    7  HPFS/NTFS
/dev/sdb3       330860544   453740543    61440000    7  HPFS/NTFS
/dev/sdb4       453755925   551415059    48829567+  83  Linux


 cat /boot/grub/menu.lst
default 7
timeout 12

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=38e428ce-aa58-4038-8300-0725b56bc8d2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=38e428ce-aa58-4038-8300-0725b56bc8d2 ro quiet splash
initrd /boot/initrd.img-2.6.27-3-generic

title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=38e428ce-aa58-4038-8300-0725b56bc8d2 ro  single
initrd /boot/initrd.img-2.6.27-3-generic

title Ubuntu intrepid (development branch), kernel Last successful boot
root (hd0,4)
kernel /boot/last-good-boot/vmlinuz root=UUID=38e428ce-aa58-4038-8300-0725b56bc8d2 ro quiet splash  last-good-boot
initrd /boot/last-good-boot/initrd.img

title Ubuntu intrepid (development branch), kernel 2.6.27-2-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-2-generic root=UUID=38e428ce-aa58-4038-8300-0725b56bc8d2 ro quiet splash
initrd /boot/initrd.img-2.6.27-2-generic

title Ubuntu intrepid (development branch), kernel 2.6.27-2-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-2-generic root=UUID=38e428ce-aa58-4038-8300-0725b56bc8d2 ro  single
initrd /boot/initrd.img-2.6.27-2-generic

title Ubuntu intrepid (development branch), memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows Vista/Longhorn (loader)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
savedefault
makeactive

---

### Post by caljohnsmith on 2008-09-19
[QUOTE=kushykush]The first PATA Harddisk (0) has three partitions. Ubuntu is installed in the third partition.[/QUOTE]
OK, you've got me confused then, because according to your fdisk output, you have 6 partitions on your PATA drive (sda), including the extended partition. So is Ubuntu-intrepid on sda5 like you said in your follow-up post? Also what is sda7 and sdb4 (they are also Linux partitions)? And did the menu.lst you posted come from Ubuntu-Intrepid in sda5?

---

### Post by nicolasdiogo on 2008-10-02
hi folks,

just a note that might help some.

if you have partitioned your installation like:

/boot
/
/swap
/home

you should change your command in grub from

find /boot/grub/stage1

to

find /grub/stage1

the reason is that there will be no folder under "/" (root) for boot


just a catch for those that do not know it.


regards,


Nicolas

---

### Post by Vishaldeep on 2009-02-12
i was initially having windows vista.. then i installed xp by ist changing the bios setting and making hard disk to ATA format... i tried many options to install the grub as linux is already installed in a separte partition sda7... following is menu.lst ... please help me out in installing the grub...


# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 8

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f9c966fa-b83b-47d0-be89-9995b5a9d19a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f9c966fa-b83b-47d0-be89-9995b5a9d19a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
uuid f9c966fa-b83b-47d0-be89-9995b5a9d19a
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f9c966fa-b83b-47d0-be89-9995b5a9d19a ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid f9c966fa-b83b-47d0-be89-9995b5a9d19a
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f9c966fa-b83b-47d0-be89-9995b5a9d19a ro single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-10-generic
uuid f9c966fa-b83b-47d0-be89-9995b5a9d19a
kernel /boot/vmlinuz-2.6.27-10-generic root=UUID=f9c966fa-b83b-47d0-be89-9995b5a9d19a ro quiet splash
initrd /boot/initrd.img-2.6.27-10-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid f9c966fa-b83b-47d0-be89-9995b5a9d19a
kernel /boot/vmlinuz-2.6.27-10-generic root=UUID=f9c966fa-b83b-47d0-be89-9995b5a9d19a ro single
initrd /boot/initrd.img-2.6.27-10-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid f9c966fa-b83b-47d0-be89-9995b5a9d19a
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f9c966fa-b83b-47d0-be89-9995b5a9d19a ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid f9c966fa-b83b-47d0-be89-9995b5a9d19a
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f9c966fa-b83b-47d0-be89-9995b5a9d19a ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid f9c966fa-b83b-47d0-be89-9995b5a9d19a
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
chainloader +1

---

### Post by mishelangelo on 2009-02-19
Thanks, Rhyder... the second method in #204 worked for me!

---

### Post by HankB on 2009-03-20
> **nicolasdiogo said:**
> hi folks,

just a note that might help some.

if you have partitioned your installation like:

/boot
/
/swap
/home

you should change your command in grub from

find /boot/grub/stage1

to

find /grub/stage1

the reason is that there will be no folder under "/" (root) for boot


just a catch for those that do not know it.


regards,


Nicolas

Yes! That's huge. 

I have replaced the hard drive in my laptop with a larger one and have been banging my head against the wall trying to get it to boot. That little hint got me past the "file not found" when trying to boot. If anyone is particularly interested, I saved (text) screen dumps of all pertinent information that got me to that point and can post.

Unfortunately, I seem to be not out of the woods yet. During the boot process, the screen just fades to white and the machine locks up.

---

### Post by D3ath on 2009-03-20
For anyone that reads this:
Use this to find Grub!
```
find /boot/grub/stage1
```
Then use the root command:
```
root (hd0,1)
```
Then setup MBR HHD1:
```
setup (hd0)
```
Quit:
```
quit
```

Then reboot. Three Lines works every time. Even with other distros. Just so everyone knows.

---

### Post by HankB on 2009-03-20
> **D3ath said:**
> For anyone that reads this:
Use this to find Grub!
```
find /boot/grub/stage1
```
Then use the root command:
```
root (hd0,1)
```
Then setup MBR HHD1:
```
setup (hd0)
```
Quit:
```
quit
```

Then reboot. Three Lines works every time. Even with other distros. Just so everyone knows.
These three lines did not work for me. As Nicholas pointed out earlier in this thread, if you have a separate /boot partition, you need to use 
```
find /grub/stage1
```since that is where the file is in that partition.

Here's what worked for me on a 8.10 AMD_64 indstall following migration to a new hard drive:

Boot live CD and mount the normal root partition at /mnt and the boot partition at /mnt/boot. This puts them in the same relation to each other as they will be in the running system:
```
root@ubuntu:~# df|grep sda
/dev/sda6             30241928   4594572  24111144  17% /mnt
/dev/sda5              1004024     94044    858976  10% /mnt/boot
root@ubuntu:~# 
```
Execute Grub - (Commands I typed are bolded)
```
root@ubuntu:~# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> **find /grub/menu.lst**
find /grub/menu.lst
 (hd0,4)
 (hd1,4)
grub> **root (hd0,4) ** 	
root (hd0,4)
grub> **setup (hd0)**
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> 
``` (Note that I had my old drive attached via an external USB enclosure and that's where the "(hd1,4)" entry came from.

This left me able to boot. On the first boot the system locked up with a white screen. <ctrl><alt><delete> eventually took me back to the boot menu and when I tried booting Vista (which had always worked) It got to the progress bar stage and remained there for a long time (with the progress bar still active.) After power cycling the machine, It booted Vista normally, so the machine must have gotten into a bad state that a reboot would not clear.

Following this, when I tried to boot Linux, it started and then dumped me into a command shell when 'fsck' was unable to check two drives. That was because the UUIDs for the drives in /etc/fstab did not match the new drive. I obtained the correct UUIDs using 'blkid', edited them into /etc/fstab and am not happily off and running. :D

For reference, here is some other information that may help others who are struggling with this:

Disk partitions:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f80c932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2         3084480   103677839    50296680    7  HPFS/NTFS
/dev/sda3       103677840   124150319    10236240    7  HPFS/NTFS
/dev/sda4       124150320   976768064   426308872+   5  Extended
/dev/sda5       124150383   126190574     1020096   83  Linux
/dev/sda6   *   126190638   187639199    30724281   83  Linux
/dev/sda7       187639263   195639569     4000153+  82  Linux swap / Solaris
/dev/sda8       195639633   976768064   390564216   83  Linux

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7935999     3963968    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$
``` 
Mount points in running system:
```
hbarta@cypress:~$ df|grep sda
/dev/sda6             30241928   4594780  24110936  17% /
/dev/sda5              1004024     94044    858976  10% /boot
/dev/sda8            384435636  45509056 319398372  13% /home
hbarta@cypress:~$
``` 
UUIDs:
```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="5C0CDB8F0CDB6296" LABEL="SERVICEV003" TYPE="ntfs" 
/dev/sda2: UUID="C4F8DDE6F8DDD730" LABEL="SW_Preload" TYPE="ntfs" 
/dev/sda3: UUID="DE62E0C562E0A38D" LABEL="Lenovo" TYPE="ntfs" 
/dev/sda5: UUID="9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2" TYPE="ext3" 
/dev/sda6: UUID="7f69072f-cea2-4ec3-bde9-81dd16744034" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="a8b4289b-34b4-4c92-a7b9-c0bd7f253cff" 
/dev/sda8: UUID="e186fa4e-a98c-49b9-b491-2205628c1f75" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="5C0CDB8F0CDB6296" LABEL="SERVICEV003" TYPE="ntfs" 
/dev/sdb2: UUID="C4F8DDE6F8DDD730" LABEL="SW_Preload" TYPE="ntfs" 
/dev/sdb3: UUID="DE62E0C562E0A38D" LABEL="Lenovo" TYPE="ntfs" 
/dev/sdb5: UUID="bd5c658d-b65c-45ee-8f7f-a36f02cc3a52" TYPE="ext3" 
/dev/sdb6: UUID="417bafd4-d886-4968-856e-bca45bb5445d" TYPE="ext3" 
/dev/sdb7: UUID="9ae3498f-964f-2097-4349-68cb88a66c33" TYPE="swap" 
/dev/sdb8: UUID="996c0b0f-d773-4b50-9497-c2f2ddd13fe3" TYPE="ext3" 
/dev/sdc1: LABEL="KINGSTON" UUID="5C3F-FC72" TYPE="vfat"
``` 
Menu.lst:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-14-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-14-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro  single
initrd		/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-13-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash 
initrd		/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-13-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro  single
initrd		/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-12-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash 
initrd		/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-12-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro  single
initrd		/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-11-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-11-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-10-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-10-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro  single
initrd		/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-7-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.27-7-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Thanks again to all who offered suggestions.

---

### Post by LinuxGuy1234 on 2009-04-25
Notice for people who have problems with the "root" command:

The disk and partition numbers start at 0, like numbers we use in real life. Some people are used to them starting at 1. 

So, you need to convert the device name under Linux to a GRUB device (no difference for SATA devices, all are hd, just get the numbers right):
sda1 -> (hd0,0)
hdb2 -> (hd1,1)
sdc3 -> (hd2,2)

---

### Post by GARoss on 2009-06-03
I really messed something up & need some help.

I have a dual boot Ubuntu/XP PC. Ubuntu is 1st on the GRUB boot list & that HDD is also 1st boot in BIOS.

So, here's what happened. I was given an external HDD that was formatted for Mac. I needed to reformat for NTFS. Somehow I couldn't do this in either Windows or Ubuntu using Gparted. So, I put the XP install disk in & went into it as if I was installing XP. I select the external HDD to format to NTFS. After it finished, it started installing XP. I thought it would pause 1st, so I panicked & hit Esc. Well, it must of erased something in GRUB because after it rebooted all it said after POST was... "A disk read error occurred. Press ctrl+alt+del to restart." Truth is, I'm not sure what happened but it would seem something happened to GRUB.

After rethinking, I changed the HDD boot order in BIOS so the XP drive would be 1st & now, at least, XP does boot.

So, after reading here, I'm not sure what to do. There are many options but as I'm not sure what exactly happened, I'm not sure which approach to take. There must be a way to analyze what changed after I formatted the external HDD & stopped the XP install process. I'm sure it has something to do with eithr GRUB or root but what? 

Please advise,
George

---

### Post by GARoss on 2009-06-03
This worked for me. Up & running!

[I]presence1960 wrote

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.[/I]

---

### Post by mjstelly on 2009-07-31
> **remmelt said:**
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I may be missing your point though, if so, please forgive me :)

Sorry to engage in thread necromancy, but I followed the directions to backup a system then restore it to another system. Well, I backed up just fine. I restored the file and totally hosed the target system. I now get: 

[B]Error 15: File not found.
Press any key to continue...
[/B]
To make matters worse, even though the BIOS settings has the cd drive set to position 1 in the boot priority, it won't boot from the cd. So, I can't even get to the desktop.

When I press a key, a list of boot kernels is displayed. I try to boot from any of them. It just returns me back to the previous screen.

I selected C for command-line, typed 
**grub> find /boot/grub/stage1**, 
I get 
**grub> root (hd0,0)**.

I type 
**grub> setup (hd0,0)**

Geeky goop prints to the screen, but finally says "install grub succeeds". Try typing **quit** but that does nothing. So I reboot, and nothing has changed. ](*,)

I tell everyone, "if you're gonna do something, do it well." And I sure the hell did. The system is completely unusable. (I also say, "if it ain't broke, break it").

I'm stumped on this one. All other directions I find assume that I can boot from the live cd, which I can't. Did I totally screw the pooch on this one? The pc has usb connections, but it's so old, I don't think it can be used to boot from.

Any ideas?

---

### Post by a94060 on 2009-08-11
@mjstelly:I got this error after trying to restore grub many times. After you find the correct entry, I think your problem lies in the UUID. in the grub> prompt, type uuid. Find out the uuid of your boot device.Write this down. Change all of the lines which make a mention of the UUID to the one. I was able to do this by using a live cd, but it doesnt seem like you are able to boot the live cd, so you will have to write it down. After that,just press b to boot, and it should work. Make sure you edit those entries once you get back in =]Also, dont forget to recreate the directories such as /sys and /proc if you are restoring system. You will end up in command line environment. Just restart after creating them and all will be fine. 

Check out HankB's post.

[http://ubuntuforums.org/showthread.php?p=6927610#post6927610](http://ubuntuforums.org/showthread.php?p=6927610#post6927610)

---

### Post by waseempki on 2009-08-26
> **vnbuddy2002 said:**
> Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.
 
Here are the steps:
 
1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions
 
/
/boot
swap
..... 
 
5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer
 
Good luck!.
  I could'nt understand step 4 and step 7.please explain tese step for me
thanks

---

### Post by olecarme on 2009-09-11
I'm amazed of the length of this discussion, and the complexity of all the solutions presented. Here is a good one:
1. Get a Debian netinst installer on [http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)
2. Boot it and choose the special entry for recovering
3. When it offers you various choices, choose to install again Grub (there is a special entry for this)
4. Reboot

That's all! If you already did point 1, the rest should need less than one minute.

---

### Post by ssri on 2009-09-17
PartitionMagic screwed up my MBR after finishing a job formating an external HDD in Windows XP SP3 (never happened before) that lead to GRUB failing at stage 1.5, error 15.  Thankfully I found this thread and I can say that post #2 was a lifesaver.  Although, my boot partition was in /dev/sda6, hence my usage of "root (hd0,5)."

---

### Post by DenysT on 2009-10-31
> **olecarme said:**
> I'm amazed of the length of this discussion, and the complexity of all the solutions presented. Here is a good one:
1. Get a Debian netinst installer on [http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)
2. Boot it and choose the special entry for recovering
3. When it offers you various choices, choose to install again Grub (there is a special entry for this)
4. Reboot

That's all! If you already did point 1, the rest should need less than one minute.

At step 3 it becomes quite confusing. There are several options from there that only the most advanced Linux user understands. Honestly, I got to that point and quit. Your 4 steps are too few for most to know what to do. :( Nothing could be further from the truth than "That's all!"

---

### Post by Mcalhoun on 2009-11-06
> **olecarme said:**
> I'm amazed of the length of this discussion, and the complexity of all the solutions presented. Here is a good one:
1. Get a Debian netinst installer on [http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)
2. Boot it and choose the special entry for recovering
3. When it offers you various choices, choose to install again Grub (there is a special entry for this)
4. Reboot

That's all! If you already did point 1, the rest should need less than one minute.

That one minute thing is a crock, I'm a greenhorn and it took me at least two minutes to do this, after download and burning the disk.  But it worked like a charm after all else had failed time and time again.  Thanks loads olecarme.

---

### Post by crosspicker on 2009-11-10
Just gonna throw my 2 cents in because I reinstalled GRUB.

I have been dual booting XP Pro and Ubuntu for a couple years and never had a problem, did a fresh install of Ubuntu Studio 9.1 and everything ran perfect. Then I decided to install Windows 7, did a fresh install and after couldn't boot into Ubuntu because Windows writes to the MBR, but I knew that would happen. Most of the posts that I read say to boot into the live CD, but unfortunately I downloaded an alternate version which apparently doesn't boot into the live cd. So instead after booting the install cd I choose to "FIX A BROKEN INSTALL", followed the regular install routine until it comes up with a list of options to perform, one of the being to install GRUB. Choose that and the location to install, (hd0,0) and it installs in a matter of seconds, then in the menu choose to reboot.

After rebooting in the GRUB menu my Ubuntu Studio is there but the Windows installation is showing as Windows XP which I can't boot into. I boot into Ubuntu and check the file /boot/grub/grub.cfg and find Windows XP listed in the boot options. Opened Terminal and ran "sudo update-grub" which updated the grub.cfg file and now reads windows 7.

Now everything works perfect. Sorry for the long winded post.

---

### Post by Ramanjit81 on 2009-11-28
posted the same thing twice in error.

---

### Post by Ramanjit81 on 2009-11-28
Hello people. First of all I'd like to thank Olecarne as your post has been the most helpful.

I'm a newbie who installed ubuntu 9.10 on a window vista machine. I resized the vista partition and reduced it's size to make a 20 GB partition for ubuntu. Ubuntu has been great by far but vista hasn't been loading at all even though it is listed under grub.

So, attempting to revive vista as well, I got to the recovery console and tried fixboot and fixmbr. Now none of the OSes are working and I started getting the error NTLDR is missing.

I have managed to reinstall grub as follows: (Olecarne's approach worked for me but I'll insert a few steps to eliminate any possibility of confusion.)

[LIST=1]
[*]Get a ubuntu live cd and boot into ubuntu.
[*]then go to system>administration>Gparted. Please the partion which has the original ubuntu installation. (just newbies, it will more than likely have an ext3 or ext4 file system). Please note this partition as you will need to select this at step 15.
[*]Get a Debian netinst installer on [http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/) (I used the full version and not the businesscard version. Either might work though)
[*]Burn the image to a cd/ usb or floppy as you prefer. (Please ensure that you have downloaded the right file format for your preferred media i.e. cd/ floppy/usb.)
[*]Boot it and then at the the menu list select advanced options and press enter.
[*]choose rescue mode(not graphical rescue mode) and press enter
[*]select language and press enter.
[*]select country and press enter
[*]select keyboard layout and press enter
[*]now the cd will detect hardware and load additional components.
[*]Then it will come to a select the network interface you may want to use. press tab key to get to go back and press enter.
[*]this will give you the debian installer main menu.
[*]go to "enter rescue mode". and press enter.
[*]It will ask you for the device to use as root file system and list the various options i.e. the various hdds and the partitions on them are listed.
[*]select the partition that has the original ubuntu installation on it and press enter.
[*]select "reinstall GRUB boot loader" and press enter.
[*]if you want the GRUB to be loaded to the MBR i.e. Master Boot Record, the enter (hd0) and press TAB to select continue and press enter.
[*]then the enter rescue mode menu comes up again after grub is installed.
[*]go to "Reboot the system" and press enter.
[*]on the computer boot up you should see the grub menu with the list of your installed OS.
[/LIST]
Your GRUB should now work properly. (Mine did.)

---

### Post by z1000000 on 2009-11-29
Here's an even simpler if not very attractive fix, for the real beginners. I'm sure it's been mentioned but I've spent too long already messing about with this problem.

I removed a partition which killed GRUB. I tried the first few pages of this thread trying to get it fixed, but nothing worked. In the end I just loaded a second copy, in the space where I had removed the partition. I know installing from a live CD/USB Stick works, so I just did that alongside my existing stuff.

A crude fix but ever so quick and easy.

---

### Post by _mikec_ on 2009-11-29
> **z1000000 said:**
> Here's an even simpler if not very attractive fix, for the real beginners. I'm sure it's been mentioned but I've spent too long already messing about with this problem.

I removed a partition which killed GRUB. I tried the first few pages of this thread trying to get it fixed, but nothing worked. In the end I just loaded a second copy, in the space where I had removed the partition. I know installing from a live CD/USB Stick works, so I just did that alongside my existing stuff.

A crude fix but ever so quick and easy.

you reinstalled ubuntu alongside with your stuff ? how can that be quick ?...


ubuntu karmic:
make changes to partitions locations below
boot from cd/usb/network/yomomma
open terminal
type:
sudo mkdir /mnt/fixboot
sudo mount -t ext4 /dev/sda5 /mnt/fixboot
sudo mount -t proc non /mnt/fixboot/proc
sudo mount -o bind /dev /mnt/fixboot/dev
sudo chroot /mnt/fixboot /bin/bash
sudo grub-install /dev/sda
sudo update-grub
sudo umount /mnt/fixboot/dev
sudo umount /mnt/fixboot/proc
sudo umount /mnt/fixboot
reboot
:D

---

### Post by nitstorm on 2009-11-29
what do i do if it says the mbr is missing, i have a squeaky clean hdd and it says mbr missing wen i try to install 9.10 on it...

---

### Post by sdowney717 on 2009-11-29
using this you boot live cd and then you can become root of the os and reinstall, update grub.
start wiht number 4 as the others have to do with reinstalling the os.


> [http://ubuntuforums.org/showthread.php?t=1326412&page=7](http://ubuntuforums.org/showthread.php?t=1326412&page=7)

Why not just install legacy grub?

I just did one today like this:

(1) Using the Live CD installer at the last step click on Advanced and choose not to install grub at all!

(2) When installation is done don't choose to restart, rather choose to keep using the Live CD.

(3) Since you just installed you should know the drive/partition # of your Karmic (or Lucid) so keep that in mind. If you have no idea the Boot Info Script should be helpful:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

(4) From the Live Desktop run:

Code:

sudo mount /dev/sdXY /mnt

(of course XY must represent your drive and partition #'s!)

Then:

Code:

sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

You should notice that the command prompt changes from ubuntu@ubuntu$ to # which means you're now root in that OS. I like to be sure I am where I want to be with "cat /etc/issue" and "df -H".

Then revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

And when you're done:

Code:

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt


---

### Post by nitstorm on 2009-11-29
i jus get bootmbr missing, press ctrl+alt+del to restart no matter how much i play with the boot order... so i can hardly get to the live installation part

---

### Post by frank cox on 2009-11-29
Hi:

   I have a Dell duo-core with 2 gb of ram and a 500 gb hd.
I was messing around with the partition copy in Puppy Linux and thought it would just create a file on a partition, instead it locked the partition.

My machine has [had?}  XP on the first partition then Ubuntu on the other three . Ubuntu 9.04 still works but I cannot open XP. Is there any way to fix that?

---

### Post by _mikec_ on 2009-11-30
> **nitstorm said:**
> i jus get bootmbr missing, press ctrl+alt+del to restart no matter how much i play with the boot order... so i can hardly get to the live installation part


Have you tried to fix the MBR using a windows installation cd ? with the fixmbr dos command ? this is only a guess since i never had this problem before and each time i had any problems with the MBR while running Windows XP i've boot the machine into dos and use the "fixmbr" command available.

---

### Post by _mikec_ on 2009-11-30
> **frank cox said:**
> Hi:

   I have a Dell duo-core with 2 gb of ram and a 500 gb hd.
I was messing around with the partition copy in Puppy Linux and thought it would just create a file on a partition, instead it locked the partition.

My machine has [had?}  XP on the first partition then Ubuntu on the other three . Ubuntu 9.04 still works but I cannot open XP. Is there any way to fix that?


maybe try Puppy Linux to unlock it ?, this has nothing to do with Ubuntu, your problem is with Puppy Linux and Windows.

---

### Post by frank cox on 2009-12-01
> **_mikec_ said:**
> maybe try Puppy Linux to unlock it ?, this has nothing to do with Ubuntu, your problem is with Puppy Linux and Windows.
 
Well it does have something to do with Ubuntu, it is the grub that is corrupt and the grub is in Ubuntu.

---

### Post by _mikec_ on 2009-12-01
please post /etc/grub/grub.cfg

---

### Post by perspectoff on 2009-12-13
> **RonKZ said:**
> avoid?  hell, for a newbie prior to actually being booted into whatever distro, commandline is virtually impossible, it's plain wilderness stuff.

These are cut and paste instructions, mate. Perhaps you should join Hare Krishna. They'll take care of you if you've had too many drugs to cut and paste.

---

### Post by margazhang on 2009-12-17
This thread is too long and I cannot go through all posts. So I don't know if someone has already posted the fix.

Anyway, I changed hard drives a few times and that gave me this error:

**error: biosdisk read error**

Inserting a floppy disk into the floppy drive made this error gone upon reboot but I could not boot from the boot menu (if everything works fine this boot menu should not have shown up) as it mis-identifies drives. 

The simplest fix is this...

I booted from the Ubuntu 9.10 live CD and then chose the last item on the list - "Rescue a broken system" to repair the GRUB. It just tried to "Reinstall GRUB boot loader" although it failed to reinstall.

Anyway, after this I could access the boot menu without the liveCD. I then picked to boot in rescue mode and then picked to update grub.

Then I have no problem booting normally! So 9.10 liveCD does repair GRUB when you encounter booting problems. That is great!

Ooops, I have problem rebooting again! Got to look for a fix :-(

Hmmm... I download Super Grub Disk iso file, burn it on a CD and boot from this Super Grub CD. I tried a few things with it and then I can boot again in the rescue mode and fixed the problem. Now I am OK now - Thanks to Super Grub!

---

### Post by Gaga0309 on 2009-12-17
Hi everyone, I think I'm having a similar problem. I need Help!! I had a triple boot (Vista/XP/Ubuntu) prior to 9.10 Update. Now my Vista desktop fails to load (solid blue screen) beyond password prompt since 9.10. My Ubuntu 9.10 & XP boots perfectly fine. XP is on secondary IDE HD. Vista & Ubuntu are on Primary 500GB SATA HD. Boot table appears to be normal. This setup was done by my brother who is now deployed overseas & I am a complete linux noob. Please help someone??  Anyone ??? :(:confused:

---

### Post by margazhang on 2009-12-17
If XP is working fine, why still using Vista? Just boot into Ubuntu and grab all the data you need it - if you install Ubuntu properly, it should be able mount both your XP and Vista partition automatically. This means that you can access both your XP and Vista partition from Ubuntu.

I would not do triple boot again. In my case I run Windows XP inside Ubuntu via VirtualBox.

---

### Post by Pelsia on 2009-12-20
Shortly I'm going to need to reinstall my windows partition, currently its set to dual boot with XP and Ubuntu 9.04; everything is working fine actually.  There's an application I need to install but some registry keys crucial to its functionality are missing.  Restoring the registry from the cd will fix the problem, but pretty much break everything. And there way too many keys to add manually, would take longer than a fresh install takes.  

So.....before I undertake this I'll see if the program works with wine; last time I checked someone managed to get it partially functional which could be enough, in which case I'll ditch XP all together (only reason for dual boot is cuz it's a laptop, otherwise would use removable drives).  When I install XP or Vista I know its going to most likely nuke the mbr.  If I leave the Ubuntu partition alone (not that I had any intentions of changing it) during the windows install process, will fixing the mbr as described on the first page be all I need to do?  Or will I need to tarball Ubuntu up and then restore it later using a bootable disk?

---

### Post by margazhang on 2009-12-28
Pelsia, I highly recommend that you install Windows (or whatever OS) INSIDE Ubuntu via VirtualBox. The advantages of doing this are numerous. One good thing is, you do not have to shut down Ubuntu to boot into Windows just to run a not-so-commonly-used program - you simply start up VirtualBox and boot up Windows inside Ubuntu and do your things. 

You will experience some issues with USB devices. Read my blog for these issues and how to solve them:

[http://gain4you.net/217/run-windows-inside-ubuntu-linux-desktop-os](http://gain4you.net/217/run-windows-inside-ubuntu-linux-desktop-os)

I just documented that for myself - in case I forget it myself :-)

---

### Post by christym on 2010-04-25
Thanks for these great contributions. 

Unfortunately, before stumbling onto this thread I found another one that proved less than reliable. Result: total loss of all my data.

It really is a pretty dumb oversight of developers not to include a "grub restore" option on the boot disk. Especially given the innevitability of having grub wiped by the innevitable windows reload.

Its this kind of oversight that must make users wary of trying to set up dual boot systems.

---

### Post by levis lover on 2010-07-11
Just installed windows vista over **Ubuntu 9.10..**
So there's no GRUB. But the only Live CD i could find is **Ubuntu 8.04 LTS.**
Would that be OK if i install GRUB using this live cd of version 8.04 over 9.10 ?

---

### Post by Sticky_Bit on 2010-07-11
vnbuddy,
This solution worked for me. Thanks! I upgraded from 9.10 this morning and think I made the wrong choice, during the upgrade as to where grub should be installed. Doh!

---

### Post by nitstorm on 2010-07-13
> **levis lover said:**
> Just installed windows vista over **Ubuntu 9.10..**
So there's no GRUB. But the only Live CD i could find is **Ubuntu 8.04 LTS.**
Would that be OK if i install GRUB using this live cd of version 8.04 over 9.10 ?

I don't think it'll work, 8.04 uses the legacy grub whereas 9.10+ use grub2... but i might be wrong, and if i am please do excuse me..

---

### Post by KeithS on 2011-03-06
Sorry for the necro, but this topic needs updating. What's the latest method for restoration of grub with 10.04.2 LTS / Windows XP dual boot. Windows boots, from the start up menu, Ubuntu does not. Solution concisely, please, if at all possible. It is unknown ground for me. Thanks.

EDIT:

Never mind. Fixed it. For info, used the Debian 6.0.0 i386 Live CD, in rescue mode. Works fine.

---

### Post by pritam_par on 2011-08-06
[FONT=Arial][SIZE=2]Here are the few steps in which you can install Grub from CD

1.Boot from the Ubuntu Desktop    

2. In Terminal tpye [COLOR=Black][COLOR=red][COLOR=blue]sudo fdisk -l[/COLOR]   [COLOR=black]. [/COLOR][/COLOR][/COLOR]
*[COLOR=black]    [/COLOR]*[COLOR=red][COLOR=black]It will display all partiton of the disk.[/COLOR][/COLOR]
[/SIZE][/FONT][CENTER] [FONT=Arial][SIZE=2][URL="http://3.bp.blogspot.com/-HRTk2qtrWYg/Tei7c9KYgbI/AAAAAAAAAJE/HTEtCP4CnSw/s1600/Grub+rescue+install.png"]
[/URL][/SIZE][/FONT][/CENTER]
[FONT=Arial][SIZE=2][COLOR=red][COLOR=black][/COLOR][/COLOR]*[COLOR=black][/COLOR]*3. Mount the ubuntu partition drive
                *sudo mount /dev/sdXX /mnt* 

4.Only if you have a separate boot partition: 
[/SIZE][/FONT] [FONT=Arial] [/FONT][FONT=Arial][SIZE=2]            *sudo mount /dev/sdYY /mnt/boot.*[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial]5[/FONT][FONT=Arial][SIZE=2].           Mount the virtual filesystems: 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*            sudo mount --bind /dev  /mnt/dev*
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*            sudo mount --bind /proc /mnt/proc *
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*            sudo mount --bind /sys  /mnt/sys*[/SIZE][/FONT]
[FONT=Arial] [/FONT][FONT=Arial][SIZE=2]
6.          [/SIZE][/FONT][FONT=Arial][SIZE=2]To ensure that only the grub utilities from the LiveCD get executed, mount /usr      
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]  *   sudo mount --bind /usr/ /mnt/usr*
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*     sudo chroot /mnt * 

7. [/SIZE][/FONT][FONT=Arial][SIZE=2]      * update-grub* 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]      or  *update-grub2*[/SIZE][/FONT]  
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]8.Now reinstall Grub 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*         grub-install /dev/sdX*  (eg. grub-install  /dev/sdaDo not specify the partition number.   [/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial] [SIZE=2]9[/SIZE][/FONT][FONT=Arial][SIZE=2]. Verify the install 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]        *sudo grub-install --recheck /dev/sdX*[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT] [FONT=Arial][SIZE=2]10. Exit chroot : *CTRL-D* on keyboard.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]11.          Unmount virtual filesystems: 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*           sudo umount /mnt/dev*
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*           sudo umount /mnt/proc*
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*           sudo umount /mnt/sys* 

[/SIZE][/FONT][FONT=Arial][SIZE=2]12. Unmount the LiveCD's /usr directory:[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*          sudo umount /mnt/usr*

13. Unmount last device:[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*           sudo umount /mnt* [/SIZE][/FONT]   
[FONT=Arial][SIZE=2] [/SIZE][/FONT] 
[FONT=Arial][SIZE=2] 14. Reboot.
*         sudo reboot.*
[/SIZE][/FONT][FONT=Arial] [/FONT]

---

### Post by x-D on 2011-08-06
_**THE METHOD I'M ABOUT TO SHOW YOU CAN BE DONE FROM:**_

. A LIVE DISK/CD/DVD
. A LIVE USB
. ANY OTHER LIVE MEDIA
. AN INSTALLED VERSION OF UBUNTU

The absolute EASIEST WAY, to (re)install GRUB is to use a little program  called Boot-Repair. It does all that work to do with commands in the  Terminal to reinstall GRUB for you, and it's really noob friendly, with a  simple GUI, that you merely have to indicate which OS you want as your  main Operating System etc, IF YOU WANT TO! This is all under advanced  options, but really, it's not so advanced, anyway to get Boot-Repair:[U][B]

Do this in the Terminal:[/B][/U]

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

```Now, run the program (search for it in Unity, or go to: System  ----> Administration ----> Boot Repair, in Gnome 2/ Classic Mode  in 11.04 Natty Narwhal)

Then, once the program is done reinstalling GRUB (should take at max 2 minutes), do this:

```

sudo update-grub

```This is probably not necessary, but it will just eradicate the potential for any errors, whatsoever!

_**Inf****o for this can be found by:**_

a) going to: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
b) messaging me here.

Hope this helped...

x-D :guitar:

---

### Post by wilberfan on 2011-08-06
Forgive me if this has already been mentioned, but Rescatux has saved my GRUBby butt on more than one occassion!

Highly recommended...    [http://www.supergrubdisk.org/rescatux/]("http://www.supergrubdisk.org/rescatux/")

---

### Post by YannBuntu on 2012-01-12
> **x-D said:**
> _**THE METHOD I'M ABOUT TO SHOW YOU CAN BE DONE FROM:**_

. A LIVE DISK/CD/DVD
. A LIVE USB
. ANY OTHER LIVE MEDIA
. AN INSTALLED VERSION OF UBUNTU

The absolute EASIEST WAY, to (re)install GRUB is to use a little program  called Boot-Repair. It does all that work to do with commands in the  Terminal to reinstall GRUB for you, and it's really noob friendly, with a  simple GUI, that you merely have to indicate which OS you want as your  main Operating System etc, IF YOU WANT TO! This is all under advanced  options, but really, it's not so advanced, anyway to get Boot-Repair:[U][B]

Do this in the Terminal:[/B][/U]

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update; sudo apt-get install -y boot-repair

```Now, run the program (search for it in Unity, or go to: System  ----> Administration ----> Boot Repair, in Gnome 2/ Classic Mode  in 11.04 Natty Narwhal)

_**Inf****o for this can be found by:**_

a) going to: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
b) messaging me here.

Hope this helped...

x-D :guitar:

Hello
little update: 
- the package to install is now "boot-repair" (not "boot-repair-ubuntu").
- And i confirm Boot-repair automatically does grub-update, so doing it manually is not necessary.

---

### Post by Trent T on 2012-01-14
Thanks, pritam_par, for your excellent instructions!

Your method worked well when I tried it, except for a small change 
needed in step 9:

You posted,
9. Verify the install 
```
sudo grub-install
``` 

It worked for me when I left out 'sudo'

```
 grub-install
``` 

Thanks again!

Trent T

> **pritam_par said:**
> [FONT=Arial][SIZE=2]Here are the few steps in which you can install Grub from CD

1.Boot from the Ubuntu Desktop    

2. In Terminal tpye [COLOR=Black][COLOR=red][COLOR=blue]sudo fdisk -l[/COLOR]   [COLOR=black]. [/COLOR][/COLOR][/COLOR]
*[COLOR=black]    [/COLOR]*[COLOR=red][COLOR=black]It will display all partiton of the disk.[/COLOR][/COLOR]
[/SIZE][/FONT][CENTER] [FONT=Arial][SIZE=2][URL="http://3.bp.blogspot.com/-HRTk2qtrWYg/Tei7c9KYgbI/AAAAAAAAAJE/HTEtCP4CnSw/s1600/Grub+rescue+install.png"]
[/URL][/SIZE][/FONT][/CENTER]
[FONT=Arial][SIZE=2][COLOR=red][COLOR=black][/COLOR][/COLOR]*[COLOR=black][/COLOR]*3. Mount the ubuntu partition drive
                *sudo mount /dev/sdXX /mnt* 

4.Only if you have a separate boot partition: 
[/SIZE][/FONT] [FONT=Arial] [/FONT][FONT=Arial][SIZE=2]            *sudo mount /dev/sdYY /mnt/boot.*[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial]5[/FONT][FONT=Arial][SIZE=2].           Mount the virtual filesystems: 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*            sudo mount --bind /dev  /mnt/dev*
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*            sudo mount --bind /proc /mnt/proc *
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*            sudo mount --bind /sys  /mnt/sys*[/SIZE][/FONT]
[FONT=Arial] [/FONT][FONT=Arial][SIZE=2]
6.          [/SIZE][/FONT][FONT=Arial][SIZE=2]To ensure that only the grub utilities from the LiveCD get executed, mount /usr      
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]  *   sudo mount --bind /usr/ /mnt/usr*
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*     sudo chroot /mnt * 

7. [/SIZE][/FONT][FONT=Arial][SIZE=2]      * update-grub* 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]      or  *update-grub2*[/SIZE][/FONT]  
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]8.Now reinstall Grub 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*         grub-install /dev/sdX*  (eg. grub-install  /dev/sdaDo not specify the partition number.   [/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial] [SIZE=2]9[/SIZE][/FONT][FONT=Arial][SIZE=2]. Verify the install 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]        *sudo grub-install --recheck /dev/sdX*[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT] [FONT=Arial][SIZE=2]10. Exit chroot : *CTRL-D* on keyboard.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]11.          Unmount virtual filesystems: 
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*           sudo umount /mnt/dev*
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*           sudo umount /mnt/proc*
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*           sudo umount /mnt/sys* 

[/SIZE][/FONT][FONT=Arial][SIZE=2]12. Unmount the LiveCD's /usr directory:[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*          sudo umount /mnt/usr*

13. Unmount last device:[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial] [/FONT][FONT=Arial][SIZE=2]*           sudo umount /mnt* [/SIZE][/FONT]   
[FONT=Arial][SIZE=2] [/SIZE][/FONT] 
[FONT=Arial][SIZE=2] 14. Reboot.
*         sudo reboot.*
[/SIZE][/FONT][FONT=Arial] [/FONT]

---

### Post by divyanshu308 on 2012-01-30
Hi everyone I've got a very bad situation.
I have a Dell inspiron 15r.
It had dual boot windows7 and Ubuntu.
I wanted to make a fresh install of both windows and Ubuntu.
When i booted win 7 DVD i accidentally deleted the Ubuntu swap partition.
Now the laptop doesn't turns on.
it's stuck at the boot screen.
I even removed the hard disk and tried to connect it to my desktop using sata to USB converter but it's not being detected it's spinning even showing an icon as if there is a USB device connected but no partitions showing.
I live booted Ubuntu without the hare disk plugged in and it works fine but obviously since no hard disk is connected there is no place to install.
Even when it's live booted up when i connected the hard disk nothing shows up.
Please help....

See the progress at the page below.
i apologize for repeating my problem but I'm helpless..

 ubuntuforums.org/showthread.php?t=1916953

---

### Post by sheds on 2012-03-27
> **wernst said:**
> Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.

If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different.  Here's are the instructions that I have for my system:

How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps. Since I use Norton Ghost to make regular backups and restores (I do a lot of testing), I do this all the time...

-Warr

Hey man, I did these steps but error 2 keeps getting displayed. I installed puppy linux, lucid pup, and it does install a bootable grub. The mint installer is the one that cannot do this. Any ideas?

Just a FYI, lucid puppy does install well and boots off ok, so I guess this is a problem with the mint installer.

---

