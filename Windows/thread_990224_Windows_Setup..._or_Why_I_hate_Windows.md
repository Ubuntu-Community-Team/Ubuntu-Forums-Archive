---
title: "Windows Setup... or Why I hate Windows"
date: 2008-11-22
forum: Windows
---

### Post by Kazade on 2008-11-22
I haven't had to have the misfortune of installing windows for a good few years. But due to some testing I have to do, I've just done it. I thought I'd share my horrible experience with everyone...

Before I start, I'll just mention that this PC is fairly standard. It's a dual core Athlon 64 with an ATI onboard graphics card, and bog standard onboard audio, network etc. The only expansion card is a wireless network adapter.

OK, so I had the following partition layout before I started:
```

Primary: /home
Extended:
      Linux Root partition
      Empty NTFS formatted partition (to install Windows)
      Swap Partition

```
So I got the 64bit edition of XP, put the disc in and got through to the partition selection screen.. so far so good. Next I selected the empty partition, pressed enter and I was greeted with something similar to the following message:
```

To install Windows on the partition you selected setup must write some startup files to the following disk:
xxxxx MB Disk 0 at Id 0 on bus 0 on atapi [MBR]

```

So, Windows won't install unless it can write to the primary partition which is my HOME partition. And it can't write there coz it doesn't understand ext3 (I'm assuming). The only option it gives me is to DELETE my home partition!!!

This meant that the only thing to do is to copy EVERYTHING to an external disk, delete the partitions, recreate them in a way so that Windows can write to the first one!! So I've wasted a couple of hours of my life so far.

Once that was all done (thanks to the GParted livecd!) I put the Windows disk in again. It boots and I can select the partition and it begins copying files.. yay...

Now, anyone that has installed Windows knows that it has to reboot 27 times or something. So when it finished copying the files it tells me to press enter to reboot. A few seconds later I get this message:

```

disk error

```

... OK, so it didn't work. I could boot from the CD, but not the hard disk. So, I go through the whole first part of the setup process once again. This time I format both the primary partition and the install partition with the "slow" option which takes another half an hour of my life. Finally when it reboots the setup continues..

So now I wait a while, fill in the stuff about where I am and my keyboard and everything, setup goes pretty smoothly after this until it reboots again and finally I get into Windows. I have a pretty big monitor (22" widescreen) and a fairly powerful graphics card so do you think:

a.) It chooses a high vesa mode
b.) Installs a driver and chooses the correct mode for my monitor
c.) Sets the resolution to 640x480 and doesn't provide any widescreen modes

I'll give you a clue... it's C.

So I log in, try to up the resolution but there's no widescreen options so everything is squashed. I go to the device manager to see what hasn't been set up...

1. My graphics card
2. My wired network adapter
3. My wireless network adapter (which works out of the box on Ubuntu)
4. My sound card
5. Something called "SM device"
6. Somthing very descriptively called "Unknown device"

So, now I'm in the process of installing Linux so I can download the drivers I need for Windows.

I'm sorry, but the next person to say "Linux isn't ready for the desktop" or "I installed Ubuntu but my wireless doesnt work" is going to get firmly redirected to this post.

Now, I'm going to try and do something more useful with what's left of my day, like stare at a wall or something.

---

### Post by Skripka on 2008-11-22
Yup.


The FUNNY part your leaving out is the adverts for HOW GREAT Windows is and how "secure" it is, how safe and secure IE6 is, etc that flash across your screen during install. :lolflag:


On my desktop box I have 2 internal HDDs and 1 removeable HDD (for backup easy movement of lots of files)--One internal goes to Linux (/root, /media, /swap), the other internal goes to windows--with GRUB living on the linux drive and the linux drive being Primary in boot order in BIOS.  Lots of failsafes-I can lose either OS and not bork anything, I can lose a whoe harddrive-and even 2 in some cases, and not lose anything really.


When I installed XP-nothing worked out of the box.  Wireless, onboard mobo audio, graphics.  All needed drivers.

When I installed Hardy Heron, similar to XP.  Only thing that worked out of the box was onboard mobo audio.

When I installed Ibex....only thing that did not work right away was wireless-which needs Ndiswrapper.  GPU driver was loaded and monitor instantly booted at native resolution, audio worked fine.

---

### Post by steeleyuk on 2008-11-22
Windows is not compatible with your wall. Stop staring at it. :)

---

### Post by prshah on 2008-11-22
> **Kazade said:**
> 
To install Windows on the partition you selected setup must write some startup files to the following disk:
xxxxx MB Disk 0 at Id 0 on bus 0 on atapi [MBR]
[/code]

So, Windows won't install unless it can write to the primary partition which is my HOME partition. 

Not really; Windows needs to set up the MBR; which will not affect either your data or your partition, but will remove GRUB, and thus the ability to boot into Ubuntu.

However, everything else you say stands; I am always surprised how well GNU/Linux handles 95% of hardware just off the live CD. Windows is like a cripple without a crutch until the drivers for everything are installed.

---

### Post by Chame_Wizard on 2008-11-22
I wonder why [IMG]http://i.fok.nl/s/emo.gif[/IMG].

---

### Post by Eisenwinter on 2008-11-22
Linked in my signature.

---

### Post by Kazade on 2008-11-22
> **prshah said:**
> Not really; Windows needs to set up the MBR; which will not affect either your data or your partition, but will remove GRUB, and thus the ability to boot into Ubuntu.

I expected it to wipe out grub. But I assure you it said I had to format the primary partition, infact even when I reorganized the partitions (and still installed to a logical partition) it formatted both the primary one and the one it was being installed to. To be honest, I'm just relieved the pain is over, and now I can begin to move on with my life :)

---

### Post by Yownanymous on 2008-11-22
Windows wants to get rid of the ability to boot into Ubuntu because of Microscum's childish little scheme of having to be the center of attention and the main OS.

Can't wait till Microsoft goes bankrupt, I'll just laugh. Of course I'll likely be a very old man and might cough, collapse and die afterwards.

---

### Post by Eisenwinter on 2008-11-22
> **Yownanymous said:**
> Windows wants to get rid of the ability to boot into Ubuntu because of Microscum's childish little scheme of having to be the center of attention and the main OS.

Can't wait till Microsoft goes bankrupt, I'll just laugh. Of course I'll likely be a very old man and might cough, collapse and die afterwards.
But at least you'll die because of a good cause, laughing at Microsoft.

---

### Post by AlanR8 on 2008-11-22
Oh dear....

My task tomorrow is to do a full XP reinstall on the Wife's Dell Dimension 9600. I did it last about 14 months ago and it was a nightmare! NOTHING worked out of the box, video, sound, network deda deda deda!

Fortunately I have five machines here, all linked to the network so I spend about an hour downloading the drivers from the Dell website and installing them. I had the presence of mind to keep them and last night burned them to a CD so that should save some time!

I'm in absolute agreement that peeps who wine about Linux not being hardware friendly should be referred to this thread. To add to the argument, a week or so after the last XP reinstall, Her In Doors said to me "Why can't I play video files or DVDs"?

WTF? Guess what, by default there were no codecs! Now, where do you go for them?

Linux at least trys to keep everything in one place, the repos.

When 8.10 came out, Kubuntu, having backed up all my files on this Sony laptop, it took about 40 minutes to install and a further 30 minutes to have the machine shared and sharing on the network, fully multimedia enabled and copying back my files.

**L**..ife **I**..s **N**..ice for **U**..sers of **X**..

---

### Post by tsali on 2008-11-22
As Linux Users are so fond of reminding windows users, Windows <> Linux

1) There isn't a stable consumer 64 bit version of Windows that is stable (despite the fact that you can buy one). If you want ease and stability, go with 32 bit.

2) Windows is not designed to be installed on top of linux. Do not expect it to do something it wasn't designed to do.

3) Windows DOES rely on third party drivers. You know this. Additionally, third party support of 64 bit is not as prevalent. You need to at least have your network driver available.

I understand your frustration and experience regularly with unsupported hardware in linux.

Ubuntu IS easier to install (if the hardware is supported), but installing Windows doesn't have to be as hard as you made it on yourself.

My last install of Vista Home Premium 32-bit went very smooth. Yes, It started with 800x600 resolution, but didn't take long for it to find the correct nvidia driver.

Lastly - it's just software. Don't let it get to you like this. I know that's easier said than done.

---

### Post by billgoldberg on 2008-11-22
> **tsali said:**
> As Linux Users are so fond of reminding windows users, Windows <> Linux

1) There isn't a stable consumer 64 bit version of Windows that is stable (despite the fact that you can buy one). If you want ease and stability, go with 32 bit.

2) Windows is not designed to be installed on top of linux. Do not expect it to do something it wasn't designed to do.

3) Windows DOES rely on third party drivers. You know this. Additionally, third party support of 64 bit is not as prevalent. You need to at least have your network driver available.

I understand your frustration and experience regularly with unsupported hardware in linux.

Ubuntu IS easier to install (if the hardware is supported), but installing Windows doesn't have to be as hard as you made it on yourself.

My last install of Vista Home Premium 32-bit went very smooth. Yes, It started with 800x600 resolution, but didn't take long for it to find the correct nvidia driver.

Lastly - it's just software. Don't let it get to you like this. I know that's easier said than done.

After the AVG super screw up, I had to reinstall XP on my Asus Eeepc.

This has to be done from a usb drive, so it's a pain to even get working.

Xp, no matter how many times I partitioned and formatted to ntfs or fat32 refused to install.

It said my drives were damaged.

Ubuntu 8.10 installed without problems.

So yes, there is a problem.

---

### Post by BlueSkyNIS on 2008-11-22
@OP 

I understand you completely, I had a similar situation last week with my PC. I wasted a whole day setting up XP. I hated it so much...

---

### Post by tsali on 2008-11-22
> After the AVG super screw up, I had to reinstall XP on my Asus Eeepc.

This has to be done from a usb drive, so it's a pain to even get working.

Xp, no matter how many times I partitioned and formatted to ntfs or fat32 refused to install.

It said my drives were damaged.

Ubuntu 8.10 installed without problems.

So yes, there is a problem.


Are you using the Asus restore instructions?

---

### Post by AlanR8 on 2008-11-22
Am just about to start the XP install now.....a few glasses of red gives courage!

---

### Post by billgoldberg on 2008-11-22
> **tsali said:**
> Are you using the Asus restore instructions?

Nope.

I don't do instructions.

---

### Post by lisati on 2008-11-22
I'm thankful that my Compaq desktop came with a recovery partition, and my older laptop came with a customized recovery DVD, both of which have the necessary drivers for the relevant machine. The down side is that some things (e.g. running FIXMBR and other related stuff when the MBR or partition tables get messed up) are sometimes more easily done from a proper Windows disk.....

---

### Post by toupeiro on 2008-11-22
> **billgoldberg said:**
> Nope.

I don't do instructions.

lol um... then the problem may not be XP here? ;)

If you didn't put together the hardware, you shouldn't assume the software will work as if you did.

---

### Post by billgoldberg on 2008-11-22
> **toupeiro said:**
> lol um... then the problem may not be XP here? ;)

If you didn't put together the hardware, you shouldn't assume the software will work as if you did.

Sure the problem is xp.

I had a windows xp cd laying around and tried to install it, but it failed.

I know they use a special xp edition, but the only way to get it on my pc is to send it to Asus and let them put it on it.

Ubuntu installed fine.

---

### Post by AlanR8 on 2008-11-22
I am in so much sh*te here!!!!

The Dell CD won't copy all the files. Looking at it there are some scratches. So I went to my regular XP Pro CD and started the process again, having already formated the disk.

The FFing keyboard is not recognised! Tried a licensed copy of XP Home with the same result.

8.10 is loading as we speak......she will probably NEVER speak again.

Nice to know you guys, I'll probably be dead in the morning.:):)

Or I could go to PC World and get a new keyboard before she gets out of bed!:lolflag:

---

### Post by toupeiro on 2008-11-22
> **billgoldberg said:**
> Sure the problem is xp.

I had a windows xp cd laying around and tried to install it, but it failed.

I know they use a special xp edition, but the only way to get it on my pc is to send it to Asus and let them put it on it.

Ubuntu installed fine.

....

if you KNOW they use a special xp edition, why would you blame the xp CD you have laying around if its not a copy of that special XP edition??

its a plus that ubuntu installs fine on it, but think of how OLD xp is compared to the version of ubuntu you are installing, and think of how NEW the eeePC is...  Sorry, I don't think you can really blame XP for that one...  You know what you have to do to fix it, you're just upset that your old XP CD can't get it done, but thats not the fault of that old XP cd.  It can't auto-update itself to support all the new goodies that are available. :)  The problem is that Mirosoft flopped on XP's successor, so you have to use a very old OS on devices like this if you want to use a Microsoft OS, and that OS is so old now that it can't work out of the box on brand spanking new hardware.  Don't fool yourself though.  Get a Linux OS CD as old as XP, and it couldn't install either I'm willing to bet. :P

---

### Post by init1 on 2008-11-22
Yeah, I tried installing XP on my laptop last year, but it complained that it couldn't find any hard drives. Apparently, the installer doesn't support SATA. You would think that the installer for the most commonly used desktop OS would include drivers for something as common as SATA, but apparently not. 
A little later, I figured out that SATA can be disabled in the BIOS. So, I tried to install it again. It installed, but gave me errors when I tried to boot it.

---

### Post by Hyper Tails on 2008-11-24
I once Had to delete ubuntu off my pc just to install vista on my pc to dual boot

Is it just me or is vista greedy for space on the harddrive?

---

### Post by tsali on 2008-11-24
> Is it just me or is vista greedy for space on the harddrive?


It's just you. Windows is simply not designed to be installed second in a dual boot system. It is unreasonable to expect that it will. It is not a vast conspiracy.

In the same way, Windows will not install properly on a hard disk that had previously had grub installed on the MBR.

---

### Post by Giant Speck on 2008-11-24
> **tsali said:**
> It's just you. Windows is simply not designed to be installed second in a dual boot system. It is unreasonable to expect that it will. It is not a vast conspiracy.

I knew this.

> In the same way, Windows will not install properly on a hard disk that had previously had grub installed on the MBR.

But I didn't know this.  Does GRUB screw up the MBR or damage it in some way? Is there some way to fix it?  And what does this mean if I ever want to upgrade to Windows 7?

---

### Post by Bibek on 2008-11-25
The fact is that if you get used to using linux it is a very difficult transition to windows. First, you have to have the drivers for almost everything ready. I have a desktop that i built myself and if I install linux there, I can get it working in no time. The graphics card, monitor etc etc all work out of the box. But if i have to install windows in that computer, i need chipset driver, graphics driver, sound driver , monitor driver, ethernt driver and what not. also, you have to install antivirus, antispyware, firewall etc etc. And the good softwares cost $$$. People who say that their hardware is not supported by linux dont understand the fact that hardware is not supported by windows as well. Its just that the device maufacturers provide drivers for windows but they dont for linux.

---

### Post by tsali on 2008-11-25
> But I didn't know this. Does GRUB screw up the MBR or damage it in some way? Is there some way to fix it? And what does this mean if I ever want to upgrade to Windows 7?


It's a pretty easy fix. You can use FIXMBR if you have it available OR you can clear the MBR using "dd" on a live linux CD like Knoppix. Once the MBR is clear, Windows will install normally, then you can install Ubuntu again.

I would expect that Windows 7 upgrade will look for a standard Vista or XP bootloader. Could be an issue.

---

