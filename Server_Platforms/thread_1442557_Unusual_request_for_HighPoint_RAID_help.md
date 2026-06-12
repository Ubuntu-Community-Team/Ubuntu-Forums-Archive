---
title: "Unusual request for HighPoint RAID help"
date: 2010-03-30
forum: Server Platforms
---

### Post by d.vanheeckeren on 2010-03-30
Hi there...I DON'T want to install on a raid array.  I want to continue using my ubuntu server on it's own hard drive.  The server it's in, however, used to be a Windows 2000 Server on it's own drive, and a highpoint 372 raid controller FOR DATA ONLY.  Now that I have ubuntu server running, fdisk recognizes both hard drives in fdisk and shows the size correctly, and even shows the partitions, but is unable to mount.

I was told to get the open source driver from highpoint, which I did, and compile it, which I can't.  Here is the results of the make command:

[http://atheists.dontexist.org:82/error.txt](http://atheists.dontexist.org:82/error.txt) (and yes, I took the trailing slash off the KERNELDIR but it still does the same thing but with one less /.)

I have no clue what I'm doing with compiling, I'm not a programmer.  But I have verified that the files it's saying it can't find do in fact exist. Anybody that can help me or point me in the right direction here?  Thanks!

---

### Post by jrssystemsnet on 2010-03-30
Highpoint cards work well under FreeBSD, but not so well under Linux.  Maybe you could bite the bullet and just buy a cheap replacement controller?

Honestly, it's what I'd do.  Flaky "it only works if I hit it with a hammer" hardware is no fun at the best of times, it's CERTAINLY no fun when it's in between you and your filesystems!

---

### Post by d.vanheeckeren on 2010-04-11
Yes, but if you recall, if I buy another controller that uses hardware RAID, I lost the data I have on there now.  Otherwise, I'd say yes.  And I'll still say yes, but only AFTER I get my data off.

---

### Post by d.vanheeckeren on 2010-04-24
Problem solved, and I didn't even have to compile a driver, because support is natively included in the kernel.  

First step, login and switch user to root so you don't have to keep typing the annoying 'sudo'.  :)

```
sudo su root
```Then download and install dmraid from your Ubuntu server if it's not already installed.
```
apt-get install dmraid
```Then let dmraid scan your disks and activate automatically the raid arrays it finds.  It will add entries to /dev/mapper automatically, so keep note of the arrays it activates.
```
dmraid -ay
```dmraid will then report the raid arrays it found and activated.  On my highpoint card, it shows as "hpt37x_bdadhhggje"  (your part after the underscore will be different)

Then create a directory (I actually created three as I had three partitions on that raid array) to use as a mount point.  In keeping with convention, I chose to create those directories under "/media".  You can choose whatever name you wish, but I used 'winraid' to denote that it was my old windows raid array.
```
mkdir /media/winraid1
mkdir /media/winraid2
mkdir /media/winraid3
```Then mount the arrays at those directories.  (Note: Webmin DID NOT support this command from Others-Command Shell - Execute Command)  Again, substitute whatever dmraid reported above for the "hpt37x_bdadhhggje" occurences shown here.  And keep in mind that I had three partitions on it, so they all showed up with their partition number after the name (e.g. hpt37x_bdadhhggje1, hpt37x_bdadhhggje2, and hpt37x_bdadhhggje3)
```
mount -t ntfs /dev/mapper/hpt37x_bdadhhggje1 /media/winraid1
mount -t ntfs /dev/mapper/hpt37x_bdadhhggje2 /media/winraid2
mount -t ntfs /dev/mapper/hpt37x_bdadhhggje3 /media/winraid3
```I was then able to access all three Windows raid partitions that were created in ntfs in /media/winraid1 - /media/winraid3.

As I wanted to share the directory on the network using Samba (I am the only one in my house who knows how to use Linux anyway and I use three different computers to do it), I also allowed full access to all three directories using chmod.  I'm certainly not an expert, but if you have your machine accessible to other users, I don't recommend you doing this for security reasons.  [COLOR=Red]Proceed to the next step at your own risk.[/COLOR]
```
chmod 777 /media/winraid1
chmod 777 /media/winraid2
chmod 777 /media/winraid3
```[COLOR=Black]

Don't forget to switch back to your regular user account so you don't accidentally screw anything up.  :)
[/COLOR]```
exit
```[COLOR=Black] Since all I needed to do was copy the files off those partitions and I didn't need to use that array permanently, I did NOT make these changes permanently so that it would always be available even after reboots.  Because I'm new at Linux and don't need to do it, I chose not to go further and research how to make it permanent.  Maybe someone else can add to this thread in case this post helps someone else who wants to make it permanent?
[/COLOR]

---

### Post by windependence on 2010-04-24
Just an FYI for in the future. If you want to use a really good controller that is super cheap, anything based on the Silicon Image 3512 chipset works really well under Linux (and VMware) and the cards should cost you no more than $25 for a two port card or $40 for a 4 port card. We use these all the time in enterprise deployments and they work great. I know it wouldn't have helped here, but thought I'd mention it.

-Tim

---

### Post by tgalati4 on 2010-04-24
Great tutorial.  Ubuntu server is not enterprise class yet, and for precisely the above reasons.  I'm sure this will help highpoint users in the future.

---

### Post by Vegan on 2010-04-24
> **windependence said:**
> Just an FYI for in the future. If you want to use a really good controller that is super cheap, anything based on the Silicon Image 3512 chipset works really well under Linux (and VMware) and the cards should cost you no more than $25 for a two port card or $40 for a 4 port card. We use these all the time in enterprise deployments and they work great. I know it wouldn't have helped here, but thought I'd mention it.

-Tim

Is that controller able to use SAS devices?

---

### Post by windependence on 2010-04-24
> **Vegan said:**
> Is that controller able to use SAS devices?

Nope. If you can afford SAS drives you can afford a good Adaptec or 3ware card for it too.

-Tim

---

