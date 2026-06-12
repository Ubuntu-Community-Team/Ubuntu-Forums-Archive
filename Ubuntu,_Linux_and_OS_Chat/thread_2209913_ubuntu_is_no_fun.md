---
title: "ubuntu is no fun"
date: 2014-03-08
forum: Ubuntu, Linux and OS Chat
---

### Post by ratchetman on 2014-03-08
Hi I joined this forum so I could express my frustration with Ubuntu. I just wanted to use DD to make an image of a hard drive. I'm booting ubuntu from a flash drive. I believe in the concept of open source software but I don't like anything about using it. I have a hard time learning about Linux in the first place. The little I do learn becomes obsolete because everything changes and I'm left with something that I can browse the net with. Windows will browse the web just fine. I am going to need to have this done by a professional because I can't figure it out. If I pose my questions in a Google search I can see that others are looking for the same information, like how to open a command prompt or how to identify the physical drives attached to the system. For the first one I find that I need to strike the windows key and use a hidden search. What kind of nonsense is this? What ever happened to a command shell icon? As for the physical drive question I can see that people who are responding are confused by it. So even experienced users don't know that we need to be able to figure out how the OS designates the dives. Which drive is hda or whatever you call it now? Probably called something else now because keeping consistent nomenclature is probably just as gauche as a user friendly GUI. Ubuntu is never going to be more than a novelty and the less I see of it the better.

---

### Post by QIII on 2014-03-08
OK.

Thanks for your input.

Not a support request.  Moved to Ubuntu, Linux and OS Chat.

---

### Post by monkeybrain20122 on 2014-03-08
Well if you bother to post to ask for help instead of just complaining you may get better advice. dd is a hard (and risky) way to clone your hard drive, there are many easier and safer solutions if you have bothered to ask.

---

### Post by cariboo on 2014-03-08
It looks to me like you'd be better off with one of the more Windows like derivatives like Xubuntu or Lubuntu, that have a more Window XP type interface.

As far as what you have learned becoming obsolete, you mentioned you wanted to use dd to duplicate a partition, I started using a Linux distribution in 1998, and most of the commands I've learned since then still work today. A simple Ctrl-Alt-F2 would drop you to a command line, where you can use the command line to your hearts content.

---

### Post by Ubi_one_2014 on 2014-03-08
Ubuntu Rocks!!!;)

i am running Kernel 3.13.6 on Ubuntu 13.10, and just figured out how to build debian files.
no more windows for me, wher i completely lost in the directurystructure.

---

### Post by mastablasta on 2014-03-08
> **ratchetman said:**
>  If I pose my questions in a Google search I can see that others are looking for the same information, like how to open a command prompt or how to identify the physical drives attached to the system.

oh you want widnows like interface? try Lubutnu, Xubuntu, Kubuntu

it's different than Windows for sure.

rather than start off usign something knew as i am the master in the topic i prefer to read about the thing i will be using a bit first. for exampel Ubuntu has a very good community made manual available. with pics, simple explanations for beginners etc. so i would start there to see how the system actually operates before moving to google and forums.

biut then again there is always *intuitive* windows8 interface for those that prefer *intuitive* interfaces.

---

### Post by su:bhatta on 2014-03-08
Yes, Ubuntu is no fun.... Windows is much more thrilling ! 
You never know what comes next, a virus, spyware, malware, system crash, Wacom needs a driver that I cant get hold of, oh my, there is not much to do in Ubuntu is there ! !
In Windows, You really have to search so hard for the Windows button , yes that too!!!

Wonder how all of us using it will survive being ignorant of the great & almighty Windows !

But then again, we do survive.
And really, you didn't have to take the pains of joining the forum to let out your frustration at Ubuntu, could have found better audience at any Windows forum.

---

### Post by slooksterpsv on 2014-03-08
I agree with the others that the DD command is risky, do take precautions when using that command, one wrong letter and bye bye drive data. Let me explain the drive lettering:

For IDE Drives they use /dev/hdX# e.g. /dev/hda1
For USB & Sata drives they use /dev/sdX# e.g. /dev/sda4

The Windows key is for Windows, its called Super in Linux and unless you map it to something specific it's nothing more than just a key on the keyboard. Linux is NOT Windows. Ubuntu uses it to open the Dash menu.

The command shell icon??? Do you mean CLI - command line interface? If so, in Linux it's called a terminal. Windows it's called command prompt. Mac it's called terminal.

The OS designates the drives depending on what drive it is in the system - primary or secondary or what other drives take precedence before it. e.g.
1st drive is /dev/sda
2nd drive is /dev/sdb
3rd drive is /dev/sdc
etc. etc. etc.

If you need to look at your drives to see the partitions on it, try using gparted it's in the Software Center. If you feel Ubuntu isn't for you, look into Kubuntu, Lubuntu or Xubuntu. Xubuntu is more like the classic Gnome look but it's XFCE not Gnome. Lubuntu uses LXDE and Kubuntu uses KDE. Each have their own special characteristics.

If you don't like using Open Source Software don't use the Internet, PS3, PS4, Xbox 360, Xbox One, or play a variety of games, heck be careful using Windows cause they all use some form of Open Source Software. Maybe just a few things for archive compression to advanced file-system items. Open Source is in Android, iPhone, Windows Phone, and a ton of every day technological items you use daily.

If you have questions ask, if they're duplicate that's been asked before hundreds of times, oh well, well help you or point you to more up to date information. We are a community here and we'll gladly help you out in any way shape or form that we can, but you need to ask for help.

I hope in time you'll see the value of Linux and Open Source.

As for the others:

Please be kind and courteous, try to help others instead of using sarcastic remarks.

---

### Post by The Cog on 2014-03-08
Hi Ratchetman,

I have to agree with the others that have suggested trying Xubuntu, Lubuntu or Kubuntu instead. I agree that recent Ubuntu is not for everyone - although some people love it, I felt it to be the most user hostile desktop I have ever tried. My personal favourite is Xubuntu, but they are all good, all different and it's a matter of taste. If you haven't compared them before, you will be astonished just how different they can be and still have the same OS underneath. 

As for the physical drives question, that can be tricky. I gather that Linux numbers the drives in the order that they are discovered during boot. I wonder how windows does it, if you think that's so different? I do know that windows sometimes denies the existence of partitions, or gets their type wrong. I've never seen Linux do that. A long time ago, Linux used to call hard drives hda, hdb etc, but for a long time now (10 years or more at a guess) it has called them sda, sdb etc. You're not confusing drives with partitions are you? This command (once you get a command prompt up) will give you a listing of all the drives and partitions:
```
sudo parted -l
```
and you can't get a more self-explanatory listing than that.

---

### Post by PaulW2U on 2014-03-08
> **ratchetman said:**
> Ubuntu is never going to be more than a novelty and the less I see of it the better.

The Ubuntu distribution is more than just the Ubuntu flavour. 

See [http://www.ubuntu.com/about/about-ubuntu/derivatives](http://www.ubuntu.com/about/about-ubuntu/derivatives).

I've used most of them in my time here. Some I will always use, some I will never use. It's all about choice and personal preference. You need to take a little time to research them and/or try them out before making such statements like the one that I quoted.

---

### Post by Gone fishing on 2014-03-08
Seriously if you think the Windows A,B,C,D method of naming drives (where you can't even tell a drive from a partition) is how it should be you have a problem. However, if you want to clone use clonezilla it comes on the Partedmagic live CD which is fantastic there is nothing comparable in Windows software. Lost a partition, formatted a drive need to clone a disk etc no problem.

You might need to learn something new - that's not a problem is it?

---

### Post by buzzingrobot on 2014-03-08
OP's post seems a classic example of a perspective totally bounded and limited by Windows coupled with an unwillingness to make any effort beyond random Googling to learn something.

---

### Post by stalkingwolf on 2014-03-08
perhaps you should try zorin with its windows like look for the desktop.

Worst case you could just open gparted and see what partitions and drives are listed.

---

### Post by farrinux on 2014-03-08
> biut then again there is always intuitive windows8 interface for those that prefer intuitive interfaces.

Hmmm, intuitive, maybe if you live in a chaotic universe!  Mostly in this universe it's crap. LOL 

I know you are being sarcastic, I just wanted to carry it a bit further.  ):P

---

### Post by 3rdalbum on 2014-03-08
Ubuntu is a fast-paced operating system. If you don't like change, Ubuntu is unashamedly not for you and other Linux distros are more suitable.

Having said that, literally everything you said about the Unity desktop is wrong. You need to play around with it more, or read more, to correct those misconceptions of yours.

---

### Post by Weslee_Hollingswor on 2014-03-08
I don't really understand much of anything about Linux, and am honestly a technological noob, but from what I do know so far I like it a lot better than anything I've experienced with Windows. One reason among many is that after just a month of use, my brand-new computer has one working OS and one non-working one. Ubuntu still works fine, but Windows 7 has some BSOD error that prevents me from even loading it, and surprise surprise, I can't even recover to an earlier state or even load it in Safe Mode. Confusion and frustration with something a little less than user-friendly is one thing, but I think the problems involved in using Windows are even less fun. I'm starting to think that Linux distributions are harder to use than Windows but work better.

---

### Post by ratchetman on 2014-03-08
Thank you all for taking the time to read and respond to my frustrated rant. Some of you have contributed thoughtful and helpful advice which I will look into.

 I was trying to identify physical drives and not logical ones. I tried a windows program and it wanted to know if I wanted an image of "C" "D" etc. That would be useless where I'm working with a bastardized version of xp running on $300 worth of hardware that costs $12,000 to buy and up to $3000 to repair. It has a hidden restore partition and a special MBR. Last time is messed with the MBR this unit had to go to California to get reimaged. My plan is to do my own repairs and having a reliable image of the drive would be the first place to start. 

 I think windows 7 works well for what I need,  I can install steam and play my games. At work we are all in the comfort of the microsoft embrace there. My special tool is one year old and came with xp because it's a cutting edge, top of the line piece of equipment. I would love to invite some people to put it in a warm dark place, but it's the only tool I can use that covers the most applications for the price.

 So all the computers I use apart from my android phone have Windows. I would run Linux at home if it weren't for the gaming. 

 As far as expressing my dislike of ubuntu on a windows forum, I can't see how that would promote any kind of intelligent discussion. I had always hoped that I would find a Linux distro that is intuitive for me to use. I am loosing hope I will find such a thing. I feel like a complete computer retard. I used to like KDE and Windows XP but now we have Unity  and windows 8. Horrible stuff if you ask me. Imagine if we made cars that way. That big ugly steering wheel is cluttering the nice clean dash board we'll move that under the drivers seat. The brake pedal? That was ugly too so we put that in the truck, but you can use a hidden search feature so you can find it. The only control device we think the modern driver needs is a large accelerator pedal in the middle of the floor. This new car goes like hell but heaven help you if there's a bend in the road.

---

### Post by Ubi_one_2014 on 2014-03-09
why not try a Kubuntu Live cd?
then you have kde

---

### Post by The Cog on 2014-03-09
ratchetman:
Have you tried the live CD of Xubuntu, Lubuntu, Kubuntu as several people have suggested?

---

### Post by ratchetman on 2014-03-09
Not yet I'm working on installing an SSD in my scan tool. I'll gladly give all three of those a try, they are new to me.

---

### Post by cariboo on 2014-03-09
@ratchetman, the only reason WIndows seems intuitive to you, is because you have probably been using it all your life. After finally getting tired of solving other peoples problems with Windows, I very rarely use it, and now it seems very unintuitive to me. I do have one system with Windows 7 on it, but I thinks it's been well over a year since I booted into it.

---

### Post by buzzingrobot on 2014-03-10
> **cariboo907 said:**
> @ratchetman, the only reason WIndows seems intuitive to you, is because you have probably been using it all your life. After finally getting tired of solving other peoples problems with Windows, I very rarely use it, and now it seems very unintuitive to me.

Ain't that the truth.  

I bought a new laptop last year.  Windows 8 was preinstalled.  I hadn't used Windows in several years but, for a couple reasons, I gave it a try. Found myself floundering around trying to do anything other than click on the cute little blocks Win8 puts up. Got the thing configured, and ran the updates (about a half-day affair). Had to keep the help file open to figure out how to do most everything. Mourned the absence of virtual workspaces and the need to keep minimizing and un-minimizing windows. And the habit of applications to assume I wanted an icon on the desktop.

After less than a week, I put Linux on the machine. (Font rendering was also awful. Broken. Still don't understand why it's so bad here in 2014. If MS has all those patents that keep FOSS from tweaking font rendering, how come they seem to do such a poor job using them?)

The point is, though, that no computing interface is intuitive.  We need to learn to use them all.  If we need to learn it, it isn't intuitive.

---

### Post by david98 on 2014-03-10
I disagree I love ubuntu with unity it's simple and user friendly once you take the time to learn how to use it. I think if you need icon's for everything any linux distro is not for you just stick to windows that has a pretty user interface and icon's. As people have recommended lubuntu might be more your taste but if you use linux at some point your going to have to type commands and to be quite honest the quickest way to open a terminal is to use short keys ctr+alt+t that is if you are in gui mode but a lot of people like to boot directly to text mode it's a lot faster to do simple task's. Download a few versions play about find one oyu like if not keep paying for your operating system. But if you do take the time to ask people on the forums when you have a problem more often than not your problem will be solved quite rapidly. So don't slander something just because you don't know how to use  it.

---

### Post by PondPuppy on 2014-03-10
> [COLOR=#000000]Mourned the absence of virtual workspaces and the need to keep minimizing and un-minimizing windows.[/COLOR]

Yes. I kept hitting ctrl-alt-arrow on my Windows 7 machine at work, which (by default) flipped the screen 90 degrees. I disabled those Windows keyboard shortcuts after about the third time it happened. You know, I tried a couple of Windows virtual workspace add-ons and neither worked well at all. 

Upshot for me is that Ubuntu is very ergonomic.

---

### Post by deadflowr on 2014-03-11
You don't have to use the search box menu feature, though Ubuntu is very keyboard friendly in that regard.
You can still search for all you apps with nothing but the mouse if you want.
It is a wee bit slower, but doable.
The Unity menu system is divided into several subsections.
The home section, which is the default to open.
Then other subsections, like apps, music,video, folders, etc etc.
If you look at the bottom of the unity menu you'll see several icons, these are those subsection.
By default the unity apps menu system doesn't list apps by category but simply in alphabetical order.
Browsing apps is simple easy to do, just click on installed and all of the apps will be listed.

That said, if you asked if there was a program to view the physical drives connected to your machine, I would have simply stated look for the program called Disks, or in 12.04 release, Disk Utility. 
I gives you a break down of media devices connected to your machine, as well as a breakdown of the partitioning of said devices.

Using Ubuntu is actually a lot easier to do than trying to explain it.
IMHO

---

### Post by mips on 2014-03-11
> **ratchetman said:**
> 
 I was trying to identify physical drives and not logical ones.


To get a list of drives,
```
sudo fdisk -l
```


example,
```
[reon@obelix ~]$ sudo fdisk -l
[sudo] password for reon: 


Disk **/dev/sda**: 232.9 GiB, 250058268160 bytes, 488395055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002c76e


Device    Boot     Start       End    Blocks  Id System
/dev/sda1             63 310394879 155197408+  7 HPFS/NTFS/exFAT
/dev/sda2 *    310394880 349456383  19530752  83 Linux
/dev/sda3      349456384 475285503  62914560  83 Linux
/dev/sda4      475285504 488394751   6554624  82 Linux swap / Solaris

```

/dev/sda would be the physical drive whereas the partitions are /dev/sda1-4.


Want more detailed information about the drive,
```
sudo hdparm -I /dev/sda
```


example,
```
[reon@obelix ~]$ sudo hdparm -I /dev/sda


**/dev/sda**:


ATA device, with non-removable media
    **Model Number:       ST3250310AS                             **
**    Serial Number:      6RY5GMSV**
**    Firmware Revision:  3.AAC   **
Standards:
    Supported: 7 6 5 4 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  488395055
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    device size with M = 1024*1024:      238474 MBytes
    device size with M = 1000*1000:      250058 MBytes (250 GB)
    cache/buffer size  = 8192 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Recommended acoustic management value: 208, current value: 0
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    DOWNLOAD_MICROCODE
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
            Write-Read-Verify feature set
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
    not    supported: enhanced erase
Checksum: correct

```



Don't like the cli? install gnome-disk-utility, gsmartcontrol, gparted and they will also give you useful device information.

---

### Post by Elfy on 2014-03-11
If you have actual support issues then post threads for them.

Thread closed.

---

