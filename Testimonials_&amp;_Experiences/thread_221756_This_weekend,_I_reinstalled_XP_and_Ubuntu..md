---
title: "This weekend, I reinstalled XP and Ubuntu."
date: 2006-07-24
forum: Testimonials &amp; Experiences
---

### Post by Jhongy on 2006-07-24
This is a bit of a rant. Lots of gory details. I have been a die-hard Windows XP convert for years. But MICROSOFT STOLE MY WEEKEND, and I just have to vent.... and sing Ubuntu's praises!

Here's what happenned. I just got a brand spanking new SATA hard disk, and hade come up with a fantastic partitioning plan for Ubuntu and Windows XP to share the disk -- and use the existing two IDE drives for backups and documents.

The plan was, after partitioning, to do what I know best: Install XP. Then: install Ubuntu.

It should've been easy. It wasn't.

I admit, the first time I read guides or "How to's" on getting things done in Ubuntu, I was shocked at all the terminal commands. I didn't believe everyone who tried to say that it was "just different". However, after messing about with a few things, I have quickly found my feet - remembering some of the UNIX commands from uni. helped.

But, installing WinXP really put things into perspective. What should'be taken me an hour, tops, took me a day and a half. A DAY AND A HALF out of my weekend... GONE.


--------------------------------
STEP 1: INSTALLING WINXP
--------------------------------

Again, it should have been sooo simple. Put CD in tray, choose partition to install to, done. But NOOO.

You see, the Windows installer - even the SP2 disk - didn't recognise my SATA controller. To get it to work, I would have to put drivers on a FLOPPY DISK, wait until just the right moment in the install process, and then hit "F6".

A floppy... a FLOPPY... I found a dusty drive in the bottom of the old parts box, plugged it in.... and, as expected, it didn't work. No dice. ](*,) 

Fortunate that I hadn't yet nuked my existing installation, I turned to the 'net. I had to spend hours sorting through disinformation to find what I wanted... and found nLite. Using this tool, I could integrate the drivers onto a new install disk.. Great. After downloading Nero, I created a disk... well two actually, as the first wouldn't boot for some inexplicable reason. 

I finally got through to a screen asking me where I wanted to install Windows... Downhill from here, right? No! Windows insisted that I set up a SECOND partition that it could "copy needed files to". It didn't tell me why. I figured that, for some obscure reason, it didn't want to install directly to the SATA disk, and would use the other partition as a file cache. So, obligingly I went back to the OS and fiddled around with the disks to create an empty partition on one of the IDE drives. This process blew away the existing Windows installation... but what the heck, I was about to install a new one, right?

Back to the installer again. After formatting the TWO partitions, it worked... well... kind of. 

It appears that, on my first try of nLite, it had turned my "media center edition" CD into a vanilla XP installation.... so, after installing network drivers, I had to spend hours surfing in order to download nLite again, download the .NET framework it needed, figure out what config files I had to change, then make another disk! Not wanting to activate Windows on what was clearly going to be jsut a "temporary" install, I had to jump through BIG FLAMING HOOPS in order to download things I needed.

This time it worked. Or, at least, I thought it had.

After booting my new Windows OS, I realised why it wanted two partitions.... it had installed the boot sector and boot files to the *other* disk. How did I figure this out? I realised it when I nuked that partition. After all, the installer said it only needed it to "copy some files to". It didn't tell me "I inexplicably need the second partition to COPY CORE FILES TO THAT MUST NEVER BE DELETED... EVER!".

Cue several hours sitting at the recovery console. FIXMBR... FIXBOOT.... going into Linux (since the console doesn't even have a text editor!!) and creating Boot.ini files with just about every combination possible, then going back to the recovery console and trying to copy them over. Trying to fix something with only about 20 commands at your disposal is a PAIN. In Ubuntu, I would have done apt-get install Lynx, and surfed for the answer. Not here! It even took me 10 minutes to figure out which partition was which, as they were all mounted - including Linux partitions which it could not even read - randomly. C: was D: and D: was F:. Arrgh! The stupid "recovery" console proved itself to be a complete waste of time that took 10 minutes to load every time I booted into it.

Fortunately the wife had gone out, for I completely wasted Saturday. I had woken up early on Saturday, planning to spend a few hours to get everything sorted. by 5pm, I was still wearing pajamas and had survived on pizza delivery. 

In the end, I found a way to fix the problem: Reinstall Windows. Again!!! But with only the SATA drive plugged in. I had to unplug the other drives. <Cue drum roll>..... It worked!!!! This time, Windows only needed one partition. Dinner pizza arrives, and the delivery boy points at my pajamas and notices my bloodshot eyes, and asks if I am sick. I was sick. Sick of the Windows installer.

Of course, having used Windows for years, I thought I was prepared - I knew that when I booted into a new install, there would be no network drivers for my nForce2 board. If I hadn't had those drivers backed up - and slipstreamed them with nLite, it would have been another hoop to jump through.

The rest of Saturday night was spent installing Office, Antivirus, and telling things like printer and webcam driver installers that I wasn't interested in installing IE toolbars and phone-home clients (God help anyone who clicks the "Standard Installation (Recommended)" button!). At least I had them all on CDs, prepared, beforehand. Oh, and there were 49 Windows Updates waiting for me.

---------------------------------
Step 2: Installing Ubuntu
---------------------------------

I inserted the Live CD. I told it my time zone and my name, and selected exactly which partitions I wanted it to install to. While it was installing, I surfed the net.

Upon restarting the computer... it Just Worked. Well, almost. When installing the nVidia drivers, I let them do their autoconfig thing, which borked my xorg.conf. So I had to use the "cp" command to copy over the backup.

I then couldn't figure out how to restart Gnome, so, determined not to have to reboot, I typed apt-get install Lynx, and Googled for an answer. Ahh.. /etc/init.d/gdm restart. It worked!

In other good news: My Audigy 2 worked otu of the box, my printer worked out of the box. I tried Mandrake a few years ago, and this is a massive, massive improvement over that.

I'm beginning to see the power of this. I have a fully-fledged GUI, which, looks pretty good in all its XGL wobbly goodness. But, if I ever find myself at the command line, I'm almost no worse off... I can read full manuals for commands, and even surf for answers!

Total time: About an hour. Two, tops.


Honestly, there are lots of Windows tools and programs I am still reliant on... the webcam integration in Skype, VBA macros, etc etc. There are lots of things in my install I still need/want to tweak. BUT... I have a NEW FOUND CONVICTION..... I'm going to decrease my reliance on Windows, with a view to eliminating it alltogether. I don't play games any more, and I see no reason to sink my money and time into Windows any more.

And I'm about to order 5 Ubuntu CDs for friends and family. Microsoft made me lose my weekend. In return, I'm going to help them lose their customers :mrgreen: . And, in the process, those customers will have a BETTER OPERATING SYSTEM BY FAR at their disposal. 

So, if you see me around the forums asking scads of newbie questions, please be nice... and help me along with my #1 Goal of Ditching THAT OTHER OS!

---

### Post by TravisNewman on 2006-07-24
That's incredible. That's all I can say.

---

### Post by orb9220 on 2006-07-24
Now to complete the Transformation "You Must sacrifice one Microsoft  Employee to the Ubuntu Fires of Reason".

And me being an ex-XP addict too welcome you. "Gee I didn't have the shakes or the sweats I thought I would have.

Good Luck!

---

### Post by CheeseEatingBulldog on 2006-07-24
I feel your pain, I really do. 

I was an IT support techie for 4 years, most of which was in windows network enviroments. My home install was a frankenstein of cracked/hacked/tweaked applications that together formed a somewhat shaky custome windows.

This all worked 'fine', I mean I can fix most windows crap. Untill I got new memory (one of which was a corrupt sim, which I did not know). This new memory caused all kinds of random errors and crashes, so thinking my install was finally up for the semi annual reinstall, I went about the reinstall. 3 times(estimate the hours yourself). Each crashing in different parts.

To keep it a little short, I was so mad (even after finding the fault), I mean steam out of the ears and all, that I grabbed the then hoary disc, and installed it. Within the hour.

Now my machine, the dapper install of course, is the only thing I use. No more windows...ever.

I have a ps2 so gaming is sorted (albeit, moved from pc to console). But this will change with the improvements they are making with WINE and CEDEGA.

You seem like many other windows users (like I was) who are just fed up with the endless walkarounds for the endless bugs in windows. Stepping over was a jump in the deep, but I grew up with DOS, so I think the command line is sort of cool now, and am starting to use it in combination with the GUI. Like, you said, reading manuals from the command line is a help when you are up that creek without the paddle.

Anyway, nice post mate, enjoy.

---

### Post by K.Mandla on 2006-07-24
Holy cow! Now that's a lot of work. I salute your diligence; I think I would have given up after a while.

By the way, I used to use nLite a lot to build custom CDs for low-end computers with slower processors, low video RAM and small hard drives. It's a nifty tool, but it does turn into a bit of a chore to build a CD, then find out it didn't work, then make another. ...

The only way I found that got around that waste of CDs was to install it with something like VMWare while it's still an ISO. Then you can at least test it (to a small degree) before you burn it, reboot, install, etc.

I don't know that it would have saved you much time overall, but I though I'd mention it. It's an idea. ;)

---

### Post by sbanjac on 2006-07-25
I had very similiar problems... with sata drives and XP. Ubuntus install is perhaps one of the best, you can play mines, surf, whatever you want. I remember, that when was doing a reinstall of windows, I used to stare at the celling of my room, and to count down the remaining time... sick lol.

---

### Post by filterpunk on 2006-07-26
I hate to sound like i'm "siding" with MS, but the driver issue is more likely to blame on your motherboard.

I hopped on the SATA bandwagon pretty early...don't recall the year, but maybe 2001-2002 or so?  I'd purchased an Albatron KX18D ProII motherboard, which sported a couple SATA plugs.  I thought that since the days of whacky IDE-SATA adapters had passed, things had finally reached maturity.  Bzzt!  Not quite.  Turns out the BIOS recognized the drives, but they were listed as SCSI.  In every instance of a motherboard that behaved this way, a floppy loaded with proper drivers was necessary.  So, every install, I had to make sure I had something on-hand to be able to load them up, otherwise I was out of luck.  

Thankfully, this little stumbling period seems to have passed.  I've since moved on to a Gigabyte GA-K8NSC-939, which runs an Athlon64 rather than AthlonXP.  No floppy junk to deal with this time, no driver oddities or BIOS funk.  My girlfriend, on the other hand, still has to deal with loading SATA drivers from a floppy...or would, if she weren't running Kubuntu.

---

### Post by GuitarHero on 2006-07-27
[http://skype.com/download/skype/linux/](http://skype.com/download/skype/linux/)
Skype is available on linux you know right?  There's even an easy to install .deb file on there for debain distros like ubuntu.  Just trying to help your anti-windows crusade.

---

### Post by Lord Illidan on 2006-07-27
I just reinstalled XP too. Needed it for Turbo Pascal (works like sh** in Dosbox and Dosemu, and never worked in Wine)

The CD is legal, and all that stuff. But I happened to have installed it one time too many on this computer, and also on my other computer. So...it refused to activate.

I then went to some warez sites to get a cd crack...and before I knew it, filled up the whole thing with spyware, and still couldn't reactivate this damn machine.

Then, I had to install Nvidia drivers, as I couldn't stand it when just moving a window took my CPU usage to 100%.

Then I had to install Genius drivers for my soundcard.

Then I had to install antispyware software.

Installing Ubuntu takes a matter of 1 hr, and everything is up and ready.

Installing XP took a whole day for me.

---

### Post by cptnapalm on 2006-07-27
This reminds me of one of the myriad times I installed Windows 98.  The OS had become too flaky so I decided on a reinstall.  So, I popped in the disc and start it up.

While clicking Continue and Custom and what not, the screen went blue.  I got a Blue Screen of Death and Windows was not even installed!  That took the cake for my Windows installation experiences.

---

### Post by Jhongy on 2006-07-27
> **GuitarHero said:**
> [http://skype.com/download/skype/linux/](http://skype.com/download/skype/linux/)
Skype is available on linux you know right?  There's even an easy to install .deb file on there for debain distros like ubuntu.  Just trying to help your anti-windows crusade.

Yeah, I know... but I need the video chat, which only the Windows version seems to have at the moment. 

I live in China, bt my family is in the UK, and so this is an important feature for me. We've tried an untold number of other packages, but Skype has provided the most reliable connection.

---

### Post by Jhongy on 2006-07-27
> **filterpunk said:**
> I hate to sound like i'm "siding" with MS, but the driver issue is more likely to blame on your motherboard.

Yeah, I see what you're sayihg... this is an Abit mobo which was one of the earlier ones to support SATA (and yes, the controller appears as SCSI).

But still... Microsoft should have thought ahead a bit and included another method to get future drivers into the installer other than floppies -- which were already beginning to die out when XP was released - from CD/DVD, USB drive, whatever... just not a floppy!

And there's no excuse for not allowing me to install the MBR to the same disk as the installation unless I unplug the other disks.....

> 
While clicking Continue and Custom and what not, the screen went blue. I got a Blue Screen of Death and Windows was not even installed! That took the cake for my Windows installation experiences.


ROTFL! That's ridiculous.

---

### Post by tenshi-no-shi on 2006-07-28
I used to run Win XP on my computer, of course it ran like a dog on it since my comp is only a P3 700hmz one, not that I mind. Anyways strangely enough I never had problem with spyware, but the install for windows always annoyed the heck out of me. I mean I had to do a zero fill for ever time I reinstalled otherwise it would fail. Anyways my friends convinced me to try linux (THis was for the third time, first was RedHat 7, then Debian). Well I downloaded the iso and installed it on a second all be it small (6 GB)HD. installed great, other than my sound being messed to hell (built in sound cards fault, since then I installed a generic card i got from my friend and have never had problems since)

  I also had to configure my mouse by hand. But strangely I enjoy it. I mean with windows you install the drivers and hope that they work, not to mention have various other programs that support the dirvers running the the background eating up space. With ubuntu configuring the system makes me feel like I am doing something. And of course the support for it is A MILLION times better than windows. (People actually care that yo uare running it and want to help you get pass your problem. :) )

---

### Post by compuguy1088 on 2006-07-30
Wow your story of installing XP sounds like heck...and I can relate to that, I've had some wierd things mess up on certain computers, even though linux will install on them hunky-dory. I've never set up and SATA drive yet, but this story will make me weary of putting one in and reinstalling xp...

---

### Post by eXcentra on 2006-07-31
Heh, I see we're all sharing our negative experiences with Windows.

For me, I've never had to reformat before and for the first time, I had to. But before I had reformatted XP, I had installed Ubuntu a separate partition. It recognized all of my components (ethernet, wireless, graphics, etc) and I was up and running. 
So I reformatted and installed XP. And then I tried to use the internet to get Firefox but for some reason, the internet didn't work. After a few minutes, I realized that I had to install the drivers (Duh! But I had no prior experience so I wouldn't have thought about it first). 
For me, it took 5-6 hours to install Windows and all the programs I need, and afterwards a few more hours to install other programs (Wasted a Saturday). For Ubuntu, about 1-2 hours. 

Well, Jhongy, it must've been a nightmare of an experience. At least it's all over now. :p

I really admire Ubuntu for it working out-of-the-box. I mean it *just works*. :)
Hooray for Ubuntu! :D

---

### Post by bbzbryce on 2006-07-31
I did a tripple install two weekends ago on my new compy with Windows Xp, Windows Vista Beta2 and Dapper Drake.  Each easily detected my serial ata drive and had no problems installing.  I did have to chose safe video mode on the Dapper CD though which took a couple of trys until I figured that one out.

Ubuntu took the cake on working out of the box though as expected.  Only had to install my fglrx rather than the default ati driver.

Vista required audio drivers as well as enhanced video drivers, and xp required those two in addition to my lan driver.

I have a Gigabyte GA-81945P-G motherboard if anyone is wondering.

---

### Post by BuffaloX on 2006-07-31
> **filterpunk said:**
> I hate to sound like i'm "siding" with MS, but the driver issue is more likely to blame on your motherboard.
...
Thankfully, this little stumbling period seems to have passed.

What do you mean?
Nothings changed, Windows don't know SATA even with servicepack 2 install CD.
Diskette drives were obsolete 10 years ago, why do I have to install a diskette drive to install a driver from diskette? Why not USB or CD instead?

I thought XP Service Pack 1 would support SATA, then I thought maybe SP2, but still I need F... diskettedrive. Diskettedrives belong in museums,
I went through much of the original posters trouble too. But finally gave up, and installed the F.... Diskettedrive.

XP unable to install to SATA without diskette is sooo embarrasing,
At the same time the installation claims to support the newest hardware!!!
Through Diskettedrives!!! :---)

---

### Post by Mikawa Ossan on 2006-08-02
I don't have any horror stories to rival that of the OP (at least not in recent memory), but I have noticed that my Intel Celeron 650MHz CPU on my laptop does a LOT less work under Ubuntu than it does on Windows XP.

That plus for some inexplicable reason my CD drive's driver inexplicably decided it didn't want to work any more on XP, but my only copy of the driver is, you guessed it, ON CD!!! (This is the reason I installed Ubuntu in the first place.)

---

### Post by hygraed on 2006-08-02
I once had to reinstall XP from a vendor disc. It took me a good two days to get everything fixed up the way I wanted it.
Ubuntu, maybe three hours. Maybe.

---

### Post by vat0r on 2006-08-02
Never had the sata issues but my first xp reinstall was truly memorable. I had to call dell support since it was my only computer and I had little access to any information. Spent hours on the phone with a guy who could barely speak english. He did get me through the process though. 

Now with ubuntu. Just boot from cd and in no time your online. I just hate the feeling of being a newb all over again. But, i'll get there eventually.

---

### Post by Metroid48 on 2006-08-03
I've never had to reinstall Windows XP, but all the Windows versions (except DOS, cause it wasn't a virus-filled GUI reliant machine) constantly have the slowdown problem.

Like, when you buy a brand new computer pre-installed, or install it on a fresh HD (the horror!:p ) then it runs fast. Then, before you know it, it takes longer to boot. And longer. And SOO much longer. Then there's Firewalls, Anti-virus programs, spyware scanners, printer drivers, all kinds of background tasks- NO WONDER IT'S SLOW!

With Linux, I can ditch most of the startup stuff, trash most services, and completely customize it. Plus, though I do have a virus scanner for it, I really don't need to waste time with slow firewalls and whatnot.

WindowsXP=slow
Ubuntu=fast!

-Metroid48

---

### Post by stalker145 on 2006-08-11
By no means am I trying to troll here, but my experience with installing XP and Ubuntu are in opposition. My current configuration is as follows:

Athlon 2600
Abit mobo
ATI Geforce w/ 128 MB
768MB RAM
intergrated sound, NIC, etc
1x DVD+- DL
1x CD/RW
1x 40GB HDD
1x 400GB HDD
1x ATA controller card
(the following are hung off the controller card)
2x 160GB HDD
1x 20GB HDD
1x 60GB HDD

With all that said, I had absolutely no problems installing XP. Of course, I have done the monthly reinstalls for the better part of 10 years with Windows platforms and have made it a habit of keeping an extra CD with all of my necessary drivers on hand. Everything "worked", though not up to specs. All HDD's were recognized and I was on the 'net and able to do everything I needed to do. Of course I still needed to get an office-type loaded and any miscellaneous programs I had before.
Enter Ubuntu... Let me start by saying that the work was worth it due to all the software that is available and easily acquired.
After booting the live CD of 6.06 and starting the install, I continued surfing (much like a previous poster, I used to stare at the walls and mutter ubsurd things to myself). The problem arose when I completed the install and rebooted into my nice, clean Ubuntu install. "OS not found". WTF :confused: 
I ended up on the forums garnering advice on editing GRUB, my FSTAB, and a few other things until I got it working. Approximate time after install until a fully operational distro: about 4 hours.
Bitch, moan, complain... it was worth it. I now have a system that I haven't needed to reinstall due to virii, spyware, or broken junk. I have a wealth of software at my fingertips. In the mean time, my wife have been victimized by the WGA bug and I'm doing my best to convince her to follow my lead.
Both of our laptops (Dell C640 and Micron Transport GX2) work perfectly with Ubuntu. Of course they don't have the oddball configuration that you see above in my server.
It is totally understandable that when loading even the best Linux distro that it's not going to work perfectly on every computer. Just like Winderz, you can not possibly forsee every possible configuration for every computer in the world. Someone, somewhere, is going to have to work harder to get thier system running. No big deal.
In closing I want to thank all of the people that participate in the forums. This is how Linux is going to make headway against the Massive Satan, MicroSloth, Winderz, pick your euphemism. This forum has helped me more in the past couple of months than the entire interweb (c) has helped me in dealing with Winderz in the last 10 years.

---

### Post by John Q (be) on 2006-08-13
hello;

Since june 06 i've switched to dapper. Reasons,... are well mentioned here.
In my college time i've even made a ghost back-up for my windows partition.
Every 3-4 months my PC (or the same PC from my brother) needed fixing.

I was fed up with the update-authenticate-need_licence_key-security policy (crap) from programs running under windows.

I can only encourage the developers from Ubuntu (Kubuntu) to keep up this   example of a GOOD OS!!!
I'm still a semi-rookie,but the ease of working and never_failing of this OS, is just...

To spread the ubuntu word, i've installed kubuntu 7 times (since half july) on PC's here in the family. And the joy of it was that it didn't took more than 90 minutes to complete it all. (AMSN,Thunderbird and so on included)

i encourage everyone who is working on this system, and hope to be able to enjoy it till ....

John

---

### Post by jive_turkey on 2006-08-17
I feel the collective pain, one suggestion for people who are still forced to constanly reinstall windows. If you are reinstalling on the same machine on a regular basis, (for me its 6 months) I would suggest using Norton Ghost. Ghost is great, it creates an image of your computer so that you can revert back to that image whenever you want. If you use that in tandem with a bootable windows based operating system like BartPE, its less than an hour to revert back to a clean windows image. That said, it does require a bit of forsight, because you have to create the image before you muck your computer up. But I do this for all my computers and store the images on a little USB drive. Good Luck.

---

### Post by Redache on 2006-08-17
I agree, Windows is and always will be a pain. Especially with the phantom problems that can appear. My biggest issue is Microsoft, not being content with making people fork out hundreds of £($) on an Os that has a mind of it's own, they then do the whole WGA thing which voids any OEM copy due to the fact that they're not as "Legit" as the ones having a box.

I installed Ubuntu last week and I'm in love with it. So much more user friendly, and even the command line makes me enjoy it. I physicaly enjoy typing in commands now, it's such a steep learning curve but worth it on so many levels.

I'm currently studying for an A+ and reading a study guide for it I'm really starting to resent Windows. Some of the problems it comes up with are rediculous. I MUCH rather Ubuntu. If only Ubuntu managed to make Microsoft poor....

---

### Post by .t. on 2006-08-20
Well, since my PC doesn't have a floppy drive; I'd be pretty stuck in that situation. Fortunately, I don't plan on ever installing Windows again.

---

### Post by LeftyAce on 2006-08-23
Just to add another experience.

I just installed XP Home from cd onto a sata drive with no problems.

That said, Ubuntu took a fraction of the time to install all the files, and XP STILL has some driver problems.

And XP doesn't have Compiz and XGL.....and I LOVE using the desktop to abuse system resources :-)

---

### Post by luvr on 2006-08-24
> **Jhongy said:**
> And there's no excuse for not allowing me to install the MBR to the same disk as the installation unless I unplug the other disks.....
Hmmm... The MBR (*"Master Boot Record"*) will be the very first sector (i.e., 512 bytes) of the boot disk--irrespective of the harddisk on which you install whichever Operation System that you wish to use. Generally, that will be the *first* hard disk, as seen by the BIOS. Modern BIOS versions, however, will likely allow you to select a different boot disk.

The MBR decides which partition it will subsequently boot.

With Windows, that partition just **has** to be on the same disk that the MBR sits on--there's no way around this. Thus, if you wish to install Windows on any other disk, you will **need** a Windows *"boot"* partition on the system boot disk, and the actual *"system"* partition can go on your selected disk.

With Linux, the boot partition is the one that hold the GRUB (or LILO) boot loader--it can be a separate *"/boot"* partition, but it can just as well be the *"/root"* (i.e., system) partition. And, it doesn't **have** to sit on the boot disk (i.e., the one that holds the MBR).

---

### Post by luvr on 2006-08-24
> **LeftyAce said:**
> and I LOVE using the desktop to abuse system resources :-)
In that case, you will **love** Windows Vista (if and when it ever ships)! :mrgreen:

---

### Post by kurniawands on 2006-08-27
know what? both OS can't buy me more times for my self (and family)... hahahaha...

windows keep me busy with fixing this and that, still remember when my wife get mad and told me to leave her and marry the company server !!! hahahaha...

ubuntu doesn't give me all those fixing stuff, it can buy me time for my family for just some couple weeks before my boss start giving me extra works on 3d, web, graphic, and lot more things... with the exact same salary... damn !!!

and my wife again told me, now, to marry my office desktop... what the...

hahahahaha... think i'll start to find another job.... hahahahaha

---

### Post by Pumm4 on 2006-08-28
Interesting story **Jhongy **- it would be a perfect script to make a short movie out of it. :D Well as for the WinXP problems - I only  had one long time ago when loosing all my data (7 hour work gone forever). It was a point when I've realised "something has to change". It was in 2003 when I typed this sentence in Google "top 10 Linux distros" and clicked the first link (wich was Distrowach) everything changed since then. It was like the Matrix affect - an [SIZE=3]**[FONT=Arial, Helvetica, adobe-helvetica, Arial Narrow][SIZE=2]ENLIGHTENMENT[/SIZE] [SIZE=1]-[/SIZE] [/FONT]**[/SIZE]"A new prespective in everything"

I've spend months reading and researching about Linux. After 2 years of investigation (+learning how things work) and popular Open Source Distro's testings it had become cristaly clear that Ubuntu is my best friend. So I'm using it as my primary OS.

---

### Post by furiousV on 2006-08-30
I know exactly how you feel. Had trouble with Windows 2000 and XP installer deciding where to overwrite MBRs and other random partitions without even warning you. You try and boot back into SUSE 10.0, and then "o-oh. . . ](*,) "

As was mentioned earlier in this thread, I'm also working on reducing my dependancy on Windows. I'm using OpenOffice as much as possible, and avoiding "cracked" proprietry programs my friends keep trying to get me to use, such as Photoshop and all.

My biggest problem is that I'm a gamer. I have paid for Cedega, however had not had much luck with that - though my friends have.

Right now, I'm wearing out the novelty of the games that I have, and others which definetly don't run on Cedega are already gathering dust on my shelf. I've decided not to purchase any more games unless they have native Linux support - which would be Quake 4, Enemy Territory: Quake Wars, and Unreal Tournament 2004. I hope UT2007 does too.

And my college course, which is based on Windows 2000/2003 Server/Professional isn't gonna make it much easier with homework. The course has Microsoft certification as part of the final award :-k
No mention of Unix or Linux at all from what was said what we were gonna learn. Really, why not???

---

### Post by gandalf2041 on 2006-08-31
Man, does that sound familiar! Staring at the ceiling, suffering through 5-6 reboots, spending HOURS downloading and applying security updates!  

I work in the IT Dept of a major nutrition company and yes...we are (unfortunately) a Windows shop.  Anyone who has had to do numerous installs of Windows knows...it takes a LOOOOOOOOONG time! :rolleyes: 

That's why I run Ubuntu at home, I want to USE my computer, not spend hours maintaining it. LOL!

I feel your pain...Welcome to the Light O:)

---

### Post by suziequzie on 2006-09-16
I just finished installing windows 98 (it's good enough for her) on my sister's computer. It took from Thursday evening till Friday afternoon (with only 4 hours of sleep in there). Why? Because of hardware drivers crashing windows. For 5 hours I was trying to configure her ethernet card and her Bell Sympatico Slipstream modem and inevitably, I'd be stuck in a safe-mode looping nightmare. I had to take out her ethernet card, (which Kubuntu and Knoppix live CD's had no problem with), and just use her mobo lan. Okay, windows liked that. It just didn't like the nicer hardware. But then her CD rom burning software needed to be installed, and the nightmare was extended further. :mad:

My plan all along was to dual boot her computer with Kubuntu, and devote a few hours to tweaking her and her boyfriend's desktops to be all pretty and personalized for each of them. So, after fighting with windows, and FINALLY getting it running ok, I load up the Dapper install CD, and install Kubuntu. Within 2 hours I have her all set to go for internet, games, music, filesharing and movies. It had no problems with her Slipstream modem, or her ethernet, or video card... it was like Dapper said "Oh, a DSL modem, okay, good to go." Windows had to go through a damned 20 minute installation procedure to get an internet connection set up. ](*,)

Sadly, the time wasted getting windows to work ate into my valuable Kubuntu time, and they at most have their own desktops/email setups/and background pics. Nothing fancy yet, but I did get a karamba app up and going for each as well.

I am just waiting for Bell to try and sell me Sympatico through one of their telemarketers.  I will have harsh words for them. 

I have learned that Windows does not play nice with others. I have had less hardware trouble with Linux than I have had with Windows. I want to get a second computer, preferably a laptop, and have it devoted only to Linux (maybe dual boot Kubuntu and another distro to have fun with.)

Sigh. Thanks for listening to me rant in turn.  I never want to have to install Windows ever again. #-o

---

### Post by xpod on 2006-09-16
I just had to re-install XP and Ubunto a few days ago too(and the mother in laws xp...twice)

Luckily a diamond of a forum member sent me his xp cd along with SP2 which was`nt soooo bad i suppose BUT the mother in laws.....THAT was a whole different kettle of fish.
 After sending XP cd`s back to my good friend the mother in laws decided it needed re-installed again after being left on M$ updates then refusing to boot past XP logo screen.
 Being a complete pc noob(relatively)i forgot about "fixmbr or even fdisk\mbr" and jumped right in with a re-install the hard way without any XP cd`s...
I aint going to describe the 4 hour process it takes to install from a dusty old i386 directory on a cd and a 98 bootdisk but suffice to say when you are flying by the seat of your pants AND your i386 data cd is corrupt in places as this one was.....well,I got that XP up and running but had to do it all again with bit`s and pieces of other "i386" data cd`s i had lying around that were actually failed results of my attempts at making the bootable cd with the slipstreamed sp2...Needless to say it all works NOW!.

Well thats my tale of woe but even my previous few months of windows prior to discovering Ubunto were`nt much better:-({|= ..

It`s THERE lurking somewhere just waiting to strike again!!!!

EDIT:..oops almost forgot the getting the mobo drivers with no ethernet drivers to start with hence no internet connection at hers

---

### Post by katiad on 2006-09-18
Ugh. Been there, done that. I'm a pretty experienced XP user, who has rarely had problems on my own computers that have run it. I run a tight ship - had one virus, and rarely any spyware, very infrequent crashing (once every few months?). I loved it.

But installing it is a pain in the rear. I've installed XP multiple times, on computers I've built, and doing reinstalls for people who are swamped in microsoft badness. It takes FOREVER. I especially love it when you don't have the driver discs for, say, the motherboard, graphics card, sound, etc. - and XP won't even tell you which video card, sound card, motherboard you HAVE, let alone tell you where to find them. Always a treasure hunt, installing XP. 

Ubuntu amazed me with the ease of install. I mean, no problems at all. Just install, and a half hour later, you have a fully functional system. I, of course, tweak and mess around, and add on loads of random software, and customize, but I do that in XP, too - but all of that time isn't added onto the major install of getting a functional system with the major apps for web browsing, word processing, image manipulation, etc. 

I'd take an ubuntu install over an XP install anyday. I still run both (separate computers). I still have less problems overall with my XP system, but I think that's because I have some hardware issues on the ubuntu one. And of course, years of XP experience verus something like 11 months of Ubuntu experience.. That helps, too. But I'm not going back to Windows - this whole WGA thing kinda grates at my nerves, and frankly, 98% of my computing is done in linux anyway. My windows box is mostly just itunes, microsoft money, photoshop, and dreamweaver. Occasionally a game. I'll probably keep it around - it's perfectly functional and stable - but I prefer the conveniences of linux overall.

---

### Post by {Rm}Gh0sT on 2006-09-29
It seems as though most persons only enjoy one OS at any one given point in time.  My perspective is: use whatever OS, program, hardware, or combination thereof that works best with the application that you need to utilize.

In my experience, there is not one "cure all" available and there never will be.  Computer programming is an art in which a group of experienced persons need to work together to formulate the best possible solution to the best possible problem.  Sticking to only one OS at any one given time will severely limit your programming abilities.  Thus, having been a programmer, graphic designer, web administrator, and network security advisor for 4 years now I have learned one truth: one needs options and an entire assortment of tools which one may use.

To best execute this ideal, I decided to have a multitude of computers, OS's, hardwares, and softwares for all of my various purposes.  Before I start a project, I decide, "which is the best way to do this?"  Then I do it.

Keep your minds open, your toolbox vast, and your abilities versatile and this world might just be a better place!

---

### Post by dolphinsonar on 2006-10-05
ubuntu is easier by far...

---

### Post by yman on 2006-10-11
OK, this isn't about installing, but it's still a horor story:

I lost about 400 MB out of the blue yesterday on WIN XP. I transfered files from D:/ to C:/ but the free space in D:/ remained the same. when I transfered the files back to D:/, the space on C:/remained the same, and the space on D:/ decreased. when I transfered the files to C:/, again the same happened. I now have a miserably small hard drive (I mean, even more miserably small. it's only 10 GB total and I'm left with less than 400MB free space). I tried de-fraging but what was lost was not recovered, however, it may be the reason the situation isn't getting worse.

I think MS is reading my visited web pages, seeing how I was clearing space for downloading SymphonyOS.;)

---

### Post by shinatru on 2006-10-18
Hi, I partitioned my 80GB SATA hard drive to XP and hoping to install linux. I installed linux successfully (i think) but when I boot my computer-xp came up. No option to use linux. Please help me. I've been reintsalling my two OS's for almost a week now, and I am afraid to mess up my hard drive. Thanks. (wilber06@smartwifi.com.ph).

---

### Post by ihavenoname on 2006-10-26
HAHAHAH, that is an amazing story that I think everyone can relate to. My last windows install was done on this computer only for games. That took several days because I also wanted to put 3 hard drives in with the last one being the windows hard drive (it was also the smallest.) Windows did really like that so I had to remove all the hard drives except the one I needed, there were some other problems but I repressed them. (I have been in therapy for a while now:p .) All I can remember is that it was like hitting my head against the wall continuously for no reason at all. I find it funny that we all ended up staring at the ceiling. Honestly though, what can you do? I tried reading their little tid bits on how awesome it is that IE is now well integrated to provide for a fantastic eXPerience......:-&

---

### Post by .t. on 2006-10-26
Well, you know what, I've spent all week trying to get a working VMware Server Windows VM **just so** I can use Sibelius. It pains me to use non-free software, but I want to do well in my GCSE! Turns out, the only Windows version (from 98 onwards, not including Vista) that works at a resonable speed is Server 2003 R2!

---

### Post by maniacmusician on 2006-10-26
Windows has always set up painlessly for me; lucky, I guess. I've installed it on machines and in vmware.

---

### Post by Kulgan on 2006-10-30
same, but I have a very standard dell laptop... The only things I have encountered in windows is that it doesn't come with network, video or sound drivers (I have system beep!). Also, the touch pad doesn't work the way I want it to, and there's no way to change that. In ubuntu all that works fine - sliding it down the right side scrolls, which I had to configure even with the original install of XP that came with all the addon programs...

I tried installing Vista over XP (clean install, though.) It worked fine... after several reboots and no less than an hour and a half install time.
Fine meaning no drivers and not being able to install graphics drivers to get above 800x600 res. Sweet! 

Nope, I'm for linux now, what ever flavour it comes in! And three cheers for QEMU!

---

### Post by Leogen on 2006-10-31
I installed UBUNTU and used the partitioner to create two drives on my master HD.  I installed UBUNTU On one drive, once finished, restarted with the windows XP Pro cd, and installed it into the other partition.  Upon restart Grub detected Win XP and all was good.

---

### Post by Kulgan on 2006-10-31
you installed XP AFTER ubuntu? And still had Grub? 

Every time I have done that, XP has overwritten everything and I have not had the option to boot into Linux at all. :/

---

### Post by Leogen on 2006-10-31
yeah seemed fine, it has been what I have always done.  As long as windows is being installed on a complete seperate partition.

---

### Post by civilian on 2006-11-27
I so know what you mean, happened to me so many times, unfortunately making backups is not my strength and I often end up losing up everything I care about. oh well I guess.

---

### Post by Kulgan on 2006-11-27
I've done this twice now... al my settings, stuff and programs all down the drain... I have just downloaded 21 gig of south park - I'm not doing it again!

I think I'll get myself an external hard drive for christmas, and I guess I'll use it for my "Stuff" as well as for a server...

---

### Post by wrycatcher on 2006-12-12
> **CheeseEatingBulldog said:**
> 
This all worked 'fine', I mean I can fix most windows crap. Untill I got new memory (one of which was a corrupt sim, which I did not know). This new memory caused all kinds of random errors and crashes, so thinking my install was finally up for the semi annual reinstall, I went about the reinstall. 3 times(estimate the hours yourself). Each crashing in different parts.

To keep it a little short, I was so mad (even after finding the fault), I mean steam out of the ears and all, that I grabbed the then hoary disc, and installed it. Within the hour.

Now my machine, the dapper install of course, is the only thing I use. No more windows...ever.


Funny how the final straw isn't necessarily something that is MS's fault (it wasn't in my case either).  I mean, software is at the mercy of the hardware, but in this case, the Windows install application *could* be quicker.  As it is, it's an extremely procedural application unable to easily resume where it left off, in case of unexpected interruption, meaning you *must* to start over at square one, like some greedy arcade game hungry for quarters.  

I'm sure you'll thoroughly enjoy Linux, despite (or perhaps because of) the occasional challenge you'll be faced with.

---

### Post by twitchku on 2006-12-13
> **CheeseEatingBulldog said:**
> I feel your pain, I really do. 
I was an IT support techie for 4 years, most of which was in windows network enviroments.

> **CheeseEatingBulldog said:**
> 
...Untill I got new memory (one of which was a corrupt sim, which I did not know). This new memory caused all kinds of random errors and crashes, so thinking my install was finally up for the semi annual reinstall, I went about the reinstall. 3 times(estimate the hours yourself). Each crashing in different parts.

You were a desktop tech for four years and never thought once to test your new memory for defects upon crashing?
Come on...

---

### Post by twitchku on 2006-12-13
> **Kulgan said:**
> 
I tried installing Vista over XP (clean install, though.) It worked fine... after several reboots and no less than an hour and a half install time.
Fine meaning no drivers and not being able to install graphics drivers to get above 800x600 res. Sweet! 

Nope, I'm for linux now, what ever flavour it comes in! And three cheers for QEMU!

You should try the releases of Vista after CTP Oct 2005. They're quite better. Even on an older machine, install time was reduced to about 40 minutes (still crap compared to Ubuntu), all the drivers worked (except odd RAID card that Ubuntu detected), and Vista set the resolution to optimal (1280x1024 @ 85Hz) resolution, as well as supports older XP drivers. Overall, a worthy competitor.
The MBR thing still sucks, and the 64-bit version (after RC2) will not ignore unsigned drivers without manually selecting the option to do so at boot.

---

### Post by DirtDawg on 2006-12-14
I also spent last weekend installing Windows and Ubuntu. Both on the laptop I'm using now (dual boot). Actually, I dont have a copy of windows except the copy that came with this Vaio. As a result, I've noticed the one huge difference between installing Windows vs. Ubuntu:

After an Ubuntu install, you spend a ton of time installing apps to get things working.

After a Windows install, you spend a ton of time *un*installing apps to get things working.

---

### Post by yman on 2006-12-18
> **wrycatcher said:**
> Funny how the final straw isn't necessarily something that is MS's fault (it wasn't in my case either).

so true. I was fed-up with Directories so I set to look for something else, the only problem is that all modern OS's use directories, so I settled for something different, although not in the way I wanted.

---

### Post by wrycatcher on 2006-12-21
No directories?  Would files be stored in some sort of new Google-esque database or something?  Wasn't this type of feature part of Vista at one point?

---

### Post by groggyboy on 2006-12-23
well, reading that testimonial makes me wanna run out and install lynx.  i try to make sure any installation i set up has a text editor (usually nano) and i recently decided a file browser (midnight commander) would also be in order.  after reading this, i'm convinced any linux installation should have a web browser too.  just in case...

---

### Post by fsando on 2006-12-23
Not so successful here.
I have tried recently to install Ubuntu on two different notebooks with no luck - ended up installing opensuse 10.2 just to see a working linux.
I believe in both cases it had to do with the screen/video card.
I have an old centrino 14'' asus (M2000N). Installation ended somewhere midway - this one is now running opensuse.
The other is a brand new asus W1J 2.16 core2duo with an x1600 and a 1680x1050 screen.
Im running xp on this machine (1st time xp for me) and as ridiculous as it may sound - it runs only barely faster than the old one with w2k (haven't tested linux vs. winxp). So I've figured that this baby should be a dream with a nice linux distro and virtualizing windows for a few essential progs.
Haven't been so lucky yet.
But my experience so far has lowered my expectations somewhat, Im not in any way giving up - my XP-experience simply will not allow that :(
The installation either stopped somewhere midway - depending on different work-arounds I found or it continued and apparently completed successfully just the screen was totally garbled. I found a few reports of similar behavior related to similar screen resolutions - some work arounds were posted but none helped. I guess that the solution may be as simple as to change a setting after install - the screen is just too unreadable to allow this.

UPDATE jan 6 2007: (Just stumpled upon my earlier post). 
Oh God! Is this only one week ago? 
Since then I've got Ubuntu to work perfectly, and with Beryl - and I'm loving it every bit :biggrin: It's fast, easy to work with, lots of help readily available, and most programs I need at my fingertips. And I simply can't wait to show off the beryl-effects at work (:)) :p
Linux is, after less than a week, my main os.
I even recall back in the old days (1 week) when it first installed successfully, I was doing some actual work I needed to finish within an hour or so of starting the installation.

This reminds of a German quote I've seen somewhere that goes:
"My God! Even a chicken can install debian if you just put enough grain on the enter key"

---

### Post by zigot on 2006-12-23
> **DirtDawg said:**
> After an Ubuntu install, you spend a ton of time installing apps to get things working.

After a Windows install, you spend a ton of time *un*installing apps to get things working.

so true


I switched because of similar technical problems, but the real reason why I switched was the fact that I always wanted an OS that will give me the chance to explore the problem(s). I got fed up with being dumbed down with the 'reinstall' philosophy.

Therefore I praise the linux (Ubuntu) community for its existance.

---

### Post by Marthinus on 2006-12-23
Why don't you just install DOS 6.22 in a VM and run Turbo of that? I had a multitude of problems trying to run Turbo Pascal on a Windows XP box, needed to download and install some patches before it worked, with DOS 6.22 it works without any hassles.

---

### Post by yman on 2006-12-23
> **wrycatcher said:**
> No directories?  Would files be stored in some sort of new Google-esque database or something?  Wasn't this type of feature part of Vista at one point?

I don't know, all I know is that the use of labels allows me to very easily categorize my stuff while directories always get it all confused. as result it would have to rely on a good search engine. of course, if you have hundreds of labels it becomes difficult to manage your stuff.

---

### Post by fsando on 2006-12-24
As said above I had some problems installing ubuntu (now tried kubuntu - same result)
I believe that when I followed the standard install of 6.10 it actually installs into some desktop as it should, just the screen is unreadable.
I hav a couple questions: 

1) Is there a way to access a text-console through the keyboard when I cannot see what I am doing? And what configurations should probably be changed to make my screen work?

2) Are there some settings for the livecd boot process that will make the screen work?

3) If this is the wrong place to ask - where is the right place?

---

### Post by Gargamella on 2006-12-26
The thing I can't explain is that we do an easy installation with a linux that may not work on every pc...and doesn't work fine windows, their native operating system.

Not only that...If you have a slow or old pc you're compleatly out with Windows, you may run win98 and you can't use newest programs...with linux you customize everything and you're always updated. (Xubuntu and DSL are an example of that)

---

### Post by Kulgan on 2006-12-26
> 1) Is there a way to access a text-console through the keyboard when I cannot see what I am doing? And what configurations should probably be changed to make my screen work?

ctrl-alt-F<anything but 7>

I think [this]("http://ubuntuforums.org/forumdisplay.php?f=138") would be a good place to start. 

No idea about the liveCD - it always seems to work, for some reason :-k 

-K

---

### Post by rs3 on 2006-12-26
i acquired a dell desktop system whose hd suffered a severe loss in functionality (not a bona fide crash, as everything was quite recoverable, but it was very slow and hit-and-miss on certain files/areas, especially the boot sector) and attempted to supplant the faulty hd with a brand new one.  the installation froze with every attempt when parsing/installing devices.

however, everything worked like a dream on the first try of an edgy desktop cd.  go figure; it's built and configured with windows xp sp1a installed from the factory, but attempts to reinstall it prove absolutely fruitless, whereas booting and installing a "renegade" operating system such as ubuntu, for which the dell was obviously not built or configured, is no sweat.

oh, well; no loss. :D

---

### Post by shearn89 on 2007-01-11
I totally feel the same - my laptop was running windowsME, and had got to the stage where it took HALF AN HOUR to boot up. I tried to do a reinstall, but lost patience after 3 hours of failed installs and boot problems. I ordered a copy of the Ubuntu Breezy disks for about £1 off tuxdiscs.com, and tried that. It was a bit slow, so i put some more RAM in the laptop, and after a couple of ACPI probs (sorted out with the help of this forum!), it all booted fine, and runs as fast as my 1GB RAM, 3Ghz processored, Windows XP Dell desktop. Which is provided by my dad's company. Free.

---

### Post by CroEragon on 2007-01-13
I installed XP million times and never had such horror story. But every time something didnt work. And best part is: I install XP SP2 on my friends computer and run update. I got 78 updates that nned to be downloaded on dial-up. After SP. Nevermind i installed just few critical updates and week after he is calling me because he got some mesaage and some porn page is always his homepage. I went and i found whole ZOO of viruses and spyware and one dthat couldnt be removed for some reason. So new reinstal, and all 79 (one more this time) updates, and whole collection of free and warez antivirus software. It works pretty good now but cant go vithout 2months checks and cleaning up.

Now i bought new computer with preinstalled XP. Best part is i payed it and i do not have official support (i dont need it, they cant help me now using ubuntu) and do not have installation cd because it is OEM and got some wacky recovery cd that doesn't work, i tried it.
And still they cant compete with my free Ubuntu that got Beryl and Kiba Dock with their Aero interface.

---

### Post by Fahuadai on 2007-01-14
I have to say, the comparison of the first post between the two OS's is incredible. 

WinXP = bloodshot eyes and multiple horrors,

Ubuntu = "i surfed the net whilst it installed."


I currently have 3 computers. 

My main computer i still run Windows XP on. It has my best hardware on. AMD 64 3700+, 1.4GB ram. 160GB hdd storage. 6600GT graphics card.  The two main reasons i still run windows :

1. I play Civilization 4 quite often and am aware of the difficulties on running game son linux. to be fair i haven't tried yet but am currently toobusy.

2. I'm at university and as a programmer I want to be able to test programs on the two formats. Plus there are compatiblity issues and things i want to work without any extra hassle.


That said, i have my other desktop running Ubuntu 6.10 and this last week have installed it on my laptop too.

My desktop install was so fast and simple and having everything running within 45 minutes. Then installing all sorts of software and almost everything else i wanted is done through the adept package mangager. No more visiting various websites to see if there are updates avialable. i can update everything in 4 clicks. 

I had some problems getting wireless working with my broadcom 4318 wireless card on my laptop, and i've still got a poor framerate. although i might turn off transparency which will no doubt help.

I'm going to see if i can get WPA working on my laptop tomorrow on the uni network which could be interesting.

I can honestly say that windows XP has "relinquished the worry of what i wanted to do for the weekend" on so many occassions than i bear to count. It would crash during the install, a problem which after 36 hours of continous install/format/change something/install/etc cycles i discovered windows would crash at different stages of the install depending entirely on which stick of RAM was in which slot on the motherboard, or what combinations .

Now i'm aware that neither ubuntu or linux can not give me back my wasted weekends, but i'm definately converted. I hope that as i become a better programmer and after i graduate i'll be able to give soemthing back to the community that promises me no more of those "Microsoft Weekend"'s that nightmares are made of.

---

### Post by jorgerosa on 2007-01-17
- "I see no reason to sink my money and time into Windows any more"
- you lost your weekend???

You think you sink your money on windows by buying games?
Try this: Buy Windows XP + Buy MS Officce or Buy MS Windows server (limited to x clients) + MS SQL (limited to x clients)...  Or activate Windows (else it will be in trial)... If its not "genuine"... etc...
Ubuntu: None of this s*** is aplicable, and its even reliable and better.
That is why im using Ubuntu, and im a pro in developing software (VB) and webmaster (ASP and ASP.NET), after more than 20 years ](*,) (more than a weekend :( ) of this s***, i´ve changed to Linux (LAMP servers) and i´ll NEVER come back again! [-( 

THX TO ALL UBUNTU GUYS! :KS :KS :KS :KS :KS 

PS: add GUI to your server edition (even its become less secure, its the future guys... not only my opinion...)

---

### Post by Tuna-Fish on 2007-02-04
> **jorgerosa said:**
> 
PS: add GUI to your server edition (even its become less secure, its the future guys... not only my opinion...)

No way ever. the point of the server edition is not to have a ready-made server straight from install, but install a linux environment with absolutely nothing unnecessary preinstalled. that way, one can install the server version and then customize it in any way they want. besides, why exactly should a server have a gui, it's not like servers have monitors.

---

### Post by Kulgan on 2007-02-04
you don't have to use the gui just because you have it installed, but it is much easier for the human brain to comprehend graphical information than a lump of white text on a black screen.

---

### Post by Tuna-Fish on 2007-02-04
> **Kulgan said:**
> you don't have to use the gui just because you have it installed, but it is much easier for the human brain to comprehend graphical information than a lump of white text on a black screen.

But having a gui installed means you have to install tens if not hundreds of megabytes of stuff that is completely unnecessary for a server, bogs down performance and is a potential security risk.

The point is, all you have to do to install gui is to type sudo apt-get install ubuntu-desktop, while if I want to get rid of a gui, it takes a LOT more work.

And again, considering that a server doesn't usually even have a screen, what is the gui for anyway? If you wanna plug in a monitor, just install a desktop. Servers are machines that you hide in the closet, without anything but ethernet and power cables coming out from the box.

---

### Post by adza on 2007-02-04
Well, i would like to add my contribution here... Last weekend, i also re-installed XP and Ubuntu... I went to easy way out however, installed the XP to the SATA drive, then installed dapper to an IDE slave drive i'm running, i wanted a full 160GB of unbuntu grindings :) 

Windows Install - A standard instal, no real problems apart from the fact i'm installing winblows... Didn't have issues with SATA drive, however i must point out, i only installed this to keep wife happy - she's on notice however.... Vista will NOT be coming home... ever..

Ubuntu Install - This is the kicker... i have never.... repeat never even seen linux before.. popped in the cd and no worries! Installed quite easily really... admittedly, i did have to do some searching around these forums to find the post that sorted out my dual booting requirements, but had that sorted in under an hour... Installed the apps i require, again, there was some probs installing skpe on the AMD 64 bit distribution however thanks to Hendrick (great post!!), that issue was sorted (hey, am i learning new stuff here?? ;)).... Now i only have to finish my install of ET (the only game i ever play, despite how much i spend of software -- doh!) and i have a fully functional, secure, non gates dependant machine!!

The wind-up: You guys obviously have some idea of the feeling in have today, it feels like a massive weight is lifted off my shoulders!! I'm out from under the M$ oppressor!! happy days!! 

Never to go back! Thanks to the developers, what a bang-up job... but most of all, thanks to the community of ubuntu, this has been an amazing experience and the best bit is that it's just beginning! I can't wait until i learn enough to start contributing to the community and development of this platform, who knows, hopefully i'll be able to help someone just like myself one day...... :)

rock on ubuntu!!

---

### Post by Deinumite on 2007-02-16
im only 16, and my computer skills basically involve torrenting and installing software, playing around with windows to get some things to work, and some java, html and php programming.

as a long time WoW / gamer addict, i was on windows all the time, the only other operating system i had used before was mac, for like 10 seconds possibly.

i switched to ubuntu because i was bored one weekend and just wanted to see what it was about, im in the phase right now where i find something cool on the internet, and try it out basically, just for kicks. unless im gaming on xp, i use ubuntu now, and coming from someone who used to pirate alot of software, opens source software is incredible, it works on par with anything you can get from M$ or any other company, and once you get the basics of ubuntu down its really an amazing OS, everything just works. period.

---

### Post by n8bounds on 2007-02-24
Nice post man.  Very nice

---

### Post by Madmoose on 2007-02-28
I had to install windows on a box last weekend, and Ubuntu on a laptop.

Windows: 

Since it seems a Windows install only has about a year shelf life for me before I have to reinstall it; I had to again last weekend. When I started it was about 11:00AM , and when I finished it was about 7:00PM. ](*,) 

The install of windows only took about 45 minutes, but the updates took HOURS! I was smart and made a driver disk before I started, so luckily I was able to get the net, video, ect installed rather quick.

When I got those installed I set forth with the Windows updates... Round 1) 79 updates, Round 2) 45 updates to update the last updates, Round 3) 23 updates, and last Round 4) 6 updates.

The whole time I watched my available resources shirking away, and by the end turned the 80G hard drive to about 40G or so available for use!  

Though this is and felt normal to me, so I was prepared for a full day. Had my books with me, and got a lot of studying in. :lolflag: 

Ubuntu:

I have to admit I was set with a feeling of unease the first time I installed Ubuntu.  Why? It was to easy... It took an hour. Only and hour, and that was installing the updates, Nvidia driver, and programs my friend said I would like. 

I fact the box I'm typing this on now I was about to toss out! It had Windows installed on it, and it would always crash, freeze, overheat, do odd things. It would do all of this, and yes it was clean. It just didn't like Windows, and now that I have Ubuntu on it a COMPLETELY different machine

---

### Post by noenter1 on 2007-02-28
I built my system myself(mostly new stuff at the time). Installed windows(xp pro sp2) myself.

Everything seemed fine until... 2 months after I installed windows, I kept getting BOSD(blue screen of death) After that I tried reinstalling again. Immediately after reinstalling BOSD within 10 minutes everytime I restart! So I tried installing Windows xp home, server 2003, 95, 98... all BOSD. 

Then I came across Ubuntu and decided why not? Now the only problem I have is getting ventrilo to work perfectly in wine.

---

### Post by FaceLeg on 2007-03-02
Ever inadvertantly deleted your XP NTDLR file?

...NTDLR is missing

Press any key to reboot

repeat ad infinitum.

I changed because my .NET programs require users to download a 22.4Mb file.   What is with that?  The program I wrote was < 200kb!

I am also about to order a bunch of Ubuntu CD's for friends.

Thanks Ubuntu team!

---

### Post by lenluin on 2007-03-02
Have I gota story for you.... About two years ago, my parent's XP installation bit the dust, and they called me up to help them. Well, when it died, it didn't go down easy, it took ALL the drivers with it, meaning that the only thing left working, was anything that could be supported by their ancient bios, which was essentially their onboard graphics and their 3.5" floppy. That was frustrating enough.... "What do you mean I can't install XP from the disk?"
My resolution to this problem? Go digging in my dad's closet until I miraculously found windows 3.1 on twenty something floppys.
Step 1: Install windows 3.1
Step 2: Use my computer to get their cd-drive drivers off the internet and put it on a floppy
Step 3: Install drivers
Step 4: Install XP? NOPE! 3.1 wouldn't recognize it, I had to install 98 first.
Step 5: Update 98 so it would read the XP disk.
Step 6: Install XP.
Step 7: Update XP.
Step 8: Install all their extra junk....

Yeah, as you can imagine, that was a HELLISH project. Now that I'm finally on Ubuntu, that install took me, well, about an hour, even though I'm still trying to figure out exactly what it is that I'm doing.

---

### Post by Madmoose on 2007-03-03
> **noenter1 said:**
> Everything seemed fine until... 2 months after I installed windows, I kept getting BOSD(blue screen of death) After that I tried reinstalling again. Immediately after reinstalling BOSD within 10 minutes everytime I restart! So I tried installing Windows xp home, server 2003, 95, 98... all BOSD. 

That's okie, because about the start of last month I bought an HP Notebook (Only thing I can afford while going to school) I got the blue screen of death about twenty minutes after taking it out of the box, and at the time I didn't have an Internet connection handy. I didn't install anything yet, so I got the screen twenty minutes on a factory installation. :( 

That should of been a sign to return it to the store, because three days later it started to remove it's MBR, and I would have to use super grub to fix the windows MBR. When I finally got home I went to connect my Cat-5 cable into my notbook, and noticed that the cable wouldn't go in. It was messed up from the factory, and so I called HP. (That's a LONG LONG LONG frustrating story.) When I sent it off they told me they would replace the hard drive, and fix the net port. When I finally got it back a week later I did an inspection to see what they fixed, and looking at the paperwork it said "Found error on system board, and replaced it. Under warranty no charge." Nothing to indicate they even touched the hard drive, so to see if some of my installed software was still on there. If so, then I don't think they replaced the drive. Well, my software was still there. I was being nice, so I thought okie maybe they just moved the whole disk image to this drive. I did some more looking around, and I notice my WLAN switch didn't light up. It was now a dead switch. You know the switch that will turn your WLAN on or off. Yeah that didn't work any more. That was about err I don't know 12:00AM, and I made the mistake of calling HP "Total Care" (Ha. Ha. What a joke.) the last time at 10PM. I didn't get off the phone with them until 4:30AM... Anyway, I shut don't the notebook and went to bed. 

 The next morning when woke up I was dreading calling HP, becouse I didn't want to talk to anymore Indian Tech support ppl. I just wasn't in the mood, but I called anyway. I turned on my notebook, and the MBR was missing again! ](*,) I've gotten good at fixing the MBR, so after about 5 min I called HP After three different Indian people, and having to deal with major communicational issues I was put on hold to talk to HP's "Most Sr. Tech support person."  I was on hold for about 2 hours, and then when finally someone picked up it was someone from Canada. So, her English was more then welcomed. After doing a bunch of stuff that didn't work she told me and I quote "Well I'm sorry Sir. I got a hold of the repair department, and they told me they were not going to fix it. You're just going to have to deal with it. Is there anything other then this issue can I help you with?" Okie... So. They are not going to fix the MBR error, and they are not going to fix the WLAN switch they broke. "Total Care" my foot. 

After I hung up with her I was upset. I called the store, and told them I wanted to return my laptop.  That I have had nothing bur trouble, and I'm not happy with the product they sold me.  They told me to go the he**, and it was HP's issue. They sat me on fire, and so I called HP and started to toss my poo at them until I hit someone at the top.  I got all the way up to the VP of something, and when I told him what tech support said he thought I was just making stuff up. I told him this was not the case, and gave him the ref number. This is neat, but he pulled up the audio file of my convo with the person, and when he heard her say that he said "Ummm. Right. She shouldn't have told you that Sir. I'll be taking care of that personally." Then he made me a bunch of promises, and told me I would have my laptop back by Friday or Monday. With the switch working, with a new hard drive (including an upgrade), and he gave me his personal contact info should I ever need to call about my laptop again. Now, I don't have to get on the phone, and talk to someone I'm going to go around and around with. Just because we can't understand each other. 

Now, I have a promise of "If you don't get it back by Monday, and/ or if you're not happy with the work done . You can return it for a FULL refund." Well, I don't care what happens. If it gets back great, but if not oh well. As of now I'm never going to buy another HP product again. Not with this poor of customer care, and such poor out-of-the-box quality. 

Yeah...

Moral of the story. HP sucks. Don't let them fool you would when they wave their "We are a J.D. Power and Associates certified Total Care blah blah blah!" It's garbage!:---)

---

### Post by joeashcraft on 2007-03-23
I just installed Ubuntu Ultimate (edgy) on my notebook (inspiron 6400).
I got the computer with winxp in November, and stopped going to class in order to customize the look and function of windows. I spent at least 2 months googling which registry key to edit and whatnot. I just installed 'buntu on Wednesday, and within a day I've got it looking great. what took the longest was getting the wireless card working (BCM43xx) but it works now.
Now I just have to find Linux equivalents to my windoze programs and I can format my NTFS partition to ext3 and say goodbye to the BSOD, workarounds, and XP home vs pro vs media center (that torqued me off the most).

one more thing: unfortunately (for some reason) not all of my firefox extensions work for ubuntu (specifically NoScript and Update Notifier). not sure why that is but they're not that important.

---

### Post by FruitieX on 2007-03-24
From everything I can remember from my Windows days, was the last months of using it. So that is why my story will start from there.

Using WinXP, I got a virus (again, surprise!) And I found the fresh, new Windows Vista RC1 download link and installed. After a week of trying to install all the "plug and play" components into Vista(least that's what they said on the box), printer, sound card webcam more... I lastly found some working drivers for them. I thrusted the security of Vista, Well i shouldn't have. Okay, luckily I did, that's why i have been using Linux for ½ a year now. The next thing that happened was... A VIRUS!, SPYWARE, adware, trojans..... Gaaah! The first time i even heard of linux was when i installed SOT linux to my old pc that had windows with a virus. I wasn't able to conf it, so i installed windows again... From here i got an idea to try Debian (maybe 3 yrs. ago). All i can remember was that the X server didn't start up. Windows again. But now, after apx. 100 reinstalls of windows (just guessing?), i installed Debian. I got it configured and working and upgraded it to sid. Working perfectly until some aptitude dist-upgrades when the kernel failed to load. Reinstall. (repeat 10 times). I got tired of this and installed Gentroo, when trying to boot for the first time, exactly the same problem that happened in Debian. After maybe 3 reinstalls it worked but then after 3 days still installing i realised that compling every package from the beginning wasn't the thing for me. Then i tried fedora, didn't install, thrash it. Then Ubuntu. Same thing happened a couple of times with the kernel panics. Then i found the solution to all the problems i have had with linux so far (Kernel panics). Too much overclocking! So the ram clock got too high (modules too hot) and data stored in it corrupted, least that's what i've read from the net. So the kernel got corrupted in some way when upgrading it. Man was I mad at myself :D! At least 1 month of my time wasted. So, here I am now with Ubuntu Feisty, and I don't think that it will change. Currently I know 1 (one) person in real life who uses Linux. And i know one who will (maybe) use Linux on his new pc (thanks to me :P). And I am an administrator for 2 Linux computers, soon maybe 3 (Not that many) or 4 if they will get the X server working on the Dell Axim X51v pocket pc ;P.

Now I have it all working with Beryl and Xfce4, and I love Linux! The GUI already kicks some Vista ***!You learn something every day of it. Truly, bring the fun back to computing; install linux!

Well my point here is: Thank you Microsoft for making such unsecure software, leading me to the wonderful world and community of Linux!

...Why did I even write all this? (pointless crap? :D)

---

### Post by j2edwards on 2007-04-08
So, I'm not sure if this will matter to anyone on this forum, from some of the backlash I've read it seems as though true Ubuntu users are starting to sound like some Mac users I know, but in reference to the original post I've lived your pain through this entire weekend.  The only problem is that I'm living it in reverse.  I'm not sure if this is the place to post this, but I have a post going in another part of the forum about the technical details.  I've spent roughly 10 hours trying to get Ubuntu to load on a machine that is only about 3 years old.  Fedora loads great!  Windows XP loads in about 45 minutes!  I've even had Suse on it about 3 weeks ago.  I'm an IT guy, for real, not one that just talks the talk.  I'm making it my mission this year to cut out as much licensing cost as possible and still remain completely functional.  I've got a staff of 15 and the entire shop is MS thru and thru.  I feel like I'm the only guy in my own little world trying to fight the good fight for open source systems and apps, and then I run into this!  I don't really want to pay for Suse or RedHat, because then I'm in a similar boat again.  If anyone would like to take on a special project to see if they can help me get a Dell Dimension 2350 working on Ubuntu, I'd be greatful.  Otherwise, I think I'm stuck using a different flavor.

---

### Post by ihavenoname on 2007-04-08
> **j2edwards said:**
> So, I'm not sure if this will matter to anyone on this forum, from some of the backlash I've read it seems as though true Ubuntu users are starting to sound like some Mac users I know, but in reference to the original post I've lived your pain through this entire weekend.  The only problem is that I'm living it in reverse.  I'm not sure if this is the place to post this, but I have a post going in another part of the forum about the technical details.  I've spent roughly 10 hours trying to get Ubuntu to load on a machine that is only about 3 years old.  Fedora loads great!  Windows XP loads in about 45 minutes!  I've even had Suse on it about 3 weeks ago.  I'm an IT guy, for real, not one that just talks the talk.  I'm making it my mission this year to cut out as much licensing cost as possible and still remain completely functional.  I've got a staff of 15 and the entire shop is MS thru and thru.  I feel like I'm the only guy in my own little world trying to fight the good fight for open source systems and apps, and then I run into this!  I don't really want to pay for Suse or RedHat, because then I'm in a similar boat again.  If anyone would like to take on a special project to see if they can help me get a Dell Dimension 2350 working on Ubuntu, I'd be greatful.  Otherwise, I think I'm stuck using a different flavor.
link us to your "technical" thread.

---

### Post by j2edwards on 2007-04-08
> **ihavenoname said:**
> link us to your "technical" thread.

Any help is much appreciated.
[http://ubuntuforums.org/showthread.php?t=404179&highlight=j2edwards](http://ubuntuforums.org/showthread.php?t=404179&highlight=j2edwards)

---

### Post by Happy_Man on 2007-04-08
Heh, I never really had problems with my XP install, other than it took 17 minutes (I timed it) to go from Welcome screen to a functional desktop (that was hell), and my parents had seen fit to install Skype, Yahoo Messenger, Windows Live Messenger, every proprietary IM client on the planet, on onto this poor overloaded PC. Then they got a brand new shiny laptop and left was then practically a useless piece of crap to me. Processor use never dipped below 90%, my pagefile was HUGE, and RAM was constantly overloading. My god it was torture. Then I heard about Ubuntu from a friend and decided to try it out. Ran the LiveCD for two days over Winter Break, then installed it and haven't looked back since. Now, my NTFS partition is mainly used for backup. Good ol' Ubuntu!

---

### Post by jabeez on 2007-04-09
Feel your pain, I went through a similar situation when I first got on the SATA bandwagon and installed XP on my newly built machine. That was a cakewalk however, compared to last weekend when my bro-in-law needed XP re-installed and wanted Kubuntu installed next to it. Should have been pretty easy, I've done enough 'Buntu/Linux installs to anticipate quirks, but the biggest quirk was dealing with the wonderful HP "recovery" CD's (7 of em). I got the partitions all set up with a shared storage partition, 1 for /home, etc., then backed up to the storage partition a folder which he forgot to back up on CD's. Went through all 7 recovery CD's, finally about an hour later XP boots up. I had a sneaky suspicion that those "recovery" CD's would hose the partitions I just set up, and I was right, all gone. Then we went through another 4 HOURS of updates before XP was workable, albeit with all the HP bloatware crap that they force you to install. Finally got the drive re-partitioned and Kubuntu installed. This whole operation took 12 hours!!! Most of which was dealing with the XP/HP alliance from hell. Getting back to 'Buntu was such a relief.........

---

### Post by darkrose on 2007-04-10
We had to install Windows at college a few weeks back as a prac exam, I tried to get out of it by not agreeing to the EULA, but still had to install it.

One of the guys in the class got a BSOD while installing...
the teacher passed him on the exam, and let him out early.

---

### Post by Flying caveman on 2007-04-11
> **darkrose said:**
> We had to install Windows at college a few weeks back as a prac exam, I tried to get out of it by not agreeing to the EULA, but still had to install it.

One of the guys in the class got a BSOD while installing...
the teacher passed him on the exam, and let him out early.

That's a signature quality quote right there:D

---

### Post by Robert98374 on 2007-05-09
> **fsando said:**
> 
This reminds of a German quote I've seen somewhere that goes:
"My God! Even a chicken can install debian if you just put enough grain on the enter key"

My god i love that quote, i read it and i couldnt stop laughing for like 5 mins.

---

### Post by weblordpepe on 2007-05-11
It would make an -awesome- youtube video. A chicken installing linux.

---

### Post by Robert98374 on 2007-05-11
Yeah thats for sure, it would totally dispel all those myths about Linux is hard to install

---

