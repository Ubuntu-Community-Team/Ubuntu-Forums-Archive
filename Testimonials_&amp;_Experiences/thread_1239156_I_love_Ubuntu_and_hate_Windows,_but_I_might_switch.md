---
title: "I love Ubuntu and hate Windows, but I might switch back so I can use certain programs"
date: 2009-08-13
forum: Testimonials &amp; Experiences
---

### Post by W.A.C. on 2009-08-13
I was a Windows user for around 11 years. During much of that time, I absolutely hated it. Sure, I originally liked Windows 95 and 98 back when I was 8-10 years old but after a while, I began to not like it so much. Then, once I switched to Windows XP in '03, it was such a dramatic improvement that I liked Windows again. Overtime though, my disdain for Windows started to come back and by 2006, I absolutely hated Windows XP.

          About two weeks ago, I built a new computer and installed Ubuntu. What a huge improvement. Easy installation, easy to get almost all non-Windows programs and hardware running, and it's much easier to customize. The problem? I can't get Foobar2000 to run decently and from the research I've done, it sounds like it isn't possible to get Cool Edit Pro 2.1 (or it's later editions as Adobe Audition) to work properly. I can tolerate the loss of my favorite music playing program, but I have done quite a bit of sound editing in the past and those files are designed to be run with Cool Edit Pro. Not only that, but it's an extremely nice sound editing program and I would absolutely hate to part with it. While I don't do sound editing a lot, I'm not willing to be inable to use those files. If I can't use them under Ubuntu, I might have to switch back to lousy Windows XP. What should I do?

---

### Post by squaregoldfish on 2009-08-13
Try having a play with Audacity - it might well have the features you need. If it does, borrow someone's machine so you can convert your CoolEdit files, and you'll be set.

If you truly can't bear to part with Adobe Audition, it looks like you're stuck with Windows. Perhaps virtualising it using something like VirtualBox will suit, so you can use Ubuntu for the rest? Just a thought...

Steve.

---

### Post by hansdown on 2009-08-13
Welcome to the forum W.A.C.

You could try dual booting both operating systems. That way you get to have everything you need to use.

[http://video.google.ca/videosearch?q=dual+booting+ubuntu+9.04+and+windows&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&ei=dvuDSpjaCoaysgPV-ISqBw&sa=X&oi=video_result_group&ct=title&resnum=4#](http://video.google.ca/videosearch?q=dual+booting+ubuntu+9.04+and+windows&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&ei=dvuDSpjaCoaysgPV-ISqBw&sa=X&oi=video_result_group&ct=title&resnum=4#)

---

### Post by W.A.C. on 2009-08-13
I forgot to mention that I also like to play fangames and the only fangame I have tried to get working on Ubuntu doesn't work.

> **squaregoldfish said:**
> Try having a play with Audacity - it might well have the features you need. If it does, borrow someone's machine so you can convert your CoolEdit files, and you'll be set.

I used to use Audacity before getting Cool Edit Pro and I can honestly say that Audacity is no where near as good as Cool Edit Pro.

> **squaregoldfish said:**
> If you truly can't bear to part with Adobe Audition, it looks like you're stuck with Windows. Perhaps virtualising it using something like VirtualBox will suit, so you can use Ubuntu for the rest? Just a thought...

Steve.

I know absolutely nothing about VirtualBox but I'll look into it later today after I get some rest.

> **hansdown said:**
> Welcome to the forum W.A.C.

You could try dual booting both operating systems. That way you get to have everything you need to use.

[http://video.google.ca/videosearch?q=dual+booting+ubuntu+9.04+and+windows&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&ei=dvuDSpjaCoaysgPV-ISqBw&sa=X&oi=video_result_group&ct=title&resnum=4]("http://video.google.ca/videosearch?q=dual+booting+ubuntu+9.04+and+windows&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&ei=dvuDSpjaCoaysgPV-ISqBw&sa=X&oi=video_result_group&ct=title&resnum=4#")

My original intention with Ubuntu was to use it as my main OS and duel-boot with a completely offline XP so I can play certain fangames. Unfortunately, Wine has turned out to be not as good as I hoped. If I duel boot and use both Ubuntu and XP, is there a way I can access certain files in both XP and Ubuntu? One idea I just had was to use both OS's and only use XP for tasks I can't do under Ubuntu. For Cool Edit Pro, I would need to have access to my music files and I would love to have equal access to those files under both XP and Ubuntu.

---

### Post by Tibuda on 2009-08-13
There's also [Ardour]("http://ardour.org/"), but have you checked the Wine APP DB? [Cool Edit Pro 1.2 is rated as Platinum]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17270") (works without tweaking).

---

### Post by Tibuda on 2009-08-13
> **W.A.C. said:**
> My original intention with Ubuntu was to use it as my main OS and duel-boot with a completely offline XP so I can play certain fangames. Unfortunately, Wine has turned out to be not as good as I hoped. If I duel boot and use both Ubuntu and XP, is there a way I can access certain files in both XP and Ubuntu? One idea I just had was to use both OS's and only use XP for tasks I can't do under Ubuntu. For Cool Edit Pro, I would need to have access to my music files and I would love to have equal access to those files under both XP and Ubuntu.

Linux can read Windows partitions (FAT and NTFS), but Windows can't read Linux partitions, so you better store your data in a shared FAT or NTFS partition, so both systems can read them.

---

### Post by mdsmedia on 2009-08-13
> **danielrmt said:**
> Linux can read Windows partitions (FAT and NTFS), but Windows can't read Linux partitions, so you better store your data in a shared FAT or NTFS partition, so both systems can read them.
While that's true, there are utilities in both Windows and Linux to read/write to NTFS/EXT3.

---

### Post by W.A.C. on 2009-08-13
> **danielrmt said:**
> There's also [Ardour]("http://ardour.org/"), but have you checked the Wine APP DB? [Cool Edit Pro 1.2 is rated as Platinum]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17270") (works without tweaking).

I use Cool Edit Pro 2.1, which came out in 2003. I can't imagine how basic the program is under 1.2.

> **danielrmt said:**
> Linux can read Windows partitions (FAT and NTFS), but Windows can't read Linux partitions, so you better store your data in a shared FAT or NTFS partition, so both systems can read them.

Thanks for the information.

> **mdsmedia said:**
> While that's true, there are utilities in both Windows and Linux to read/write to NTFS/EXT3.
 
Good to know.

---

### Post by murderslastcrow on 2009-08-13
VirtualBox now supports DirectX, so if you can't get it running in the newest versions of Wine, you can install Windows XP in a VirtualBox, and reboot it into safe mode to install the Direct3D additions along with the normal additions. This works great for me when it comes to those few programs that aren't working perfectly in Wine, yet.

Of course, I suggest dual-booting until you feel comfortable running a VirtualBox instance of Windows, just due to ease. Hopefully there will be a solution to these problems in the coming years as Linux continues to grow as a platform.

---

### Post by steveneddy on 2009-08-13
Install Windows on a Virtual Machine like [VirtualBox]("http://www.virtualbox.org/").

It is easier than dual booting and is very convenient to use and you can use Ubuntu and Windows simultaneously.

The best VirtualBox to use is version 3.0 that you can [URL="http://www.virtualbox.org/wiki/Downloads"]DL from the website.
[/URL]

---

### Post by Radioman991 on 2009-08-13
> **W.A.C. said:**
> I was a Windows user for around 11 years. During much of that time, I absolutely hated it. Sure, I originally liked Windows 95 and 98 back when I was 8-10 years old but after a while, I began to not like it so much. Then, once I switched to Windows XP in '03, it was such a dramatic improvement that I liked Windows again. Overtime though, my disdain for Windows started to come back and by 2006, I absolutely hated Windows XP.

          About two weeks ago, I built a new computer and installed Ubuntu. What a huge improvement. Easy installation, easy to get almost all non-Windows programs and hardware running, and it's much easier to customize. The problem? I can't get Foobar2000 to run decently and from the research I've done, it sounds like it isn't possible to get Cool Edit Pro 2.1 (or it's later editions as Adobe Audition) to work properly. I can tolerate the loss of my favorite music playing program, but I have done quite a bit of sound editing in the past and those files are designed to be run with Cool Edit Pro. Not only that, but it's an extremely nice sound editing program and I would absolutely hate to part with it. While I don't do sound editing a lot, I'm not willing to be inable to use those files. If I can't use them under Ubuntu, I might have to switch back to lousy Windows XP. What should I do?

W A C

I would absolutely LOVE Audacity IF it could write the metadata (header) info for WAV files.  That is what makes Audition such a staple in radio stations.  Makes it a breeze to interface to automation systems.

If Audacity could do that, I would have VERY FEW Windows machines in stations now...especially in studios where jox could load them up with crap.

My 0.02

---

### Post by Teamgeist on 2009-08-14
> **Radioman991 said:**
> W A C

I would absolutely LOVE Audacity IF it could write the metadata (header) info for WAV files.  That is what makes Audition such a staple in radio stations.  Makes it a breeze to interface to automation systems.

If Audacity could do that, I would have VERY FEW Windows machines in stations now...especially in studios where jox could load them up with crap.

My 0.02

Have you contacted the developers of Audacity about that and (kindly) requested that feature?

If they don't know about it, they can't implement it. ;)

That's the cool thing about open source software... YOU can make a difference!

So go to [http://audacity.sourceforge.net/contact/](http://audacity.sourceforge.net/contact/) and let them know.

---

### Post by ubuntu27 on 2009-08-14
You can try Linux Multimedia Studio (LMMS):

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)


I don't know if it is in the repositories.

---

### Post by pirate_tux on 2009-08-14
> **W.A.C. said:**
> I was a Windows user for around 11 years. During much of that time, I absolutely hated it. Sure, I originally liked Windows 95 and 98 back when I was 8-10 years old but after a while, I began to not like it so much. Then, once I switched to Windows XP in '03, it was such a dramatic improvement that I liked Windows again. Overtime though, my disdain for Windows started to come back and by 2006, I absolutely hated Windows XP.

          About two weeks ago, I built a new computer and installed Ubuntu. What a huge improvement. Easy installation, easy to get almost all non-Windows programs and hardware running, and it's much easier to customize. The problem? I can't get Foobar2000 to run decently and from the research I've done, it sounds like it isn't possible to get Cool Edit Pro 2.1 (or it's later editions as Adobe Audition) to work properly. I can tolerate the loss of my favorite music playing program, but I have done quite a bit of sound editing in the past and those files are designed to be run with Cool Edit Pro. Not only that, but it's an extremely nice sound editing program and I would absolutely hate to part with it. While I don't do sound editing a lot, I'm not willing to be inable to use those files. If I can't use them under Ubuntu, I might have to switch back to lousy Windows XP. What should I do?

Using programs which save files in proprietary formats it's not a clever decision.

---

### Post by W.A.C. on 2009-08-15
Well, I tried to installed VirtualBox and failed. Why? I can never get Software Sources to work. I have no idea why, but I manage to fail everytime. I put "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free" into Software Sources for third parties, went to close the program, got some reload message, and then received the following message.

> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.:/

Edit-

VirtualBox is installed.

---

### Post by Arthur_D on 2009-08-15
> **Radioman991 said:**
> W A C

I would absolutely LOVE Audacity IF it could write the metadata (header) info for WAV files.  That is what makes Audition such a staple in radio stations.  Makes it a breeze to interface to automation systems.

If Audacity could do that, I would have VERY FEW Windows machines in stations now...especially in studios where jox could load them up with crap.

My 0.02
It can, in Audacity 1.3.8 (beta). I found it in 1.3.7, and for a beta it's been incredibly stable for me. :KS

---

### Post by warreno on 2009-08-16
> **W.A.C. said:**
> VirtualBox is installed.

Others suggested it too. I hope it works for you. Its install on my Mac (OSX.5.8) was quirky and the documentation for it was out of date, but now that I've got it up and running it seems to be working fairly well.

I'd like to know what your experience is in using it. Does it seem to do what you need it to do?

---

### Post by W.A.C. on 2009-08-16
> **warreno said:**
> I'd like to know what your experience is in using it. Does it seem to do what you need it to do?
I didn't realize VirtualBox was limited in graphical capabilities. For hours now, I've been trying to find a way to shrink my partition for Ubuntu so I can have space for Windows 7. Unfortunately, I can't seem to find a way to shrink it. :/ I tried unmounting it but I get [this message](http://img197.imageshack.us/img197/9821/screenshot2yno.png). I'm at quite a lost. :/

---

### Post by joshedmonds on 2009-08-16
> **W.A.C. said:**
> I tried unmounting it but I get this message

It looks like you're trying to unmount the / filesystem from a running install. You will need to use a liveCD/USB to make changes to that partition.

> **W.A.C. said:**
> I didn't realize VirtualBox was limited in graphical capabilities.

Have you installed the guest extensions yet?

---

### Post by W.A.C. on 2009-08-17
> **joshedmonds said:**
> It looks like you're trying to unmount the / filesystem from a running install. You will need to use a liveCD/USB to make changes to that partition.
I don't know how to get the live CD running during the screens that appear before Ubuntu begins. :/ [This]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") is the correct link to the .iso file, right?

> **joshedmonds said:**
> Have you installed the guest extensions yet?
Yes.

Edit-

I needed to change some setting in the bios for it to run the CD.

---

### Post by joshedmonds on 2009-08-23
Sorry for the delay.

The GParted liveCD will be fine, although you can use a full Ubuntu CD (even an old version) if you already have one.

To change the boot device, you will need to either make the changes in the BIOS or press a key while booting (look for a message to press del or f8 or f12 or similar before Grub boots).

---

### Post by stinger30au on 2009-08-23
> **W.A.C. said:**
>  Not only that, but it's an extremely nice sound editing program and I would absolutely hate to part with it. While I don't do sound editing a lot, I'm not willing to be inable to use those files. If I can't use them under Ubuntu, I might have to switch back to lousy Windows XP. What should I do?


dual boot windows and ubuntu. 

use ubuntu for send/receive emails and surf net

use windows for the rest

---

### Post by Dullstar on 2009-08-25
Are there any easier to use Linux Virtual Machines?

---

### Post by tubasoldier on 2009-08-25
> **W.A.C. said:**
> VirtualBox is installed.

I really don't think a virtual machine will work for you. Audio always lags in virtual machines. For audio editing so intense that you would need cool edit then this would be a no go.

Just a thought. I wouldn't count on it for audio.

---

### Post by stinger30au on 2009-08-25
> **W.A.C. said:**
>  If I can't use them under Ubuntu, I might have to switch back to lousy Windows XP. What should I do?



easy

dual boot your pc with xp and ubuntu

use ubuntu for send/recieve emails and surf the net

you xp for everything else

this way your quite well immune to email virii and web trojans etc

and still can use the programs u want

install windows to hdd first and set it up, then install ubuntu to same hdd and bobs your uncle

---

### Post by mdsmedia on 2009-08-26
> **stinger30au said:**
> easy

dual boot your pc with xp and ubuntu

use ubuntu for send/recieve emails and surf the net

you xp for everything else

this way your quite well immune to email virii and web trojans etc

and still can use the programs u want

install windows to hdd first and set it up, then install ubuntu to same hdd and bobs your uncle
While I hate to admit it, I agree.

I use Ubuntu for everything that I don't HAVE to use Windows for. I have some software which is Windows only and I haven't yet been inclined to try it in Wine. If you have Windows anyway, you might as well use it, until you find Linux alternatives that work for you. Continue to look for Linux alternatives. 

Think outside the box, like one Linux app might not do it, but 2 might do the trick when combined.

For me, if a Linux alternative to a Windows app doesn't quite do exactly what you expect of the Windows app, ask yourself if you really need that feature or if you're simply expecting a drop in replacement.

For example, I used Lotus 123 for about 80% of my work, for about 4 years. Excel replaced Lotus 123 as the "standard" and I got used to using Excel. Excel is a great product, has some minor bugs, and I got used to Excel. Now I use OpenOffice on my home PC and Excel at work. Excel is still far superior to OpenOffice Calc. That won't make me buy Office or Excel (if it can be purchased separately). I use OpenOffice and learn to live with its quirks. It does the job.

There are other examples, but that is an easily explained one. Linux has its better apps, too. I find the positives of Linux far outweigh the negatives of Windows, so I use Linux as much as I can. When I can't, and I absolutely have to, I use Windows.

I buy a PC with Windows pre-installed and I load Linux next to it. To me, I haven't paid for Windows. The OEMs have. Those who are "paying" for Windows are those who lock themselves in to Windows only software or hardware.

---

### Post by stinger30au on 2009-08-26
> **mdsmedia said:**
> 

For me, if a Linux alternative to a Windows app doesn't quite do exactly what you expect of the Windows app, ask yourself if you really need that feature or if you're simply expecting a drop in replacement..



i could not have said it any better myself! :P

---

### Post by cascade9 on 2009-08-26
> **W.A.C. said:**
> The problem? I can't get Foobar2000 to run decently and from the research I've done, it sounds like it isn't possible to get Cool Edit Pro 2.1 (or it's later editions as Adobe Audition) to work properly. I can tolerate the loss of my favorite music playing program, but I have done quite a bit of sound editing in the past and those files are designed to be run with Cool Edit Pro. Not only that, but it's an extremely nice sound editing program and I would absolutely hate to part with it. While I don't do sound editing a lot, I'm not willing to be inable to use those files. If I can't use them under Ubuntu, I might have to switch back to lousy Windows XP. What should I do?

 Seems that if you have the right version of cooledit and wine, it should work. I cant really speak for cooledit, but it is listed at winehq.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=19](http://appdb.winehq.org/objectManager.php?sClass=application&iId=19)

As for foobar, its working fine here. Even my ather modded version (SCP, album art, album list, etc) orks fine (the channel spectrum display is a bit slower though). Have you checked this?-

[http://www.hydrogenaudio.org/forums/index.php?showtopic=54933](http://www.hydrogenaudio.org/forums/index.php?showtopic=54933)

That helped be a lot with my foobar under wine setup. :) I will admit I'm not using it for transcoding (SoundKonverter does that for me) or ripping (not that I ever used foorbar for ripping). The only issue I'm really having with foobar under wine is my .dts files dont work, but realy, who uses .dts files? Not many of us. 

> **Radioman991 said:**
> W A C

I would absolutely LOVE Audacity IF it could write the metadata (header) info for WAV files. That is what makes Audition such a staple in radio stations. Makes it a breeze to interface to automation systems.

If Audacity could do that, I would have VERY FEW Windows machines in stations now...especially in studios where jox could load them up with crap.

My 0.02

AFAIK, you cant get a normal metadata on a  .wav file. You can with bwav (broadcast wav).

---

### Post by Dullstar on 2009-08-26
And let's not forget some formats (including mp3, if I'm not mistaken, correct me if I'm wrong about this parts) have Ubuntu codecs that are illegal in some countries.  I'm not taking the risk.  I don't really have a use for those codecs right now anyways.  So why bother installing useless codecs?  ESPECIALLY ones that *might* be illegal.

---

### Post by W.A.C. on 2009-08-28
Wow. I'm surprised this thread is still active. o_O

> **tubasoldier said:**
> I really don't think a virtual machine will work for you. Audio always lags in virtual machines. For audio editing so intense that you would need cool edit then this would be a no go.

Just a thought. I wouldn't count on it for audio.
When I tried using VirtualBox in the past, I had audio lag problems. Is there some way to prevent this? I have Ubuntu dual booted with Windows 7 and I heard there's a way where you can access a Windows partition through VirtualBox on Ubuntu. It would be really awesome if I could do that and have audio work fine.

> **cascade9 said:**
> Seems that if you have the right version of cooledit and wine, it should work. I cant really speak for cooledit, but it is listed at winehq.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=19](http://appdb.winehq.org/objectManager.php?sClass=application&iId=19)

The version that works is way too outdated.

> **cascade9 said:**
>  As for foobar, its working fine here. Even my ather modded version (SCP, album art, album list, etc) orks fine (the channel spectrum display is a bit slower though). Have you checked this?-

[http://www.hydrogenaudio.org/forums/index.php?showtopic=54933](http://www.hydrogenaudio.org/forums/index.php?showtopic=54933)

That helped be a lot with my foobar under wine setup. :) I will admit I'm not using it for transcoding (SoundKonverter does that for me) or ripping (not that I ever used foorbar for ripping). The only issue I'm really having with foobar under wine is my .dts files dont work, but realy, who uses .dts files? Not many of us.
I tried many times attempts to get foobar to work under Wine and I kinda gave up on doing that. :/

---

### Post by SeePU on 2009-08-29
Why does Instant Messengers in Linux SUCK SO MUCH?!?

---

### Post by CleverTrick on 2009-08-29
I need to use two different programs that have zero chance of running on Linux, so I just installed them in Vista and went on my way. :) My webcam works under Linux, but booting into Vista is much less hassle than setting it up (from what I've read), so Windows takes cares of that as well. 
Ubuntu is working nicely for my other tasks so far.

---

### Post by cascade9 on 2009-08-30
> **W.A.C. said:**
> I tried many times attempts to get foobar to work under Wine and I kinda gave up on doing that. :/

What was going wrong? I havent had any problems with base foobar on linux, its only when I've tried to get some of the plugins going its played badly. 

One of these days I'll find a linux based media player that does what I can do with foobar. Well, I would even settle for having an interface that looks the way I want it to. Maybe I should just mod exaile LOL

---

### Post by W.A.C. on 2009-08-30
> **cascade9 said:**
> What was going wrong? I havent had any problems with base foobar on linux, its only when I've tried to get some of the plugins going its played badly.
Well, the album art was in limited colors, I experience lag, I couldn't move the buttons, etc.

> **cascade9 said:**
>  One of these days I'll find a linux based media player that does what I can do with foobar. Well, I would even settle for having an interface that looks the way I want it to. Maybe I should just mod exaile LOL
Exaile is horrible. It doesn't even allow gapless play.

---

### Post by cascade9 on 2009-08-30
The album art problem is GDI+ (or it should be). Never had any lagging, that might have been the WINE version/foobar version. 

Exaile 'horrible'? Not IMO, it works. Gappless play is something I care not about at all really. Whats a 1-2 second gap? Not a problem. Only reason I was even thinking Exaile is because it seems to be the easiest media player to mod with linux. (I really want _decent_ sized album art, not a tiny 50x50 thumbnail, and from local sources, why waste bandwidth and quota d/ling art that I almost always have in 500x500 or better?) I havent checked that, so if you know something else easier, suggest it :D 

*Unless you suggest amarok (no no no! I dont want a media player to install OO + konq..its  media player not a flippin DE LOL)

---

### Post by W.A.C. on 2009-08-30
> **cascade9 said:**
> The album art problem is GDI+ (or it should be). Never had any lagging, that might have been the WINE version/foobar version.
Hmm... I might look into that sometime.

> **cascade9 said:**
> Exaile 'horrible'? Not IMO, it works. Gappless play is something I care not about at all really. Whats a 1-2 second gap? Not a problem. Only reason I was even thinking Exaile is because it seems to be the easiest media player to mod with linux. (I really want _decent_ sized album art, not a tiny 50x50 thumbnail, and from local sources, why waste bandwidth and quota d/ling art that I almost always have in 500x500 or better?) I havent checked that, so if you know something else easier, suggest it :D
To me, any music player that can't have gapless playback is worthless. I would rather switch back to CDs than have to deal with gapless playback.

> **cascade9 said:**
>  *Unless you suggest amarok (no no no! I dont want a media player to install OO + konq..its  media player not a flippin DE LOL)
Amarok's interface is horrible.

---

### Post by cascade9 on 2009-08-31
Just out of interest, exaile now has "Experimental support for gapless". 

[http://exaile.org/](http://exaile.org/)

---

### Post by zipperback on 2009-08-31
Check the [http://www.winehq.org/](http://www.winehq.org/) to see if the Windows applications will run with Wine on Linux. If it works with Wine, GREAT, if not, then find something else to use.

If you don't want to put a little effort into finding an alternative to use under Linux, you can either dual boot your system, run a virtual machine system (virtual box, vmware, etc...), or simple keep using Windows.

It isn't the fault of Linux your Windows software doesn't run. You could contact the developer and complain and tell them you want a version to work with Linux. The more people contact developers about getting their software on the Linux desktop, the more chance you will have of actually seeing it released for it.

There are numerous alternatives available on Linux for just about every possible Windows application. Many of them are far better in my opinion as well.

Linux however isn't Windows, so we can't really expect Windows software to run on it.

- zipperback
:popcorn:

---

### Post by SunnyRabbiera on 2009-08-31
> **SeePU said:**
> Why does Instant Messengers in Linux SUCK SO MUCH?!?

Its more from the IM providers really, I hate AIM, YIM and MSN anyhow

---

### Post by W.A.C. on 2009-08-31
> **zipperback said:**
> If you don't want to put a little effort into finding an alternative to use under Linux, you can either dual boot your system, run a virtual machine system (virtual box, vmware, etc...), or simple keep using Windows.

For a music player, I couldn't find an alternative that was anywhere near as good as foobar2000. I tried over ten different music playing programs one night so it's not like I didn't try. As for an alternative to Cool Edit Pro, I honestly don't want to switch to a program that's not as good.

> **zipperback said:**
> It isn't the fault of Linux your Windows software doesn't run. You could contact the developer and complain and tell them you want a version to work with Linux. The more people contact developers about getting their software on the Linux desktop, the more chance you will have of actually seeing it released for it.

It's 100% true that it isn't Linux's fault those programs don't work. Unfortunately, Microsoft holds a huge monopoly and I'm sick of having to constantly switch between OS's when I want to do certain tasks. Because of this, I may make Windows 7 my main OS. :/ What can I say? I like using my programs.

> **zipperback said:**
> There are numerous alternatives available on Linux for just about every possible Windows application. Many of them are far better in my opinion as well.

I do like some open source programs better than some of the more professional ones I used to use on XP.

> **zipperback said:**
>  Linux however isn't Windows, so we can't really expect Windows software to run on it.

True.

---

### Post by SeePU on 2009-09-01
> **SunnyRabbiera said:**
> Its more from the IM providers really, I hate AIM, YIM and MSN anyhow
I got it to work in Kubuntu.  I sometimes use the Yahoo protocol to communicate with relatives and a couple of friends who use it.  It's not really my cup of tea but it's an easy way to keep in touch.  

It was really odd the way it finally worked.   I think it had to do with 'taking' the password after being logged in.  It wasn't acquiring it properly or something?   Something about the 'wallet' came up and after fooling with that for a bit, it finally worked and I could send messages, both online and offline.

---

