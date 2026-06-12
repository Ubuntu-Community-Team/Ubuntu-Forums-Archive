---
title: "Elementary OS (Ubuntu) - No boot media"
date: 2017-04-17
forum: Ubuntu/Debian BASED
---

### Post by jcamilowps on 2017-04-17
I've been trying to install Elementary OS which as I understand is pretty much just a decorated version of Ubuntu - after an installation completion, restarting just leads me to a black screen where I'm instructed to reboot and select boot media. I tried to search under their StackExchange but they didn't seem to have any good suggestions.

I feel like I've tried everything I could find regarding this issue and Ubuntu (apparently this seems to happen in Ubuntu a lot too). I tried using boot-repair with the recommended repair settings, I tried making sure secure-boot was turned off and attempted to reinstall the OS, I've plugged in and out the SATA cable just in case the issue was the drive, I'm really not sure what to do.

A lot of threads suggested from users to post their boot-info so below is that:

[http://paste2.org/wFeA0XtH](http://paste2.org/wFeA0XtH)

Any insight would help.

---

### Post by vasa1 on 2017-04-17
> **jcamilowps said:**
> I've been trying to install Elementary OS which as I understand is pretty much just a decorated version of Ubuntu - ... I tried to search under their StackExchange but they didn't seem to have any good suggestions.
...

I'm not sure the developers of Elementary OS will agree that it "is pretty much just a decorated version of Ubuntu".

There's also [https://elementaryforums.com/index.php](https://elementaryforums.com/index.php) for support.

---

### Post by jcamilowps on 2017-04-17
That's understandable. The ElementaryForums don't seem to have anything posted regarding this issue either. I went ahead and made a thread there too but any help is appreciated!

---

### Post by oldfred on 2017-04-18
You have a mis-mash.
Or not a standard UEFI install.

UEFI uses gpt as standard, but in a pinch you can use MBR(msdos) as that is what most UEFI installers are.
But much better to use gpt.

But do you also have Windows? 
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.

You somehow show Microsoft folder in ESP - efi system partition but drive is MBR. Did you convert from gpt to MBR?

Best to decide if you really want UEFI or BIOS and only boot system in that one boot mode. How you boot installer is then how it installs. And setting in UEFI on boot mode must then match how you have installed.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See also link below on UEFI in my signature.

---

### Post by jcamilowps on 2017-04-18
I have another drive that has Windows 10 that is currently unplugged and at my workplace (I can't plug it back in atm) - there are some important files in the drive I would like to install Elementary into that made me want to create some free space and make the appropriate partitions for my installation as opposed to a full format. 

Ideally, I'd like to dual boot both operating systems. Judging by the screenshots, I think I installed Linux/Elementary in UEFI when using the LiveUSB. 

I don't have the Windows 10 hard drive with me but I can get it at my workplace tomorrow if I need to replug it (I honestly don't know if the drive is booting UEFI or BIOS).

I'm sorry if I misuse any of these terms, this is the first time I've ever had to deal with this stuff in a Linux install (I used to have Windows 7 and I never had this problem installing Linux!) so I'm not 100% sure knowledgeable on these things. 

You said gpt is better so I suppose I would want to make sure that all the partitions and all my drives are booting UEFI? How would I move forward to do that?

---

### Post by oldfred on 2017-04-18
Best to check how Windows is installed. 
If your Windows 10 is an upgrade from Windows 7 if probably is BIOS/MBR. Only have seen a very few Windows 7 systems that were UEFI.

If you have a drive dedicated to Ubuntu or a drive that will only have data not Windows, you can use gpt on those drives whether UEFI or BIOS.
I had XP with MBR partitioning on my BIOS system and converted another drive to gpt to install 10.10(?) or there abouts. Had no issues which I thought was a good thing. But with BIOS boot you have to have a bios_grub partition for grub to correctly install.

When Windows converted to UEFI/gpt with Windows 8, I knew I would eventually get a newer UEFI system. Took several years as I added a SSD and old BIOS system was much faster.
But all new drives purchased or totally repartitioned since that first gpt conversion are gpt with both the bios_grub & the ESP. Even data only drives, but I always have at least one small bootable partition on every drive.

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)

---

### Post by jcamilowps on 2017-04-18
I went to my workplace and I finally got a hold of the other drive and plugged it in. 

My computer booted Windows flawlessly so it's good to know that whatever I did didn't screw that up. I followed some of the info you have in your signature and checked - it says 'Legacy' instead of 'UEFI' under System Information (which I assume it means that it's using BIOS instead of UEFI?).

I have to go out to do an errand so I'll be following this thread on my phone and doing changes as I get a chance; I apologize if my responses are super slow. Is there a way to change my Windows boot from Legacy to UEFI without formatting the drive or getting rid of my data? Is it even worth the effort doing the conversion (assuming it's possible) - am I better off just attempting to install Elementary/Ubuntu as indicated here [http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside_8.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside_8.html) ?

I can access a similar screen to the one shown in the BIOS install of Linux screenshot (this one: [http://pix.toile-libre.org/upload/original/1347445119.png](http://pix.toile-libre.org/upload/original/1347445119.png)) if I go to my BIOS and select the LiveUSB manually but my monitor won't detect any signals if I try to do that one. If I access that and get my monitor to actually display the install, would that be me installing it in BIOS and would it just dual boot fine if I made new partitions in the install after creating free space again?

---

### Post by oldfred on 2017-04-18
Windows makes it very difficult to convert, but I believe somewhere in the ether I saw a thread. I would not suggest it, unless you really want that.
UEFI/gpt is slightly better, but probably not worth the hassle to change.

But I would consider making all drives other than the Windows drive gpt partitioned and include both bios_grub for current BIOS boot, but include an ESP for future UEFI boot.
Once you start booting in one mode you cannot switch.  Or you can only boot other systems installed in same boot mode as grub. 
If you have mixed UEFI/BIOS installs, you can only dual boot from UEFI boot menu, not from grub menu. 

Grub also only boots working Windows. With UEFI you can always directly boot Windows from UEFI boot menu.
But with BIOS, it is better to have multiple drives so you can have Windows boot loader on Windows drive and grub boot loader on Ubuntu drive.
Windows  8 or 10 uses fast start up or always on hibernation. Grub cannot boot hibernated Windows and Windows on updates will keep turning it on. So you either need a way to directly boot Windows when grub cannot, or a Windows repair disk to temporarily restore a Windows boot loader if only one drive or one MBR used for booting. 

With multiple drives only use Something Else install option, then you control partitions and in particular which drive to install grub2's boot loader.
       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

