---
title: "Close to stop using Ubuntu"
date: 2005-08-11
forum: The Cafe
---

### Post by granite230 on 2005-08-11
Hi, I've been using Ubuntu for about half a year now. I started with Warty, my very first Linux installation!
I've learned a lot from Ubuntu but since I upgraded to Hoary I really cant trust my computer anymore!
Every now and then (without warning) X fails to start and I see a blue/white/red screen saying something failed, could not start X blah blah blah. Then a login prompt appears.

After I reboot the system, it starts perfectly like it should. However I'm pretty sure my dad will not be amused when he sees a screen like I described above. He knows nothing about computers and I'm the one who forced him into using Ubuntu.

Also, I reinstalled Ubuntu about 4 times within that 6 months... I'm seriously thinking about trying another distro now... 

I'm not even sure that it's Ubuntu's fault but I really cant use these random failures.

---

### Post by Stormy Eyes on 2005-08-11
If you want help, it would *really* help if you gave us some actual information -- like  information about your hardware and how you upgraded to Hoary -- instead of just whinging. Meet us halfway here, please.

---

### Post by henriette_holm on 2005-08-11
Hi.
Have you tried testing some of your hardware - like ram, disk etc. It sounds a bit like a hardware failure. No computer - no matter what OS - should act like that.

-Henriette

---

### Post by KingBahamut on 2005-08-11
Sounds like xorg is no happy. Is your video card or monitor questionable?

---

### Post by nocturn on 2005-08-11
When it shows that error, it probably gets logged to a file in /var/log

Can you send us the error messages?

I'm running Hoary fine on 3 machines, so it must be something with your configuration.

---

### Post by granite230 on 2005-08-11
The first time I used Hoary I dist-upgraded from Warty. The first-to-last reinstall was from a shipit cd. 

My hardware:

Intel Pentium 2400MHz
2 x 128 SDRAM
NVidia GeForce 4 MX 400
I cant see what's on my harddisk but it's a Seagate or a Western Digital (160GB)

I also have another harddisk with Windows XP on it, that harddisk boots perfectly, no hardware failures at all! I'm not dual booting, I just switch the drive because I barely use Windows XP.

It's a little hard to explain the problem I'm experiencing in Ubuntu since I can't make a screenshot of it and I don't know if and where the log files are saved.

---

### Post by -Rick- on 2005-08-11
For the gfx card, are you using the nv driver(default) or the binary drivers provided by nvidia?

---

### Post by granite230 on 2005-08-11
I usually install the driver from the NVidia website, but I had some problems with it. Then I tried the binary packages but that also gave me some problems. Now I'm using no drivers at all because I gave up playing World of Warcraft on Ubuntu so I don't need the driver anymore. But I'm still having problems with X. I tried a lot of conigurations and reinstalled a lot of things but I never seem to get things work right.
I always have some booting problems, random, usually solved by a reboot but not always. Sometimes I have to reboot a few times and sometimes I try to reinstall everything but it's just a matter of time before something happens again.

---

### Post by Stormy Eyes on 2005-08-11
Exactly how old is this machine? I had to replace mine after three years because the components got flaky and caused all kinds of crashes.

---

### Post by tikal26 on 2005-08-11
it souds like a hardware issue Maybe is the hardrive since the windows hardrive sis different. Have you try running memtest

---

### Post by Seti on 2005-08-11
The best thing you could do if you can't find any mention of the same error in your logs is to pay very careful attention the next time you have the problem, and then write down the error messages that you get when it happens again. 
The previous poster has already mentioned running memtest (to check your RAM), in addition, it could also be a problem with your disc as well. There are utilities that you can use that will check your harddrive for problems; my girlfriend had probs with the drive on her laptop once and I was able to diagnose the problem using a live CD. I don't know if Knoppix has it or not, I do know that Mepis comes with a disc-diagnostic tool that will tell you if you have bad blocks. Also, maybe take another close look through /var/log/syslog and see if there is anything there indicative of a problem.

Cheers!

---

### Post by ubuntu_demon on 2005-08-11
have you done a memtest ? (in the boot options)
are you sure your computer isn't too hot or dusty ?

First do a memtest. Then you should try cleaning your pc up and check whether it acts strange when you run it with the case open.

It could also be a different hardware problem (like a faulty motherboard or psu)and you should post some logs if my suggestions don't work. 

You can also do some stuff like cpuburn. Try to think a bit logical and do a stepwise check. I don't know a nice english website with such a checklist and I don't have more time right now.

edit:
Like Seti suggested try a live disc so you are sure it's not your harddrive.

good luck!

---

### Post by granite230 on 2005-08-11
okay, here's a few facts:

- My computer case is always open on one side (it's standing next to my desk so nothing much can get in it anyway).
- The computer is not too hot or dusty.
- The computer is about 2.5 years old.
- I have tried a live cd (I think it was Knoppix) and it did mount my harddisk.
- This harddisk isn't even a year old. The first thing installed on it was Warty. After that the only thing this harddisk has ever seen is Hoary.
- When I plug in the other harddisk with Windows XP on it, I don't have any problems I shouldn't have when running Windows.
- When I see the error again I will write some stuff down and post it.
- I'm trying to find some useful logs and running the memtest right now, I'll post the results later. 

Thanx for listening. Usually I'm not complaining a lot about little problems, but when I get home from work and see this error AGAIN after multiple reinstalls it becomes a little frustrating.

---

### Post by ubuntu_demon on 2005-08-11
also don't forget to check for bad sectors

---

### Post by WirelessMike on 2005-08-11
Hey--  He's from "Holland" and you're from "Netherlands."

Why not drive over there and help him?  Charge him a couple euros or somethin'

;)

---

### Post by KiwiNZ on 2005-08-11
What make of mainboard are you using ?
Random failures may well be indicative of a failing mother board. Closely check your mainboard for swollen or leaking capacitors.

---

### Post by granite230 on 2005-08-11
Yes, I've heard of that leaking capacitors stuff, but the thing is: I don't have any trouble/random failures when I'm using another OS.
I've been running memtest for over 5 hours without a single error and I cant find any useful log files.

I think it's a good idea to check my harddisk for bad sectors and stuff...
If I get the error again I will definately write it all down and post it!

btw, which log-file do you want to see? I really cant find anything useful.

---

### Post by ubuntu_demon on 2005-08-11
[QUOTE=granite230]Yes, I've heard of that leaking capacitors stuff, but the thing is: I don't have any trouble/random failures when I'm using another OS.
I've been running memtest for over 5 hours without a single error and I cant find any useful log files.

I think it's a good idea to check my harddisk for bad sectors and stuff...
If I get the error again I will definately write it all down and post it!

btw, which log-file do you want to see? I really cant find anything useful.[/QUOTE]
 syslog
dmesg
Xorg.0.log (if it turns out the video problem is a seperate problem)

---

### Post by ubuntu_demon on 2005-08-11
[QUOTE=WirelessMike]Hey--  He's from "Holland" and you're from "Netherlands."

Why not drive over there and help him?  Charge him a couple euros or somethin'

;)[/QUOTE]
 I don't have a drivers license (and I don't want one but that's offtopic)

granite230: you can add me on msn/icq .. maybe I can help you out a bit when I have time

---

### Post by Brunellus on 2005-08-12
[QUOTE=ubuntu_demon]I don't have a drivers license (and I don't want one but that's offtopic)[/QUOTE]

Get on yer bike and ride! :-)

My Dutch friend tells me that, at her high school, there was always a rivalry between the guys who rode Batavus and the guys who rode Gazelle--which is funny, because in the states, the rivalry was historically between Ford and Chevrolet (cars!).  

But for me, give me an old Nottingham Raleigh.

---

### Post by ubuntu_demon on 2005-08-12
[QUOTE=Brunellus]Get on yer bike and ride! :-)

My Dutch friend tells me that, at her high school, there was always a rivalry between the guys who rode Batavus and the guys who rode Gazelle--which is funny, because in the states, the rivalry was historically between Ford and Chevrolet (cars!).  

But for me, give me an old Nottingham Raleigh.[/QUOTE]
 :-P

---

### Post by KingBahamut on 2005-08-12
[QUOTE=ubuntu_demon]:-P[/QUOTE]
 Give me a Bontrager and im happy.=)

---

### Post by granite230 on 2005-08-13
okay this morning I got the message again!

here's what it says:

[I]I could not start the X 
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled. Please restart gdm when
the problem is corrected.

                            <Omodprobe: FATAL: Error inserting apm (/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/apm.ko): No such device

Ubuntu 5.04 "Hoary Hedgehog"(none) tty2

(none) login: [/I]

So after this I am able to login and all (without X of course) but I really don't like this message popping up randomly. After I reboot the system it works fine again and starts X perfectly like it should. After that it's only a matter of time before I see the message again.

I don't see any useful information in my logfiles. 
- syslog didn't contain a lot of info, I saw nothing strange. 
- dmesg probably logged my reboot, which was perfectly fine. 
I also searched my very long Xorg.0.log file on (EE)'s (error's) but nothing shows up.

---

### Post by Lord Illidan on 2005-08-13
A question.. You are using an Intel processor or AMD processor? And Pentium 2, 3, 4? Or Celeron?

I think that if you upgrade your kernel through synaptic, it will cease these problems..

---

### Post by granite230 on 2005-08-13
[QUOTE=Lord Illidan]A question.. You are using an Intel processor or AMD processor? And Pentium 2, 3, 4? Or Celeron?

I think that if you upgrade your kernel through synaptic, it will cease these problems..[/QUOTE]

Intel Pentium 4 2400 Mhz

But I don't know how to upgrade my kernel. Sounds a bit tricky.

---

### Post by Lord Illidan on 2005-08-13
So try to upgrade your kernel through synaptic..

Do a search for everything 686 related..

And install libc-686, the latest linux headers of 686, the linux image of 686, etc.. 

Don't install anything with SMP support, unless you have a dual processor machine..

Then do a search for 386 and and take out anything installed of 386..

It should work now..

---

### Post by granite230 on 2005-08-13
I can install headers for kernel version 2.6.10 and 2.6.11... I have 2.6.10
can I install everything or should I avoid 2.6.11 packages?

---

### Post by Lord Illidan on 2005-08-13
I have the .10 packages, and it all works fine.... But try installing the .11, maybe there are some bugs in the .10 which got ironed out.

---

### Post by TravisNewman on 2005-08-13
I've had nothing but trouble with the 2.6.11 kernels. but some have had good luck.

You need the linux-image though, along with the headers.

---

### Post by ubuntu_demon on 2005-08-13
try changing your videocard and look if the problem disappears. 

If this doesn't solve your problem then I think it's a hardware related problem. (for example dust,heat,broken hardware) 

Maybe your motherboard isn't compatible with Ubuntu. I have encountered that once before myself. You might try a bios update or install breezy or post a seperate topic about your mainboard.

log in using the terminal next time you have that problem and then save your dmesg in bla.txt by :

$ dmesg > bla.txt

post your log files and bla.txt as an attachement (tar.gz or something)

This will probably not help but it's worth trying and it will give you a bit more performance =>

If you have an intel processor you can try this :
$sudo apt-get install linux-686

this will install the newest 686 kernel including restricted modules and such. If you have HT then the linux-686-smp will give you some more performance.

if you have an amd then :
$sudo apt-get install linux-k7

---

### Post by granite230 on 2005-08-13
Synaptic asked me if I'm sure to remove the running kernel image and I answered 'No' because Synaptic said this is very dangerous.

I did install the 686 stuff, but what happens if I reboot now? Will it use the 686 kernel image or will my computer go nuts?

---

### Post by ubuntu_demon on 2005-08-13
[QUOTE=granite230]Synaptic asked me if I'm sure to remove the running kernel image and I answered 'No' because Synaptic said this is very dangerous.

I did install the 686 stuff, but what happens if I reboot now? Will it use the 686 kernel image or will my computer go nuts?[/QUOTE]
 You will get the option to choose the 686 kernel in grub. If booting that kernel fails then you don't have an intel processor (or a very old one but I doubt that very much :-P)

Also I just editted my previous post please take look.

---

### Post by granite230 on 2005-08-13
Ubuntu automatically loaded the 686 stuff and booted perfectly!
I hope that problem is solved now, but only time will tell.

I'm pretty sure my mainbord is Ubuntu-compatible because Warty worked on it and so did Hoary at the beginning.
I just had a lot of strange random bootproblems. I hope it's fixed now.

If it works like it should, I'll try to reinstall the Nvidia driver, Cedega and World of Warcraft. Hopefully everything will be OK from now on... 

Cant wait till Breezy comes out... almost switched to another distro because of these strange problems.

But I have a few more (n00b?)questions:

How is it possible that the 386 packages were installed? Why did Ubuntu not upgrade to 686? Is 386 the default stuff that gets installed from the shipit cd's and do I have to do this every time I install Ubuntu from these cd's?
And what if it happens again? How do I know what version/packages I need?

---

### Post by wmcbrine on 2005-08-13
[QUOTE=granite230]- My computer case is always open on one side [/QUOTE]
You realize this is actually very bad for cooling, right? The case is designed for proper airflow when it's *closed*. Not to say that's the source of your problem, though.

386 packages are indeed the default, and they shouldn't be causing problems, either -- 686 packages just give you a minor performance boost.

---

### Post by Quest-Master on 2005-08-13
This happened to me as well as everything getting slow, lagging, and especially apps. taking a while to load up. I went through maybe 3 topics of trying to get help to no avail, so since then I've been on a Windows box (don't kill me) with open-source software, though still supporting the Ubuntu cause. :)

---

### Post by granite230 on 2005-08-15
I think the strange error is gone now, Ubuntu booted perfectly for like... 6 times.
This morning I booted up Ubuntu and launched XMMS like I always do. Then after 10 minutes the music stopped playing. This happens quite often so double clicking the pause button will make the music play again. Only this time it was for like... one second. Then it stopped again.
Then I tried to launch Gaim and I got an error telling me I couldn't use Gaim. Then I Clicked the Applications button and it showed up but without any icons on the left and the whole system froze up!
The only thing still moving was my cursor and the song selected in XMMS. Alt-Ctrl-F2 did work, but I couldn't get X running again. 
So I reset the computer and now Grub gives me an Error 16.
I haven't figured out what that means yet, but one thing is for sure: Ubuntu will not boot!

You see... this is a new problem. Never had this one before. And I lost count on the Ubuntu problems I encountered. That's why I started this topic. It's SO annoying! 

Also, if this is a hardware related problem, then why is Windows XP not complaining?

---

### Post by Lord Illidan on 2005-08-15
Can you boot in failsafe? Try running fsck...

---

### Post by heimo on 2005-08-15
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)
 > 
16 : Inconsistent filesystem structureThis error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.            Which motherboard do you have?

---

### Post by granite230 on 2005-08-15
My mainbord:

Gigabyte P4 Titan 533 (Supports Intel Pentium 4 Processor, Socket 478.)

---

### Post by heimo on 2005-08-15
[QUOTE=granite230]My mainbord:

Gigabyte P4 Titan 533 (Supports Intel Pentium 4 Processor, Socket 478.)[/QUOTE]

Is it one of these?
[http://www.gigabyte.com.tw/MotherBoard/Products/Products_Socket+478.htm]("http://www.gigabyte.com.tw/MotherBoard/Products/Products_Socket+478.htm")

What I'm after here is that it's known that some sis chipsets and Seagate hard disks are a bad combination and you earlier told your disk is Seagate or WD.

---

### Post by granite230 on 2005-08-15
Yes this is the one:

[I]Intel 845 Chipset
Model 	Description
GA-8ID533 (Rev 1.0) 	


   1. Socket 478 for Intel® new 0.13 micron-process Pentium® 4 processor
   2. Auto detect FSB and optimized settings for Pentium® 4 processor
   3. 3 x 168-pin DIMMs support up to 3GB PC133 SDRAM
   4. Provides 4 USB ports
   5. Integrated high quality AC’97 audio
   6. Supports UDMA ATA100/66 IDE devices
   7. GIGABYTE unique EZ-Fix AGP slot [/I]

It's an 160GB Harddisk I purchased for Ubuntu only. So maybe now I should try to install Ubuntu on my older 80GB Maxtor harddisk?

---

### Post by phen on 2005-08-15
the error messages sound like your harddisk is the problem. it would explain that windows is running fine. i am having the same problems at the moment, and it is my harddisk. i have to run fsck about once a week, and it will find hundreds of errors each time.

hope you can fix your box, as i hope i can fix mine :-)

---

### Post by granite230 on 2005-08-15
Thanks!

Thanks to this community I'm a happy Ubuntu user again! Never heard about this problem before. It explains everything!

Is this hardware combination only a problem to Ubuntu or to all Linux distributions?
I'm asking because next time I will double check my hardware before installing ANY Linux distribution on ANY computer.

Thanks for the help folks!

---

### Post by ubuntu_demon on 2005-08-15
[QUOTE=granite230]Thanks!

Thanks to this community I'm a happy Ubuntu user again! Never heard about this problem before. It explains everything!

Is this hardware combination only a problem to Ubuntu or to all Linux distributions?
I'm asking because next time I will double check my hardware before installing ANY Linux distribution on ANY computer.

Thanks for the help folks![/QUOTE]
 probably your harddisk is broken this can happen to windows too ofcourse

There's a small chance your harddrive isn't broken but I wouldn't bet any money on it. Just run fsck. if you have fixed all the errors and the filesystem errors keep popping up(using fsck) then it's definitely broken.

to get info on fsck type :
$ man fsck

---

### Post by granite230 on 2005-08-15
yes, but I can't do anything on that harddisk anymore... I just installed Ubuntu on my 80GB Maxtor harddisk. If it works fine, I don't need the other harddisk anymore.
Maybe I'll use it later to test some stuff... but I'll keep it in mind, thank you.

---

### Post by granite230 on 2005-08-17
So, now that I reinstalled everything on a Maxtor harddisk everything runs like a sunshine fairytale! No strange problems at all! Not a single error, no ramdom bootproblems anymore. I'm very happy with my fresh system, it runs everything I want, including World of Warcraft! 

Check out my new desktop [here](http://home.quicknet.nl/qn/prive/jg.rinkel/Screenshot.png) and [here](http://home.quicknet.nl/qn/prive/jg.rinkel/Screenshot2.png). It's perfect!

---

### Post by Buffalo Soldier on 2005-08-17
[QUOTE=granite230]So, now that I reinstalled everything on a Maxtor harddisk everything runs like a sunshine fairytale! No strange problems at all! Not a single error, no ramdom bootproblems anymore. I'm very happy with my fresh system, it runs everything I want, including World of Warcraft! 

Check out my new desktop [here](http://home.quicknet.nl/qn/prive/jg.rinkel/Screenshot.png) and [here](http://home.quicknet.nl/qn/prive/jg.rinkel/Screenshot2.png). It's perfect![/QUOTE]Glad to hear it work out fine for you :) I sure didn't help much. But I'm sure there are a lot of those who were helpful to you.

Enjoy your Ubuntu and spread the Ubuntu spirit :)

---

### Post by crispingatiesa on 2005-08-17
Seems that your problem is with Advancd Power Management. 

Disable power management in the BIOS (pressing Del or F1 or whatever it is in your Mobo)

To be even more certain, use synaptic to install the bootmanager tool. (I can´t tell you the exac name now because I´m not close to any Ubuntu box.

After installing it running and prevent the Ubuntu from loading any power management feature at boot time. This should stop the problem. Anyways, the kernel update could help. But, I´ll recommend to disable any power management feature at BIOS level.

---

### Post by ubuntu_demon on 2005-08-17
[QUOTE=crispingatiesa]Seems that your problem is with Advancd Power Management. 

Disable power management in the BIOS (pressing Del or F1 or whatever it is in your Mobo)

To be even more certain, use synaptic to install the bootmanager tool. (I can´t tell you the exac name now because I´m not close to any Ubuntu box.

After installing it running and prevent the Ubuntu from loading any power management feature at boot time. This should stop the problem. Anyways, the kernel update could help. But, I´ll recommend to disable any power management feature at BIOS level.[/QUOTE]
 no it was the harddisk

---

### Post by granite230 on 2005-08-20
I actually have one more question!

Now that I've installed Ubuntu on a 80GB Maxtor harddisk everything runs perfectly fine! But now I still have the 160GB Seagate/Western Digital (still don't know what it is, but it was the cause of all my strange (boot)problems).
Now I'm wondering if I can format that 160GB disk with ext3 somehow and hook it up next to the Maxtor so Ubuntu will mount it and I have 160GB extra space.

Will this not cause any (new) problems I should know about?
The last thing I want is more trouble. 80GB is good enough, but I might need more space later.

And how does someone actually format a harddisk with ext3 without installing the entire OS with it?

---

### Post by ubuntu_demon on 2005-08-23
[QUOTE=granite230]I actually have one more question!

Now that I've installed Ubuntu on a 80GB Maxtor harddisk everything runs perfectly fine! But now I still have the 160GB Seagate/Western Digital (still don't know what it is, but it was the cause of all my strange (boot)problems).
Now I'm wondering if I can format that 160GB disk with ext3 somehow and hook it up next to the Maxtor so Ubuntu will mount it and I have 160GB extra space.

Will this not cause any (new) problems I should know about?
The last thing I want is more trouble. 80GB is good enough, but I might need more space later.

And how does someone actually format a harddisk with ext3 without installing the entire OS with it?[/QUOTE]
 search the maxtor website. download some software. first diagnose the problem. If it's not too bad try a low level format. If you get lucky your data won't get corrupt again so don't use it for important stuff.

In other words probably isn't worth the trouble. If I were in your shoes I would use my guarantee to get another one.(if you have still guarantee on it)

to make another harddrive accesible in Ubuntu just install and run gparted or qtparted and put the newly created partitions in your fstab after that. search the forums for more on this.

---

### Post by madhusker on 2008-09-04
I see there is some activity in this thread. Anyone care to tackle the mysterious random reboot problem? It's impossible to use ubuntu as a reliable OS until this gets solved.

[http://ubuntuforums.org/showthread.php?t=839082](http://ubuntuforums.org/showthread.php?t=839082)

[http://ubuntuforums.org/showthread.php?t=896435](http://ubuntuforums.org/showthread.php?t=896435)

[http://ubuntuforums.org/showthread.php?t=877037](http://ubuntuforums.org/showthread.php?t=877037)

[http://ubuntuforums.org/showthread.php?t=909768](http://ubuntuforums.org/showthread.php?t=909768)

[http://ubuntuforums.org/showthread.php?t=909289](http://ubuntuforums.org/showthread.php?t=909289)

---

### Post by Joeb454 on 2008-09-04
There's no point in reviving threads that are 3 years old. Thread Closed.

---

