---
title: "Planning to move from windows 7 to Linux, some basic questions."
date: 2020-10-23
forum: Ubuntu, Linux and OS Chat
---

### Post by wugubee on 2020-10-23
I have Lenovo E450, i5-5200u, 2.2 Ghz, 16 GB RAM, and spinning HDD,

with 2 partitions, both on NTFS,
First one is for OS, and non portable programs such as office, vmware workstation pro, printer driver, free comodo internet security...
The other is for DATA, and all my portable programs, PDFs, office files, so on, it has 66% usage of total 851 GB, so alot of stuff and archive,

I put it that way, with old reason, that if somehow the OS part is screwed, than I simply recopy image of main partition,

I feel now the laptop is getting old each day, and considering to move to Linux,

1. What is the best way to move or migrate? Mostly, I just worry with my data from this windows world
2. What if I want to use native linux filesystem for both partition?
3. If somehow Im forced to stay with NTFS for data partition, is there any drawbacks, may be security reasons?
4. Security software, are they needed in linux world? Im using the laptop as desktop environment
5. How am I supposed to have peace of mind as desktop user, **while usually in windows world i just assume the security software will do the job for me? we know linux is not 100% secure right...**
6. Where is **technical detail comparison** of Ubuntu flavors? Which one is the fastest but still give flexibility when I want/need to?

I dont like dual boot option, Im just gonna go ahead with the move, just want to make sure, no problem with the move to different world,

Thank you so much,

---

### Post by mikewhatever on 2020-10-23
1. Not sure what's best or second best ..., does it really matter? As you don't want to dual boot, the way forward is to remove and install. Backup all important data to an external device.
2. You can, but the installer will make its own partitions, so I'd say, backup all important data to an external device, and give Ubuntu all the HDD space.
3. This makes most sense when dual booting. Either way,you can.
4. & 5. [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812) There is lots more on the topic.
6. All official Ubuntu flavors have the same base system, but different GUIs and programs, aka DEs (Desktop Environments). So, technically, all have the same kernel/library versions, same drivers, same hardware detection scripts, etc. Ubuntu, as other Gnome3 distros tend to use more RAM, but that should not be a problem with 16GB. All are pretty fast and flexible, however relative it may be. You'll need to do some homework to pick the one you like best. [https://distrowatch.com/](https://distrowatch.com/) is a good resource for reviews.

PS: You should probably expect problems when moving to a "different world". Naturally, there is a learning curve, but we are here to help.

---

### Post by oldfred on 2020-10-23
Was this a Windows 8 system downgraded to Windows 7?
It looks like it has specs that are newer and would be UEFI with gpt partitioning.
But Windows 7 usually was installed in BIOS boot mode with MBR(msdos) partitioning.
But Microsoft required vendors to install Windows 8 starting in 2012  in UEFI/gpt.

Also check if you have UEFI update.
Best not to keep NTFS partition unless dual booting as it need maintenance like chkdsk or defrag that cannot be done from Linux.

[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

Comparison of desktop environments - diffences in software
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
[http://www.makeuseof.com/tag/gnome-based-desktop-environments-explained-mate-vs-gnome-shell-vs-unity-vs-cinnamon/](http://www.makeuseof.com/tag/gnome-based-desktop-environments-explained-mate-vs-gnome-shell-vs-unity-vs-cinnamon/)
Screenshots
[https://en.wikipedia.org/wiki/Desktop_environment](https://en.wikipedia.org/wiki/Desktop_environment)

If then doing newer UEFI install, see link below in my signature.
Lots of info and links to even more. Not all applies, so skim read those parts otherwise too much for new user.

---

### Post by TheFu on 2020-10-23
> **wugubee said:**
> I have Lenovo E450, i5-5200u, 2.2 Ghz, 16 GB RAM, and spinning HDD, with 2 partitions, both on NTFS,
First one is for OS, and non portable programs such as office, vmware workstation pro, printer driver, free comodo internet security...
The other is for DATA, and all my portable programs, PDFs, office files, so on, it has 66% usage of total 851 GB, so alot of stuff and archive,

[https://www.cpubenchmark.net/mobile/cpu.php?cpu=Intel+Core+i5-5200U+%40+2.20GHz](https://www.cpubenchmark.net/mobile/cpu.php?cpu=Intel+Core+i5-5200U+%40+2.20GHz) says this system has a passmark of about 2500. This should be fine for non-Gnome3 use. You can do virtualization on it, but only a few VMs concurrently. With linux, you'd probably want to use virtualbox.
Make a list of all your programs and rank them in terms of mandatory vs close-enough solutions.  For example, running MS-Office is a PITA under an emulator and often doesn't work perfect.  OTOH, if you can use LibreOffice and be happy, then none of this matters.
There is little cause to run any AV suite.  The OS design is different enough that unless you have a habit of clicking lots of unknown attachments and visiting the seedier parts of the Internet, then it just isn't needed.  MS-Office Macro viruses don't work on LibreOffice.

> **wugubee said:**
> 
I put it that way, with old reason, that if somehow the OS part is screwed, than I simply recopy image of main partition,


You don't want to use NTFS, if it can be avoided.  The OS and HOME directories cannot have NTFS as a file system. Those must be native Linux file systems, period.

> **wugubee said:**
> 
I feel now the laptop is getting old each day, and considering to move to Linux,

It isn't the slowest that people here use. I have 3 laptops. Passmark 7600 ($305 used Win10-wiped), 3300 ($430 new chromebook), and 1450 ($212 new chromebook). I'd love for the fastest machine to be in the middle-performance case. I always use a lite desktop, so all of these performed fairly well.

> **wugubee said:**
> 
1. What is the best way to move or migrate? Mostly, I just worry with my data from this windows world

Backup everything you cannot lose. Do not skip this. It is very common for people new to Linux to accidentally format and wipe all the storage.  The backup storage needs to be 100% disconnected from the machine. In a few years, when you are better at Linux, you'll be able to safely do lots of stuff without these concerns, but there aren't any automatic protections against foolishness or stupidity. The system will do what you tell it to do, even if that is to wipe all data everywhere.  The terminology is different enough that you may not understand and may allow it.

> **wugubee said:**
> 
2. What if I want to use native linux filesystem for both partition?

There is no migration.  Backup the data, format the partition to a native Linux file system, then restore the data.  Windows won't be able to access it at this point, except through some file sharing protocols over the network.  The claimed drivers for Windows to access ext2/3/4 stuff don't have the best reputation. But I've never used those.

> **wugubee said:**
> 
3. If somehow Im forced to stay with NTFS for data partition, is there any drawbacks, may be security reasons?

Yes. There are lots of drawbacks. That's a huge question, best asked alone.

> **wugubee said:**
> 
4. Security software, are they needed in linux world? Im using the laptop as desktop environment

Nothing replaces a smart user, making good choices.  The only times I run AV on my systems is when a contract mandates it. Had a client who required professional E&O insurance. That insurance policy mandated running current, patched, AV software on all systems, so we did. Violating an insurance policy is a good way to have claims denied.  I do run AV on my email server, but not on any desktops or other servers.  I do not run any AV or security suite on my Windows systems either, but those are blocked from 99.999999999% of internet access at the firewall. They are only allowed to pull stock quotes down from 1 specific internet domain. I don't have email programs on them.

> **wugubee said:**
> 
5. How am I supposed to have peace of mind as desktop user, **while usually in windows world i just assume the security software will do the job for me? we know linux is not 100% secure right...**

No OS is 100% secure.  On Windows, the best security software was found to be only 50% effective, so you had a false sense of security. With Linux as a desktop, the most likely issues for someone new will be self-inflicted due to ignorance.

> **wugubee said:**
> 
6. Where is **technical detail comparison** of Ubuntu flavors? Which one is the fastest but still give flexibility when I want/need to?
 How can we know what you want/need?  On your system, I'd choose Ubuntu-Mate or Xubuntu. That is mainly due to the CPU performance. You can load whatever software you like.  The core kernel isn't any different between Ubuntus, including the "server" version. If you want to do "server" things later, you can just load the package and use it.

> **wugubee said:**
> 
I dont like dual boot option, Im just gonna go ahead with the move, just want to make sure, no problem with the move to different world,

There will be problems.  I'd really recommend that you run a few different Ubuntus inside a VM on your current system for a month each to get a feel first. When you do that, work through your list of programs needed, seek out native Linux alternatives, learn more about the OS.

Linux isn't Windows.  If you've only used Windows, be ready for culture shock.  Things do not work the same way. There are vastly different OS design choices that you've always assumed everyone else follows.  But remember that all the most popular OSes in the world used today are based on Unix and the Unix philosophy, except 1.  That 1 is MS-Windows.  After a few years in the Linux/Unix world, you'll find Windows extremely frustrating, but for the first 6 months using Linux, if you are like most people, including me, you'll get really frustrated.  I've been a Linux user since 1993.  It is 1000x easier today than it was back then.

Read this: [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed) 
It has a link to a 2014 primer that is still relevant for the main differences between Windows and Linux. 
The next link is to start thinking the Unix way, not the Windows way.  One of comments there captures this migration you are planning.
> "Coming from Windows, I found Linux is ‘hard’. Soon, I just realized it is not, it’s just different, and in a way much better."

Hopefully, you can find a local LUG - Linux Users Group - to get personalized help.  With the pandemic, many of these groups have moved online, so anyone from anywhere in the world can join, share, learn.  My LUG has seen people from all over the USA joining the last few months.

---

### Post by wugubee on 2020-10-25
My laptop is fresh install from Windows 7,
I do have CentOS/Red Hat experience, so Linux is not new to me,
but for desktop I only try this and that, and use a bit of it like Kali, Tiny Core Linux, Alpine,

I do want CentOS to be my desktop, since my work will always related to it, but I guess the repo packages is not massive as Ubuntu, is this correct?
we need massive support of packages and software (free/commercial) to support desktop work right?

Well to me this laptop is slow, may be because of this Windows 7 is plaguing the system? :D
I ordered Sandisk SSD 3D Ultra Sata 3 1TB and USB to Sata 3 adapter, so now backup plan is solved,
I have not browse around software replacement, but I have a strong feeling the answer will be VirtualBox, LibreOffice, 
I know ESXi, and in near time I plan to move my office servers into XCP-ng, so hopefully desktop virtualization software that Im going to use, will be in sync (not much hassle) and compatible with both mentioned,

I think Im gonna go for latest Lubuntu with its default desktop,

THANKS FOR ALL OF REPLIES!!

---

### Post by The Cog on 2020-10-25
TheFu said this:> There will be problems. I'd really recommend that you run a few different Ubuntus inside a VM on your current system for a month each to get a feel first. When you do that, work through your list of programs needed, seek out native Linux alternatives, learn more about the OS.

Linux isn't Windows. If you've only used Windows, be ready for culture shock. Things do not work the same way. There are vastly different OS design choices that you've always assumed everyone else follows. But remember that all the most popular OSes in the world used today are based on Unix and the Unix philosophy, except 1. That 1 is MS-Windows. After a few years in the Linux/Unix world, you'll find Windows extremely frustrating, but for the first 6 months using Linux, if you are like most people, including me, you'll get really frustrated. I've been a Linux user since 1993. It is 1000x easier today than it was back then.
I strongly agree - it is well worth repeating. Except that maybe a month is outside your patience limit. As a minimum, try the live installer for an hour or so for the most popular desktops, just so you have a vague idea what the options look like. You will be surprised how different they all are. And different people have different preferences, sometimes quite passionately so.

One problem with the culture shock is that people tend to find lots of things that they can't do the way they used to in Windows quite quickly. It takes somewhat longer to pick up the things that you can do much more easily, one by one as you get familiar with the system. And there is a whole way of thinking about what goes on underneath that has a different approach.

That said, I think it is well worth learning Linux, whichever desktop you choose. Don't let me put you off. Just don't expect to become fully familiar in a month.

---

### Post by TheFu on 2020-10-25
CentOS is a server.
Use Fedora if you want an RPM desktop or perhaps Scientific Linux.
Win7 can't slow down Linux, unless it is the hostOS for a hypervisor.

I would strongly recommend trialing XCP-ng and KVM+Libvirt before deciding.  We used Xen for a few years and had stability issues from time to time. After switching to KVM+libvirt, no stability issues.  Plus, if you intend to run desktops inside the VMs, you really want the SPICE display option. Local or over the network, SPICE is crazy fast.

---

### Post by helen314 on 2020-10-29
I have Lenovo E450, i5-5200u, 2.2 Ghz, 16 GB RAM, and spinning HDD,
with 2 partitions, both on NTFS,

After so many detailed suggestion I really feel your primary objective should be - KISS 

With assumption that you want to ditch Windows and use Linux as SINGLE OS , not multiboot ( ! KISS) ,
and since you are in Ubuntu forum  I would suggest this:

Invest in  few , cheap, USB sticks of capacity co-measurable with you spinning HDD.
Copy , no "backup",  your HDD . However, if you desire to be safe - use different methods , even Window copy / backup.

Download your favorite version of Ubuntu ISO onto USB stick ( 2 GB size stick is plenty ) . I will refrain from suggesting the "latest and greatest "  version - but it is your choice.

If you really want to live dangerously - before you progress from here - make sure you  have minimum of  8GB empty , unallocated space on your HDD..
This is important step if you decided to try installing Ubuntu as multboot. 

But it has MAJOR caveat - you cannot change "partition type" , not without wiping the entiure disk! 

But you can try multiboot  and see how it works for you even when using "old style" partition type. 
(Since your were happy with TWO partitions you really do not "need" GPS - again KISS ) 



Insert the Ubuntu USB ISO stick , reboot and "follow instruction" BUT choose "try Linux / do not install "  - you have better control of what is coming next.
If you are lucky - you MAY get to choose " install Ubuntu alongside of Windows"   

Now the ball is in your court and you have to CHOOSE....

---

### Post by mastablasta on 2020-10-30
1. What is the best way to move or migrate? Mostly, I just worry with my data from this windows world
[COLOR=#ff0000]Get an external drive and backup the data to it. 1 TB spinning drives are about 50 EUR now.[/COLOR]

2. What if I want to use native linux filesystem for both partition?
[COLOR=#ff0000]you need to format both, erasing any data on them. this is not an issue if you have backups made.[/COLOR]

3. If somehow Im forced to stay with NTFS for data partition, is there any drawbacks, may be security reasons?
[COLOR=#ff0000]you can't fix the NTFS partition with linux tools, if something happens on it (e.g. hard reboot corrupts it), you need windows tools to fix it. i think oyu can use freeDOS on USB stick as well to do the fix.[/COLOR]

4. Security software, are they needed in linux world? Im using the laptop as desktop environment
[LIST]
[*][COLOR=#ff0000]UFW (gUFW) firewall is built in system.
[/COLOR]
[*][COLOR=#ff0000]don't open any ports without securing them, by default all are closed (in windows some are open).
[/COLOR]
[*][COLOR=#ff0000]You can use antivirus but most detect windows malware.
[/COLOR]
[*][COLOR=#ff0000]since you download software form trusted and vetted source only (software center), the only entry point is browser. install script blocker and only allow trusted sites to run scripts. also browsers are same in win7 and linux (except for explorer)
[/COLOR]
[*][COLOR=#ff0000]if you move laptop around and you take it to other places, then a full disk encryption is a must. you can do it at install.
[/COLOR]
[/LIST]
[COLOR=#ff0000]
most people don't run anything extra. but if you want to you can harden the system so much that even North Korea will have a tough time breaking in. but your user experience will suffer. see ubuntu hardening for more information.[/COLOR]

5. How am I supposed to have peace of mind as desktop user, [B]while usually in windows world i just assume the security software will do the job for me? we know linux is not 100% secure right...

[/B][COLOR=#ff0000]malware scanners are also not 100%. they are more closer to 95%. best free one is windows 10 built in one (security essentials). but it still doesn't prevent the breach. if you want sandboxing an jails there are containers and snaps (sand boxed applications) for that. 

For example Avast is one of my favourites on windows:
[/COLOR][TABLE="width: 373"]
[TR]
[TD="align: left"][COLOR=#ff0000]Antivirus[/COLOR][/TD]
[TD][COLOR=#ff0000]OFFLINE[/COLOR][/TD]
[TD][COLOR=#ff0000]ONLINE[/COLOR][/TD]
[TD][COLOR=#ff0000]ONLINE[/COLOR][/TD]
[TD][COLOR=#ff0000]FALSE[/COLOR][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][COLOR=#ff0000]Detection Rate[/COLOR][/TD]
[TD][COLOR=#ff0000]Detection Rate[/COLOR][/TD]
[TD][COLOR=#ff0000]Protection Rate[/COLOR][/TD]
[TD][COLOR=#ff0000]Alarms[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000]Avast[/COLOR][/TD]
[TD][COLOR=#ff0000]92.0%[/COLOR][/TD]
[TD][COLOR=#ff0000]99.4%[/COLOR][/TD]
[TD][COLOR=#ff0000]100%[/COLOR][/TD]
[TD][COLOR=#ff0000]10[/COLOR][/TD]
[/TR]
[/TABLE]
[COLOR=#ff0000]
Bt defender which normally has good detection rate (95%) has a linux version

Linux has many security layers built in by default. you will see them once you install the system. it's juts layer upon layer and they all add up. usually the O Sis not the issue, the user is.

major banking, various large company ERP sytems google, facebook... they all run on linux. so something must be right.[/COLOR]

6. Where is **technical detail comparison** of Ubuntu flavors? Which one is the fastest but still give flexibility when I want/need to?

[COLOR=#ff0000]Distrowatch website has very good overview of individual OS: various linux distributions (Ubuntu, Mint, CentOS, Debian, OpenSUSE...), various BSD distributions (FreeBSD, OpenBSD), and other OS such as  reactOS and specialised OS that is broderline firmware (like to run routers)... you can compare them and they also provide links to trusted OS reviews (they do some themselves).  
From user standpoint dedoimedo website has good reviews, but he is often a bit harsh. but then again sometime sou have to push for a change and praising a badly built version won't bring any progress.

Personally i landed on Kubuntu (ubuntu with KDE desktop). it is fast, does what i need it to do, is easy to configure and my dad and my wife had no trouble switching to it from windows. last year i moved my final PC (16 year old single core) from XP to Kubuntu. before it took 10 minutes to boot to a usable state (load antivirus&comodo). now it takes 45 seconds to boot. firefox, open office... everything loads faster than it did on windows, 4GB in the PC is utilised properly and the os is 64 bit. i play most games i played before on XP and i added some new ones. including CS:GO. system uses less than 450 MB ram at boot. windows used over 1 GB to load all the stuff.[/COLOR]

> **wugubee said:**
> 
I dont like dual boot option, Im just gonna go ahead with the move, just want to make sure, no problem with the move to different world,

run it live, try it out. you can use a cheap USB and load multiple distributions on it using Yumi or similar multiboot application. Yumi: [https://www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)


finally [COLOR=#ff0000]**do a full backup**[/COLOR] before any changes. i suggest a disk image, in case you want to go back to windows.

---

