---
title: "Can I just vent about my Ubuntu troubles?"
date: 2010-02-28
forum: Testimonials &amp; Experiences
---

### Post by Donny Bahama on 2010-02-28
I hope no one takes this the wrong way. I think Ubuntu is very cool... and I really WANT it to work... but man, oh man am I having a lot of troubles. And the really frustrating part is that I'm extremely tech/computer savvy!

On my notebook I'm dual booting Ubuntu hardy and Windows 7. I'd prefer to run Ubuntu as my primary OS, and I'm really pleased with my desktop configuration, etc. BUT...

[LIST]
[*]I can't get my microphone to work in Skype. (I've tried all kinds of Alsa updates and tweaks, tried installing and configuring Pulse, completely removing pulse - nothing will make it work.)
[*]Can't get my fingerprint reader working.
[*]I'm bummed that my iPhone won't sync - even jailbroken
[*]I find Gimp to be counterintuitive and I just don't have time for the learning curve. I'm used to using Paint.net, and supposedly I should be able to install Paint.mono but it throws an error about a dependency every time.
[*]I installed VirtualBox and set up a Windows VM so I could launch it to run Paint.net (and a few other things like iTunes) as needed, but iTunes crashes every time I launch it ~AND~ I can't get internet access in the VM.
[*]After trying various documented procedures to get the net working in the VM, the WLAN icon (in my gnome panel on the host machine) is now gone and I have no wireless networking. << ***This one thing, more than any of the others, has me very close to just dumping Ubuntu and going back to Windows exclusively.***
[/LIST]
My (technophobic) wife, who is quite comfortable with Windows XP, bravely decided to give Ubuntu a go (with a promise of good help and support from me.) She, too, is having a issues and I'm having trouble fixing them...

[LIST]
[*]The first time we connected her printer, I was prompted that drivers were found and installed smoothly and it printed perfectly. Ever since, no printing.
[*]Her machine frequently hangs coming out of suspend and/or hibernation and has to be brute powered down.
[/LIST]
Next we have my HTPC which I built to run XBMC on top of a minimal Ubuntu karmic installation. I downloaded the kk minimal installer iso and ran it. I wanted to use LVM so I set that up manually, but when I went to install GRUB, it threw up an error. LILO installed, but then wouldn't boot. It took half a dozen installs (and the use of grub2) to get a bootable system -- and even then I had problems. This system is now running Windows 7 very smoothly - but unfortunately, XBMC doesn't support VDPAU under Windows.

Finally, there's my media server which I just started setting up. Again, I used KK minimal, and again I used LVM (although this time I allowed it to use guided partitioning). Completed the install, booted up and got:[INDENT]GRUB loading.
error: no such partition
grub rescue>
[/INDENT]Is there a known bug with KK minimal and LVM?

The worst part of all this is that, if I was running Windows, I'd know where to look and how to fix the problem. In Ubuntu, I don't know the basics of troubleshooting. I know there are tons of great tutorials and getting started guides out there, but I'm working two full-time jobs (and doing this for fun in my "spare" time). I don't really have time for the learning curve, and all these mysterious issues are taking the fun out of my hobby!

Is there a "Troubleshooting Essentials" guide for Windows gurus?

I have to say, if this is THIS painful for me, Linux still has a long way to go before it sees widespread acceptance among "normal" users.

---

### Post by hwttdz on 2010-02-28
You can vent, just don't do it in the help forum.  It slows down the rate at which people get help.  See the testimonials forum: [http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

If you want to ask questions please do so one problem per thread after searching to see if an answer already exists.

---

### Post by uRock on 2010-02-28
> **Donny Bahama said:**
> <snip>

I can agree with you about Gimp. I prefer the simpleness of Paint also.

I hope you can find a fix for the problems you are having.

BTW, If you want help with your problems, you need to start seperate help threads so that they get the proper attention. As for the server you want, why not use the Ubuntu Server Edition instead of the minimal install?

---

### Post by Nick_Jinn on 2010-02-28
There is also the bug that might damage hardware due to energy saving settings that causes the harddrive to rotate too fast. That was a major blow to my confidence in Ubuntu, though I love Ubuntu.

I would suggest going back to the previous stable version of Ubuntu before Karmic....There are a lot of nifty upgrades with Karmic but they allowed a lot of bugs and compatibility issues this time. They should have waited longer. It wasnt ready. 

I almost think they should scratch Karmic and go back to the drawing board and release a more stable version that is based on the previous installment.

---

### Post by uRock on 2010-02-28
@Nick Just because Karmic didn't work for you doesn't mean others had any problems. I have 4 Systems in my house running Karmic without any problems. A Lenovo, HP, Asus, and a Dell. I haven't heard about the HDD issue and if there is such an issue, I am sure that a bug was filed and the problem was quickly fixed.

---

### Post by Sugoi48 on 2010-02-28
> **iRock said:**
> I can agree with you about Gimp. I prefer the simpleness of Paint also.
I don't think its fair to compare GIMP and Paint. It's like comparing Word and Notepad.

---

### Post by Nick_Jinn on 2010-02-28
> **iRock said:**
> @Nick Just because Karmic didn't work for you doesn't mean others had any problems. I have 4 Systems in my house running Karmic without any problems. A Lenovo, HP, Asus, and a Dell. I haven't heard about the HDD issue and if there is such an issue, I am sure that a bug was filed and the problem was quickly fixed.

The bug doesnt seem to have been fixed. I think it has to do with what hard drive people are using rather than the manufacturer of the laptop.

I have lost multiple hard drives to this bug and know many others who have the same story.

---

### Post by 3rdalbum on 2010-02-28
> **Nick_Jinn said:**
> There is also the bug that might damage hardware due to energy saving settings that causes the harddrive to rotate too fast. That was a major blow to my confidence in Ubuntu, though I love Ubuntu.

The bug that was never demonstrated to have any appreciable effect on hard disks, and the same bug that was fixed years ago? *sigh* Some people have memories that are too long.

---

### Post by Gemnoc on 2010-02-28
> **Donny Bahama said:**
> [*]I find Gimp to be counterintuitive and I just don't have time for the learning curve. I'm used to using Paint.net, and supposedly I should be able to install Paint.mono but it throws an error about a dependency every time.
Sorry I can't help out about all your troubles...

But for this particular one (Gimp), you might try [this new project, Pinta]("http://pinta-project.com/"), which is [described by its author]("http://jpobst.blogspot.com/2010/02/over-holiday-break-i-stumbled-upon-this.html") as a Paint.NET clone for Gtk. It uses Mono.

---

### Post by GodLikeCreature on 2010-02-28
> **Donny Bahama said:**
> I hope no one takes this the wrong way. I think Ubuntu is very cool... and I really WANT it to work... but man, oh man am I having a lot of troubles. And the really frustrating part is that I'm extremely tech/computer savvy!

On my notebook I'm dual booting Ubuntu hardy and Windows 7. I'd prefer to run Ubuntu as my primary OS, and I'm really pleased with my desktop configuration, etc. BUT...

[LIST]
[*]I can't get my microphone to work in Skype. (I've tried all kinds of Alsa updates and tweaks, tried installing and configuring Pulse, completely removing pulse - nothing will make it work.)
[*]Can't get my fingerprint reader working.
[*]I'm bummed that my iPhone won't sync - even jailbroken
[*]I find Gimp to be counterintuitive and I just don't have time for the learning curve. I'm used to using Paint.net, and supposedly I should be able to install Paint.mono but it throws an error about a dependency every time.
[*]I installed VirtualBox and set up a Windows VM so I could launch it to run Paint.net (and a few other things like iTunes) as needed, but iTunes crashes every time I launch it ~AND~ I can't get internet access in the VM.
[*]After trying various documented procedures to get the net working in the VM, the WLAN icon (in my gnome panel on the host machine) is now gone and I have no wireless networking. << ***This one thing, more than any of the others, has me very close to just dumping Ubuntu and going back to Windows exclusively.***
[/LIST]
My (technophobic) wife, who is quite comfortable with Windows XP, bravely decided to give Ubuntu a go (with a promise of good help and support from me.) She, too, is having a issues and I'm having trouble fixing them...

[LIST]
[*]The first time we connected her printer, I was prompted that drivers were found and installed smoothly and it printed perfectly. Ever since, no printing.
[*]Her machine frequently hangs coming out of suspend and/or hibernation and has to be brute powered down.
[/LIST]
Next we have my HTPC which I built to run XBMC on top of a minimal Ubuntu karmic installation. I downloaded the kk minimal installer iso and ran it. I wanted to use LVM so I set that up manually, but when I went to install GRUB, it threw up an error. LILO installed, but then wouldn't boot. It took half a dozen installs (and the use of grub2) to get a bootable system -- and even then I had problems. This system is now running Windows 7 very smoothly - but unfortunately, XBMC doesn't support VDPAU under Windows.

Finally, there's my media server which I just started setting up. Again, I used KK minimal, and again I used LVM (although this time I allowed it to use guided partitioning). Completed the install, booted up and got:[INDENT]GRUB loading.
error: no such partition
grub rescue>
[/INDENT]Is there a known bug with KK minimal and LVM?

The worst part of all this is that, if I was running Windows, I'd know where to look and how to fix the problem. In Ubuntu, I don't know the basics of troubleshooting. I know there are tons of great tutorials and getting started guides out there, but I'm working two full-time jobs (and doing this for fun in my "spare" time). I don't really have time for the learning curve, and all these mysterious issues are taking the fun out of my hobby!

Is there a "Troubleshooting Essentials" guide for Windows gurus?

I have to say, if this is THIS painful for me, Linux still has a long way to go before it sees widespread acceptance among "normal" users.

Hey, sorry that you are having such problems.

The understanding that Ubuntu can do the same as Windows in terms of hardware recognition when the former has such limited driver support is not realistic.  That's not necessarily your fault, mainly because we in the community should be a lot more clear about it.

On a different note, it is very hard to help you, because you are trying a number of far from standard things, and it is hard to understand where exactly you got stock.  For example, sharing a network connection with a VirtualBox VM machine is a piece of cake.  As long as the connection is working on the host, it just works, so not sure what you did there.  In addition, losing a printer once you have already set it up well is like science fiction.  I have done it tons of times and never experienced it, so I am guessing there was something that was not done correctly there.

My recommendation is that if you must have that mic and fingerprint recognition hardware working, or your iPhone synching, you go back to Windows.  If you can live without it, or at least wait a bit longer until you get some Linux skills, then keep it simple.  

To begin with, forget about your Windows skills.  I am thinking that your Windows confidence is leading you to try things you don't understand yet, and that's not necessarily better than not knowing anything at all.

Linux is a whole different game, so stick to the basics as you take your first steps.  For example, instead of installing Ubuntu straight away, install Ubuntu using Wubi from within Windows.  That is very simple, you just need to boot your Windows session and stick your LiveCD in.  That will ask you if you want to install it inside Windows, take 10-12 GB of disk space and run the install.  This is a very safe way to start playing around with Ubuntu (unless your hard drive is encrypted, which will make it fail).  Winboot will be modified and you will get a dual boot setup.  If yo do nothing, or select the boot menu default, you will start Windows as usual.  If you want to try Ubuntu, just select the corresponding menu option.

When using such setup, you have the opportunity to learn and experience Ubuntu at your own pace, to start finding things you like about it.  If something does not work, you can fix it at your own pace, because you have Windows in there.  Believe me, you will progressively start to find more and more things you like about Ubuntu, but with a safety net.  Similarly, you will be able to find Linux alternatives to your favorite Windows applications, but again, with time to test them and find your preferred option at your own pace.  

If you are like me, it won't be long before you are left with one or two things from Windows you can't exactly get from Ubuntu.  When that happens, you will probably feel a lot more confortable with Ubuntu, so I would recommend trying a native dual installation, which implies partitioning your hard drive to accomodate both Windows and Ubuntu.  When you do that, keep in mind Ubuntu will require two partitions (root and swap), and that you should install Ubuntu LAST.  That will get you a dual setup, with GRUB2 managing the boot menu this time.  This will also get you to experience Ubuntu's performance in full.

I would recommend you spend months or even a year with that setup, and only attempt to completely migrate to Ubuntu when you are fully confident there are no show stoppers.

Linux takes time before you master it.  Start slow and safe, and you will eventually love it, Ubuntu in particular.

Good Luck!

---

### Post by uRock on 2010-02-28
> **Nick_Jinn said:**
> The bug doesnt seem to have been fixed. I think it has to do with what hard drive people are using rather than the manufacturer of the laptop.

I have lost multiple hard drives to this bug and know many others who have the same story.

Sounds like crappy hardware to me. If your OS really killed your HDD, why did you replace it with the same brand part? And, why would you keep using the OS you think is to blame for that?

If Ubuntu were causing such an issue that couldn't be fixed, then I would suspect the kernel and that would mean that other distros that used the same kernel would have produced the same issues. I just don't see it.

---

### Post by Donny Bahama on 2010-02-28
> **hwttdz said:**
> You can vent, just don't do it in the help forum.  It slows down the rate at which people get help.  See the testimonials forum: [http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)Sorry. I overlooked that forum. I see that the thread has been moved, though, so that's good.> If you want to ask questions please do so one problem per thread after searching to see if an answer already exists.I will, but searching for an answer (and finding one that's truly relevant) can be like the proverbial needle and haystack. Very time consuming - and to the extent that I don't have lots of time to spare, that's the source of much of my frustration.

---

### Post by Donny Bahama on 2010-02-28
> **Sugoi48 said:**
> I don't think its fair to compare GIMP and Paint. It's like comparing Word and Notepad.If I was comparing Gimp with Paint, that would be true, but Paint**.*net*** is a far more sophisticated editor than Paint (and is in no way analogous to notepad.) That said, I ***do*** understand that Gimp is on another level from Paint.net, but for those of us without the time for Gimp's learning curve, Paint.net offers most of the functionality while being far easier to use.

---

### Post by Donny Bahama on 2010-02-28
> **3rdalbum said:**
> *sigh* Some people have memories that are too long.If such a bug was found in Windows or OS X, it would be a long time indeed before people stopped bringing it up. That said, I think it's a testimony to Ubuntu (and its developer community) that people hold it up to the same level of scrutiny and have such high expectations for it.

---

### Post by Donny Bahama on 2010-02-28
> **iRock said:**
> BTW, If you want help with your problems, you need to start seperate help threads so that they get the proper attention.I will. I really did just need to vent a bit in this thread. :)> As for the server you want, why not use the Ubuntu Server Edition instead of the minimal install?What got me started with the minimal install was a HOW-TO on the XBMC forums. It said to start with the minimal install so I did. Having already burned it to a CD-RW, I just went with that. I'll look into the Server Edition - thanks for the suggestion!

---

### Post by Donny Bahama on 2010-02-28
> **Nick_Jinn said:**
> I would suggest going back to the previous stable version of Ubuntu before Karmic....Based on your suggestion, I downloaded the minimal install of jaunty and gave it a try on my media server. Same results. Definitely goinb to look into Server Edition.

---

### Post by Donny Bahama on 2010-02-28
> **Gemnoc said:**
> But for this particular one (Gimp), you might try [this new project, Pinta]("http://pinta-project.com/"), which is [described by its author]("http://jpobst.blogspot.com/2010/02/over-holiday-break-i-stumbled-upon-this.html") as a Paint.NET clone for Gtk. It uses Mono.Thanks for that! I'll definitely look into it. I'm concerned that it uses mono (since Paint.mono wouldn't launch) but hopefully I'll have better luck with Pinta.

---

### Post by Donny Bahama on 2010-02-28
> **GodLikeCreature said:**
> Hey, sorry that you are having such problems.Thanks. And thanks for taking the time for such a detailed response. :)
> The understanding that Ubuntu can do the same as Windows in terms of hardware recognition when the former has such limited driver support is not realistic.It seems odd to characterize Ubuntu as having "such limited driver support"... I've now installed Ubuntu on 4 different machines (two of the laptops) and with the exceptions I've noted, it has done a stellar job at recognizing the hardware and installing the appropriate drivers. I've installed Windows many, many, many times, and I've seen it fail to recognize and support hardware, too. IMHO, I'd say Ubuntu has very good driver support.> On a different note, it is very hard to help you, because you are trying a number of far from standard things, and it is hard to understand where exactly you got stock.  For example, sharing a network connection with a VirtualBox VM machine is a piece of cake.  As long as the connection is working on the host, it just worksNot sure what's so non-standard about what I'm doing. As for VirtualBox, I'm sorry but you're mistaken. Pretend that you're having the same problem and do a search. You'll find plenty of posts from people for whom it does *not* "just work".
> In addition, losing a printer once you have already set it up well is like science fiction.  I have done it tons of times and never experienced it, so I am guessing there was something that was not done correctly there.Sounds like just my luck to be the one in a million for whom this doesn't work! :P I didn't do anything incorrectly, though. I just plugged in the printer, got a notification that a driver was available for my printer (which was correctly identified), clicked "yes" to install the driver, then printed. Everything worked fine. Now it doesn't. No monkeying around in between, just normal day-to-day use by my wife (who basically uses it for web access, email, and word processing. Nothing more.)
> My recommendation is that if you must have that mic and fingerprint recognition hardware working, or your iPhone synching, you go back to Windows.  If you can live without it, or at least wait a bit longer until you get some Linux skills, then keep it simple.My iPhone is jailbroken, so I have workarounds for transferring files. And the fingerprint scanner is cool, but far from essential. Not being able to use Skype is a bit of a deal-breaker, though. I'll post a thread to get help getting it working and hope that something comes from that. As for "getting some Linux skills", I *am* getting them, slowly but surely. And that was the main point of doing all this to begin with. But if I'm constantly booting into Windows because of things like Skype, then I won't acquire any Linux skills because I'll rarely be using it.
> To begin with, forget about your Windows skills.First off, my Windows skills are a bit beyond what you'd find for most  confident Windows users. I'm very skilled at the Windows command line  and have done extensive/sophisticated Windows shell scripting. I do realize that Linux is a whole different ball game, but if ever a Windows user was well-suited for the Linux world, I think it's me.
> I am thinking that your Windows confidence is leading you to try things you don't understand yet, and that's not necessarily better than not knowing anything at all.I hear what you're saying. Frankly, I have already been guilty of plodding my way through the execution of multiple lines of shell commands (as posted in these forums) without necessarily bothering to fully understand what was going on. On the other hand, many of my Windows skills (which are founded on my DOS skills which go clear back to DOS 3.3) are built on my experiences of really royally screwing things up then fixing them -- and learning from those mistakes. I'm backing up all my important files on a very regular basis, so I'm not *too* afraid to really make a mess of things. That said, when something happens (like losing my wireless networking capability), it tends to render my Ubuntu installation almost useless to me such that I'm disinclined to even boot into it. (I'm writing this from my Win7 installation.) Still, as long as I have the ability to plug in an ethernet cable and get help/try fixes, I'm sure I'll find a way to recover from this rather than just abandoning Ubuntu.
> Linux is a whole different game, so stick to the basics as you take your first steps.  For example, instead of installing Ubuntu straight away, install Ubuntu using Wubi from within Windows.I'm way beyond that. Both my and my wife's laptops have been running Ubuntu for some time, and mostly successfully except for the frustrations I've documented here.
> Believe me, you will progressively start to find more and more things you like about Ubuntu, but with a safety net.  Similarly, you will be able to find Linux alternatives to your favorite Windows applications, but again, with time to test them and find your preferred option at your own pace.

If you are like me, it won't be long before you are left with one or two things from Windows you can't exactly get from Ubuntu.  When that happens, you will probably feel a lot more confortable with Ubuntu, so I would recommend trying a native dual installation, which implies partitioning your hard drive to accomodate both Windows and Ubuntu.Yep. Already there. Bluefish has proven to be an acceptable alternative to UltraEdit (for my web development projects), and I've long used OO over MS Office (even in Windows). For some of the Windows apps I can't live without and/or can't find an acceptable alternative for, I've been able to get working very nicely in Wine (Evernote, Wink, NoteTab Pro). For others I'm still looking. (Hopefully Pinta will resolve my Paint.net needs, but I fear I'll never find anything I like as well as IrfanView. And while I did get IrfanView working in Wine, I have yet to find a way to set it as the default app for opening image files.) I know that there are certain apps that I may always have to run in Windows (e.g. AnyDVD-HD) but I don't mind keeping a Windows partition (or two) around. I have a number of clients for whom I provide Windows support, so it's a necessary evil anyway.
 >   When you do that, keep in mind Ubuntu will require two partitions (root and swap), and that you should install Ubuntu LAST.  That will get you a dual setup, with GRUB2 managing the boot menu this time.Again, way beyond this already. I've been setting up multi-boot systems for years. FYI, there's a product called [Bootit NG]("http://www.terabyteunlimited.com/bootit-next-generation.htm") that allows >4 primary partitions and is a much better boot manager than grub. On my notebook, currently, I can boot into Windows 7, Ubuntu, Windows XP and Solaris 10. (I rarely use the XP or Solaris but I can if I need to.) A large NTFS "file vault" partition is visible/accessible regardless of which OS I boot. Side note: my attempts to get a Hackintosh version of OS X installed have failed so  far, but I know it's possible because someone has posted a YouTube  video showing OS X running on the exact same notebook I have.

---

### Post by ninjamaster945 on 2010-02-28
I know exactly what you are talking about with the issue of itunes crashing in virtualbox. For some reason that only happened to me with the newest version of itunes. I installed an older version and everything worked as it should. You will need the closed source version of virtualbox to get USB support, however.

---

### Post by uRock on 2010-02-28
I use the VBox from the Sun website for my virtual machines and I have had no problems with USB devices.

---

### Post by Nick_Jinn on 2010-02-28
There are a lot of reasons that I prefer Ubuntu over Windows. For one thing I like not having viruses. I think that the OS has been improving and went from being a pain in the *** to install most application to being even easier to install them than it is in windows. I love all the free software that I can download directly from inside the repositories. 

However, this is NOT the problem that was fixed ages ago. If by "long memory" you mean 30 minutes ago, that isnt very long in my opinion.

I just plugged in my western digital external hard drive and what I was hearing was a .....click....click.....click....click. Never happened when I plugged it into windows. I heard it has to do with the power saving mode.

This problem never happened to me with any of the 8,0 releases, but started again with Karmic. I dont believe this problem has been fixed for all hardware.



And I dont think its purely the hardwares fault if its not happening with other operating systems.

---

### Post by Donny Bahama on 2010-02-28
> **Nick_Jinn said:**
> I just plugged in my western digital external hard drive and what I was hearing was a .....click....click.....click....click. Never happened when I plugged it into windows. I heard it has to do with the power saving mode.HOLY CRAP! So *THAT'S* what happened to my new 1.5TB external drive!

---

### Post by Donny Bahama on 2010-02-28
> **ninjamaster945 said:**
> I know exactly what you are talking about with the issue of itunes crashing in virtualbox. For some reason that only happened to me with the newest version of itunes. I installed an older version and everything worked as it should. You will need the closed source version of virtualbox to get USB support, however.That's good to know. Thanks!

---

### Post by Nick_Jinn on 2010-02-28
Unfortunately whenever I talk about it people just get angry like I am insulting them personally instead of just sympathetically passing on any updates or helpful advice.

"Get a better brand"

Well, I am poor and I take what I can get. I cant afford to run out and buy new hardware that my OS prefers, but I also dont like windows. I would buy a mac but again I cant afford one with the specs I want.

---

### Post by uRock on 2010-03-01
> **Nick_Jinn said:**
> There are a lot of reasons that I prefer Ubuntu over Windows. For one thing I like not having viruses. I think that the OS has been improving and went from being a pain in the *** to install most application to being even easier to install them than it is in windows. I love all the free software that I can download directly from inside the repositories. 

However, this is NOT the problem that was fixed ages ago. If by "long memory" you mean 30 minutes ago, that isnt very long in my opinion.

I just plugged in my western digital external hard drive and what I was hearing was a .....click....click.....click....click. Never happened when I plugged it into windows. I heard it has to do with the power saving mode.

This problem never happened to me with any of the 8,0 releases, but started again with Karmic. I dont believe this problem has been fixed for all hardware.



And I dont think its purely the hardwares fault if its not happening with other operating systems.

When you filed the bug report, how many others had this problem with Karmic?

---

### Post by mastablasta on 2010-03-01
@ Donny Bahama
 
About the non standard things - You do things like trying to have a very closed system devices (such as IPhone) work in another system.
 
Also there are plenty programmes in Linux that are good alternatives to their windows counterpart. In fact to me there is too many so it's a bit hard to choose.
 
As for not having time to learn well i read the Ubuntu pocket guide (mentioned & stuck in newbie posting area). It's not such a long read and explains quite a bit of things. And it got me to realise that commands are indeed very different and even the ones that are the same work in a different way. so my previous knowledge won't help me much. So time to go back to basics and i first tried to understand from this guide is how the system actually works. how "it does things". how it installs programmes, how it installs itself, how it manages devices, how drivers are managed etc. and only when i read this i decided to install it dual boot. ran into two problems which could be incompatible hardware but most likely my incompetence. rad two guides but found out they are a bit obsolete, so i made a post here. Hopefully someone in community has the answer to it (because the two of hardware should be quite compatible with Ubuntu or at least they used to be). Once these two are solved it will be time to delete the WinXP partition and add it to Ubuntu. 
 
I was surprised for some open source alternatives (even in Windows) for better known programmes. What i couldn't do with corel draw (didn't know how despite trying for hours) i easilly solved with open source programme that was even written in my language (wow!). I understood everyhting and icons were intuitive. I haven't played arround with Gimp. I does seem a bit strange to me as i am not used to have things separated like that. But if the new Ubuntu Intalation will become used then i am sur ei will learn that one as well.

---

### Post by houseworkshy on 2010-03-01
Good honest title to your post, I like it.   I too feel like blowing steam sometimes but not in an agressive way.  Don't want to upset or critisise anyone, just want to scream for the sake of pressure releace. 

9.10 had me feeling the same way and after far too much time head-banging against the system instead of creating I just got rid of it and replaced it with 9.04.  
Since 8.04 I've noticed that each release of Ubuntu needs more fiddling around before everything  works.  It has been display, keyboard mapping ( try fixing that one in the terminal, copy and paste as if one were putting together a ransom note from newspapers...aarrhhh!), repositories not working ...oh lots of things.  
So what I do now is have one which has been around for a while on one drive for work and recreation and the latest on another so I can play with all the new bells and whistles, try to make it all work and post bug reports to launchpad.  
Using the latest release as soon as it comes out does feel a bit like testing beta software, partly due to closed source drivers not having caught up.   This annoyed me when it started being standard but now that I know the score and don't do silly things like "I'll just install this in the morning which will leave the whole afternoon to meet my clients deadline"  Yeah really; 7.04 to 8.04 inclusive got me so used to problem free set-ups I really was that stupidly overconfident once.
I suppose if one wants "stable" to actually mean stable then the old original Debian is the best bet.  That said any supported version of Ubuntu which has been around for a few months has had most of it's bugs updated out of it and can be relied on so I stick with it.  Plus, if I have the time, messing with the new ones I learn a lot and as long as I can just drop them and switch to an older system in order to get work done or play something other than geek-tech-fiddling I quite enjoy it.
Linux and windows are very different.  I prefer Linux.  I really like the easy availability of help in the terminal; one could probably learn most of what there is to know just using the &#8220;man&#8221;, &#8220;info&#8221;, and &#8220;apropos&#8221; commands to start the journey.  That would of course be doing things the hard way, using a site like [http://linuxcommand.org]("http://linuxcommand.org/") is much better.
 I also like the applications and, personally, think gimp, with it's plug-ins, blows photo shop away on all but the range of file types it can handle.   Have you seen gimp-gap for example?  The learning curve is long rather than steep in my opinion.  This is the site which really got me into it [http://meetthegimp.org]("http://meetthegimp.org/")  especially the tutorial videos [http://meetthegimp.org/getting-the-old-shows/](http://meetthegimp.org/getting-the-old-shows/)
 

 You are probably way past this but others, frustrated others given the post title, may read this post so;  this book  [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
 was the one which gave me the basic foundation on which all I have learned since rests.  The PDF is a free download.  Very concise and well written.
 

 As you have several systems maybe have one old, but still supported, Ubuntu.  Then the newest buggy one won't bother you so much as it's only for playing and learning with.  8.04.4lts is a beauty for stability and is supported until April 2011 by which time the new long term support release, 10.04, will have been around for long enough to be mostly bug free and the proprietary drivers will have caught up.  
 Frustration can sometimes feel a lot like anger and that's heavy stress.  The occasional vent is probably good for the health.  Ubuntu is my favourite by a very long way yet I too feel the need to blow steam sometimes, I guess a lot do.

---

### Post by ElSlunko on 2010-03-01
Hopefully you get your issues resolved as Ubuntu can be a very attractive alternative for some ... if they can get it working! As far as computer knowledge goes knowing windows inside & out helps you very little in the Linux world (and is actually counter-productive in some ways) as was a harsh lesson for me in Ubuntu. I stuck it out though and eventually built a system with Linux compatible hardware and I haven't had any big issues yet.

Unfortunately it's not as universally supported hardware wise as most machines built in the real world and it often takes more effort than it's worth to get things working. In the short run you might not make much progress but if you really want a smooth Ubuntu experience in the long run invest in a new machine.

Oh! And I hear that iPod touch & iPhone syncing work in 10.04 (I'll have to test it out with my girlfriend's ipod at a later time).

---

### Post by cariboo on 2010-03-01
> **Donny Bahama said:**
> I will. I really did just need to vent a bit in this thread. :)What got me started with the minimal install was a HOW-TO on the XBMC forums. It said to start with the minimal install so I did. Having already burned it to a CD-RW, I just went with that. I'll look into the Server Edition - thanks for the suggestion!

This is probably way late, but I just installed [XBMC Live]("http://xbmc.org/download/") on my atom powered media center pc, it works as a Live CD as well as being installable. It uses the text based installer from the Alternate install CD. I haven't played with it to much, as it just works. the only thing I had to set up was auto mounting nfs shares as all my media is on a file server. 

I previously did the same thing as you, using the minimal install iso to setup a command line system, then adding LXDE for the desktop, but because of the low resources, 1.6Ghz cpu and 1Gb ram, I found that some things just didn't work as expected, full screen HD flash, brought the unit to it's knees. I plan on adding a browser of some sort within the next week or so to see if that problem has gone away.

---

### Post by GodLikeCreature on 2010-03-01
> **Donny Bahama said:**
> Thanks. And thanks for taking the time for such a detailed response. :)

My pleasure:p

> **Donny Bahama said:**
> It seems odd to characterize Ubuntu as having "such limited driver support"... 

I think I didn't explain myself.  I meant to say that Ubuntu has very limited support **from hardware manufacturers**.  That's why it is not fair to compare it to the industry standard, which has dedicated support from pretty much any hardware vendor there is.  It is because of that that Ubuntu does amazingly well given its imposed limitations.

After reading some of your other posts, it seems you were looking for a frustration outlet rather than actual support/advice, so I will leave it at that.

Btw, fine stuff you got with all of those OS running on your notebook.  I personally don't see a use for that, but it sure is an interesting technical proof of concept...  Having said so, if you consider that standard, we definitely have a different understanding of a standard installation!  Just kidding, but you are trying lots of stuff that most users don't try, and that go beyond what Ubuntu (or any other OS) can/will support.  

I am pretty sure neither Windows nor Mac will support you if you ran into boot problems because of that multi-boot setup.  That's what I was talking about when I mentioned "standard" stuff.

Good luck!

---

### Post by GodLikeCreature on 2010-03-01
> **Nick_Jinn said:**
> There are a lot of reasons that I prefer Ubuntu over Windows. For one thing I like not having viruses. 

Careful with such assumption.  Linux can indeed have viruses, spyware, malware, etc.  In fact, it is probably easier to create a Linux virus today.  I very much agree that Linux architecture is more secure than that of Windows, but don't assume you are safe just like that.

Here's a very interesting article about creating a virus for Linux in no time, and if you read it throughout, you will see that it wouldn't be so difficult to get root password either.  We can only avoid these problems by educating everybody in the community not to just assume they are safe.

[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

I know this is mostly based on a GNOME/KDE vulnerability, but those are the most popular desktop managers in the Linux community, so lots of impact already.  Also note that this guy is pointing out a vulnerability that is self evident, but lots more would appear if we had a legion of virus developers studying our code.

EDIT: Before I get replies pointing to the exact definition of a virus, I know that viruses are very unlikely.  As the writer of that article points out, that definition is no longer that clear, the word "virus" is used as a general term most of the time, many times referring to things that may not fall under the definition of virus.  

Having said so, considering the impact of social networking right now, I think that malware and spyware are also very dangerous and concerning.

---

### Post by penguinv on 2010-03-01
I'm in a much simpler version of your situation.

I posted today QV on some disadvantages to wubi.

Quick shot, consider having another simple computer to run your windows applications. I sure understand about paint and itunes. And wordpad, cause OO takes forever and is too impudent (does things auto that I dont want) while gedit doesnt do any bold etc at all.

Peace today.

---

### Post by hwttdz on 2010-03-01
> **GodLikeCreature said:**
> 
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)


That's not a virus, that's like emailing out a script that runs "touch ~/i_am_a_virus", it's only a virus if it does something the user doesn't have permission for it to do i.e. "touch /etc/i_am_a_virus".  The key difference being that it doesn't bother me (or root), when someone nukes their home directory because they (not the OS) do something stupid.

If you're looking for paint alternatives you can try gpaint (it's like paint for gnome, get it gnome paint), or kolourpaint (it's like paint for kde if you can't spell), or ....

And if oo-writer is too heavy and gedit is too light, try abiword.  Or.... or .... or ...  the point is if the application you first tried doesn't do what you expect maybe it's because you're using the wrong application.  Sort of the everything looks like a nail if you only have a hammer effect.  

And I stand by my claim of, if you want to vent do it in the proper forum, and if you have a question ask one per post here.

---

### Post by GodLikeCreature on 2010-03-01
> **hwttdz said:**
> That's not a virus, that's like emailing out a script that runs "touch ~/i_am_a_virus", it's only a virus if it does something the user doesn't have permission for it to do i.e. "touch /etc/i_am_a_virus".  The key difference being that it doesn't bother me (or root), when someone nukes their home directory because they (not the OS) do something stupid.

Ah, it seems my clarification edit didn't really work...

Now, if that was a "blonde_p_o_r_n_scene.exe" attachment that some Windows user downloads and executes, then the Windows user is stupid and Windows is terrible because its flooded with viruses .  When the same is used in Linux, well, "it's not really a virus"...

If our best excuse is to stand by the definition of virus, instead of acknowledging a potential threat...

---

### Post by hwttdz on 2010-03-01
Of course I didn't say it would be a virus in windows either.  However it would be more effective malware as it would likely have permissions for edit something in C:\windows\system\superimportant.dll (this is the important difference, you can't edit things outside of ~ unless you have permissions), which if I shared a computer with someone would be bad news for me as suddenly the action of someone else has messed with my files and the ability to function of the system.  

windows user does something stupid -> nukes whole machine
linux user does something stupid -> nukes user's account
linux admin does something stupid (includes users with sudo privileges) -> nukes whole machine

It's not that complicated.  Viruses (or other malware) which exploit things other than user stupidity are exceedingly rare in an _up_to_date_ version of any OS.

Just because it's not a virus doesn't mean it's not worth looking into.  I will look into disabling this treatment of .desktop files on machines I administer, and also into some assurance that sudo is actually referencing /usr/bin/sudo and not ~/bin/sudo (which could be bad, as shown in the article).  Nonetheless if I run ~/bin/sudo and give it my rootpass it's because I was stupid.

Finally all this hype about "I made a virus, see look I can make a file named virus in the users home directory" detracts from focus on real security (see: [https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults) , though I'm totally ok with the defaults).

---

### Post by cariboo on 2010-03-01
> **GodLikeCreature said:**
> Careful with such assumption.  Linux can indeed have viruses, spyware, malware, etc.  In fact, it is probably easier to create a Linux virus today.  I very much agree that Linux architecture is more secure than that of Windows, but don't assume you are safe just like that.

Here's a very interesting article about creating a virus for Linux in no time, and if you read it throughout, you will see that it wouldn't be so difficult to get root password either.  We can only avoid these problems by educating everybody in the community not to just assume they are safe.

[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

I know this is mostly based on a GNOME/KDE vulnerability, but those are the most popular desktop managers in the Linux community, so lots of impact already.  Also note that this guy is pointing out a vulnerability that is self evident, but lots more would appear if we had a legion of virus developers studying our code.

EDIT: Before I get replies pointing to the exact definition of a virus, I know that viruses are very unlikely.  As the writer of that article points out, that definition is no longer that clear, the word "virus" is used as a general term most of the time, many times referring to things that may not fall under the definition of virus.  

Having said so, considering the impact of social networking right now, I think that malware and spyware are also very dangerous and concerning.

Please stop using that article to throw a scare into people, it has been so throughly debunked in the Recurring Discussions section.

---

### Post by GodLikeCreature on 2010-03-01
> **cariboo907 said:**
> Please stop using that article to throw a scare into people, it has been so throughly debunked in the Recurring Discussions section.

What?  Throw a scare?  Can you please show me where I was doing that?

I was simply pointing out that saying "Linux/Ubuntu is virus free" is not necessarily the most useful/wise point of view, nor the most realistic, to be honest.  It seems some users are finding things they can improve/do differently, so not sure why you are asking me to stop sharing information that can only be benefitial to users here?

---

### Post by GodLikeCreature on 2010-03-01
> **hwttdz said:**
> It's not that complicated.  Viruses (or other malware) which exploit things other than user stupidity are exceedingly rare in an _up_to_date_ version of any OS.

Of course it isn't complicated, don't think I asked for your lecturing?  I can understand what the impact is on both a Linux and a Windows box, but as far as I am concerned, it should not be justified just because Linux can handle it better.  

A vulnerability is a vulnerability, why not acknowledge it and address it?

What you consider "user stupidity" has caused tons of problems for Windows users.  Be sure the same would happen if the "year of the Linux desktop" ever arrives.  Assuming Linux users "know better" is just as dumb, in my opinion.

I personally think it is wiser to acknowledge a vulnerability rather than demeaning it.  I believe it is better to address it than to ignore it, and I am not really sure I like both GNOME and KDE staff saying this is a "feature" and not a "vulnerability".

I heard an interview on the radio recently.  An antivirus company CEO mentioned they got 4000+ new viruses (general term, meaning viruses, trojans, malware, etc) a day.  Are we really that superior that we could stand such level of attack just like that if it was directed to Linux clients?

I just believe a more humble attitude could be useful in the Linux community, one that would keep our eyes open.  New Linux users join every day, taking for granted an invulnerability that is not real.  I read often how those users believe they can visit any website, open any kind of file, do whatever they please...  

I believe it is wise and good that we keep it real and honest, specially for those users.

---

### Post by uRock on 2010-03-01
> **cariboo907 said:**
> Please stop using that article to throw a scare into people, it has been so throughly debunked in the Recurring Discussions section.

I agree, I read the article and yeah, FUD at best.

---

### Post by aysiu on 2010-03-01
> **GodLikeCreature said:**
> What?  Throw a scare?  Can you please show me where I was doing that?

I was simply pointing out that saying "Linux/Ubuntu is virus free" is not necessarily the most useful/wise point of view, nor the most realistic, to be honest.  It seems some users are finding things they can improve/do differently, so not sure why you are asking me to stop sharing information that can only be benefitial to users here? You are, in fact, throwing a scare. You aren't providing information that is beneficial, unfortunately. Is it possible that you can create an email attachment that, once you have tricked a user into downloading and double-clicking, could compromise your Ubuntu installation? Sure. Does that mean Linux is susceptible to viruses? No. Does that mean Linux is as susceptible to viruses as Windows is? No. But based on your previous post, it would be very easy for the uninitiated to assume *Yes* answers to either of those questions.

If you're going to inform people for their benefit, then make sure to give all the information and the proper context. Remember: social engineering can work on any platform, because the vulnerability it exploits is user gullibility, not software flaws.

---

### Post by uRock on 2010-03-01
> **aysiu said:**
> You are, in fact, throwing a scare. You aren't providing information that is beneficial, unfortunately. Is it possible that you can create an email attachment that, once you have tricked a user into downloading and double-clicking, could compromise your Ubuntu installation? Sure. Does that mean Linux is susceptible to viruses? No. Does that mean Linux is as susceptible to viruses as Windows is? No. But based on your previous post, it would be very easy for the uninitiated to assume *Yes* answers to either of those questions.

If you're going to inform people for their benefit, then make sure to give all the information and the proper context. Remember: social engineering can work on any platform, because the vulnerability it exploits is user gullibility, not software flaws.

Just means Linux is susceptible to humans. I don't go double-clicking things unless I know what they are. The implication that someone would download a picture file and grant it sudo powers just to see it is ridiculous, which is what the link is implying.

---

### Post by ElSlunko on 2010-03-01
By the way iPod Touch works with music (so far anyways) in 10.04. Hopefully that stays true for the release.

---

### Post by GodLikeCreature on 2010-03-02
> **aysiu said:**
> You are, in fact, throwing a scare. You aren't providing information that is beneficial, unfortunately.

Right, beneficial = "Ubuntu is perfect and has no weak spots", is that what I should have said?  

My message is beneficial in that I am warning people to not be careless, to think twice about what they do, because Linux is NOT immune.  Again, I see how many new users get that impression, and judging by most replies here, I can see why.

> **aysiu said:**
> Does that mean Linux is susceptible to viruses? No.

Could I ask you to read my post again, please?  I simply was warning a user who seemed to believe Linux was invulnerable, so that s/he would have more information and realize that that is actually not the case.  I stand by my statement that we would be in trouble if thousands of people were trying to find a vulnerability and exploit it.  And again, the average Joe would call the exploit presented here a virus.

So let me get this straight, if someone can trick a user to double click a file (not unheard of, it's happened as users installed gnome-look.org themes packed as ".deb" files for "convenience", and we are not talking here about unexperienced users) that can potentially lead them to give away their admin password, that's no concern?

Raising that concern is throwing a scare?  I don't get it, really.

> **aysiu said:**
> If you're going to inform people for their benefit, then make sure to give all the information and the proper context. Remember: social engineering can work on any platform, because the vulnerability it exploits is user gullibility, not software flaws.

I know that, but do you really believe they have all the information and context believing Linux is free of viruses, exploits, etc?  Your kidding, right?

The article I linked to contains lots of posts from people that did not agree with the writer.  He in turn edited it and added some changes.  There is also a very interesting discussion going on, with plenty of nice posts and useful information.  I truly believe that anybody who's read it all will have a very balanced perspective about the whole thing.

Having said so, if I had to choose what is preferable, I'd say it is better that Linux users know they are indeed NOT immune, and that they would be better off keeping their eyes open.

Up to this point, I still don't understand why such message is creating such turmoil, really.

---

### Post by howlingmadhowie on 2010-03-02
it does seem to be quite a push to say "it's easier to write a virus for ubuntu than for windows nowadays" with your justification being "in ubuntu you can delete your own files".

---

### Post by GodLikeCreature on 2010-03-02
> **iRock said:**
> The implication that someone would download a picture file and grant it sudo powers just to see it is ridiculous, which is what the link is implying.

Hmmm...  Not sure you understood that article at all?  

The article actually explains how launchers can actually be executed with a double click, not needing further user interaction, not requiring anybody to grant executable grants.  That happens on KDE and GNOME, at least.

Again, I understand this is low tech, just like the article clearly states many times.  It is a very simple example, which is exactly why the writer is using it prove his point, to show that we are indeed not immune.

Once again, I very much agree with the writer that lots of unexperienced Linux users come to Ubuntu and other distros with the understanding that it is virus free because of its superior architecture and second to none security.  That is indeed mostly true, but they don't understand the fine print.

In the minds of those unexperienced users that translates as "I can do whatever I want, I am immune, I am superior to those Winlosers".  I know because most people I know, including myself, were thinking that very same thing when we started using Linux.

All I am saying is that we should not contribute to that distorted image, but clarify exactly how far our security goes.  No more, no less.

---

### Post by GodLikeCreature on 2010-03-02
> **howlingmadhowie said:**
> it does seem to be quite a push to say "it's easier to write a virus for ubuntu than for windows nowadays" with your justification being "in ubuntu you can delete your own files".

I am no hacker, but I am thinking that the amount of code and skill that needs to be put in place today for a successful Windows virus, considering the huge antivirus market available, is considerably larger than what this article shows?

My point being, we have not been attacked consistently for years like Windows has, so we are probably not as prepared to face the same threat.  It only seems logical?

---

### Post by Nick_Jinn on 2010-03-02
No OS is invulnerable, but the vast majority of viruses are written for the most common platform which is a PC running windows. 

Despite my gripes with Ubuntu and the hardware compatibility (Costing me money in damaged hard drives), I have probably saved more than that by not buying anti-virus software or Microsoft works and all that other crap.

Ubuntu is way more secure than windows, but dont go fooling yourself into thinking you are invincible. A determined hacker can compromise your security with any operating system.

---

### Post by Dayofswords on 2010-03-02
ubuntu works great on my laptop, kinda bad on my small factor form desktop

issues on laptop: 1, update best server freezes
issues on desktop: at least 6
including this issue [http://ubuntuforums.org/showthread.php?t=1418834](http://ubuntuforums.org/showthread.php?t=1418834)

---

### Post by GodLikeCreature on 2010-03-02
> **Nick_Jinn said:**
> Ubuntu is way more secure than windows, but dont go fooling yourself into thinking you are invincible. A determined hacker can compromise your security with any operating system.

Man, I am envious.  Your phrase here summarizes what I have been trying to state in several (fail) posts!  :p

Thanks!

---

### Post by ndefontenay on 2010-03-02
Hi.

Despite the frustration, keep up the good work.
I have to give you some encouragement here.

Using linux is like visiting a new country. You need to have a mind set. You can't complain that they do different than in your own country when you are not even in your home country.

So with this in mind, linux does things different. When it comes to buying a printer or a music device of any kind, you have to think in terms of what will work with linux and then buy this specific hardware. 

I know your printer did work and somehow you got some over problems and it stopped. I'm waiting for your specific threads to give you a help. 

I've switched my step daughter to linux recently but she is struggling too. She was mentioning "problems" she was having.
It turns out after a check this week end that she has downloaded cracked versions of photoshop and Microsoft Office and was trying to open them in linux. She also had a publisher file she was trying to open with linux. 

Not understanding that it's 2 different world makes it really frustrating for her because she is a young tech savvy person but too young to grasp the differences.

I know this is not your case, but simply, there are things which might seem simple or their might be assumptions in the air lpus I guess the pressure from maintaining stuff for your wife who nicely accepted to do the switch with you and now feel handicapped and you kind of feel responsible for that (I totally understand the feeling if that's what you feel).

So hang in there. It's an amazing experience and to be honest. I'm not in it because it works so much better. I'm in it for an ideal where it's ok to share and distribute knowledge. and yeah there is no viruses hahaha.

---

### Post by aysiu on 2010-03-02
For more information with full context, read:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

No OS is invincible. People are the weakest link in security. But not all OSes are equally susceptible to viruses. Viruses are not the only type of malware (trojans rely on social engineering, and social engineering can work on any platform).

---

### Post by GodLikeCreature on 2010-03-02
> **aysiu said:**
> For more information with full context, read:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

No OS is invincible. People are the weakest link in security. But not all OSes are equally susceptible to viruses. Viruses are not the only type of malware (trojans rely on social engineering, and social engineering can work on any platform).

Thanks for the link, that was a good read.  

Having said so, I don't agree my post or that article were lacking context.  The context was the following:  Many new users believe their brand new Linux box is invincible because so their techie neighbor said, and now they can feel superior too.  The article writer wanted to clarify they are indeed not that safe, and that certain precautions should be taken.  The "virus" he presents is just prove that it doesn't take an incredible amount of time or skills to create something that could potentially hit lots of inexperienced users.  It was just a point to support his argument, nothing else.  Most people will jump straight into complicated technical definitions and very thorough articles to prove that part of his argument wrong, when in fact all he's saying is: "Boys, don't get confused, you are not immune"

Other than that, I obviously agree 100% that Linux security is superior.  As far as I am concerned, and considering its imposed limitations, I believe Linux is the best OS out there.

---

### Post by aysiu on 2010-03-02
I never said Linux is invincible.

I believe in balance. The balance is this: stop being so paranoid. The viruses will not just magically infect your new Ubuntu installation unless you do something stupid, but be aware that you could do something stupid.

I'm very opposed to calling what you linked to a "virus," not because it's a matter of petty semantics, but because people tend to think of viruses as somehow just suddenly spreading without user interaction. Trojans, on the other hand, rely primarily on user gullibility. It's about tricking the user. In that case, it's a matter of educating the user on not installing from untrusted sources. This has nothing to do with Linux/Ubuntu and viruses. It has everything to do with not being a dupe.

I don't espouse the philosophy of "I'm on Linux. There are no problems in Linux. I can do whatever I want and not worry." Nor do I espouse the philosophy of "Linux is just as vulnerable to viruses as Windows. Watch out. You're never safe. Run that antivirus." You were not saying the latter, but most new users migrating from Windows already come with that attitude, so saying Linux could have viruses just serves to reinforce it.

Believe me, if someone comes in here saying Linux is invincible, I'm on them, too.

---

### Post by GodLikeCreature on 2010-03-02
> **aysiu said:**
> I never said Linux is invincible

I never said you did, I never talked about you, I was always talking about new Ubuntu users.

> **aysiu said:**
> I believe in balance. The balance is this: stop being so paranoid. The viruses will not just magically infect your new Ubuntu installation unless you do something stupid, but be aware that you could do something stupid.

That's exactly what I have been defending since I posted first about this topic.

> **aysiu said:**
> I'm very opposed to calling what you linked to a "virus," not because it's a matter of petty semantics, but because people tend to think of viruses as somehow just suddenly spreading without user interaction. Trojans, on the other hand, rely primarily on user gullibility. It's about tricking the user. In that case, it's a matter of educating the user on not installing from untrusted sources. This has nothing to do with Linux/Ubuntu and viruses. It has everything to do with not being a dupe.

I already mentioned how most would go into a technical explanation like the one you are giving to prove what is and what is not a virus.  In reality, in practical terms, only people who know about computers care about what a virus exactly is.  As long as their computer does something they don't want it to, users with no computer skills or interest will refer to that as "virus".  The example from my link clearly shows how that can happen if the user is not careful enough.  

Let's forget about technically inclined definitions for a second and recognize that a lot of those so called "virus" in Windows come from exactly that user misuse you refer to.  How many times have you heard about users getting infected because they double clicked on "blonde_with_huge_ti_ts.exe"?  Lots.  How many times did they actually use the exact technical term to explain how their machine was infected?  Very few.

That's part of my point as well.  If we say "Linux is virus free", what exactly do people understand?  Do they get that Linux runs kernel and interface processes in different CPU rings?  Or do they understand that they are 100% safe?  The writer of that article, and I agree with him, believes that they will understand the latter.

> **aysiu said:**
> I don't espouse the philosophy of "I'm on Linux. There are no problems in Linux. I can do whatever I want and not worry." Nor do I espouse the philosophy of "Linux is just as vulnerable to viruses as Windows. Watch out. You're never safe. Run that antivirus." You were not saying the latter, but most new users migrating from Windows already come with that attitude, so saying Linux could have viruses just serves to reinforce it.

You sure about that?  Not sure why they would migrate to Linux if it is more difficult, requires a learning curve and is just as insecure?  I think it is the complete opposite, as far as my experience goes.  They read that there are no viruses in Linux and they come with a "suicidal" attitude.

[QUOTE=aysiu;8905367]Believe me, if someone comes in here saying Linux is invincible, I'm on them, too[/QUOTE=aysiu;8905367]

---

### Post by uRock on 2010-03-02
Recurring Discussion? Not to sound rude, but you guys have hijacked the thread. (I admit, I was in on it, too)

---

### Post by dnguyen1963 on 2010-03-02
[QUOTE=Donny Bahama;8893604]I hope no one takes this the wrong way. I think Ubuntu is very cool... and I really WANT it to work... but man, oh man am I having a lot of troubles. And the really frustrating part is that I'm extremely tech/computer savvy!

On my notebook I'm dual booting Ubuntu hardy and Windows 7. I'd prefer to run Ubuntu as my primary OS, and I'm really pleased with my desktop configuration, etc. BUT...

[LIST]
[*]I can't get my microphone to work in Skype. (I've tried all kinds of Alsa updates and tweaks, tried installing and configuring Pulse, completely removing pulse - nothing will make it work.)


I could not get Skype to work on any version of Ubuntu even though my internal microphone works fine in other applications.  The only way I could get Skype to work was to use a Skype USB-microphone...annoying to have a headset on when you talk, but it works.

Regarding Ubuntu 9.04 and 9.10, I have had nothing but troubles (I have posted these troubles elsewhere).  I have gone back to 8.10...smooth sailing.  I hope 10.04 will be like 8.04 LTS in term of stability and compatibility.

---

### Post by Donny Bahama on 2010-03-02
> **Nick_Jinn said:**
> Well, I am poor and I take what I can get. I cant afford to run out and buy new hardware that my OS prefers, but I also dont like windows. I would buy a mac but again I cant afford one with the specs I want.Pretty much sums up my position. (Except for the part about the Mac. While I love the gorgeous design work, Apple is almost as closed as MS, so I *really* want to get Linux working well.)

---

### Post by uRock on 2010-03-02
> **Donny Bahama said:**
> Pretty much sums up my position. (Except for the part about the Mac. While I love the gorgeous design work, Apple is almost as closed as MS, so I *really* want to get Linux working well.)

It'll come to you. I fought with it at first, then as I learned what it was doing it all became easier.

---

### Post by Donny Bahama on 2010-03-02
> **mastablasta said:**
> About the non standard things - You do things like trying to have a very closed system devices (such as IPhone) work in another system.My expectations on that are really quite low. (Although I do still dare to hope...)
 > Also there are plenty programmes in Linux that are good alternatives to their windows counterpart. In fact to me there is too many so it's a bit hard to choose.Agreed - although in a couple of instances (so far) I've been unable to find anything that I like nearly as well. (E.g. IrfanView)
 > And it got me to realise that commands are indeed very different and even the ones that are the same work in a different way. so my previous knowledge won't help me much.I understand what you're saying, and I do realize that most of my Windows knowledge irrelevant. That said, compared to the average Windows user who has one giant partition and has never used a command line, I'm in a better position to be successful with Linux.
 > So time to go back to basics and i first tried to understand from this guide is how the system actually works. how "it does things". how it installs programmes, how it installs itself, how it manages devices, how drivers are managed etc.Reading it now. Thanks for the recommendation!

---

### Post by uRock on 2010-03-02
> **Donny Bahama said:**
> (E.g. IrfanView)
Isn't that an open source program? I think it is. I remember using that on XP. Good program.

> **Donny Bahama said:**
> Windows user who has one giant partition
 I have actually talked a few people into making a small 20 gig partition to install Windows, then make another larger partition to save files and to save backups into.

---

### Post by Tamlynmac on 2010-03-02
> Donny Bahama
Agreed - although in a couple of instances (so far) I've been unable to find anything that I like nearly as well. (E.g. IrfanView)

You mean something like [this]("http://www.xnview.com/en/index.html")? Not identical, but extremely similar.

Thanks for sharing your experiences & good luck.

---

### Post by Donny Bahama on 2010-03-02
> **houseworkshy said:**
> 9.10 had me feeling the same way and after far too much time head-banging against the system instead of creating I just got rid of it and replaced it with 9.04.  
Since 8.04 I've noticed that each release of Ubuntu needs more fiddling around before everything  works.  It has been display, keyboard mapping ( try fixing that one in the terminal, copy and paste as if one were putting together a ransom note from newspapers...aarrhhh!), repositories not working ...oh lots of things.  
So what I do now is have one which has been around for a while on one drive for work and recreation and the latest on another so I can play with all the new bells and whistles, try to make it all work and post bug reports to launchpad.  
Using the latest release as soon as it comes out does feel a bit like testing beta software, partly due to closed source drivers not having caught up.   This annoyed me when it started being standard but now that I know the score and don't do silly things like "I'll just install this in the morning which will leave the whole afternoon to meet my clients deadline"  Yeah really; 7.04 to 8.04 inclusive got me so used to problem free set-ups I really was that stupidly overconfident once.
I suppose if one wants "stable" to actually mean stable then the old original Debian is the best bet.  That said any supported version of Ubuntu which has been around for a few months has had most of it's bugs updated out of it and can be relied on so I stick with it.  Plus, if I have the time, messing with the new ones I learn a lot and as long as I can just drop them and switch to an older system in order to get work done or play something other than geek-tech-fiddling I quite enjoy it.That's a great idea. I like it. Problem is, I'm running 8.04 on both my and my wife's notebooks - and still finding certain problems to be insurmountable (given my current knowledge level.) Given that, it'll probably be a while before I feel ready to play with new releases!
> Linux and windows are very different.  I prefer Linux.  I really like the easy availability of help in the terminal; one could probably learn most of what there is to know just using the “man”, “info”, and “apropos” commands to start the journey.  That would of course be doing things the hard way, using a site like [http://linuxcommand.org]("http://linuxcommand.org/") is much better.So far, your description of "the hard way" is exactly how I'm doing it, so thanks for the link!
> I also like the applications and, personally, think gimp, with it's plug-ins, blows photo shop away on all but the range of file types it can handle.I don't doubt that the gimp outshines Photoshop in many areas... thing is, you're talking to a guy who never had time for P'shop's learning curve, either! :P

---

### Post by Donny Bahama on 2010-03-03
> **iRock said:**
> Isn't that an open source program? I think it is.It's freeware, but (last I knew), not open source.

---

### Post by Donny Bahama on 2010-03-03
> **Tamlynmac said:**
> You mean something like [this]("http://www.xnview.com/en/index.html")? Not identical, but extremely similar.That's one I haven't tried yet. I'll check it out. Thanks!

---

### Post by Gemnoc on 2010-03-03
> **iRock said:**
> [QUOTE=Donny Bahama;8907822]although in a couple of instances (so far) I've been unable to find anything that I like nearly as well. (E.g. IrfanView
Isn't that an open source program? I think it is. I remember using that on XP. Good program.[/QUOTE]
Nope, IrfanView is freeware, not open source. It's a terrific little program though and I too wish it was available on Linux. A suggestion: use the KDE app Gwenview along with kipi-plugins. It comes close. Personally I've started using DigiKam, it uses the same kipi-plugins for batch operations. I really liked F-Spot's UI better as it is much more user-friendly, but feature-wise it's miles (and I say miles) behind DigiKam, plus it's much slower at photo import. I was able to make DigiKam conform to my Gtk theme (I'm on GNOME) by installing the KDE System Settings.

As for your iPhone, I don't know about syncing mail/contacts, but I read an article today from a tech journalist who tried Ubuntu 10.04 Alpha 3, and it seems his iPhone 3G S was recognized right away, he was able to import pictures in F-Spot and his music in Rythmbox. I'm not linking as the article is in French.

[Edit: beaten to the punch...]

---

### Post by Donny Bahama on 2010-03-03
> **GodLikeCreature said:**
> if you consider that standard, we definitely have a different understanding of a standard installation!Clearly that's non-standard, but it's also non-OS-specific. By the time Ubuntu boots up, it has no awareness of any of that stuff, and what's left is a very standard Ubuntu installation.

---

### Post by Donny Bahama on 2010-03-03
> **ElSlunko said:**
> By the way iPod Touch works with music (so far anyways) in 10.04.I wish that helped me. My understanding is that USB communications with an iPhone is a whole 'nother ballgame.

---

### Post by Donny Bahama on 2010-03-03
> **Gemnoc said:**
> As for your iPhone, I don't know about syncing mail/contacts, but I read an article today from a tech journalist who tried Ubuntu 10.04 Alpha 3, and it seems his iPhone 3G S was recognized right away, he was able to import pictures in F-Spot and his music in Rythmbox.Not too worried about mail/contacts/calendar - that all syncs now via Gmail/Google Calendar and some Thunderbird plugins. And I actually managed (with a lot of reading and playing around) to get my iPhone recognized (as some sort of digital camera device) when I plug it in so that I can download pictures from it. But music (and later, maybe movies) - that's very cool news! If the Ubuntu dev community manages to get even mediocre iPhone support in 10.04, that would be quite a coup.

---

### Post by Donny Bahama on 2010-03-03
> **ndefontenay said:**
> Using linux is like visiting a new country. You need to have a mind set. You can't complain that they do different than in your own country when you are not even in your home country.I kind of understood that, but that analogy really helped to crystallize it for me. Really well said! Hopefully, I've struck the right tone, here... Not, "this country sucks!" but rather, "I'm really having some trouble adjusting to life in this country." The things I really hoped to get out of this thread were some words of encouragement (thanks for yours!), and some solid pointers from people who've been where I'm at now. I've gotten both, which is awesome! (Thanks also for the link in your sig. Since I can print from *my* notebook, I'll print that out and keep it handy.)> I know your printer did work and somehow you got some over problems and it stopped. I'm waiting for your specific threads to give you a help.I really appreciate that! For the past few days, my focus has been on getting my file server set up and working. (I call it my media server but I'm not streaming or anything - it's really just a file server that's predominately serving media files, and it's primary client is my HTPC.) Anyway, I've been tenaciously working on that - to the neglect of all the other issues. Still need to get wireless networking restored on my notebook's Ubuntu installation, and still need to try to figure out what's up with my wife's printing issues. And I *will* get to those things... soon.
> I know this is not your case, but simply, there are things which might seem simple or their might be assumptions in the air plus I guess the pressure from maintaining stuff for your wife who nicely accepted to do the switch with you and now feel handicapped and you kind of feel responsible for that (I totally understand the feeling if that's what you feel).Yeah, I used to be the superhero who could fix anything that went wrong for her... now I'm the guy who says, "Hmmm.... wonder how the heck THAT could happen!" All in all, though, she's pretty happy.
> So hang in there. It's an amazing experience and to be honest. I'm not in it because it works so much better. I'm in it for an ideal where it's ok to share and distribute knowledge. and yeah there is no viruses hahaha.I'll tell you why I'm in it (and this is actually a pretty cool story)...

Somewhere around 1998, a co-worker of mine decided to install Linux (I think it was Red Hat). He decided to go the net install route. He didn't have any blank 1.44MB floppies available, but he did have some 720K floppies (which, at the time, nobody was still using, but they were nevertheless still supported by the wonderful Linux tradition of continuing to support that which is otherwise obsolete!) 

Anyway, he wrote the diskette images and booted the machine. At some point, he was asked for some info (time zone/locale - something along those lines) which he supplied. Later in the install process, he was asked for the same info again. The install completed fine, but he thought it was odd that he'd been asked for the same information twice, so before going home, he posted to some mailing list asking why it had happened. When he came to work the next day, he had his answer.

Some developer in some country far, far away told him that this was a bug, and it had been fixed for the code branch that created 1.44MB boot disks, but the changes hadn't been carried over to the branch that created 720K boot disks -- "but they have now."

He fixed it. It was an incredibly innocuous bug, in a branch of code that few people would ever execute, yet because it was *there*, he fixed it. I thought that was the coolest thing I'd ever heard of, and it made me really want to be a Linux convert.

Ever since that day, I've dabbled with Linux on and off, but it wasn't until the abominations of Windows Vista and Office 2007 that I finally committed to converting (as much as possible) all my computers to (some flavor of) Linux - and evangelizing it to others as well. (That said, it's hard to evangelize a product when you're struggling to make it work properly yourself!)

---

### Post by Donny Bahama on 2010-03-03
> **dnguyen1963 said:**
> I could not get Skype to work on any version of Ubuntu even though my internal microphone works fine in other applications.  The only way I could get Skype to work was to use a Skype USB-microphone...annoying to have a headset on when you talk, but it works.Wearing a headset wouldn't really bother me so much, but my discretionary income is nonexistent. I'm launching a startup, and haven't had a salary in over 2 years ( = the "war chest" is empty.) I do web design and IT consulting to help make ends meet, but I try not to justify any expense that isn't truly essential. That said, I know that USB headsets can be had pretty cheap, and if it turns out that - even with the help of the good people on these forums - I'm still unable to get my microphone working, then I'll probably break down and buy a USB headset and consider it money well spent.
> I hope 10.04 will be like 8.04 LTS in term of stability and compatibility.+1 :)

---

### Post by GodLikeCreature on 2010-03-03
> **Donny Bahama said:**
> Clearly that's non-standard, but it's also non-OS-specific. By the time Ubuntu boots up, it has no awareness of any of that stuff, and what's left is a very standard Ubuntu installation.

Well, you are clearly messing around with boot sectors and yes, that could have an effect, theoretically.  Personally, I agree with you that what you are doing should work, but I am pretty sure no support line would agree.  I believe they would not support you until you went back to the vanilla boot.

---

### Post by GodLikeCreature on 2010-03-03
> **iRock said:**
> Recurring Discussion? Not to sound rude, but you guys have hijacked the thread. (I admit, I was in on it, too)

You are right, my apologies to all other members of this thread and to the OP.  Got too much into it!  ;)

---

### Post by dnguyen1963 on 2010-03-03
> **Donny Bahama said:**
> Wearing a headset wouldn't really bother me so much, but my discretionary income is nonexistent. I'm launching a startup, and haven't had a salary in over 2 years ( = the "war chest" is empty.) I do web design and IT consulting to help make ends meet, but I try not to justify any expense that isn't truly essential. That said, I know that USB headsets can be had pretty cheap, and if it turns out that - even with the help of the good people on these forums - I'm still unable to get my microphone working, then I'll probably break down and buy a USB headset and consider it money well spent.
+1 :)

Bought mine at Radioshack for $10.00.:D

---

### Post by Nick_Jinn on 2010-03-03
While I am upset that the harddrive compatibility issues (Damage occurring during reformatting mostly) hasnt been given the attention it deserves, I still love Ubuntu. It is by far the best distro of linux (in my opinion) with OpenSuse a close second.

You havnt lost me yet, but I would like to see some investigation into the formatting issues and hard drive compatibility before 10.4 is released.

---

### Post by uRock on 2010-03-03
> **Nick_Jinn said:**
> While I am upset that the harddrive compatibility issues (Damage occurring during reformatting mostly) hasnt been given the attention it deserves, I still love Ubuntu. It is by far the best distro of linux (in my opinion) with OpenSuse a close second.

You havnt lost me yet, but I would like to see some investigation into the formatting issues and hard drive compatibility before 10.**0**4 is released.

I like SuSe and Solaris. Mostly because I like Novell and Sun.

---

### Post by ndefontenay on 2010-03-03
Hi.

if it is about making your pictures slightly better, Gimp is just fine. The lurning curve is not huge. Just need to give it a go.

There's a huge amount of tutorial on how to do things with gimp which should give you a nice quick jump start.

---

### Post by uRock on 2010-03-03
I used to do a lot of editing in Photoshop, but Gimp, to me, has everything in the wrong place. I would be happier using an MS Paint-like tool. I guess I can use that as my excuse for keeping Windows around on my system.

---

### Post by ElSlunko on 2010-03-03
> **iRock said:**
> I used to do a lot of editing in Photoshop, but Gimp, to me, has everything in the wrong place. I would be happier using an MS Paint-like tool. I guess I can use that as my excuse for keeping Windows around on my system.

Yeah I used to use PS a lot and GIMP took forever to get used to (Never thought I would). Eventually I figured it out & the free plugins from fx foundry made it even better.

---

### Post by Donny Bahama on 2010-03-03
> **ndefontenay said:**
> Hi.

if it is about making your pictures slightly better, Gimp is just fine. The lurning curve is not huge. Just need to give it a go.It's not about photo enhancement; more like graphic design. The times when I would use Gimp is when I'm doing web design. 

I've tried to use Gimp multiple times. Every little thing I try to do, I end up googling to figure it out. Nothing is intuitive. It's OK, though. I'll either use Pinta or fire up a Windows VM to run Paint.net.  
> There's a huge amount of tutorial on how to do things with gimp which should give you a nice quick jump start.Yes, I do know that. But that's my point. The time I'd spend on those tutorials is time I can't really afford (especially in light of everything else I'm trying to do/learn.)

---

### Post by gruvn on 2010-03-03
I think I can help you with your skype/microphone problem since I solved mine last night.  Well, I didn't solve it - Steve Jackson @ [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433055](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433055) did.  Essentially, install pulseaudio volume control (pavucontrol), and then unlock the left and right faders (for the mic).  Set one to max and the other to min, and it should work.  If no love, reverse them (ie set the opposite to max).

Hope that helps get your skype working.

---

### Post by Donny Bahama on 2010-03-04
Thanks. I'll give that a try. :)

---

### Post by Donny Bahama on 2010-03-04
Here is a perfect example of the frustration I'm feeling. The general response to *this* thread has been, "Post your problems, one per thread, and you'll get help." [So I did that]("http://ubuntuforums.org/showthread.php?p=8911234"), and what do I get?> **samosamo said:**
> Why are you doing it the hard way?  You'll be  sorry when you lose all your data.  I hope you have a backup.  Just copy  the data over to another physical device.The hard way??? How the heck was I to know it's "the hard way"? Since I don't have another physical device that will hold that much data, it's the only way available to me. Of course, had I known it's not just "the hard way" but apparently "the way that will certainly result in the permanent loss of all my data", I would have steered clear.

When I responded that I didn't have anotherr large physical drive to use for "the easy way", I got this valuable gem...> **KiLaHuRtZ said:**
> [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148412](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148412)This would have been immensely helpful if I was too f$#%ing stupid to find somewhere to purchase a large physical drive on my own. But I'm not an idiot. I'm an intelligent person who doesn't happen to have $100 to spare.

What really gets me is that apparently ntfsresize doesn't work well and should not be used. [I][B]Why, then, is it out there, with documentation, so that any noob can come along and lose a terabyte of valuable data??? 
[/B][/I][SIZE=4][B][COLOR=Red]
[/COLOR][/B][/SIZE]To continue with the previous analogy, it's like I'm in a foreign country and I needed to get somewhere so I followed the signs that point the way. Only they took me to a freeway that isn't finished yet and I drove my car off a piece of the freeway that dead ends in mid-air and my car is now hanging there, precariously on the brink. And people are saying, "Why did you go THAT way?" and "You shouldn't have followed those signs."

Seriously, [SIZE=4][B][COLOR=Red]WTF?!?!
[/COLOR][/B][/SIZE]

---

### Post by Gemnoc on 2010-03-04
I agree with you, that guy posting a NewEgg link acted like a prick.

I just came upon this, I thought it might interest you:

[http://www.omgubuntu.co.uk/2010/03/sync-iphone-and-ipod-touch-in-ubuntu.html](http://www.omgubuntu.co.uk/2010/03/sync-iphone-and-ipod-touch-in-ubuntu.html)

---

### Post by Donny Bahama on 2010-03-04
> **Gemnoc said:**
> I agree with you, that guy posting a NewEgg link acted like a prick.

I just came upon this, I thought it might interest you:

[http://www.omgubuntu.co.uk/2010/03/sync-iphone-and-ipod-touch-in-ubuntu.html](http://www.omgubuntu.co.uk/2010/03/sync-iphone-and-ipod-touch-in-ubuntu.html)Thank you!!! If that works, it's going to be SWEET!

---

### Post by longtom on 2010-03-06
Coming back quickly to your fast photo editing woes:

I also miss IrfanView and have a n old thread about that somewhere in the beginners section.  Also there were loads of suggestion I never found a real native solution for the problem without going to Gimp.

At the end I settled for the second best (imo), which is running [PhotoScape](http://www.photoscape.org/ps/main/index.php) in wine.

Let that be stated - I do consider wine an advanced toy to try to get windows applications running (drawing from my personal experiences and with no disrespect to anybody working on it), but it works really well with PhotoScape with me.

Hope it does for you.

---

### Post by Tamlynmac on 2010-03-06
> longtom
I also miss IrfanView and have a n old thread about that somewhere in the beginners section.

I did earlier suggest [XnView]("http://www.xnview.com/en/index.html") in this thread. It's very similar to IrfanView. It does take a few minutes to setup and learn to use, but it's our photo editor of choice. Saving a photo in a different format is simply and it lists a substantial number of formats to select from. The filters are there and of course thumb view is easy.

Might I suggest you give it a try. All one need do is download the file, extract it to a folder labeled XnView and place a link to Xnview (located in the bin folder) in your menu. The first screen you see will be a small window for setup, after that the when XnView is selected, it will open to a full size window - if setup properly.

---

### Post by Donny Bahama on 2010-03-06
XnView looks great as far as features & screenshots, but I can't seem to install it! It's not in the channel and there's no .deb file. apt doesn't find 'xnview' or 'XnView'. I downloaded the tarball and extracted it, but when I try to run sudo ./install, I get 
```
  OS  : Linux, version 2.6.24-27-generic
This script will install nview/nconvert/xnview in the /usr/local/bin directory
cp: cannot create regular file `/usr/lib/X11/app-defaults/XnView': No such file or directory
chmod: cannot access `/usr/lib/X11/app-defaults/XnView': No such file or directory

Done!

```

---

### Post by uRock on 2010-03-06
Did you run ```
sudo chmod +x filename
``` before running ```
./flename?
```

---

### Post by Donny Bahama on 2010-03-06
> **iRock said:**
> Did you run ```
sudo chmod +x filename
``` before running ```
./flename?
```Thanks for the ultra-noob support! ;) At first I forgot to do that (and got some other error about permissions.) But I figured that out and chmodded it. That's when I got the error I posted above.

---

### Post by Donny Bahama on 2010-03-06
By the way, for all those who like Paint.net, Pinta is awesome. Virtually identical and works without running under Wine.

---

### Post by Tamlynmac on 2010-03-06
> Donny Bahama
XnView looks great as far as features & screenshots, but I can't seem to install it! It's not in the channel and there's no .deb file. apt doesn't find 'xnview' or 'XnView'. I downloaded the tarball and extracted it, but when I try to run sudo ./install, I get

> 
Tamlynmac
All one need do is download the file, extract it to a folder labeled XnView and place a link to **xview (located in the bin folder)** in your menu. The first screen you see will be a small window for setup, after that the when XnView is selected, it will open to a full size window - if setup properly.

No need to use the install, simply run xnview located in the bin folder. Link it to your menu in edit menus and use "Home Folder/Folder Name/bin/xnview" as the command.

---

### Post by uRock on 2010-03-06
> **Donny Bahama said:**
> Thanks for the ultra-noob support! ;) At first I forgot to do that (and got some other error about permissions.) But I figured that out and chmodded it. That's when I got the error I posted above.

Is it in the home folder? Whenever I install programs like such I put them in the home folder so that they are easier to run.

BTW, I usually remember to chmod, but then I end up forgetting the ./ in front of the program to make it run. It's the easy stuff that brings me down.

---

### Post by kg4cna on 2010-03-06
> **iRock said:**
> Is it in the home folder? Whenever I install programs like such I put them in the home folder so that they are easier to run.

BTW, I usually remember to chmod, but then I end up forgetting the ./ in front of the program to make it run. It's the easy stuff that brings me down.

If you copy the binary to the BIN directory, with "sudo cp xnview /usr/bin", you should be able to call it up from a terminal by just using the command "xnview" (without quotes).

THEN add an entry to the applications menu. In the path section, put "/usr/bin/xnview" (without quotes) and you should be ready to go.

A~

---

### Post by Gemnoc on 2010-03-06
> **longtom said:**
> At the end I settled for the second best (imo), which is running [PhotoScape](http://www.photoscape.org/ps/main/index.php) in wine.
If you run what you consider the second best app in Wine, why not run IrfanView itself in wine? I hear it's been done.

Oh, I see: IrfanView gets a [gold rating]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834"), Photoscape gets a [platinum one]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19044") (better).

Still, as I already said, I absolutely love IrfanView, IMHO the best freeware on Windows, and used to miss it terribly on Ubuntu, until I stopped grumbling and adapted to what's available on Ubuntu. I realized that with Gwenview and kipi-plugins installed, I can do all that I used to with IrfanView. Actually, I use DigiKam as I wanted to manage my photo collection, but the tools are the same. Gwenview is easier to work with.

I use Windows apps in Wine only if there are absolutely no alternative (like Sketchup). I absolutely hate the fact that they don't integrate well in GNOME. UI consistency over all apps is very important to me. Windows apps render text badly, and icons are too small.

@Donny Bahama

Glad to know you like Pinta. I haven't managed to install it yet!

---

### Post by Gemnoc on 2010-03-06
> **kg4cna said:**
> If you copy the binary to the BIN directory, with "sudo cp xnview /usr/bin", you should be able to call it up from a terminal by just using the command "xnview" (without quotes).

THEN add an entry to the applications menu. In the path section, put "/usr/bin/xnview" (without quotes) and you should be ready to go.

A~
Uh, shouldn't you rather place a symlink to it in /usr/bin than actually copy the file? At least that's what I understand should be done usually.

---

### Post by Donny Bahama on 2010-03-06
> **Tamlynmac said:**
> No need to use the install, simply run xnview located in the bin folder. Link it to your menu in edit menus and use "Home Folder/Folder Name/bin/xnview" as the command.OK, but the purist in me wants to put it where it belongs. (Not in my home folder.) Now if I only understood where, exactly, that is...

> **iRock said:**
> BTW, I usually remember to chmod, but then I end up forgetting the ./ in front of the program to make it run. It's the easy stuff that brings me down.Amen to that!

> **kg4cna said:**
> If you copy the binary to the BIN directory, with "sudo cp xnview /usr/bin", you should be able to call it up from a terminal by just using the command "xnview" (without quotes).

THEN add an entry to the applications menu. In the path section, put "/usr/bin/xnview" (without quotes) and you should be ready to go.Cool. Thanks!

> **Gemnoc said:**
> If you run what you consider the second best app in Wine, why not run IrfanView itself in wine? I hear it's been done.Yep. I have it set up. But I don't think you can associate it so that it opens by default when you open an image.

> I absolutely love IrfanView, IMHO the best freeware on Windows, and used to miss it terribly on Ubuntu, until I stopped grumbling and adapted to what's available on Ubuntu. I realized that with Gwenview and kipi-plugins installed, I can do all that I used to with IrfanView. Actually, I use DigiKam as I wanted to manage my photo collection, but the tools are the same. Gwenview is easier to work with.I've played with both Gwenview (no idea about the kipi-plugins) and DigiKam and wasn't thrilled with either. Maybe I didn't give them enough of a chance.

> Glad to know you like Pinta. I haven't managed to install it yet!For me, it was a breeze. But then, I already had mono installed from when I tried to get Paint.mono working.

> **Gemnoc said:**
> Uh, shouldn't you rather place a symlink to it in /usr/bin than actually copy the file? At least that's what I understand should be done usually.Then where should the actual program live?

---

### Post by Donny Bahama on 2010-03-06
Looks like my graphics app trials and tribulations are far from over...

I tried running XnView from where I had extracted it (home folder). When I opened an image, it opened with like 25% opacity. You could barely make out the image with my desktop background showing through. Pretty unusable.

I took a screenshot to show everyone, but when I went into Pinta to resize it, I found out that Pinta crashes every time I try to save an image. (I thought maybe there was some permissions issue, so I tired doing a save as to a new image. Same result.) Another problem I've discovered with Pinta is that it can't seem to handle associations. Make it (for example) the default app for opening PNG files, then open a PNG file -- Pinta opens to a new/empty image. :(

---

### Post by uRock on 2010-03-06
When you load it with the paper clip looking attachment thing when posting, it will downsize the picture for you. 

Sadly, when I have a photo project, I drop the picture into the NTFS partition and open it with MS Paint or Photoshop.

---

### Post by Gemnoc on 2010-03-06
> **Donny Bahama said:**
> OK, but the purist in me wants to put it where it belongs. (Not in my home folder.) Now if I only understood where, exactly, that is...
Some commercial programs install in /opt. You can also save the odd program folder in /usr I think, at least that's where I put them. Do it in CLI though, if you use Nautilus chances are you'll create troubles with permissions, I know I always do.
> Yep. I have it set up. But I don't think you can associate it so that it opens by default when you open an image.
Don't know about that...
> I've played with both Gwenview (no idea about the kipi-plugins) and DigiKam and wasn't thrilled with either. Maybe I didn't give them enough of a chance.
The kipi-plugins add functionality (batch operations among others) to KDE apps like Gwenview and DigiKam. You have to install this package separately. Without it, Gwenview is severly limited.
> For me, it was a breeze. But then, I already had mono installed from when I tried to get Paint.mono working.
When I said I didn't manage to install Pinta, I meant I didn't find the time to do it. :p

But seeing the troubles you're having, I wonder if it's worth it! It is the first release, so I guess it must be unstable...

> Then where should the actual program live?
Possibly in /usr, as I said earlier, then you create a symbolic link of the program executable in /usr/bin which is populated with a lot of symlinks. The actual real executable files you find there all seem to be system ones. But hey, I still am much of a newbie, so don't take my word for it! ;)

---

### Post by Gemnoc on 2010-03-06
Hey,

Found this in the Getting Started documentation for Ubuntu 6.06. No idea why it's not in the 9.10 doc, but I think it's still useful:

[Linux Basics]("https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html")

According to it, I was right about /opt and /usr.

---

### Post by ElSlunko on 2010-03-07
> **Donny Bahama said:**
> Looks like my graphics app trials and tribulations are far from over...

I tried running XnView from where I had extracted it (home folder). When I opened an image, it opened with like 25% opacity. You could barely make out the image with my desktop background showing through. Pretty unusable.

I took a screenshot to show everyone, but when I went into Pinta to resize it, I found out that Pinta crashes every time I try to save an image. (I thought maybe there was some permissions issue, so I tired doing a save as to a new image. Same result.) Another problem I've discovered with Pinta is that it can't seem to handle associations. Make it (for example) the default app for opening PNG files, then open a PNG file -- Pinta opens to a new/empty image. :(

What is it that you require from a program like XnView?

---

### Post by sophicsage on 2010-03-07
> **Donny Bahama said:**
> 

I have to say, if this is THIS painful for me, Linux still has a long way to go before it sees widespread acceptance among "normal" users.

I am in the same boat.  I worked with Ubuntu 9.10 from Nov. through Feb.  It does work out of the box for most things.  However, the fatal blow for me was the audio problems.  I couldn't get it to work no matter what I did.  I really needed it to work so that I could record my music, but to no avail.  My internal mic never did work, though I finally got a USB mic working.  The Jack Audio malfunctioned every time I tried to use a program that required it, such as music recording / mixing.

Audio problems are a VERY serious Ubuntu problem.  If the audio problems could be solved, Linux would be well on its way to being a viable desktop in the marketplace.  I have to agree with you that Linux is not ready for "regular" end users.  It has potential.

I'm going to try a dual boot with 10.04 when it comes out just to see if the audio issues have been solved.  Hopefully, they have.

---

### Post by Donny Bahama on 2010-03-07
> **ElSlunko said:**
> What is it that you require from a program like XnView?Great question, thanks for asking! Let's see...

[LIST=1]
[*]I should be able to set it as the default app for opening JPG, PNG and GIF files.
[*]Images should open at actual size unless they're too large for the maximized window (in which case they should be fit to the window.)
[*]There should be simple keystrokes (spacebar/backspace or left/right arrows) for navigating to the next/previous image in the directory.
[*]There should be simple keystrokes for rotating the image in either direction
[*]I should be able to do a high-quality resize (e.g. resample) - with or without maintaining the aspect ratio, either by percentage of original size or by specifying a height and/or width.
[*]Batch renaming/resizing
[*]A simple and easy to use cropping tool - click and drag to select an area, grab handles and drag to modify the selection, then a keystroke to crop to the selection.
[*]Basic image manipulation  such as brightness, contrast, gamma, saturation, color balance and maybe sharpen
[*]If I ***had to***, I suppose I could settle for a keystroke that opens the image in a (user-configurable) image editing app (GQview has this) for cropping and image manipulation, but I do cropping and gamma correction *a lot *in IrfanView and am very accustomed to/spoiled by it in this regard.
[/LIST]
 That's the off-the-top-of-my-head short list of things I depend(ed) on IrfanView for.

---

### Post by Donny Bahama on 2010-03-07
> **GodLikeCreature said:**
> sharing a network connection with a VirtualBox VM machine is a piece of cake.  As long as the connection is working on the host, it just works, so not sure what you did there.I think I see, now, where this statement came from. I managed to totally break my wireless while trying to make this work. Until I could get it fixed, I've been using a wired connection. I fired up a VirtualBox VM and the networking "just worked". Wish it played well with wifi.

---

### Post by Donny Bahama on 2010-03-13
These seems as good a place as any to say that the whole "sudo" thing makes no sense to me. It would make sense if I was required to enter root's password -- but I'm not. All I have to do is put in my own password and I can destroy things just as catastrophically as if I was root! I don't get it.

---

### Post by ElSlunko on 2010-03-13
> **Donny Bahama said:**
> These seems as good a place as any to say that the whole "sudo" thing makes no sense to me. It would make sense if I was required to enter root's password -- but I'm not. All I have to do is put in my own password and I can destroy things just as catastrophically as if I was root! I don't get it.

By default your password = root password IIRC. So it's best to make a strong one.

---

### Post by longtom on 2010-03-15
> **ElSlunko said:**
> By default your password = root password IIRC. So it's best to make a strong one.

Or - to elaborate on this - the first user is automatically root.  The second user (and all following) won't be.
This is different from a lot of other distros.  Whether it's better or worse is a question of debate....

---

### Post by coffeecat on 2010-03-15
> **ElSlunko said:**
> By default your password = root password IIRC. So it's best to make a strong one.

Point of information. The first created user's password is not the root password which, in Ubuntu, is a randomly generated one and unknown because is not needed. A subtle point but an important one if you are going to understand the sudo model. The first created user has administrative rights and can elevate to root privileges temporarily with their own password. The first created user can choose whether or not to grant administrative rights to subsequently created users. More here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **Donny Bahama said:**
> These seems as good a place as any to say that the whole "sudo" thing makes no sense to me. It would make sense if I was required to enter root's password -- but I'm not. All I have to do is put in my own password and I can destroy things just as catastrophically as if I was root! I don't get it.

An illogical argument in my view. If you are the administrator of your system you can destroy things catastrophically whether you use sudo or su to root. In Ubuntu you have to remember one password in order to be able to hose your system :wink:. In Fedora, for example, you have to remember two - unless you set the root password to be the same as your account password. In fact, iirc, openSUSE does just that by default - that is, same password for root and first user account.

Also, it is [trivially easy]("http://www.mjmwired.net/resources/mjm-fedora-f12.html#sudo") to set up sudo in a distro such as Fedora.

---

### Post by aysiu on 2010-03-15
> **coffeecat said:**
> Point of information. The first created user's password is not the root password which, in Ubuntu, is a randomly generated one and unknown because is not needed. It's not randomly generated. It's actually disabled entirely. Check the /etc/shadow file for more details.

---

### Post by coffeecat on 2010-03-15
> **aysiu said:**
> It's not randomly generated. It's actually disabled entirely. Check the /etc/shadow file for more details.

Thanks for the correction. I think my misunderstanding is based on my memory of Breezy/Dapper days. It was widely said then that there was a randomly-generated but hidden and unused root password, but a bit of googling just now tells me that this random password business is a sort of urban myth. 

Whatever - I don't understand why people get so worked up about the sudo model and want to fight it. I used Gentoo as my main distro for about 18 months and I lived most of that time in a root terminal. You do when you run Gentoo as your main distro. :( I find the Ubuntu way of doing things makes sense.

---

### Post by cariboo on 2010-03-15
> **Donny Bahama said:**
> These seems as good a place as any to say that the whole "sudo" thing makes no sense to me. It would make sense if I was required to enter root's password -- but I'm not. All I have to do is put in my own password and I can destroy things just as catastrophically as if I was root! I don't get it.

The reason the root account is disabled, is not to stop you from destroying your system, as you said you can destroy it using sudo, but to protect your system from the nasties on the internet. The way the default system is set up, the first thing a cracker has to do is to find out your user name, then crack the paswword. With the root account enabled, the cracker is already half way there, once he knows that root is enabled, all he has to do is brute force root's password.

As bodhi,zazen always likes to say security is like an onion, the more layers there are the harder it is to crack.

---

