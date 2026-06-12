---
title: "Call for testing: GRUB 2.00"
date: 2012-09-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dino99 on 2012-09-12
Quantal will probably get Grub 2.00

so if you dont care about possible breakages, and have time for testing and send debugging info, its up to you :p

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-September/035887.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-September/035887.html)

[https://launchpadlibrarian.net/114955298/NEWS.diff](https://launchpadlibrarian.net/114955298/NEWS.diff)

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

):P

---

### Post by dino99 on 2012-09-12
Feedback:

tested on a system with several pata/sata hdds and multiple distro installed:

- quantal i386 ubuntu/lubuntu : all fine
- precise i386 : want to remove apport & other grub packages (so not installed)

booting is easier and faster.

---

### Post by cariboo on 2012-09-12
thanks for that dino99, I saw the email just before I left for work, and didn't have time to post it.

I just installed grub 2.00 on my pretty vanilla 64-bit Ubuntu install, and aside from it being initially installed on the wrong drive, it works quit well when it is on the correct drive, :) It does seem to be faster than the previous version.

---

### Post by mcellius on 2012-09-12
I'd give it a try, but this one scares me.  I don't mind messing up my Quantal partition to the point of making it unusable, necessitating a complete reinstall, but messing with Grub has the potential of making it difficult for me to boot into a partition that I can't afford to lose (e.g. my 12.04 installation).  I know that in the end recovery from a Grub bug or error will almost always be possible, but along with being faint of heart I am also lacking in knowledge about how to do it.

I think I'll have to wait for this one to be settled.  But I'll follow the subject with interest!

---

### Post by dino99 on 2012-09-12
More comments:

- the first test was fine
- then a new eglibc was upgraded (2.15-0ubuntu18  )

the trouble was on the next cold boot:

config: 3 hdds 2 pata & 1 sata; each having a mbr grub (but not exactly the same version, 1.98+)

Previously i was booting on a pata (selected inside bios) and calling a distro on an other hdd: the result was that grub was needing time before showing its menu, but that was working.
Now with grub 2.0, with the above config, the grub process is killed before getting the menu (too confused to find the pathes).

So the solution was to change the selected boot hdd inside the bios to have both distro called and mbr grub on the same hdd.
This is a regression, and have reactivated the bug #420933

---

### Post by raja.genupula on 2012-09-12
you accept the testing at virtualbox ?

---

### Post by Stinger on 2012-09-12
I bit the bullet and tried the new GRUB2, works fine here from my hard disc sda1.

Did this after adding the ppa and updating the grub packages:
```
sudo update-grub
```
And this to look for the bootloader location:
```
grub-probe -t device /boot/grub
```

Rebooted a couple of times, no problems so far.
 
Processor: AMD Phenom(tm) II X4 B45 Processor × 4 
Graphics: Gallium 0.4 on AMD RV730 
OS-type: 64-bit
Hard disc: 310,8 GB PATA

---

### Post by balloons on 2012-09-12
> **raja.genupula said:**
> you accept the testing at virtualbox ?

This is intended to test physical systems.. Be prepared for breakage, and please do email Colin directly with results. Thanks for testing :-)

---

### Post by chrismine on 2012-09-12
Installed without a hitch, it even booted into my Windows 8 RC - with the previous GRUB Windows 8 gave BSOD and rebooted.

Working fine for me then.

---

### Post by balloons on 2012-09-12
> **guitara said:**
> This is intended to test physical systems.. Be prepared for breakage, and please do email Colin directly with results. Thanks for testing :-)

I didn't mean to say you can't test in virtualbox -- if you do, please note it. However, the key concerns are with physical system setups. :-)

---

### Post by ventrical on 2012-09-12
> **dino99 said:**
> Feedback:

tested on a system with several pata/sata hdds and multiple distro installed:

- quantal i386 ubuntu/lubuntu : all fine
- precise i386 : want to remove apport & other grub packages (so not installed)

booting is easier and faster.

 I like the layout. I don't have to figure which kernel to boot from on multiple installs :)

Time for cold boot.

*edit*

Ligthdm did this really weird thing (not Grub 2 related I think) and unity DE all of a sudden has lost it's punchiness.

---

### Post by nm_geo on 2012-09-12
Installed the Grub2 packages on two of my test boxes and it seems to work well.  Will try on a windows dual booting system this weekend after I do some clonezilla backups.

---

### Post by dino99 on 2012-09-13
new ppa2 version : get big trouble with it, cant get the grub menu on that 3hdds system with bios (no raid, no encrypt, no ...)
only get Alloc Magic is broken at ...

so take care ;)

Edit: finally found that mess was due to grub-customizer that i've had used in the past and purged everywhere; but sadly it left some modified settings behind. But thanks to boot-repair to cleanly removed that garbage and cleanly reinstalled grub 2.0 working smootly now :)

---

### Post by Stinger on 2012-09-13
> **dino99 said:**
> 
Edit: finally found that mess was due to grub-customizer that i've had used in the past and purged everywhere; but sadly it left some modified settings behind. But thanks to boot-repair to cleanly removed that garbage and cleanly reinstalled grub 2.0 working smootly now :)
Thanks for the tip, I'll get rid of the grub-customizer and use boot-repair.
Haven't had any trouble though, but I'm only having a single hard disc on my system.

---

### Post by dino99 on 2012-09-13
> **Stinger said:**
> Thanks for the tip, I'll get rid of the grub-customizer and use boot-repair.
Haven't had any trouble though, but I'm only having a single hard disc on my system.

Yeah grub is mainly having issue with multiple hdds and multiple distros installed; it seems to scan everything instead of only the partitions with an OS, so it is confused & need more time to display its menu; hope this will be fixed in the near future (i've mailed Colin about that & reactivated an old bug report too)

---

### Post by smartboyhw on 2012-09-13
Oh how great is GRUB 2.00! Fast and fluid (as in Microsoft's UX says) Thanks to the GRUB team and cjwatson:)

---

### Post by dino99 on 2012-09-13
Grub2 2.00-3ubuntu1 is compiling now to land into main quantal repo very soon  :P

---

### Post by Ubunterrific on 2012-09-13
> **dino99 said:**
> Grub2 2.00-3ubuntu1 is compiling now to land into main quantal repo very soon  :P

Delicious :popcorn:

---

### Post by balloons on 2012-09-13
> **Ubunterrific said:**
> Delicious :popcorn:

Changelog:

[https://launchpad.net/ubuntu/quantal/+source/grub2/2.00-3ubuntu1](https://launchpad.net/ubuntu/quantal/+source/grub2/2.00-3ubuntu1)

---

### Post by dziki on 2012-09-13
just got it! works fine ..even on my old laptop (1Gb, Centrino duo), on which 12.04 lts shares the space with the windowsxp ;)
tomorrow more tests ..

---

### Post by mcellius on 2012-09-13
I just ran Software Updater and I saw that Grub 2 came through.  Cool!

However, when I installed QQ on this machine, I already had 12.04 installed; I put QQ into a separate partition.  I didn't let QQ install Grub at that time because I wanted to keep the settings I had created for Grub with Precise.  So now, if I want to use Grub 2, how would I do it?  Ordinarily, when I want to install a new Grub, I boot from a LiveDVD, but obviously I don't have Grub 2 on a live DVD.

[UPDATE]  Got it, piece-o-cake.  On my system, which has just one HDD and three versions into which I can boot (12.04.1, QQ, Tuquito) it works just fine.

---

### Post by Elfy on 2012-09-14
Worked fine here - but all it had to find was some *buntu installs.

I'd like to know how to get to recovery mode from it though :)

---

### Post by dino99 on 2012-09-14
> **Elfy said:**
> Worked fine here - but all it had to find was some *buntu installs.

I'd like to know how to get to recovery mode from it though :)

have had some issues too, and finally found that the previous used grub-customizer (been purged a while back) was to blame due to left some settings behind. So using boot-repair recreate a clean grub install/menu.

But that new grub 2.0 version does not set a menu with all the kernels installed for the other distros installed ;)

It only get access to the multiple kernels for the main booting partition, the others only have 1 kernel & its recovery entry; thats bad. (not reported yet)

---

### Post by stinkeye on 2012-09-14
The latest grub works fine here.
I have 3 Ubuntu installs (12.10, 12.04 and 10.10-UbuntuStudio) and grub lists an 
advanced option for each install where once selected, I have access to all old kernels and recovery mode.
Looks a lot better now with the release number shown rather than
just Ubuntu and the kernel number.

---

### Post by philinux on 2012-09-14
Info on grub 2.

A major updating of grub to 2.0 is happening now in quantal. This change drops alot of custom patches and brings quantal in line with upstream, fixing bugs and offering a better experience (hopefully!). That said, if you find any issues or find yourself unable to boot, etc, as always have a plan in place. Make sure you have a copy of a live usb or cd image of ubuntu to recover with. [https://launchpad.net/ubuntu/quantal/+source/grub2/2.00-3ubuntu1](https://launchpad.net/ubuntu/quantal/+source/grub2/2.00-3ubuntu1)
 If you need any help, feel free to ping the list, IRC, or consult the ubuntu wiki on repairing grub. Safe testing everyone!

Nicholas

---

### Post by pulpo69 on 2012-09-14
that means grub2 and not grub1.99 wil be the default in ubuntu 12.10?

---

### Post by dino99 on 2012-09-14
> **pulpo69 said:**
> that means grub2 and not grub1.99 wil be the default in ubuntu 12.10?

its already the case since yesterday :lolflag:

---

### Post by dino99 on 2012-09-14
> **philinux said:**
> Info on grub 2.

A major updating of grub to 2.0 is happening now in quantal. This change drops alot of custom patches and brings quantal in line with upstream, fixing bugs and offering a better experience (hopefully!). That said, if you find any issues or find yourself unable to boot, etc, as always have a plan in place. Make sure you have a copy of a live usb or cd image of ubuntu to recover with.[https://launchpad.net/ubuntu/quantal/+source/grub2/2.00-3ubuntu1If](https://launchpad.net/ubuntu/quantal/+source/grub2/2.00-3ubuntu1If) you need any help, feel free to ping the list, IRC, or consult the ubuntu wiki on repairing grub. Safe testing everyone!

Nicholas

May be too late (or too early, a future version will raise a day or an other) as grub 2.0 is already the default since yesterday ;)
and your link point nowhere :
[https://launchpad.net/ubuntu/quantal/+source/grub2/2.00-3ubuntu1If](https://launchpad.net/ubuntu/quantal/+source/grub2/2.00-3ubuntu1If)

---

### Post by dino99 on 2012-09-14
> **stinkeye said:**
> The latest grub works fine here.
I have 3 Ubuntu installs (12.10, 12.04 and 10.10-UbuntuStudio) and grub lists an 
advanced option for each install where once selected, I have access to all old kernels and recovery mode.
Looks a lot better now with the release number shown rather than
just Ubuntu and the kernel number.

hm, will purge then reinstall it, thanks.

---

### Post by jerrylamos on 2012-09-14
"Ubuntu" is all it says on the top line.  

Got to be the ultimate "Dumbing Down".

I've got several Ubuntu's.

Which one is it going to boot?

What partition is it?  I've got a bunch of partitions, on two hard drives, Windows 7 etc. LTS, a couple last running levels of QQ, etc.

Is there any way this new Grub will tell me which partition and what level of Ubuntu?  Does it even know?  Why is it discarding what I want to know?

---

### Post by Elfy on 2012-09-14
> **jerrylamos said:**
> "Ubuntu" is all it says on the top line.  

Got to be the ultimate "Dumbing Down".

I've got several Ubuntu's.

Which one is it going to boot?

What partition is it?  I've got a bunch of partitions, on two hard drives, Windows 7 etc. LTS, a couple last running levels of QQ, etc.

Is there any way this new Grub will tell me which partition and what level of Ubuntu?  Does it even know?  Why is it discarding what I want to know?

It's going to boot the one grub is installed - just like it did the day before.

The other partitions are below it - just like they were the day before.

---

### Post by Elfy on 2012-09-14
> **dino99 said:**
> ...

It only get access to the multiple kernels for the main booting partition, the others only have 1 kernel & its recovery entry; thats bad. (not reported yet)

reported it for not showing recovery options for any bootable os on the front screen

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050983](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050983)


mmmm - now I look more - I'm not sure that's the case - possibly the advanced options is the 'original' and it's recovery mode ... oh well if it is it can be added to the other ignored bugs

Edit - I was confused - recovery is in the advanced options.

---

### Post by cariboo on 2012-09-14
I've got Precise, Quantal, Gnomebuntu and Windows 8 installed on this system, there is even recovery options for Precise and Quantal in the grub menu.

---

### Post by dino99 on 2012-09-14
in some cases the grub.cfg is corrupted (watch Bug #1050774 ) and Colin have identified & reproduced this issue.
maybe i've made too much customization (grub_gfxmode); but even purging grub then reinstalling it does not solve the problem. So dont tweak too much like i've done ;)

---

### Post by Elfy on 2012-09-14
> **cariboo907 said:**
> I've got Precise, Quantal, Gnomebuntu and Windows 8 installed on this system, there is even recovery options for Precise and Quantal in the grub menu.

On the front or in the Advanced ?

---

### Post by cariboo on 2012-09-14
> **Elfy said:**
> On the front or in the Advanced ?

In the top portion of the menu in Advanced, and the lower portion below memtest, in the front.

---

### Post by jerrylamos on 2012-09-14
I'm retired, look for pc sales, so I've got atom i386x2 1.6 gHz netbook with hard drive and USB hard drive and TV monitor, amd64x2 1.6 gHz notebook hard drive USB hard drive external monitor, i386x1  celeron 3.3 gHz tower with one sata and one ide hard drive.

So using 12.10's "Grub 2" I see two ubuntu 12.04's.  Now which one is on the pc hard drive and which one on the USB hard drive?  According to Grub Development I don't need to know that. 

Play around with "e" and look for hd0 and hd1.  To me, sda2 and sdb1 on the main grub menu are a whole lot more user friendly, if that is even a goal.

Now on the tower with sata and ide, on some ubuntu's the boot drive is sda and the secondary sdb.  Other ubuntu's the boot drive is sdb and the secondary is sda.

Grub will furiously search on one of the hard drives looking for a UUID and can't find it.  Never occurs to Grub to look on the other hard drive...

Moral is, run the configurations the Grub developers use, whatever that is.

---

### Post by ventrical on 2012-09-14
> **cariboo907 said:**
> I've got Precise, Quantal, Gnomebuntu and Windows 8 installed on this system, there is even recovery options for Precise and Quantal in the grub menu.


 I just racked 4 hdds together and have most of the above. Works ok here so far.

ventrical@ventrical-P4M266A-8237:~$ sudo update-grub
[sudo] password for ventrical: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-13-generic
Found initrd image: /boot/initrd.img-3.5.0-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda1
Found Ubuntu quantal (development branch) (12.10) on /dev/sdb1
Found PCLinuxOS on /dev/sdc1
done

---

### Post by sammiev on 2012-09-14
Been testing it for a few days now and seen a few updates come in as well. So far no issues running multiple OS with more than a few Ubuntu versions. The only thing I miss really is just the version number a long the display.

---

### Post by ventrical on 2012-09-14
Ok.. I found that if you want to remove a hdd from your rack that to have your GRUB edited it is important to run : sudo update-grub from the first Primary master. Running it from any other disk will not add or delete the appopiate entries.

---

### Post by jerrylamos on 2012-09-14
> **ventrical said:**
> Ok.. I found that if you want to remove a hdd from your rack that to have your GRUB edited it is important to run : sudo update-grub from the first Primary master. Running it from any other disk will not add or delete the appopiate entries.When I run 
sudo update-grub
from another partition I then run
sudo grub-install /dev/sda
or /dev/sdb or /dev/sdc or whatever boot device you are going to choose.

Subsequently, you don't have to do the grub-install if you use the same partition for sudo update-grub.

---

### Post by drs305 on 2012-09-14
Updated Quantal today on an amd64 desktop and Grub 2.0 worked fine. 

Then I added cjwatson's ppa and purged/installed it on a current i386 version of Precise on my laptop. It also installed without a hitch.

---

### Post by cecilpierce on 2012-09-14
Has anyone tried the starfield theme ?

The colors are kinda weird, seems like everything is dark...:confused:

The grub-emu doesn't work with the theme but does without it.

I wonder if some of the other theme will work ?

---

### Post by OGpmpdog on 2012-09-14
Greetings Testing Brethren:

I also Have Precise, Opensuse 12.2, and Windows 7 installed on various HDs.

Just updated QQ and Grub 2.00 hosed my boot screen (YUCK!!), despite latter being on another partition.

It's cool being a tester because I learned how to reinstall GRUB from Live CD!!

*I sense a how-to fix GRUB after youve upgraded to QQ thread*

Everything is OK now, all partitions & HD's recognized...First impressions of GRUB 2? I've got multiple installations/kernels, so I don't mind tabbing down to see the bootable kernels in each partition.

---

### Post by Elfy on 2012-09-15
> **cariboo907 said:**
> In the top portion of the menu in Advanced, and the lower portion below memtest, in the front.

Odd, apparently recovery mode should be in the advanced bits.

---

### Post by nervis on 2012-09-15
with new grub my windows 7 partition is loost

---

### Post by ventrical on 2012-09-15
> **Elfy said:**
> Odd, apparently recovery mode should be in the advanced bits.


When you click advanced options you will get your tabbed recovery option. A tleast I do here.

---

### Post by Elfy on 2012-09-15
this is getting even more confusing now :)

I was referring to cariboo's > and the lower portion below memtest, in the front.

I know :)

---

### Post by ventrical on 2012-09-15
Doh!  :)

Brain fart !

 sorry..

:)

---

### Post by Elfy on 2012-09-15
> **ventrical said:**
> Doh!  :)

Brain fart !

 sorry..

:)

It's ok - I had a massive one from beginning to end with it - at least I got sensible replies to the bug report - made it more logical :D

---

