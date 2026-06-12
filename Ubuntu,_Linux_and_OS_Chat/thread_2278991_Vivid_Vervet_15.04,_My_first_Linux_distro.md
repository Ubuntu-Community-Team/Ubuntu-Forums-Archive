---
title: "Vivid Vervet 15.04, My first Linux distro"
date: 2015-05-20
forum: Ubuntu, Linux and OS Chat
---

### Post by acedia2 on 2015-05-20
After doing tons of research, I decided linux is right for me. Currently I am running Vivid Vervet 15.04 on a desktop @ 3.4ghz ×8cores, 8 gb of ram and 350 GB of HDD (will be upgrading to SSD once my order arrives)
My NVIDIA graphics card is only 1gb and is running on a driver I am unfamiliar with. 

First Impressions:
Amazed how refined the interface is. My roommates and I found it easy to do all the important things like email, word processing and streaming media on their own. For something I made off a spare thumb drive and a bricked/dead windows 7 PC, I couldn't be happier and it was free! (Students cannot denie that last point)

Digging deeper:
I have never entered a command line in my life and after a few days it is my absolute go to for everything. It was hard learning how to get into root acess and add applications and even harder to remove applications. It seemed like solving one problem exposed me to another. It was great having vast resources online to guide me through. Currently I'm trying to set my PC as a media center/hub for all my devices. 

Current to do list:
1) Set up multiple screens 
2) Enable my S5 to mount and read contents
3) Find a controller/manager for graphics
4) Enable Steam, Origin and other services
5) Learn command lines and terminal 

2. After installing mtp tools and restarting my computer, I still get mounting errors. Files on the device had no memory and would give me an error when viewing photos on my phone. 
I turned off USB debugging and it allowed me to mount and acess my Samsung galaxy S5. Then I went into properties and it calculated the amount of memory taken up on my phone. When trying to view the photos I was unable to. After inspecting the file size in properties, I copied it to the desktop and the picture came up in the thumb nail and I could view it normally. This goes with music files and movies once they are moved onto the desktop. Unfortunately I am still not able to view the files freely when acessing the mounted device and the thumbnails are just the file types. This will be my next troubleshoot. I'm almost certain it's something to do with the security on my phone. It seems that if it's unlocked and awake it works better but any suggestions would help. Also I noticed my android security ramp up a bit when doing this so I might disable it and try again.

Other Interests:
Read if getting ubuntu on my phone is a good idea or not. My device is not rooted at the moment but could be in the future. Has anyone tried on a newer smartphone? Personally I want something less bulky. More than 70% of my phones ram is eaten up by feature I don't use and bloated ware. 

Tomorrow I plan to install photo editing software and a music player that's compatible with my devices. 

So far it's been a good learning experiance, I wanted to make a post and test the waters I guess. Feedback on forums have really helped me and I plan to post my problem and fix as a go along.

What's the best forum/sub for casual linux related discussion? Anyways that was lots of text, cheers.

---

### Post by dino99 on 2015-05-20
> What's the best forum/sub for casual linux related discussion? Anyways that was lots of text, cheers.
Looks like you have already found it ):P

you can click on the links below to get more info/howto/wiki

---

### Post by acedia2 on 2015-05-20
> **dino99 said:**
> Looks like you have already found it 

Awesome, I'll do my best to keep track of exactly what I do, fix and change. Once I get a bit more technical, my feedback will be of better use. Right now it's just exciting leaving  another OS for an open source OS. Not only is it free, I am learning something. :D

---

### Post by SeijiSensei on 2015-05-20
Just a cautionary note. 15.04 will only be supported through next January.  Next time you install Linux, you should choose an LTS version.  They come out every other April; the current one is 14.04 (April, 2014) and will be supported until [2019](https://wiki.ubuntu.com/Releases); the next LTS release will be available a year from now.

---

### Post by wildmanne39 on 2015-05-20
*Thread moved to **Ubuntu, Linux and OS Chat**.* Welcome to the forum and Ubuntu!

---

### Post by coffeecat on 2015-05-20
> **SeijiSensei said:**
> Next time you install Linux, you should choose an LTS version.

Unless, like me and many others, they want to run the latest version, are happy to tolerate a few minor glitches, and are happy to re-install or upgrade every 6 months. I would never tell someone what they **should** do, but I would agree with your sentiment if it is intended to caution a newcomer that better stability and a longer release life are to be found in the LTS releases.

And...

@acedia2, welcome to the forums. Happy Ubuntu-ing! :)

---

### Post by grahammechanical on 2015-05-20
Hi

> It was hard learning how to get into root access and add applications  and even harder to remove applications. It seemed like solving one  problem exposed me to another.

Use the Ubuntu Software Centre. It will tell you when it needs to run with root or administrator privileges. It will ask you to authenticate by putting in your password. And this wiki page will explain the commands that can be used in a terminal to update/upgrade and install packages and remove them. But we do not have to do things the hard way.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

As for installing Ubuntu on a phone it is a completely different situation to installing Ubuntu on desktop and laptop machines. The Ubuntu phone OS is meant for phone manufacturers to pre-install on devices for retail. The code is available for experimentation by those who want to port Ubuntu for Devices (as it is called) on to different devices.

Follow the links

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/)

Or wait awhile and buy a new Ubuntu phone.

[http://www.bq.com/gb/aquaris-e4-5-ubuntu-edition](http://www.bq.com/gb/aquaris-e4-5-ubuntu-edition)

[http://www.mobileworldlive.com/meizu-debuts-ubuntu-phone-developers-china](http://www.mobileworldlive.com/meizu-debuts-ubuntu-phone-developers-china)

Good things are coming.

Regards.

---

### Post by neu5eeCh on 2015-05-20
> **SeijiSensei said:**
> Just a cautionary note. 15.04 will only be supported through next January.  Next time you install Linux, you should choose an LTS version.  They come out every other April; the current one is 14.04 (April, 2014) and will be supported until [2019]("https://wiki.ubuntu.com/Releases"); the next LTS release will be available a year from now.

Not necessarily. Much depends on your hardware. Choosing an LTS version, depending on the kernel and what Canonical has chosen to back port, could be counterproductive. For instance, installing LTS on any of the newest laptops or desktops, like the latest Lenovos and HP Streams, would be (to put it positively) "a teachable moment".

---

### Post by craig10x on 2015-05-20
Upgrades seem to work very well these days, as long as you don't make heavy modifications to the system...just install regular apps, and remember to turn off any ppas (like if you install google chrome from their website, it adds a ppa in your software sources to update chrome) prior to doing the upgrade (turning them back on after you're on the new version)... they usually work out fine...so i think there is no harm in always using the latest version...in fact, gets you improvements in the kernel, drivers, new versions of apps, new features...LOTS of advantages...

---

### Post by monkeybrain20122 on 2015-05-20
Instead of the Software centre, get synaptic. Much better package manager.  Either install it from the Software Centre (so that you can forget about the SC) or via command

sudo apt-get install synaptic

---

### Post by acedia2 on 2015-05-20
Thanks for the feedback everyone!
I have more questons now.
After 9 months of support,  what happens to the vivid vermet distro, am I able to install new applications and update drivers extra? 
My Ideal distro would be very light, updates very easy and will last a really long time without crashing. (Hence my last OS's I paid for crashes every 2-3 years) 
Also it just occurred to me I have no torrent, which would be the most standard for Vivid vervet? 
Is Antivirus/Firewall even important? Im worried about performance and security conflicts. 

After reading those links on the ubuntu phone OS, I should just wait and buy a second phone to mess around on. I can't really afford to brick this phone since I use it for work.

---

### Post by monkeybrain20122 on 2015-05-20
> **acedia2 said:**
> Thanks for the feedback everyone!
I have more questons now.
After 9 months of support,  what happens to the vivid vermet distro, am I able to install new applications and update drivers extra? 
My Ideal distro would be very light, updates very easy and will last a really long time without crashing. (Hence my last OS's I paid for crashes every 2-3 years) 
Also it just occurred to me I have no torrent, which would be the most standard for Vivid vervet? 
Is Antivirus/Firewall even important? Im worried about performance and security conflicts. 

After reading those links on the ubuntu phone OS, I should just wait and buy a second phone to mess around on. I can't really afford to brick this phone since I use it for work.

After 9 months you will have to move to a newer or older release (it would be either 15.10 or back to14.04 which will still be supported) (I strongly advise against 'upgrade', a fresh install is a lot faster and less problematic) So if the priority is low maintenance, you should stay with 14.04. It is supported til 2019, but you have the option to migrate to the next LTS in 2016 April (16.04). Believe me unless you run a server you won't want to stick with a LTS for its entire 5 year life span, at some point it just become too outdated.

The catch with LTS is that software gets old. Software in official Ubuntu repos doesn't get feature or version updates, only security updates so all applications in the software centre are old. But in Ubuntu you have the options to selectively update to the latest through ppas. Some here have a thing against ppas because they are not 'official' IMO they vastly exaggerate the risks.Personally I find it a most attractive feature of Ubuntu comparing to Debian or Arch. There is no easy mechanism to install up to date software in Debian (unless you are on Debian unstable which is very unstable) and in Arch everything gets updated, including system components. With ppas you can choose which to upgrade and as long as it doesn't bring in too many dependencies the risk is localized and problematic updates can be rather easily reversed (In Arch's model a bad upgrade of key system components could break the whole thing, even though Arch users swear by its stability, I have my doubts)


Edited: But if you are interested in Unity 8 and the phone stuffs maybe you should probably get a test partition to run a developemental release on the side, those things are under rapid development and not fit for everyday use.

---

### Post by SeijiSensei on 2015-05-20
> **coffeecat said:**
> I would agree with your sentiment if it is intended to caution a newcomer that better stability and a longer release life are to be found in the LTS releases.
Yes, that was exactly my point.  For instance,
> After 9 months of support, what happens to the vivid vermet distro, am I able to install new applications and update drivers extra?
I'll let you explain the process of upgrading between non-LTS versions.  I haven't done it in ages, so I wouldn't want to lead someone astray.

In general, [I think new users should be encouraged to install LTS releases](http://ubuntuforums.org/showthread.php?t=2276862) unless they have some hardware incompatibility, or need a specific feature, that requires a more recent release. I might have held a different opinion five or ten years ago when Linux distributions were less stable than they are today.  I haven't upgraded to Kubuntu 15.04, for instance, because I want to wait at least another 6-12 months until KDE5 has all the bugs worked out. I have a copy running in a VM for testing and evaluation purposes but haven't yet seen much reason to switch.

---

### Post by acedia2 on 2015-05-20
> **monkeybrain20122 said:**
> Personally I find it a most attractive feature of Ubuntu comparing to Debian or Arch

I am finding, the more I learn about using Terminal, the more comfortable I get with using commands to install and remove applications. I was originally scared of anything that would require me to come up with lines in order to do things verse Icons and interfaces. You mentioned Arch, at first I wanted something I could just run and not be so lost, after some more exposure I might consider it. I was warned that it is not something someone should play around with when starting out because you are almost guaranteed to crash it if you play around. 

By the time I am able to upgrade from 15.04, hopefully I will have enough knowledge to do it successfully. I have about 2 months of free time coming up once I finish the first summer class session. I plan to learn 15.04 in and out in that period.

My work phone is currently official so until I know enough about what I am doing, I will probably stay away from rooting it. I do however have a original Iphone 4 that I would have no problem testing on. My latest device is the pebble steel, it has been fun tinkering with that, once it gets boring I'll boot up the old Iphone and root it. 

I am soon going to get a tablet as a family member has got a new one, I can't wait to get my hands on it and see what I can do on it. If I do buy one, do you have any suggestions as to what would be the best hardware wise to tinker with? I'm not to worried about cost since I might be able to write off the expense.

Thanks and sorry about the technical post, my thread was moved, I should probably stay more on point when posting. :popcorn:

---

### Post by acedia2 on 2015-05-20
> **SeijiSensei said:**
> [I think new users should be encouraged to install LTS releases]("http://ubuntuforums.org/showthread.php?t=2276862") unless they have some hardware incompatibility, or need a specific feature, that requires a more recent release.

I totally agree with that statement. Right now I have 15.04 on a thumb drive and my friend wants me to breath new life into his PC. It was only after I installed 15.04 I realized most of the Q&A revolves around older versions with larger user base. Perhaps I will format my thumb drive and put an earlier version on it for my friend. 

On my desktop I cant even boot up my original OS and I have tons of media I would like to gather from it. After my lab today I am going to stay up all night and figure out how to rip the media off the other partitions. Either try to fix the start-up files or use a tool to extract it. 

Thanks for sicking around, it is awesome how active everyone seems. :D

---

### Post by monkeybrain20122 on 2015-05-20
> **acedia2 said:**
> I totally agree with that statement. Right now I have 15.04 on a thumb drive and my friend wants me to breath new life into his PC. It was only after I installed 15.04 I realized most of the Q&A revolves around older versions with larger user base. Perhaps I will format my thumb drive and put an earlier version on it for my friend. 



By installing in a thumb drive I take it to mean running a live session? That is not a real install and if persistence is not enabled you will lose all settings and things you may have downloaded or upgraded on reboot.

---

### Post by acedia2 on 2015-05-20
> **monkeybrain20122 said:**
> By installing in a thumb drive I take it to mean running a live session? That is not a real install and if persistence is not enabled you will lose all settings and things you may have downloaded or upgraded on reboot.

Two options:

I have the option to run 15.04 live off of my thumb drive and hold 4gb of data, this comes handy when on other computers and want to use 15.04 and save what I do and leave the PC without leaving anything behind. 

Also, I have the option to install the full 15.04 operating system and create a partition for it from the thumb drive. My computer was black screen of death and now it runs like new with the full 15.04.

Edit: Right now I am learning how to use Lynx (A browser in terminal, yes its a text only browser) in order to preform operations when the only option is terminal. Super old school, but tons to learn and I have an old pentium in my closet that could use it.

---

### Post by monkeybrain20122 on 2015-05-20
> **acedia2 said:**
> Two options:

I have the option to run 15.04 live off of my thumb drive and hold 4gb of data, this comes handy when on other computers and want to use 15.04 and save what I do and leave the PC without leaving anything behind. 

Also, I have the option to install the full 15.04 operating system and create a partition for it from the thumb drive. My computer was black screen of death and now it runs like new with the full 15.04.

There is a third option, if you have a spare hard drive (you can buy one, but even an old one taken from a dead computer is fine provided the drive is not dead of course) and do a full install in it so that it will become portable just like the thumb drive but can be customized and used like a real installation(well it IS a real installation). Theoretically you can do it on a thumb drive (8G would be enough for a basic install, it would use less but good to have some room for comfort) but in my experience performance is poor, it is slower than live because it doesn't run in ram like a live usb. But installing in an external hard drive gives you full speed, except boot may be a little slower comparing to internal install depending on where you want to boot it. 

Some people here talk about usb2 vs usb3 but I haven't noticed any difference in speed working from an external hard drive or internal one using a usb2 port, it is very fast. I think I am qualified in saying this because for a year I ran ubuntu like this on my work's Windows machines. I didn't notice any lag vs an internal install and much faster than Win7 in the internal drive. I also brought the hard drive when I visit my parents and booted it off my dad's labtop so I didn't have to carry mine, no speed difference.

---

### Post by acedia2 on 2015-05-20
On campus at the moment but I find portable operating systems interesting as you can take advantage of hardware that you encounter. I heard about new thumb drives that are more like SSD's with a integrated chip. One I was looking at recently was 120gb and supports both USB 2 and 3. I think this will likely be the future since carrying around a entire operating system to work, school and home on something that fits on a key chain is a real game changer. Personally having this on a micro SD on my phone and docking it to hardware would be ideal. I'm excited to see the possiblites once I get a better grip on open a source OS.

---

### Post by craig10x on 2015-05-20
Upgrading is actually a quite easy process on ubuntu...you will just need a few "tips" before you do it for the first time (such as the things i mentioned earlier) although it does help to have a good speed on your internet connection because there is a lot of packages to download...I have a pretty high speed cable internet connection so for me the 1300 packages or so download in about 2 minutes...;)

Once that is done, the upgrade only takes about an hour and at the end, a little "clean up janitor" offers to remove packages you no longer need from your old version (you know like old kernels for example) so i always say "yes" when it asks me at the end :D

Just as a precaution, it''s always a good idea to back up important data on an external drive (ex: usb flash drive) and download and burn an iso dvd of the new version....JUST IN CASE you end up needing to do a clean install, but odds of that are unlikely...

---

### Post by acedia2 on 2015-05-20
I heard it is best to strip your system of any add on's and revert back to the original OS before upgrading to avoid errors. It is probably not necessary but when the time comes I'll know the answer by then. I'm wondering what I can put on a cloud storage, If it's anything then I don't need to worry about buying extra hardware!

---

### Post by SeijiSensei on 2015-05-20
> **acedia2 said:**
> Edit: Right now I am learning how to use Lynx (A browser in terminal, yes its a text only browser) in order to preform operations when the only option is terminal. Super old school, but tons to learn and I have an old pentium in my closet that could use it.
You might take a look at elinks as well.  I haven't used lynx in a very long time now, but I do use elinks from time to time.  Just today I used it to check whether a web site was visible from a machine where I was running a shell using SSH.  elinks is in the repositories.

---

### Post by acedia2 on 2015-05-21
Interesting, I should defiantly check it out. If it is really basic then it should mesh well with my ancient hardware. I'm mostly doing it for educational purposes and curiousity sake. I may find a instance where I can only use it. If that's the case then it's a good thing I tried it out.

---

### Post by monkeybrain20122 on 2015-05-21
> **acedia2 said:**
> I heard it is best to strip your system of any add on's and revert back to the original OS before upgrading to avoid errors. It is probably not necessary but when the time comes I'll know the answer by then. I'm wondering what I can put on a cloud storage, If it's anything then I don't need to worry about buying extra hardware!

Instead of going through that trouble and wait for an hour to "upgrade", --during which a lot can happen, --why not just do a clean install? It takes me 15 minutes to install the system, another 20 to reinstall the software. If you have a separate /home then your settings will be kept (don't format /home)

---

### Post by craig10x on 2015-05-21
I know monkeybrain20122 isn't too fond of the upgrade process...but i am just going by my own personal experience....i can tell you that i originally installed 14.04 when it came out, then upgraded to 14.10 when that came out, then to 15.04 and each time it was 100% perfect...but as i mentioned earlier, i make sure i uncheck any ppas, back up my data on a usb flash drive, and burn a copy of the new version on an iso (just in case)...but never ended up calling upon by "back up plan"... ;)

Oh, one of the upgrades was only 99.99% perfect...one of the icons disappeared from my unity dock launcher, so i needed to open that program and "re-pin" the icon to the unity dock :mrgreen:
I can tell you what is NOT reliable....using the upgrade option that is available on the live session iso installer....i used that in the past....and it DOES often have problems....It's best to do the upgrade using the software updater method because it is done while you are actually ON your hard drive...far more reliable!

---

### Post by kurt18947 on 2015-05-21
> **acedia2 said:**
> On campus at the moment but I find portable operating systems interesting as you can take advantage of hardware that you encounter. I heard about new thumb drives that are more like SSD's with a integrated chip. One I was looking at recently was 120gb and supports both USB 2 and 3. I think this will likely be the future since carrying around a entire operating system to work, school and home on something that fits on a key chain is a real game changer. Personally having this on a micro SD on my phone and docking it to hardware would be ideal. I'm excited to see the possiblites once I get a better grip on open a source OS.

Some of the fastest flash drives use SSD controllers so the limitation becomes RAM/connection speeds. I have a full Mint 17 install on a 16 GB. flash drive. It is somewhat slow but it works. I've had better luck with generic flash drives than I have with branded except Sandisk. I've had decent luck with Sandisk Cruiser drives. Sandisk Extreme is one of the lines that use an SSD controller (at least some do) so it would be interesting to do a full install on one of those.

---

### Post by flaymond on 2015-05-24
I avoid upgrading and do fresh install. Also, using LTS version is much better, lesser bugs and stable, plus it's supported years longer. Using Terminal is very fun, and it's free and open source!

---

