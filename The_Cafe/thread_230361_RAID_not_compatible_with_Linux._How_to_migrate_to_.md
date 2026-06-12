---
title: "RAID not compatible with Linux. How to migrate to a Linux Software RAID?"
date: 2006-08-05
forum: The Cafe
---

### Post by RAV TUX on 2006-08-05
so here is my problem after testing many distros on XPsp2 computer I decided to load FreeBSD,...bad idea...not only did the install fail but it wiped out XPsp2....not a big loss no big deal...I have been meaning to replace windows all together on this computer.

I have 3 computers in our household:

1. Older computer 98 Compaq which I have run Ubuntu on flawlessly for almost a year now. I used to test on this computer but now Ubuntu is my primary and only OS on this computer.

2. My wife has a brand new Fujitsu Lifebook T4210 Convertible (Tablet/notebook). It has XP Tablet Edition. I have not YET changed her computer to Linux.

3. Our other computer we bought late last year Dell XPS Gen 5 desktop,...processor Intel EM64T (dual core/64 bit)I have 2 hard drives 149.01 GiB each RAID0(stripe)  drive model  ST3160023AS(or 5 on end), sound card Creative Labs sound blaster audigy Platinum edition 

Anyway her is the problem I just discovered that RAID0....

are not supported by the Linux software RAID drives

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-1.html#ss1.2](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-1.html#ss1.2)

so my challenge now is to convert these to Linux software RAID

[http://en.opensuse.org/SDB:Migration_to_Linux_Software_RAID](http://en.opensuse.org/SDB:Migration_to_Linux_Software_RAID)

I am posting this here for two reasons

1. to look for help

2. document this problem and solution so others may find a solution 


I little more history: on this computer I have installed multiply distros and 1 BSD

Gentoo
Knoppix
SUSE
Puppy Linux
Musix
Dreamlinux
PC-BSD

they all install fine

but the bootloaders don't work GRUB or Lilo

I have gotten a series of different error messages including but not limited to:

1. GRUB Error 21
2. GRUB Error 17
3. GRUB no OS
4. Lilo error ( I don't remember specifics)

so I am researching first how to migrate my RAID to Linux Software....

feel free to post advice for me....links...discuss....I will follow up

---

### Post by jason.b.c on 2006-08-05
It kind of raises a question for me...Why would you want to do this..??

> RAID-0

    * Also called "stripe" mode. The devices should (but need not) have the same size. Operations on the array will be split on the devices; for example, a large write could be split up as 4 kB to disk 0, 4 kB to disk 1, 4 kB to disk 2, then 4 kB to disk 0 again, and so on. If one device is much larger than the other devices, that extra space is still utilized in the RAID device, but you will be accessing this larger disk alone, during writes in the high end of your RAID device. This of course hurts performance. 

Are you sure that you want a **"Striping"** system..??   Why not **RAID+1**( mirrored )..?  

Now i understand that there is **software raid** , What about a hardware raid..??  does that work in linux.?

---

### Post by TravisNewman on 2006-08-05
do raid+1 devices work in Linux? I'd suggest using that, much better for data protection.
If you don't want to do that, I'd suggest just setting them up as individual drives and setting up an LVM in Ubuntu setup

---

### Post by RAV TUX on 2006-08-05
ok help me out here. I can actually change the RAID 0?

This is the way it came from Dell....they also set up the Master to CD instead of DVD/CD drive so I can't boot from DVD...

Anyway I have been unable to load Ubuntu and other Distros on here...

But I was able to load SUSE...but I have to configure the DSL connection, printer and sound card.

This is the only OS I have been able to install...but I can not shut it down because the bootloader doesn't work Lilo or GRUB

---

### Post by RAV TUX on 2006-08-06
The ironic part since I can't boot from DVD I can't even reload windows

---

### Post by RAV TUX on 2006-08-06
> **jason.b.c said:**
> It kind of raises a question for me...Why would you want to do this..??



Are you sure that you want a **"Striping"** system..??   Why not **RAID+1**( mirrored )..?  

Now i understand that there is **software raid** , What about a hardware raid..??  does that work in linux.?


here is one reason why:

> The read and write performance will increase, because reads and writes are done in parallel on the devices. This is usually the main reason for running RAID-0. If the busses to the disks are fast enough, you can get very close to N*P MB/sec.

I don't know if I can get it to work in Linux yet.....

---

### Post by RAV TUX on 2006-08-06
ahhhh I thought this was the way to do this....I was experimanted with the Bios....earlier....by george I think I got it!!!!

> As the Linux kernel 2.6.x no longer supports this kind of RAID controllers, you should migrate to a Linux software RAID. To do this, disable the RAID function in the BIOS of your controller in order to use the hard disks as normal IDE hard disks.

---

### Post by RAV TUX on 2006-08-06
> **yozef said:**
> ahhhh I thought this was the way to do this....I was experimanted with the Bios....earlier....by george I think I got it!!!!

YES! YES! this is it! this is the answer!

ok so if this ever happens to anyone keep this little thread in mind:

This is what you do: 

reboot your system

select system set up

from there go down to your drives 

for me I had seven or eight listed (only two active)

the last option will control what controls your hard drives....Bus System I believe....

hit enter to enable changes here

then hit your arrow keys to make your selection

I had 4 choices listed:

1. RAID Autodetect/AHCI
2. RAID Autodetect/ATA
3. RAID ON (=SATA configured for RAID on boot)
[COLOR=Blue] 4. Combination (=SATA/PATA combo mode)[/COLOR]

Choice # 1 was enabled.

I changed it to choice #4!

This is the one to use for Linux!!!

save your changes, confirm and save and WALLA!!!!!:p

My boot loader worked with out fail and booted into DreamLinux!!!!

haha quite appropiately!!!!!;)

I installed and re-partitioned my harddrive so many damn times I forgot what I actually had left loaded!!!

Dreamlinux I'll take it! so now I use Ubuntu 6.06 on one computer and Dreamlinux 2.0 Works Edition on the other!!!!

[IMG]http://www.dreamlinux.com.br/english/imagens/download-ico_box.jpg[/IMG]             [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Dreamlinux                  2.0 WORKS Edition ** [COLOR=#0066cc]**625                  MB**[/COLOR][/SIZE][/FONT] 

                                                    [FONT=Verdana, Arial, Helvetica, sans-serif][[IMG]http://www.dreamlinux.com.br/english/imagens/download.jpg[/IMG]]("http://www.linorg.usp.br/isos/dreamlinux/DLxfce2.0_WORKS-060712en.iso")[/FONT]                   [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]                      [B]MIRROR 1 [COLOR=#0066cc]english version
[/COLOR][/B][/SIZE][/FONT][FONT=Verdana, Arial, Helvetica, sans-serif][[IMG]http://www.dreamlinux.com.br/english/imagens/download.jpg[/IMG]]("http://streaming.serv.iv.fapesp.br:8000/vod/dreamlinux/dreamlinux-works/DLxfce2.0_WORKS-060712en.iso")[/FONT]                   [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]                      **MIRROR 2 [COLOR=#0066cc]english version[/COLOR]**[/SIZE][/FONT]                                               
              [FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=#666666]md5sum:                41bb3fb5379c93b6be692eaa64df6ec5 [/COLOR][/SIZE][/FONT]                

Simply Awesome!!!!!

---

### Post by peabody on 2006-08-07
This is very cool.  Just a thought though.  If experimenting with so many Linux distributions is something you want to do, I'm curious if upping your RAM and doing most of this through something like VMware is a better choice?  A lot less rebooting.

---

### Post by ice60 on 2006-08-07
thanks. i had the same problem. 

now that it boots, i see i need to fix the reason it hangs at "mounting root file system" lol

---

### Post by RAV TUX on 2006-08-07
I have just discovered that Gentoo has documentation/instructions
on Gentoo Linux X86 with software RAID and LVM2 Quick install Guide:

[http://www.gentoo.org/doc/en/gentoo-x86+raid+lvm2-quickinstall.xml](http://www.gentoo.org/doc/en/gentoo-x86+raid+lvm2-quickinstall.xml)

>  **Note: ** The partition you boot from must not be striped. It may not be raid-5 or raid-0. 
   **Note: ** On the one hand, if you want extra stability, consider using raid-1 (or even raid-5) for your swap partition(s) so that a drive failure would not corrupt your swap space and crash applications that are using it. On the other hand, if you want extra performance, just let the kernel use distinct swap partitions as it does striping by default.
  
I am going to start first by installing and getting used to Gentoo then progress to installing Gentoo Linux RAID software....thus allowing me to re-configure my BIOS menu and fully utilize RAID

> **Summary: ** The Quick install guide covers the Gentoo install process in a non-verbose manner. Its purpose is to allow users to perform a stage3 install with software RAID and LVM2 in no time.  Users should already have prior experience with installing Gentoo Linux if they want to follow this guide.

---

### Post by RAV TUX on 2006-08-23
an update:

I never configured the Linux drives for RAID, yet.

or installed Gentoo.

I haven't had time....I simply turned RAID off via the BIOS menu....

I have installed and am very happy with Knoppix 5.01

Here are some links for people who need help with their RAID:

[http://www.tldp.org/HOWTO/software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/software-RAID-HOWTO.html)

[http://en.wikipedia.org/wiki/redudant_array_of_independent_disks](http://en.wikipedia.org/wiki/redudant_array_of_independent_disks)

I hope this helps....

(a side note on this computer Dell XPS Gen 5,....Dell set the CD drive to master making it impossible to boot from DVD...I called Dell Tech support...the only way around this 'according' to them is to go to your BIOS menu and turn off the CD drive, thus enabling the DVD/CD drive to be the master.....after installing your OS simply go to BIOS and turn your CD drive back on.....I know whacky but hey it's Dell)

---

### Post by RAV TUX on 2006-08-23
This has all been a learning process;)

---

### Post by jdong on 2006-08-23
The Ubuntu "alternate" installer supports making software RAID's. It should be easy enough to use that you can figure it out in a try or two. Just keep these basic considerations in mind:

(1) You need to create a separate /boot partition outside the RAID, else your system will not be able to boot up. Usually this is an ext2 partition around 100-200MB large on your primary boot hard drive.

(2) The rest of your physical drives should be partitioned into RAID space.

(3) Now, you can assemble the RAID partitions together using the installer's RAID configuration tool.

---

### Post by RAV TUX on 2006-08-24
> **jdong said:**
> The Ubuntu "alternate" installer supports making software RAID's. It should be easy enough to use that you can figure it out in a try or two. Just keep these basic considerations in mind:

(1) You need to create a separate /boot partition outside the RAID, else your system will not be able to boot up. Usually this is an ext2 partition around 100-200MB large on your primary boot hard drive.

(2) The rest of your physical drives should be partitioned into RAID space.

(3) Now, you can assemble the RAID partitions together using the installer's RAID configuration tool.

Great support...I think more focus needs to be given to advanced hardware, especially since affordablity for new such systems is being integrated....

I found overall Ubuntu a dream on my older system,....which is great from an environmental perspective...

on my new system not so easy...Ubuntu needs to work for advanced systems or include instructions upon install to help overcome these hurdles...

---

### Post by jdong on 2006-08-24
LOL I'm not gonna lie -- SUSE/Fedora/Redhat's RAID installation options are much easier to use than Ubuntu/Debian's... but it's still doable.

---

### Post by RAV TUX on 2006-08-24
> **jdong said:**
> LOL I'm not gonna lie -- SUSE/Fedora/Redhat's RAID installation options are much easier to use than Ubuntu/Debian's... but it's still doable.

SUSE has a great troubleshooter...this is what I used to troubleshoot my computer;)

---

### Post by nnaeem on 2006-10-18
A question as regards to the original post. Did you or anyone else ever manage to install linux on Fujitsu's T4210

---

### Post by RAV TUX on 2006-10-19
> **nnaeem said:**
> A question as regards to the original post. Did you or anyone else ever manage to install linux on Fujitsu's T4210

Yes I have installed Ubuntu on my friends T4210....works simple and easy....like a dream...you will need to tweak it a bit for the pen enabled functions but do-able

---

### Post by nnaeem on 2006-10-20
yozef, thanks for the reply. If you have time you could update [http://www.linux-laptop.net/](http://www.linux-laptop.net/) with this information. Your answer to my question just convinced me to get the T4210 and i have seen other ppl on the internet looking for this info too.

---

### Post by RAV TUX on 2006-10-23
> **nnaeem said:**
> yozef, thanks for the reply. If you have time you could update [http://www.linux-laptop.net/](http://www.linux-laptop.net/) with this information. Your answer to my question just convinced me to get the T4210 and i have seen other ppl on the internet looking for this info too.

Good Welcome...I will work on this later.

Jozef

---

### Post by jpkotta on 2006-10-23
There is already a wiki page for this.  If those instructions don't work or are confusing, please consider updating it.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Also, [https://help.ubuntu.com/community/FileServerOnLVMOnRAID1](https://help.ubuntu.com/community/FileServerOnLVMOnRAID1)

---

### Post by RAV TUX on 2007-02-12
> **RAV TUX said:**
> YES! YES! this is it! this is the answer!

ok so if this ever happens to anyone keep this little thread in mind:

This is what you do: 

reboot your system

select system set up

from there go down to your drives 

for me I had seven or eight listed (only two active)

the last option will control what controls your hard drives....Bus System I believe....

hit enter to enable changes here

then hit your arrow keys to make your selection

I had 4 choices listed:

1. RAID Autodetect/AHCI
2. RAID Autodetect/ATA
3. RAID ON (=SATA configured for RAID on boot)
[COLOR=Blue] 4. Combination (=SATA/PATA combo mode)[/COLOR]

Choice # 1 was enabled.

I changed it to choice #4!

This is the one to use for Linux!!!

save your changes, confirm and save and WALLA!!!!!:p

My boot loader worked with out fail and booted into DreamLinux!!!!

haha quite appropiately!!!!!;)

I installed and re-partitioned my harddrive so many damn times I forgot what I actually had left loaded!!!

Dreamlinux I'll take it! so now I use Ubuntu 6.06 on one computer and Dreamlinux 2.0 Works Edition on the other!!!!

[IMG]http://www.dreamlinux.com.br/english/imagens/download-ico_box.jpg[/IMG]             [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Dreamlinux                  2.0 WORKS Edition ** [COLOR=#0066cc]**625                  MB**[/COLOR][/SIZE][/FONT] 

                                                    [FONT=Verdana, Arial, Helvetica, sans-serif][[IMG]http://www.dreamlinux.com.br/english/imagens/download.jpg[/IMG]]("http://www.linorg.usp.br/isos/dreamlinux/DLxfce2.0_WORKS-060712en.iso")[/FONT]                   [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]                      [B]MIRROR 1 [COLOR=#0066cc]english version
[/COLOR][/B][/SIZE][/FONT][FONT=Verdana, Arial, Helvetica, sans-serif][[IMG]http://www.dreamlinux.com.br/english/imagens/download.jpg[/IMG]]("http://streaming.serv.iv.fapesp.br:8000/vod/dreamlinux/dreamlinux-works/DLxfce2.0_WORKS-060712en.iso")[/FONT]                   [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]                      **MIRROR 2 [COLOR=#0066cc]english version[/COLOR]**[/SIZE][/FONT]                                               
              [FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=#666666]md5sum:                41bb3fb5379c93b6be692eaa64df6ec5 [/COLOR][/SIZE][/FONT]                

Simply Awesome!!!!!This has been a very helpful post which I just returned to for reference.:popcorn:

---

