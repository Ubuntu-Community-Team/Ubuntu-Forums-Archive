---
title: "Beginner needs help with Ubuntu Studio"
date: 2013-02-03
forum: Ubuntu Studio
---

### Post by DjRadu on 2013-02-03
I am an amateur dj and music producer of electronic dance music and i terminated all my relations with windows,i have a few ideas of ubuntu studio and the software in it but i have some major questions :

1. How to clean up my system like you do in windows; Disk Cleaning, DIsk Defragmentation, optimization just like in windows, using cleaning and optimization software in windows, advanced system care, ccleaner, System Mechanic, registry defrag and others for example. Basically how to clean up, maintain and optimize Ubuntu Studio, Software, Ideas, .ETC. I also installed LMMS (Linux Multimedia Software) from Terminal and wine and wine related stuff installed with lmms does this affect the way to maintain, cleanup and optimize Ubuntu Studio. What software or methods to clean, optimize and maintain Ubuntu Studio

2. Do I need a firewall or an antivirus for Ubuntu Studio, and what are those programs - Firewall & Antivirus in case I need it. Also, how would I configure it.

Sorry for my bad english , im from Romania, and i hope youl give me as much tips and advice as you can on this thread of this great comunity,i have searched all this things but its allot to dig for  beginner and i want to become ,in time, a good ubuntu user, and sorry if i repeated allot !THANKS ALLOT :) RADU !

---

### Post by snowpine on 2013-02-03
Welcome, Radu!

1. not necessary
2. not necessary

Ubuntu is easy! :)

---

### Post by CrocoDuck on 2013-02-03
> **snowpine said:**
> Welcome, Radu!

1. not necessary
2. not necessary

Ubuntu is easy! :)

Yeah. Linux doesn't need to be cleaned or defragmented:  because of its design it doesn't go into rubbish accumulation and the filesystem doesn't fragments files. To install software you can easily use ubuntu software center, shipped with any ubuntu release. You will find a lot of guides to install software from terminal too. An antivirus is not required: this is controversial, but there are not currently viruses that can infect linux, and the most dangerous ones you could invent need your explicit permission to infect the system (and you are not going to give them this permissions;)). As always, install only programs that comes from trusted sources and you will not have any trouble (you will not infect your system just by going on internet as it happens with windows). Be careful using browsers: this is general, for any OS (as browsers can be a lot "os-indipendent"). Don't memorizing passwords and usernames into your browser is the best way to be invulnerable to the malware that could run "into" the browser. You can configure a firewall too, I never done it. Here a guide: [https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html) .

---

### Post by DjRadu on 2013-02-04
Ok i got it untill now,no antivirus,no firewall.But i did see some software called BLEACHBIT,SWEEPER,GCONFCLEANER witch they say its for maintainance,do i need them if i install,uninstall or reinstall software (more often some times) ? As i said i installed linux multimedia studio and allongside installed WINE could this be a thing that i need antivirus,firewall and maintainance,cleaning and kind of defragment ? Because of the WINE thing witch is used just for LMMS ? Thank you all for the answers and sorry,again,about my english and about my repetittive beginer talk :-D

---

### Post by mastablasta on 2013-02-04
> **DjRadu said:**
>  As i said i installed linux multimedia studio and allongside installed WINE could this be a thing that i need antivirus,firewall and maintainance,cleaning and kind of defragment ?
 
no.
 
i mean windows virus can't affect linux system as it is a comepltelly different OS. works in a different way. so you can have it on computer but it won't launch itself and it won't spread. just like oyu cna't launch windows programmes.
 
as for the firewall - it's actually installed just not enabled because linux doens't listen to any ports by default. you can install graphical interface called gufw to it. or do it like on servers and modify config files.
 
defragmentation is not necessray as ext filesystem have very, very little defragmentation. almost 0.
 
there are claning tools. but they are not so good. i mean they can cause trouble if you don't know what you can (is safe) and can't clean. they are not necessary. there is a safe pruge command f oyu want to remove all bits and pieces.
 
otherwise programmes in linux do not bring dependencies (for example .dll files in windows) with them so they are A LOT smaller than their windows version. they almost always share their dependencies among them. which is sometimes a good thing but somtimes this can cause issues (but if you install from software center you won't have any issues).
 
you can see how much space the whole system takes and you will see that even with plenty of programmes it is a lot less than windows. additionally as i mentioned before since the system is not really fragmanted having more installed programmes won't slow down your computer.
 
otherwise i think there is computer janitor and also ubutnu tweak has a "cleaning "untility if you need more disk space.

---

### Post by DjRadu on 2013-02-04
THANK YOU ALL SO MUCH IT WAS A BIG HELP. Now i got a new question.In windows there are places lice PROGRAM FILES and stuff were you can look for things or load libraries of sounds for music making for example in windows it kind like this c : program files..flstudio...samples folder etc. but in ubuntu i cant seem to find where or from where to load samples or any other data,it seems ( for me as a beginner ) so messed up but I WANT TO LEARN to navigate trough system folders and use the terminal,how to do stuf like above mentioned ? Thank you !

---

### Post by jejeman on 2013-02-04
What samples you want to load and in which software?
Does LMMS not have already all it's samples avaible?
Programs are instaled in /usr, but you rarely need to go there.
You need to stop thinking as windows user.

---

### Post by DjRadu on 2013-02-04
**jejeman** You are right i got to stop beeing a window :lolflag: so there in the  /usr . Gotta have patiance im a beginer who divorced windows ! Thank you !

---

### Post by DjRadu on 2013-02-09
Another question.  I can install software from Ubuntu Software Center,and if i download from internet i can install them if the program ends wit  *.deb but wath about software downloaded that is made for linux wich seems to be archived and when extracted i cant install the ? Can i install Linux software on ubuntu or other software not debian ? Thanks !

---

### Post by black3agl3 on 2013-02-09
Depends on what is within the archive. Sometimes its binary files. You just run them and that's it. Sometimes you will have to go into more complicated stuff like compiling them. Either way, there will be usually a text file within the archive which will point you to what you should do. Look out for names like **readme, help** and stuff like that.

Oh and i think you should take your time to get used to linux. I'm under the impression that you are trying to rush through the process of switching from windows to linux.

---

### Post by wildmanne39 on 2013-02-09
Hi DjRadu, please use normal fonts.
Thanks

---

### Post by DjRadu on 2013-02-13
So hear is another new linux user problem:

my hdd is 500 Gb and has 2 OS on them; [Ubuntu]("http://ubuntuforums.org/ubuntustudio.org/") studio and [Artistx]("http://artistx.org/blog/") Now my question is the next one ,  if i want to erase the arist x partition and instead of artist x install another OS how can i do it,first installed is Ubuntu Studio,second Artistx ! In the photo you will see how the 2 partitions look,but i dont know witch one to keep,i mean witch is ubuntuu studio , how to delete artistx and use ishis space for another os ? Thank u ! :D

[[IMG]http://imageshack.us/scaled/thumb/845/screenshot0214201301530.png[/IMG]](http://imageshack.us/photo/my-images/845/screenshot0214201301530.png/)

---

### Post by snowpine on 2013-02-13
Take a look at the "mount point" column and you will see the current OS is using /dev/sda6 as its / (or "root" as it is sometimes incorrectly known) partition.

You didn't mention whether you took that screenshot in Ubuntu or ArtistX. If you took the screenshot in ArtistX and you want to replace ArtistX, then you should install the new distro on /dev/sda6. If you took the screenshot in Ubuntu, then presumably ArtistX is the unmounted /dev/sda1 partition, and so you should install the new distro on /dev/sda1 if you want to replace ArtistX.

Of course you should make full backup to an external drive (and then disconnect the drive ;)) before you make any permanent changes to your system.

---

### Post by DjRadu on 2013-02-13
> **snowpine said:**
> Take a look at the "mount point" column and you will see the current OS is using /dev/sda6 as its / (or "root" as it is sometimes incorrectly known) partition.

You didn't mention whether you took that screenshot in Ubuntu or ArtistX. If you took the screenshot in ArtistX and you want to replace ArtistX, then you should install the new distro on /dev/sda6. If you took the screenshot in Ubuntu, then presumably ArtistX is the unmounted /dev/sda1 partition, and so you should install the new distro on /dev/sda1 if you want to replace ArtistX.

Of course you should make full backup to an external drive (and then disconnect the drive ;)) before you make any permanent changes to your system.

Thank you verry much,the screensoot is in ubuntu studio ! So delete that partition,boot and reinstall ?

---

### Post by snowpine on 2013-02-13
> **DjRadu said:**
> Thank you verry much,the screensoot is in ubuntu studio ! So delete that partition,boot and reinstall ?

No need to delete any partitions (when you install, it will erase and replace whatever's currently on the partition). 

I have no idea what you mean by "that partition." Please use the correct name (such as /dev/sda1) if you want to make your meaning clear. If you took the screenshot in Ubuntu Studio, then Ubuntu Studio is /dev/sda6, and ArtistX is presumably /dev/sda1.

---

### Post by DjRadu on 2013-02-14
Yet another problem,i got a friend to install (i installed) Ubuntu Studio on his machine,he enjoys it,problem is he wants windows xp as well, i tarted installing and when i got to the point of deleting,formatting,installing it wass a total blak out,how in the world to install windows xp as a second OS when first OS is Ubuntu (Ubuntu Studio) in this case ? Thank you ! :-)

---

### Post by snowpine on 2013-02-14
> **DjRadu said:**
> Yet another problem,i got a friend to install (i installed) Ubuntu Studio on his machine,he enjoys it,problem is he wants windows xp as well, i tarted installing and when i got to the point of deleting,formatting,installing it wass a total blak out,how in the world to install windows xp as a second OS when first OS is Ubuntu (Ubuntu Studio) in this case ? Thank you ! :-)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by DjRadu on 2013-02-14
[snowpine]("http://ubuntuforums.org/member.php?u=479885") thank you,oh and the Linux/ubuntu world its wonderfull:->)

---

### Post by DjRadu on 2013-02-23
And another question,i want to buy the Korg NanoKey 2 and i wanted to know if it is compatible with Ububuntu Studio,or ubuntu & linux in general, how to install what to do :-) Thanks ! ;)

---

### Post by jejeman on 2013-02-23
I have nanoKEY1. It works, I guess the nanoKEY2 will also.
Just plug it, and it should be recognised automaticly as MIDI device. Just to understand, nothing will popup or show. It will just appear as ALSA MIDI device on the ALSA tab in Qjackctl or other views showing MIDI devices.

NanoKEY1 is poor built, it is hard to play on it, keys will stop working.
Buy it only if you really need it - traveling with laptop.

---

### Post by DjRadu on 2013-04-04
And one more thing please,if i only have installed Ubuntu Studio,but i install windows software like LMMS Linux Multimedia System or other free and open source software that runs on windows and i install it in ubuntu studio trough wine can i get affected by viruses,trojans,worms,spyware,adwer,etc ? Do i need special "cleaning" stuf for the wine part of ubuntu other than bleachbit or remove orphaned packages ? Thank you !

---

### Post by jejeman on 2013-04-04
Why would you use windows versions of the program that also has linux version?

WINE can run windows viruses, so be carefull. It will not contaminate Ubuntu Studio.
If you install just free software, as you mentioned, you will not get any malware.
There is no need for cleaning tool for WINE. Simple virus scaner will suffice, if you are looking for that.

---

### Post by zequence on 2013-04-04
I would just like to point out that having a Firewall is really recommended, but usually you have this on your router or default gateway. If you are connecting directly to your ISP, without a firewall in between, you should think about getting one. It is possible to configure firewalls in Ubuntu as well, but usually, it's just easier to use a router for that.

---

### Post by DjRadu on 2013-04-05
Thank you ! Problem is when i install LINUX MULTIMEDIA STUDIO from Ubuntu Software Center WINE automaticly installs as well ! But even with auto installation of wine windows viruses,trojans and spyware can not affect my ubuntu studio witch is single on a 500Gb hdd right ? Sorry for my bad english !

---

### Post by zequence on 2013-04-05
I don't know how possible it is to get Windows trojans or viruses through WINE. But, merely installing WINE should not pose much of a security risk. After all, it won't run until you start Windows software.

LMMS has support for VST I believe, and it is only the 32bit version of LMMS that depends on WINE.

---

### Post by DjRadu on 2013-08-28
I meant if you install a windows software in ubuntu studio (my case) trough wine if its posible to get malware,viruses,trojans,spyware,etc. Thanks !

---

### Post by jejeman on 2013-08-28
Everything what is in the code of the program will be executed.
But, you can not expect that win trojan will install it self and set self up to be run on every startup of the Ubuntu. Because it is not win OS.

---

### Post by su:bhatta on 2013-08-28
what version of Ubuntu Studio are you using? 

Ubuntu Studio 13.04 comes with LMMS preinstalled i.e. it has LMMS once you install Ubuntu Studio 13.04! Also, LMMS is for Linux only, why need Wine for that?

As Jejeman pointed out: Please don't bother so much about windows viruses, as they cannot run in Linux environment and hence hardly poses any threat!

---

### Post by cub on 2013-08-28
> **bhattabhishek said:**
> what version of Ubuntu Studio are you using? 

Ubuntu Studio 13.04 comes with LMMS preinstalled i.e. it has LMMS once you install Ubuntu Studio 13.04! Also, LMMS is for Linux only, why need Wine for that?
Probably to use VSTs which depends on Wine.

---

