---
title: "Down and up again - lessons learned."
date: 2009-06-16
forum: The Cafe
---

### Post by Polaris96 on 2009-06-16
I have several PCs in my office.  One is a "dedicated tweaker." Problem is, I'm so fond of the tweaker machione that I usually wind up doing real work on it and then losing that data when I break the the box.  Happened again, today.  Here's what I took away from my latest meltdown:

1.  Net Install images blow.  This isn't stricly applicable to Ubuntu, where most people are using the live cd installer.  But, as I was updating Debian, the grub init script kept hanging and leaving me at the mercy of satellite broadband for ANOTHER whack at installing the bloody system.

2.  You CAN'T SHARE /boot between systems!!!  I figured, "ahh, what the heck, there's some space there.  Let's see what happens.  What happened was a /boot directory with all data wiped and No /vmlinuz or initrd to speak of.  
   a.  Now, this might've been caused by the failed grub-install process.  I'm not sure.

3.  You CAN (and I always do) share a /home partition between different distros.  Makes life MUCH more enjoyable.

4.  If you do that, though, you can't encrypt unless you have a better knowledge of ecryptfs than I do.  I'm positive there's a way so I'm gonna study n post it when I figure it out.  While I'm at it, don't use RAID for /home - the files don't need blistering speed and, if you whack the system, it can be a pain to get the array up, again.  I do like using LVM though, because I always wind up resizing partitions and LVM makes it so painless.  It's also much more intuitive from the terminal that mdadm is.

4a.  Also LVM can stripe like RAID0.  I'm not sure how it compares for speed.  I'm currently conducting an experiment to find this out but my data got hosed when I blew up the old system.  back to the drawing board...  LVM also supports a data recovery feature called snapshot.  Check it out.  It's a good system and very easy to work with.

5.  You will be frustrated if you're able to resurrect a dead RAID0 array AND mount your /home partition using a rescue terminal only to discover that you can't decrypt it.  I cursed.

6. You can quickly whack an HDD for repartitioning by using fdisk to write a brand new partition table.  The device then LOOKS pristine.  Beware!  the old data isn't wiped out until it's overwritten.  Don't leave anything on the drive that shouldn't stand the light of day..

7.  The best way to load KDE3.5 onto a RAID platform in Jaunty is to use the alternate install Kubuntu CD.  Hit F4 and choose "install command line system" then Create the array and install the base system.  After that, you can use elinks (terminal web browser)  to pull down the pearson computing repository data.  Then follow their directions to install Kde 3.5.  This way, you're installing into a naked system and there's no nastiness left hanging around from kde 4.x.

7a.  About paralleling kde3 and kde4.  I have not been able to make them work well, together.  There may indeed be a way, but I had lots of problems with kde4 services worming their way into kde3.5.  I couldn't even fully remove kde4 with an apt-get purge.  

8.  For what it's worth:  I WANT to like kde4.  It has some really great ideas and the UI's animation is really sane and intuitive to me.  Unfortunately, after a one month trial, I just don't think it's worked out, yet.  I'm back on kde3.5 for a while.

---

