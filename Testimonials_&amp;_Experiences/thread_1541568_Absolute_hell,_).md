---
title: "Absolute hell, :)"
date: 2010-07-29
forum: Testimonials &amp; Experiences
---

### Post by polomint77 on 2010-07-29
Ok, the thread title might sound bad, but it's actually a good thing.  Bearing in mind that I'm new to Linux but am very experienced with Windows (pfft).
First, some important information.  My laptop is a Pentium Mobile 1.6, 768MB RAM, 120GB HDD, Intel 855GM Gfx, wireless etc..
My CD/DVD drive only works with some discs, rarely DVDs but sometimes CDs work.  This laptop does not boot from USB, and I have *no* Ubuntu LiveCDs.. 

This is what happened (I posted this on the Virtual Pool 3 forum as I went along)...

> 

I decided to dual boot my laptop with ubuntu and winxp, so I had a go....
I  had no LiveCD so I thought I'd use VMWare to install using the ISO I  had but allow VMWare access to my physical/real HDD.  Installed fine,  reboot PC, and got a major GRUB_RESCUE error...  Oh dear...
Thank God I have a working netbook, 
Anyway,  couldn't do anything about the error, my DVD drive on the laptop  wouldn't read any DVDs for some reason, so I couldn't fix Windows or use  a different distro DVD to fix the boot error..
Anyway, found an  Ophcrack CD (for cracking Windows passwords), and that booted, so I  booted with that and made sure I could access the Windows partition that  held the Ubuntu ISO.  I could, so I tried to burn that ISO onto a CD.   Doh! I forgot that you can't use the DVD drive when you are running a  LiveCD from it...  Sooooooooooo...  installed Ophcrack to a spare  partition I made, rebooted into that installation without needing to use  the CD/DVD drive.  That worked fine, so I used 'wodim' (CD burning  tool) using xterm and am currently burning the Ubuntu LiveCD to a CD,  Yayyy....
Ahhh, it's just finished burning, now to see if I can boot from the LiveCD, wish me luck...

What a night.. grr

UPDATE:  Seems that the darn iso was written as Track-At-Once, which my laptop  decided it didnt want to boot from.  So, I'm now writing it as  Disc-At-Once.. ffs
Oh ffs, my drive doesn't want to write discs at all... Time to try and get clever... brb, :)


Hmmm, I seem to be getting somewhere after doing this.... (found on a forum, cant remember which one though)

Step  1. Use gparted to create a new primary partition and format it to ext3.  You need slightly more than 700MB of free space on it. 750MB should be  sufficient. Let's say the name of the partition is /dev/sda1. If your  new ubuntu install is going to coexist with your old system, you might  find it convenient to create space for your new system as well at this  point using gparted. 

Step 2. Copy CD contents over to the new partition using the command 

 mkdir /tmp/install_cd
 mkdir /tmp/installer

 sudo mount disk-image.iso -o loop /tmp/install_cd
 sudo mount /dev/sda1 /tmp/installer

 sudo rsync -a /tmp/install_cd/ /tmp/installer

 sudo umount /tmp/install_cd
 sudo umount /tmp/installer

Replace the name of the iso to whatever you downloaded and /dev/sda1 with whatever your new partition is.

Step  3. Edit your grub configuration file (typically /etc/grub.conf or  /boot/grub/menu.lst) to boot from the new partition by adding the lines 

title           installer
root            (hd0,0)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd          /casper/initrd.gz



Rebooted, selected the install boot.,..  seems to be working,.. so far....
Damn, black screen as it tries to boot...

Changed the kernel line to

kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw i915.modeset=1 xforcevesa quiet nosplash


Seems  to be booting now.. I've got the startup screen atleast, it seems to be  scanning for index files it seems...  I'll give it some time to sort  itself out...
Well, it's booted into the LiveCD I had copied from my  ISO to a spare partition, I've started the install process again, so  fingers crossed...

Yayyyyyyyyyyyyyyyy, it works... :)  I'm now running linux, my winxp partition still works too, :)

But,  I'm currently installing Windows XP in VirtualBox to see if I can get  Virtual Pool 3 running smoothly (ish) in it.  Will report back with my findings  soon... :)

WinXP and GamespyArcade work fine in VirtualBox, now time to get VP3 installed.....

EDIT:  I spoke too soon, GamespyArcade starts but it doesn't look like anyone can see my  typing. Either that or the feckers are ignoring me, lol. This is  probably to do with my router. I need to persuade it to forward the  ports to the pretend WindowsXP network. I'll see what I can do, :)
VP3  works kind of, the mouse pointer moves very strangely, although I think  that is something to do with VirtualBox Mouse Integration. There are  some settings I can mess with so I will, :)

UPDATE:  Ok, GamespyArcade is working fine now.  Just need to see if I can sort out the mouse issue with VP3 under VirtualBox...

I started all that at around 10pm last night, finally getting it all working great at about 7am this morning, lol

I am *very* happy with Ubuntu 10.04 and will be doing everything on it, just need to install monodevelop and codeblocks and I'll be happy, :)
I'm also very surprised that I've not had more problems with the 855GM graphics though (besides needing to do the i915.modeset=1).  I've noticed a lot of people have had problems with it. Maybe I'm just lucky....

Just one question though, how do I get the modeset to persist between boots, instead of having to add parameters when loading grub...?  I'm assuming there is a file somewhere I could edit?  Maybe /boot/grub/menu.lst?

Thanks to everyone who unknowingly helped me with their posts on here, :)

---

### Post by Tamlynmac on 2010-07-29
> polomint77
Just one question though, how do I get the modeset to persist between  boots, instead of having to add parameters when loading grub...?  I'm  assuming there is a file somewhere I could edit?  Maybe  /boot/grub/menu.lst?

Perhaps, the best way to answer your question is to suggest you start a thread in the appropriate "Help/Support Section". As this section is not a support section of the forums, see this [sticky]("http://ubuntuforums.org/showthread.php?t=1343965").
Support responses in this section will not be reflected in searches of the help sections. Thus, any members searching for solutions to this issue may find zero returns when querying the help sections. Resulting in a duplication of Q&A's.

Good Luck

---

### Post by polomint77 on 2010-07-29
Oops, good point, thx for reminding me, :)

---

