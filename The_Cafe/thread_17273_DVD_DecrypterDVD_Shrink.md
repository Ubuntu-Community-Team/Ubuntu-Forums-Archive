---
title: "DVD Decrypter/DVD Shrink?"
date: 2005-02-27
forum: The Cafe
---

### Post by Jonathan_ on 2005-02-27
DVD Decrypter and DVD Shrink are two programs stopping me from completely letting go of Windows. Also some form of video creating software similar to 'windows movie maker' would be great.

Are there programs similar to these in Linux?

---

### Post by TravisNewman on 2005-02-27
If I'm not mistaken, they both run well under Wine in Linux. I've never messed with them though, because I just got my first DVD burner yesterday.

And my second, technically, since I only had my first one for about 30 minutes before taking the piece of junk back. I should have known better than to buy a 16x Dual Layer DVD+-RW for 60 bucks. I also should have known better than to buy anything from a company called Micro Advantage.

Anyway, I've been wanting to see if they DO work well, so I think I'll give them a shot and report back ;)

---

### Post by mark on 2005-02-27
[QUOTE=panickedthumb]If I'm not mistaken, they both run well under Wine in Linux. I've never messed with them though, because I just got my first DVD burner yesterday.

And my second, technically, since I only had my first one for about 30 minutes before taking the piece of junk back. I should have known better than to buy a 16x Dual Layer DVD+-RW for 60 bucks. I also should have known better than to buy anything from a company called Micro Advantage.

Anyway, I've been wanting to see if they DO work well, so I think I'll give them a shot and report back ;)[/QUOTE] Did you go with a "name-brand" dual-layer drive?  My Lite-On SOHW 812S has served me well - but I want the 8+GB of dual-layer!

---

### Post by TravisNewman on 2005-02-27
I went with a Mad dog dual-layer, and it works amazingly.

I've used some Lite-On drives and they all work very well-- It's a name I'd trust.

---

### Post by eldados on 2005-02-28
[QUOTE=Jonathan Steel]DVD Decrypter and DVD Shrink are two programs stopping me from completely letting go of Windows. Also some form of video creating software similar to 'windows movie maker' would be great.

Are there programs similar to these in Linux?[/QUOTE]
 DVDRIP will do what decrypter does, once you have your iso just burn with K3b.
I'm runing decrypter under CrossOver Office with no problems what so ever! if this is the only programs stopping you from moving to Linux allt ogether, concider yourself a lucky man! :)
Give it a go, good luck

---

### Post by poofyhairguy on 2005-02-28
[QUOTE=Jonathan Steel]DVD Decrypter and DVD Shrink are two programs stopping me from completely letting go of Windows. Also some form of video creating software similar to 'windows movie maker' would be great.

Are there programs similar to these in Linux?[/QUOTE]

Here is how I do it. First, get a program called DVDrip (in the same repo that the win32codecs is in) and use it to dump the image to your harddrive. Then use DVDShrink under Crossover Office (or regular wine if you don't want to pay for/steal Crossover Office) to shrink the files DVDrip makes.

Its not as easy as in Windows.....but its pretty easy.

---

### Post by Ste on 2005-02-28
[QUOTE=poofyhairguy]Here is how I do it. First, get a program called DVDrip (in the same repo that the win32codecs is in) and use it to dump the image to your harddrive. Then use DVDShrink under Crossover Office (or regular wine if you don't want to pay for/steal Crossover Office) to shrink the files DVDrip makes.

Its not as easy as in Windows.....but its pretty easy.[/QUOTE]
 Pretty much the way I did it, except I used dvdbackup, very easy but when I went to shrink the files DVDShrink couldn't see any of my drives.

I guess it has to do with my fstab but I don't want to go editing it, I can wait for a more native way to shrink files.

---

### Post by TravisNewman on 2005-02-28
You have to set up wine to see your linux filesystem, or if you're using crossover, it's the Z drive

---

### Post by nocturn on 2005-03-02
Wine from Universe is not playing very well with DVDShrink for me.

It crashes multiple times, but once the resizing is running, it stays on, it crashes directly after again, but I have the files by then.

Does anyone else see this?

---

### Post by yoha on 2005-03-04
[QUOTE=Ste]Pretty much the way I did it, except I used dvdbackup, very easy but when I went to shrink the files DVDShrink couldn't see any of my drives.

I guess it has to do with my fstab but I don't want to go editing it, I can wait for a more native way to shrink files.[/QUOTE]
 ste, if you found that dvd shrink does not detect your drive, don't despair! do the following: In a shell, make a new dosdevice (something like "ln -s /mnt/cdrom2 /home/usr/.wine/dosdevices/e:" without quotes. Then still in shell do a wine /path/to/DVD\ Shrink\ 3.2.exe e: (or whatever path drive letter you chose). It should start analyzing your dvd now with no aspi error!!!

---

### Post by Jonathan_ on 2005-03-04
With DVD Decrypter it says 'Source - No devices Detected'.  Someone said previously about setting up wine to see your linux file system, How do you do that?

---

### Post by yoha on 2005-03-04
[QUOTE=Jonathan Steel]With DVD Decrypter it says 'Source - No devices Detected'.  Someone said previously about setting up wine to see your linux file system, How do you do that?[/QUOTE]
 i cant set dvd decrypter to work w/ wine either. I can try copying system & system32 folders from windoze but too lazy to try. what is your purpose of using dvd decrypter?

---

### Post by jdodson on 2005-03-04
[QUOTE=yoha]what is your purpose of using dvd decrypter?[/QUOTE]

to copy movies you get from blockbuster..... wait, no police are breaking down my door!!!! ARGH!  

er i mean to backup you entire DVD collection!  right, it is for backups......

</sarcasm>

though seriously i do backup my music discs.  havent gotten around to backing up a dvd yet.  i make them all the time from my sony DV camera though.  go kino!  then again i don't steal music or movies or software.  damn, i am boring.

---

### Post by bored2k on 2005-03-04
[Linux Video Tools](http://www.videohelp.com/tools?s=23)

this is dvd:rip
[IMG]http://www.videohelp.com/toolsimages/dvd__rip_495.jpg[/IMG] 

this is kino
[IMG]http://www.videohelp.com/toolsimages/kino_529.jpg[/IMG]

---

### Post by Jonathan_ on 2005-03-04
Thanks i'll try them out

Edit: Actually i just noticed there is no DVD shrinking program there for linux, which I kinda need. So it would be better if i could get DVD shrink working with wine.

---

### Post by bored2k on 2005-03-04
[QUOTE=Jonathan Steel]Thanks i'll try them out

Edit: Actually i just noticed there is no DVD shrinking program there for linux, which I kinda need. So it would be better if i could get DVD shrink working with wine.[/QUOTE]

aight

just make sure if u are ever doing avi 2 dvd, use linux ... winblow's TMPGenc Plus [its still my fav. video app anywhere]/ Sony DVD ArchitecT/Santa take an awful lot of time

---

### Post by poofyhairguy on 2005-03-04
[QUOTE=Jonathan Steel]Thanks i'll try them out

Edit: Actually i just noticed there is no DVD shrinking program there for linux, which I kinda need. So it would be better if i could get DVD shrink working with wine.[/QUOTE]


First of all, you need one of the aformentioned programs to rip DVDs to your harddisk. Emulated DVDShrink won't do that.

Then you need to install DVDShrink using Crossover Office. There are torrents of it out there. As long as you are only using DVDShrink for the actual shrinking- it works fine.

---

### Post by deviant03 on 2005-03-05
DVD Shrink ran really well for me in Crossover Office.

---

### Post by yoha on 2005-03-05
[QUOTE=jdodson]to copy movies you get from blockbuster..... wait, no police are breaking down my door!!!! ARGH!  

er i mean to backup you entire DVD collection!  right, it is for backups......

</sarcasm>

though seriously i do backup my music discs.  havent gotten around to backing up a dvd yet.  i make them all the time from my sony DV camera though.  go kino!  then again i don't steal music or movies or software.  damn, i am boring.[/QUOTE]

jdodson,
   to fully backup the movies collection you have to blank dvd medias, you could use dvd shrink which on my setup works all the time, although you need to tweak some settings should it does not work the first time. You can either backup the whole movie or "re-author" it. See[http://mrbass.org/dvdshrink/](http://mrbass.org/dvdshrink/)  Set dvd shrink to output *.iso image and btw the decryption as you probably already know is handled by dvd shrink. after that use growisofs w/ the "-dvd-compat" flag to burn it. for example: sudo growisofs -dvd-compat -Z /dev/hdc=/path/to/the/iso/image  #assuming /dev/hdc is your dvd burner

To backup your ps2 games, should you want, you can use the dd command: dd if=/dev/hdc of=/path/to/save/whatevername.iso. #again assuming /dev/hdc is your dvd burner. then use the aforementioned growisofs command to burn it.

---

### Post by linuxNewb on 2005-03-31
Which repo is required for DVDRip? I can 'apt-cache search dvdrip', but it won't install due to "uninstallable" dependencies :mad:  

I am running warty on a Compaq Presario 900 Laptop. Also, in case it's relevant, I can watch DVDs with xine no problem. Thanks.

---

### Post by bored2k on 2005-03-31
[QUOTE=linuxNewb]Which repo is required for DVDRip? I can 'apt-cache search dvdrip', but it won't install due to "uninstallable" dependencies :mad:  

I am running warty on a Compaq Presario 900 Laptop. Also, in case it's relevant, I can watch DVDs with xine no problem. Thanks.[/QUOTE]
 Do you have Chris Marillat, universe, multiverse, backports on ? 
By the way [thoggen](thoggen.net/screenshots/) is also good .

---

### Post by linuxNewb on 2005-03-31
[QUOTE=bored2k]Do you have Chris Marillat, universe, multiverse, backports on ? 
By the way [thoggen](thoggen.net/screenshots/) is also good .[/QUOTE]
 Here is a list of all my repos:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

---

### Post by bored2k on 2005-03-31
what about 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main ??

---

### Post by jdodson on 2005-03-31
[QUOTE=linuxNewb]Which repo is required for DVDRip? I can 'apt-cache search dvdrip', but it won't install due to "uninstallable" dependencies :mad:  

I am running warty on a Compaq Presario 900 Laptop. Also, in case it's relevant, I can watch DVDs with xine no problem. Thanks.[/QUOTE]

enable mailrat from [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by linuxNewb on 2005-03-31
I've added/updated  

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

but it still won't install due to uninstallable transcode dependencies.

UPDATE: If you want to easily rip/backup dvds on your warty install, read my post at [http://ubuntuforums.org/showpost.php?p=118866&postcount=18](http://ubuntuforums.org/showpost.php?p=118866&postcount=18)

---

### Post by henrik79 on 2007-09-22
-

---

### Post by kinematic on 2007-09-22
Why the hell has nobody mentioned k9copy, it does the same job as dvdshrink for windows (even better imo). Takes me half an hour to rip a movie to a dvd5 and the quality is perfect.

---

### Post by 3rdalbum on 2007-09-22
> **kinematic said:**
> Why the hell has nobody mentioned k9copy, it does the same job as dvdshrink for windows (even better imo). Takes me half an hour to rip a movie to a dvd5 and the quality is perfect.

I expect that's because most of the posts were in 2005... someone has bumped the thread.

---

### Post by kinematic on 2007-09-22
> **3rdalbum said:**
> I expect that's because most of the posts were in 2005... someone has bumped the thread.

Lol, missed that. Beer does that to the mind :lolflag:

---

### Post by nonewmsgs on 2007-09-22
well i dont know if this is moot since the post is old, but dvd decrypter works VERY well under wine but the win version must be set to NT4.0.  

dvdshrink works sort of well.  sometimes the window dissapears (but only in the inital stages and after an operation -- like after reauthoring a cut off point in the end or after the inital analysis) but once it does start ia process, it finishes.   so i always breath a sigh of relief once i hit backup because it will be fine though deep analysis and sharp advanced error correction.

i will try the k9copy.

incidently
[http://ubuntuforums.org/showthread.php?t=553602](http://ubuntuforums.org/showthread.php?t=553602)
:P
4 days an no reply when i asked if comercial dvdripping was something someone would pay for and no one has any opinions but so many people say this is the exact reason they use windows...

---

### Post by bruce89 on 2007-09-22
dvd95 for GTK+ people.

---

### Post by jmax on 2007-09-25
Not having used UBUNTU to any great degree before - I could never get it to run on my old computer - 7.o4 runs without flaw on it - I found dvdsrhink and decrypter to work extremely well under wine, no hassles at all. Install wine, set it to NT4 as the default, install dvd shrink and decrypter [with a dvd in the drive!] and away you go. When I saw it worked well, I got rid of xp pretty quick.

---

### Post by mips on 2007-09-25
I just use k9copy.

---

### Post by Hallvor on 2007-10-04
Sorry to revive this old thread. K9copy tends to crash on my computer, but fortunately I found DVD95, which is very similar to Dvdshrink, and just as easy to use. (And finally, I can get rid of those large KDE libraries.)

---

### Post by jfluet on 2007-11-09
i am new to lynx and i have Ubuntu 7.10. i have DeVeDe and i thought it worked fine till i watched the burnt DVD all was burnt was the menu. i also have dvd::rip and K9copy and i can't seem to solve th problem. what other program do i need or could i fix it with what i got.

---

### Post by svtfmook on 2007-11-09
i have found that k9copy and k3b work better and easier.

---

### Post by Absolom on 2007-11-09
deleted no longer need help

---

### Post by King_Critter on 2007-11-10
There *is* a DVD Shrink in the Ubuntu repositories, you know. :-/

---

### Post by BigSilly on 2007-11-10
> **svtfmook said:**
> i have found that k9copy and k3b work better and easier.

Me too. I tend to find K9Copy does the job of both DVDShrink and DVDDecrypter, and I've never had any bother with it. Quicker and easier.

---

### Post by mastergunner on 2007-11-11
Where is dvd shrink in the repos cause I can find it. Is there a How-To on DVD95?

---

### Post by King_Critter on 2007-11-12
Oh, whoops -- it's not in the repos. :P Sorry, I saw it in synaptic and thought it was, but I must have downloaded the .deb file from a website. :(

---

### Post by themcman on 2008-10-30
Thank you, all.

I just installed Crossover and DVD Shrink and it works great.

---

### Post by jwooton on 2010-11-06
I've always preferred ripping with HandBrake to a single file.  Then when I want a copy on DVD to play in the DVD player I use DeVeDe against that single file to create a physical DVD again.  This lets you keep your video collection in a consistent file format on your pc that doesn't have to be .ISO or a directory of .VOB files.  And most importantly, it's all Native to Ubuntu.

---

### Post by handy on 2010-11-06
> **jwooton said:**
> I've always preferred ripping with HandBrake to a single file.  Then when I want a copy on DVD to play in the DVD player I use DeVeDe against that single file to create a physical DVD again.  This lets you keep your video collection in a consistent file format on your pc that doesn't have to be .ISO or a directory of .VOB files.  And most importantly, it's all Native to Ubuntu.

I still have need on occasion to use DVDShrink, very rarely I must use SmartRipper, to get me around a problem that DVDShrink can't handle, & even more rare than that I must use DVD Fab Decryptor. As it can backup ANY DVD movie no matter what kind of protection. They all run fine in Wine, the first two are free-ware.

Apart from that I agree, with the above quoted post. I have shrunk my entire movie collection from DVD to .mp4 using HandBrakeCLI. I put a couple of oft used HandBrakeCLI command lines in my ~/.bashrc as aliases, so I don't have to work it out again. :) Though the HandBrakeCLI --help option surely gives you a very good run down on just what your options are, it it truly an incredibly powerful tool; fast, & extremely configurable.

---

### Post by cariboo on 2010-11-07
This thread was started 5 years ago, and the last reply was in 2008. Closed.

---

