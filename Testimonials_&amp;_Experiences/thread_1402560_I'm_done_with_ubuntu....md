---
title: "I'm done with ubuntu..."
date: 2010-02-09
forum: Testimonials &amp; Experiences
---

### Post by serpentracer on 2010-02-09
ok gang this is the last straw...ubuntu has crashed several times now on me with major system failure problems.   my files system keeps getting all messed up.  
and several other oddities that are highly annoying.
I'm going back to windows.  you guys enjoy linux. 

I've never had this kind of problem from this computer from windows.

---

### Post by Nunu on 2010-02-09
Hi serpentracer, 

I am sorry that you have had such a bad experience using linux. 

I just need to ask if you happened to come across a trend that could cause your system to go bad? If I could state my question a bit differently did you notice specific things like plug and play hardware or anything along those lines?

---

### Post by kellemes on 2010-02-09
> **serpentracer said:**
> I've never had this kind of problem from this computer from windows.

Computer is probably made for Windows.

---

### Post by timgood on 2010-02-09
> **kellemes said:**
> Computer is probably made for Windows.

User most certainly is.

---

### Post by howefield on 2010-02-09
> **timgood said:**
> User most certainly is.

How cruel, but I can't resist a smile. Just a brief one.

@OP, seeing as you posted in "General Help", do you want any, or is this a thread for Testimonials & ect ect. ?

---

### Post by El Zoido on 2010-02-09
Am I the only one with a sense of Déjà-vu here?

---

### Post by serpentracer on 2010-02-09
it's a built computer it's not from a company like compaq/hp etc.

so it's not specifically for windows etc.

while I'm using it it will randomly freeze and nothing responds.  then I get messages popping up with all 0000000 and no words.  it will not shut down so I am forced to shut it down manually.

this is what come back when I turn it back on,

[IMG]http://farm3.static.flickr.com/2784/4342923235_0483855bec_o.jpg[/IMG]

---

### Post by serpentracer on 2010-02-09
you guys can make wise cracks all you want,  the simple fact is, I didn't cause this problem.  ubuntu has done it all on it's own...something windows has never done.  I've never even had the blue screen of death from windows xp or vista.
this ubuntu on the other hand cant even maintain it's file system properly without destroying my hard drive in the process. it just randomly started this last night.

I've had more problems in 5 days using ubuntu than in 8 years using xp pro.  and it's all ubuntu's errors. not something I did.

[IMG]http://farm5.static.flickr.com/4067/4342923335_ff12e10e97_o.jpg[/IMG]

---

### Post by stoneage on 2010-02-09
You say you built it yourself, can you list the hardware? If it is very recently released it could be something is unsupported by the default install.

---

### Post by auh2o on 2010-02-09
You can get some very good help here at these forums, so I urge you to not give up without a fight! 

Also, if you have major problems, at least try a clean reinstall before giving up. Something might've gotten seriously messed up the first time for some reason or another.

Personally I really like Ubuntu, and think it is better than Windows in almost every way. I installed it in a dual boot setup when I got Windows 7, thinking I should finally give Linux a try and that it would be my backup OS. Instead, I've found myself hardly using Windows 7 at all! Good riddance!

---

### Post by Calmor on 2010-02-09
Can you tell us a little about what you're running (Ubuntu release, filesystem, etc)?

fdisk -l from that root prompt should give you the filesystems on your drive

Did fsck run, and if so, any errors?

---

### Post by NFblaze on 2010-02-09
I dont think he can even boot it.Lol

Though, yea if you have the newest hardware, full support might not be in the kernel yet, but you did try it with the LiveCD first right?

So, what are you going to do if you go back to say Windows XP and it does the same? Are yo going to install a different version of Windows...like Windows Vista or Windows 7? What I mean is maybe you try a different version of Linux.

---

### Post by davidmb on 2010-02-09
Yes, and it wouldn't be the first time either if he eventually comes back saying it was a **hardware failure**.

---

### Post by serpentracer on 2010-02-09
> **stoneage said:**
> You say you built it yourself, can you list the hardware? If it is very recently released it could be something is unsupported by the default install.

oh it's def older equipment. I think I bought it all in 2003.

shuttle av41p mother board
don't recall name brand of memory 1 gig
wd 160 gig hard drive (actually this is about 2 years old)
pentium 4 2.66 ghz processor
ATI radeon 9000

ubuntu 9.10

---

### Post by serpentracer on 2010-02-09
> **Calmor said:**
> Can you tell us a little about what you're running (Ubuntu release, filesystem, etc)?

fdisk -l from that root prompt should give you the filesystems on your drive

Did fsck run, and if so, any errors?

I posted a pic of just some of the fixes fsck was performing.

it was able to fix them all as it did the first time this same thing happened.  so this is the 2nd time I've gotten this problem.
it just started this yesterday.

---

### Post by Calmor on 2010-02-09
With such limited info, I'm guessing it's a potential filesystem issue (ext4, using a Windows ext2 driver on an ext3 filesystem, or possible power-off corruption and no fsck run to fix it) or a hardware issue.  I'd try a clean install with ext3 and avoiding any file system access from Windows/VirtualBox for a while.

---

### Post by El Zoido on 2010-02-09
Ok, as it seems you may indeed be interested in getting help I would probably go for a reinstall. Maybe something got messed up during install (this may even happen with windows, although it did happen for me only with Ubuntu so far ;) ).

If thats not fixing it and supposing you aren't using any exotic hardware here, maybe some component broke down after you installed Linux, which would be most likely purely coincidential.

---

### Post by lykwydchykyn on 2010-02-09
The error means that the bootloader is having trouble locating your root partition, and the subsequent errors seem to indicate filesystem corruption.

I would suspect a bad hard drive, and even if you decide not to stick with Ubuntu you'd be well advised to scan the disk for bad blocks.  Windows isn't going to be happy with a dying hard drive either.

If you don't have a utility to scan with, you can boot to the Ubuntu disc and run this from a command line:
```

sudo badblocks -v /dev/sda

```

---

### Post by serpentracer on 2010-02-09
> **NFblaze said:**
> I dont think he can even boot it.Lol

Though, yea if you have the newest hardware, full support might not be in the kernel yet, but you did try it with the LiveCD first right?

So, what are you going to do if you go back to say Windows XP and it does the same? Are yo going to install a different version of Windows...like Windows Vista or Windows 7? What I mean is maybe you try a different version of Linux.

I've downloaded suse 11.2 and the latest fedora..might give them both a try first.
I really like this ubuntu but for some reason it keeps crashing HARD.
I thought linux wasn't supposed to crash at all from what people keep telling me.
it for sure does.

---

### Post by Calmor on 2010-02-09
> **serpentracer said:**
> I posted a pic of just some of the fixes fsck was performing.

it was able to fix them all as it did the first time this same thing happened.  so this is the 2nd time I've gotten this problem.
it just started this yesterday.

Did you start doing anything yesterday that was different?  Any upgrades, program installs, changes to any system files, install Windows on another partition, resize the filesystem, etc?

I've heard rumors that ext4 doesn't take too kindly to resizing...

---

### Post by El Zoido on 2010-02-09
> **serpentracer said:**
> 
I thought linux wasn't supposed to crash at all from what people keep telling me.


In a perfect world maybe ;)

In my experience Linux either works, in which case you will have a pretty stable system for ages or it causes problems right from the start, in which case the only solution may be using a different version/release.

---

### Post by Calmor on 2010-02-09
> **serpentracer said:**
> I've downloaded suse 11.2 and the latest fedora..might give them both a try first.
I really like this ubuntu but for some reason it keeps crashing HARD.
I thought linux wasn't supposed to crash at all from what people keep telling me.
it for sure does.

Anything will crash given the right circumstances.  I used a Mac for about 8 hours before I needed to kill something off.  Granted, I didn't see a crash of this magnitude, but it was a program crash nonetheless.  And an Apple program at that, not third party. (might have even been the mighty iTunes)

Linux is highly resilient and in many cases will run for years and years without the need for as much as a reboot... but there are some cases where it will go down.  I'd say in my experience it's been far less than Windows.

---

### Post by lykwydchykyn on 2010-02-09
> **serpentracer said:**
> I've downloaded suse 11.2 and the latest fedora..might give them both a try first.
I really like this ubuntu but for some reason it keeps crashing HARD.
I thought linux wasn't supposed to crash at all from what people keep telling me.
it for sure does.

If my suspicions are correct, any OS would crash.  

Even if not, every OS can come to a halt at some point.  Bugs are just an inevitable part of fallible humans writing software and breakable hardware running it.

Use Linux because you like it, not because it's some magical shangri-la operating system that never has problems.  It has problems, like everything else.

---

### Post by cascade9 on 2010-02-09
> **davidmb said:**
> Yes, and it wouldn't be the first time either if he eventually comes back saying it was a **hardware failure**.

That is what I am thinking it could be. I've seen bad controllers, and a few other things, make just this sort of mess with linux and windows. Of course, its always possible that ubuntu has made a right mess of things. 

@serpentracer- you could try running a HDD diagnostic test, some of them will show up any errors in the controller as well as the actual drive. If you do end up putting windows back on, good luck, hopefully for you I'm wrong.

---

### Post by serpentracer on 2010-02-09
> **lykwydchykyn said:**
> The error means that the bootloader is having trouble locating your root partition, and the subsequent errors seem to indicate filesystem corruption.

I would suspect a bad hard drive, and even if you decide not to stick with Ubuntu you'd be well advised to scan the disk for bad blocks.  Windows isn't going to be happy with a dying hard drive either.

If you don't have a utility to scan with, you can boot to the Ubuntu disc and run this from a command line:
```

sudo badblocks -v /dev/sda

```

I'll give that a try, but my hard drive has S.M.A.R.T  and my bios checks it's status on start up and says it's fine.  the last time my hard drive failed, the bios stopped and said "hard drive failure is eminent"  

I'll run my disc utilities disc that came with my hard drive to find out for sure.

---

### Post by serpentracer on 2010-02-09
> **Calmor said:**
> Did you start doing anything yesterday that was different?  Any upgrades, program installs, changes to any system files, install Windows on another partition, resize the filesystem, etc?

I've heard rumors that ext4 doesn't take too kindly to resizing...

installed firefox 3.6.   the updates were installed on thursday or friday last week.

---

### Post by serpentracer on 2010-02-09
I'm going out to play in the snow....and run some drive testing...I'll report back later today.

---

### Post by cascade9 on 2010-02-09
> **serpentracer said:**
> I've downloaded suse 11.2 and the latest fedora..might give them both a try first.
I really like this ubuntu but for some reason it keeps crashing HARD.
I thought linux wasn't supposed to crash at all from what people keep telling me.
it for sure does.

It will crash, for sure. I started using linux distros as a 'tester' OS for hardware that windows (9x and NT) would crash/BSOD on constantly. Linux in general is far less crashable than windows is, but it even a super-stable OSes will crash on dodgy hardware.

---

### Post by Alexandre Putt on 2010-02-09
> **serpentracer said:**
> 
I thought linux wasn't supposed to crash at all from what people keep telling me. it for sure does.

It's not a crash as such. The system is operating and telling you that something is wrong and it's not able to fix it. Actually having a trap screen of some sort is better than not having one and getting your data corrupted in an unnoticed way.

This is certainly a hardware failure imo. Did you expect that the system will work fine when the hardware does not? A good system has the means to expose you to the problem. It does not imply you will be able to fix it in any situation. 

And I wouldn't rely very much on BIOS messages. You should also run a full memtest.

---

### Post by davidmb on 2010-02-09
> **serpentracer said:**
> I'll give that a try, but my hard drive has S.M.A.R.T  and my bios checks it's status on start up and says it's fine.  the last time my hard drive failed, the bios stopped and said "hard drive failure is eminent"  

I'll run my disc utilities disc that came with my hard drive to find out for sure.

Seriously speaking, it really looks like a hardware failure.
However, it could be not HDD related: I once had a computer that kept throwing disk errors with 3 different hard drives, until I found out it was a broken RAM module!
Try to run a memtest from the GRUB menu or LiveCD.

---

### Post by bonevg on 2010-02-09
If it was me on your place Id put some effort towards solving the problem.. after all.. so many people responded to your desperation.

Did it ever occur to you the problem is not in "the linux" itself but maybe your approach ?

I am interested in if your PC keeps crashing under Windows with "the blue screens of death".. then Id like to know how M$ will respond to your problems for free.

---

### Post by cottfcfan on 2010-02-09
Serpentracer,

I don`t think this is a hard drive failure.
I`ve seen the message "mount of hard drive failed" come up on 2 different computers recently, one running Ubuntu 9.10 and the other using Linux Mint 8 (which is based on Ubuntu). Both of which have no hardware problems. I did a reinstall on both, and thought nothing else of it, but you may have hit on an issue here.
 By the way which kernel are you using, because both these issues happened on the 2.6.31.14 kernel?

---

### Post by Nunu on 2010-02-09
I am also thinking in the line of drive failure but I know from personal experience if SMART is enabled in the bios then 9.10 will most certainly pop up with a window complaining about HDD issues as soon as you log in. 

I had to replace my laptops drive yesterday afternoon. Ubuntu started warning me for about a week now and by yesterday morning no boot at all. Drive went to the big recycling centre in the sky. :(

---

### Post by physeetcosmo on 2010-02-09
> **serpentracer said:**
> ...but my hard drive has S.M.A.R.T  and my bios checks it's status on start up and says it's fine.  the last time my hard drive failed, the bios stopped and said "hard drive failure is eminent"...

serpentracer,

i read up a bit on SMART and it looks like this is just a HDD monitor built into the BIOS and Firmware of the HDD. This feature can predict "up and coming" failures as well as detect actual failures on the platters.

i am wondering if Your BIOS isn't playing nice with the SMART monitoring, or SMART isn't playing nice with the chipset/IDE controller, or due to certain read/write cycle profiles SMART is "detecting" imminent failures as you said when there really aren't any failures.

You describe your experiences with this SMART HDD that it has detected a failure on the HDD before. Did you re-install the OS after SMART declared the disk bad? If you have, I wouldn't blame the OS so fast, the disk could very well be bad, or I'm not understanding your experience.:shock:

Have you tried Ubuntu with another HDD on the same system? :) If you have a spare HDD (or even an external, to test a different interface) try loading on another HDD to verify the rest of your system.

-Dustin

---

### Post by serpentracer on 2010-02-09
this computer works/worked just fine with XP pro up till about 5 or 6 days ago when I installed ubuntu. (it was on the same drive) in fact it performed much faster than it does with ubuntu.
if my drive is failing, I think ubuntu caused it. since I've had to force it off so many times from it crashing and erroring so often.
some times it won't start up with a working keyboard or video.
 
I used my wd disc data lifeguard tools and it found no errors with the drive.
 
I know I sound like I'm hating on ubuntu but it's not impressing me at all.  the las os that worked this bad was windows 98se and ME.
I like all the free software etc you guy have and all of my stuff works like my video camera will import video all the cd/dvd burners actually work etc etc...I do want to keep ubuntu now that I've used it.
 
I just tried fedora...it had errors from the first start up so it's gone.
suse wouldn't even install without a error..so it's gone.
kubuntu seems nice...but I just don't like the kde desktop.

---

### Post by mickie.kext on 2010-02-09
> **serpentracer said:**
> 
if my drive is failing, I think ubuntu caused it. 

That is not possible. No way, no how. Just like Windows can't kill hardware and just like viruses can't kill hardware either. If it could, hardware companies would spray viruses to increase sales.

Your problem might be faulty hardware, but more likely is driver problem. Your computer is very old and shuttle might used some quirky HDD controller which is not supported by kernel. Hold on, I will Google little bit about your mobo.

---------------------------EDIT--------------------------

Is this your mobo [http://www.firingsquad.com/hw/4154/Shuttle_AV41P/](http://www.firingsquad.com/hw/4154/Shuttle_AV41P/)

If it is, they it uses VIA VT8235 southbridge for controlling hard drives and that chip should be supported with kernel.

You said you bought HDD 2 years ago, did you maybe bought PCI to SATA adapter with it? Is it SATA or IDE harddrive?

---

### Post by Methuselah on 2010-02-09
Sorry it didn't work out for you...sometimes that happens.
It really sounds as if your drive might have issues so you might want to rule that out.
Good luck!
):P

---

### Post by NFblaze on 2010-02-09
> **serpentracer said:**
>  
I know I sound like I'm hating on ubuntu but it's not impressing me at all.  the las os that worked this bad was windows 98se and ME.
I like all the free software etc you guy have and all of my stuff works like my video camera will import video all the cd/dvd burners actually work etc etc...I do want to keep ubuntu now that I've used it.
 
I just tried fedora...it had errors from the first start up so it's gone.
suse wouldn't even install without a error..so it's gone.
kubuntu seems nice...but I just don't like the kde desktop.

Sounds like Linux doesnt like your computer...or your computer doesnt like Linux. Either way, sounds like your having a terrible time I think you better go back to Win98SE or WinME (actually at least go to Win2k if that old box can even run it).

---

### Post by HappyFeet on 2010-02-09
> **serpentracer said:**
> I just tried fedora...it had errors from the first start up so it's gone.
suse wouldn't even install without a error..so it's gone.
kubuntu seems nice...but I just don't like the kde desktop.[/I]

That right there tells me your computer isn't very linux compatible. It happens. Some computers are very proprietary, and will not work with linux no matter how much you want it to. My advice is to get a computer with linux preinstalled (like you did with windows ;) ) or just stay with windows. It's OK, we won't hate you for using windows.

You can't just throw linux on any computer in the world, and expect perfection. Most computers will work just fine, but not all. Why do you think most people buy computers with windows or mac preinstalled? Because the hardware has been chosen for compatibility. Do the same with linux, and you will be rewarded with a great running system.

And if your pc is very old, you can't expect a modern OS to run good on it. Stay with winME and have a blast!

---

### Post by serpentracer on 2010-02-10
alrighty folks I reinstalled her and we'll see what happens..I'm not letting it install the new kernel updates this time just to see what happens.

I've got it all back up and going without any noticeable problems so far.

I did do the mem test like mentioned it found no errors.

---

### Post by serpentracer on 2010-02-10
> **NFblaze said:**
> Sounds like Linux doesnt like your computer...or your computer doesnt like Linux. Either way, sounds like your having a terrible time I think you better go back to Win98SE or WinME (actually at least go to Win2k if that old box can even run it).

well I can go with xp pro as many times as I wish...I can't tell you how....lets just leave it at that.;)  and it is a validated legal copy.

I do have a copy of 2k pro and ME still. lol

---

### Post by rahilm on 2010-02-11
have some patience, friend..there is no limit to patience..be persistent.. you'll thank urself later

---

### Post by bleeding±the±dead on 2010-02-11
> **serpentracer said:**
> ok gang this is the last straw...ubuntu has crashed several times now on me with major system failure problems.   my files system keeps getting all messed up.  
and several other oddities that are highly annoying.
I'm going back to windows.  you guys enjoy linux. 

I've never had this kind of problem from this computer from windows.

i can't be bothered to read through all the replies, but try fsck at the maintenance shell. if not, just use windows.

---

### Post by whiteman on 2010-02-11
> **serpentracer said:**
> ok gang this is the last straw...ubuntu has crashed several times now on me with major system failure problems.   my files system keeps getting all messed up.  
and several other oddities that are highly annoying.
I'm going back to windows.  you guys enjoy linux. 

I've never had this kind of problem from this computer from windows.

The only badtime I had with U was when I tried this upgrade..9.14. I didnt recognize it at all. It was based on the "k" thing and not the Gnome desktop that was familiar to me. I paniced and tried to reinstall. I lost all of my home files. HOWEVER...being an old hand I had saved everything on my external. It was just annoying. I had lotsa cool little applets setup and now I have to remember how I made them.
NOW getting to windows....I do a lotta torrenting etc. I have a little Pavilion..I have had to do two total wipe/installs since August. I have to run half a dozen AVG..Spyhunter chasers, malware destroyeres. And none really work. Linux and my dependable MAc(my 1st choice) never NEVER let me down.If I behave myself.The Ubuntu would have been fine had I not experimeted with new release. I miss Itunes..yes. I dont use my iphone or ipods with ubuntu. Just not foolproof yet.(Must be foolproof when dealing with a fool) Yes I am sorry to see you go, because I think you wont find what yer looking for over at Windowsland. Windoze7 seems better. But stll requires all of the security garbage.(I have my own theory on malware, spyware, viruses....THEY ARE WRITTEN BY Virusware companies.<g> Create the disease..then offer a cure. I dunno...leave Ubuntu if you must..but get an Apple. Dont go back to windoze. IMHO

---

### Post by Tibuda on 2010-02-11
> **kellemes said:**
> Computer is probably made for Windows.

almost any desktop computer is made for Windows, except Macs off course.

---

### Post by Whiteice on 2010-02-11
I think I have found a solution to your problem if your willing to give ubuntu one last shot. I did a little bit of searching into the problem and found a form already that someone else has encountered the same problem. I would state my life on the linux system and mainly ubuntu It is the best system I have seen in my time and the only problem most users have is getting it work the first time which I will credit you and even others it is sometimes very difficult to use. But if you ultimately wish to switch I am not holding you back but I thought I was done along time with it but gave it another shot and sat down and figured it out and mi not going back unless I have to. well good luck and I hope this helps

[http://swiss.ubuntuforums.org/showthread.php?t=1305434](http://swiss.ubuntuforums.org/showthread.php?t=1305434) 

If this does not help I have proposal of my own. Why not try using a system like Hiren's boot disk and completely formatting the drive using a slow low lvl format I believe you may have some damaged sectors on the Hard drive and if that is so you may encounter the same problem with windows. My favorite formatting tool would be active kill disk which is on Hiren's Boot Disk. Now this will take a long, long time so I recommend running before you go to work or turn in for the night and just let it cook. Then trying installing ubuntu or if you wish windows.

---

### Post by Mr. Picklesworth on 2010-02-11
/me glares at the people who keep posting cookie-cutter responses without reading the thread

> **serpentracer said:**
> this computer works/worked just fine with XP pro up till about 5 or 6 days ago when I installed ubuntu.
What happened then? Did you reformat the entire hard drive or is Win XP still there? Is there some history to why you did it? (Sorry if that's an annoying question, but was XP doing anything unusual?)

---

### Post by ElSlunko on 2010-02-11
I've had bad crashes cause node errors like this before. It was usually video card issues that were the root of the domino effect of crap. Eventually I just learned how to manually install the latest drivers for my Nvidia card and that was pretty much it. No more freezing which forced me to restart which caused HD errors.

---

### Post by Jason Raub on 2010-02-11
I've had a computer "Toshiba Satellite" laptop, every time I installed window's xp the entire xp o.s would fail on update or fail on driver installation. I installed Xubuntu on that same Toshiba Satellite laptop computer and it worked like a dream up until complete hardware failure (thank chocolate milk & children for that), I've been frustrated with Ubuntu in my life but I've got the gut's to say it was me (inexperienced) not the operating system (nothings perfect) and I expect more out of something than it's built to do. It's free for goodness sake so we gotta learn to quit crying over spilled milk. As I'm sure it was mentioned you are most likely having hardware problem's, I have experienced the same problem's such as an entire operating system failing due to the simple fact my hard drive went bad or a faulty burn of the live installer.

---

### Post by Woolio1 on 2010-02-11
The good thing about Linux is that if you understand what you're doing, it can work wonders. If you have no idea what you're doing, like I did when I first started, you'll be spending a majority of your time in the help forums here.

However, did you check the MD5 sums? Those occasionally cause some of my problems. 

-Ericson

---

### Post by jdrodrig on 2010-02-13
> **Woolio1 said:**
> The good thing about Linux is that if you understand what you're doing, it can work wonders. If you have no idea what you're doing, like I did when I first started, you'll be spending a majority of your time in the help forums here.

However, did you check the MD5 sums? Those occasionally cause some of my problems. 

-Ericson

+1

Also, for next time...*dual booting* is always a safer choice specially when you are still shopping around for OS; if you do dual-boot it would be interesting if on the same hardware, Linux gives you error messages and Windows were not to give you similar messages.

---

