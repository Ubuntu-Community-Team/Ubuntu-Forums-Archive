---
title: "3 Weeks of Ubuntu, the Good &amp; Bad"
date: 2008-08-12
forum: Testimonials &amp; Experiences
---

### Post by airjrdn on 2008-08-12
I've been using Ubuntu for about 3.5 weeks now, only booting into Windows for gaming a few times.  I wasn't really out to switch from Windows to Linux, I just wanted to play with it and see what happened.  So far, so good.  Some experiences have been good, some have been bad.  I've listed below the ones I can remember for sure.

For the record, I'm a Windows software developer, and have been (professionally) for over 10yrs.  Honestly, I think that makes switching a little more difficult in some ways than for an average user.  While I have deeply routed opinions on how some things should work, a basic user probably doesn't.  It's very important to me for instance, to group photos from my digital camera by the date the pictures were taken.  Given that I have over 15,000 photos in ACDSee, I'm not going to switch photo applications anytime soon, and getting them into a photo application just to figure out the date a picture was taken is simply not going to happen.

Where I do think a basic user is going to have issues though, is when applications specific to a piece of hardware they own don't work.  I was able to get iTunes working in both VirtualBox & VMWare for instance, but attempting to do an iPhone update hosed the phone.  The only way to get it working was by doing a "restore" in iTunes from a Windows machine.

In any case, these are some of the experiences I had.  Feel free to comment/ask questions.

The Good:

[LIST]
[*]Price - Ubuntu, and Linux is general, is free
[*]Stability - Ubuntu 8.04 has been solid.  I've had to kill Nautilus once, but that's it
[*]Safety - I can't imagine how hard it would be to code malware for Linux since no two machines have the same versions of software installed - (some sarcasm, some truth)
[*]Installing Software - If it's in the repository, it's great
[*]Cross Platform Apps - Since I already used Firefox, Thunderbird, VMware, VLC, Filezilla, GIMP, and Open Office, much of the switch was painless
[*]WINE - PSPad, my editor of choice since it has a built in FTP client, runs fine under WINE
[*]Compiz - It's just eyecandy, but it's still pretty cool
[*]Firefox & Thunderbird - Most extenions/addons work in both platforms
[/LIST]


The Bad:

[LIST]
[*]Drivers - Had to recompile the kernel, adding ALSA to get sound card to work
[*]Drivers - Doing Ubuntu updates often breaks sound, requiring killing X-Windows & working from terminal to do "make uninstall" & get working again
[*]Drivers - There don't seem to be any for my Olympus P400
[*]Drivers - When they get hosed, you don't immediately know it.  Sound for instance will work until I logout or reboot, then not work upon logging back in
[*]File Manager - Nautilus can't seem to show "Date Picture Taken" which is how many users group photos
[*]Installing Software - For non-repository software, you really have to pay attention to precisely what version of Ubuntu the HowTo steps are for
[*]Installing Software - For non-repository software, you often have to know exactly what version of X or Y you have installed before proceeding
[*]Burn Network Files - None of the CD/DVD Burning apps seem to be able to burn files from SMB Shares
[*]Seeing SAMBA Shares - Share's aren't seen in Nautilus.  If you know the share name, and type it in, it works
[*]Keyring Access - Some apps seem to have access to the password keyring, while others (VLC) don't.  I think that's why it can't play files from an SMB share
[*]Compiz - When docking windows at the edge of the screen, they often "bounce" above the top of the desktop, or to the desktop to the left
[*]Compiz - Clicking the titlebar on a window sometimes causing the window to move unexpectedly instead of just bring the window to the forefront
[*]Cross Platform Apps - In Firefox for example, you use Tools->Options, and in Linux you use Edit-Preferences
[*]Cross Platform Apps - In Firefox the address is highlighted if you simply click there in Windows, but isn't in Ubuntu
[*]Cross Platform Apps - In Filezilla in Windows, there's a dropdown arrow next to the site manager icon, and in Ubuntu, there isn't
[*]Clipboard - Sometimes it seems like the clipboard is cleared after pasting.  I haven't quite figured out the exact pattern that causes it though
[*]Text File work - Using only the Text Editor in Ubuntu, somehow single quotes got replaced with some funky character, and I had to use PSPad to fix the file
[*]Flash - Sometimes it works, sometimes it doesn't.  I'm running the non-free version
[*]iTunes - I'm no fan of Apple, but iPods & iPhones are popular, and while I was able to get it working in VirtualBox & VMware, that required a Windows license and more knowledge than most users have
[*]Numeric Keypad - Numeric keypad stopped working after no changes from me, but a couple of updates from Ubuntu
[*]Samba Shares - Couldn't browse SMB Shares even when typing them in.  Again, no changes by me, but after a couple of updates from Ubuntu
[/LIST]


For reference, here's the machine Ubuntu 8.04 64bit is installed on:
Case:     Antec Nine Hundred
PSU:      OCZ GameXStream 700W
MB:       EVGA NVIDIA nForce 680i SLI
CPU:      Intel Core 2 Quad Q6700
HS/Fan:   Arctic Cooling Freezer 7 Pro Cooler
Video:    (2x) EVGA GeForce 8800GTX
RAM:      (2x) DDR2 2GB (2x1GB) - 4G Total
HD:       Seagate 500GB Serial ATA/300, Maxtor 250G PATA
DVD:      Black NEC 18x DVD Multi Writer Burner
Sound:    Creative X-Fi Xtreme Gamer
Monitor:  Gateway FHD2400 24" LCD

---

### Post by cszikszoy on 2008-08-12
> **airjrdn said:**
> 
[LIST]
[*]iTunes - I'm no fan of Apple, but iPods & iPhones are popular, and while I was able to get it working in VirtualBox & VMware, that required a Windows license and more knowledge than most users have
[/LIST]


There is not really any iPhone support yet, but I can use rythmbox, amarok, or gtkpod to sync music and videos with my iPod.  It works quite well actually.

---

### Post by airjrdn on 2008-08-13
I think the iPhone will do ok in VirtualBox or VMware for general iTunes syncing, but not for updates.

---

### Post by overdrank on 2008-08-13
Moved :)

---

### Post by airjrdn on 2008-08-13
Sorry, I didn't see the Testimonials & Experiences forum.

---

### Post by ibutho on 2008-08-13
Some of the problems e.g. nautilus, clipboard, editor etc seem to be GNOME specific issues. If you use a different environment, editor etc, those problems probably won't exist.

---

### Post by 3rdalbum on 2008-08-13
> **airjrdn said:**
> 
The Bad:

[LIST]
[*]Drivers - Had to recompile the kernel, adding ALSA to get sound card to work
[*]Drivers - Doing Ubuntu updates often breaks sound, requiring killing X-Windows & working from terminal to do "make uninstall" & get working again

Those two problems are related - if you have a kernel update, you'll lose the new ALSA version. The good news is that the next version of Ubuntu will have the new ALSA in it, and it's quite rare to have your particular problem in the first place.

Creative X-Fi is a problem on Vista too from what I hear.

> [*]Installing Software - For non-repository software, you really have to pay attention to precisely what version of Ubuntu the HowTo steps are for
[*]Installing Software - For non-repository software, you often have to know exactly what version of X or Y you have installed before proceeding

I haven't found this at all, except when using an old version of Ubuntu.

> [*]Compiz - Clicking the titlebar on a window sometimes causing the window to move unexpectedly instead of just bring the window to the forefront

I haven't seen this since about Ubuntu 6.06; if you have any unusual plugins enabled, try disabling them.

> [*]Cross Platform Apps - In Firefox for example, you use Tools->Options, and in Linux you use Edit-Preferences
[*]Cross Platform Apps - In Firefox the address is highlighted if you simply click there in Windows, but isn't in Ubuntu
[*]Cross Platform Apps - In Filezilla in Windows, there's a dropdown arrow next to the site manager icon, and in Ubuntu, there isn't

I wouldn't classify these as "The Bad" - it's just that the programs differ slightly between platforms.

> [*]Clipboard - Sometimes it seems like the clipboard is cleared after pasting.  I haven't quite figured out the exact pattern that causes it though

If you copy from one program and then quit that program, the clipboard will be erased. It's a limitation of the X Window System. There's a very easy fix fortunately - install Glipper. It's a little program that saves both clipboards, and has the upside of keeping track of your clipboard history so you can re-paste something you copied over before.

BOTH clipboards? Yes - if you just select some text and then middle-click somewhere else, it pastes the selected text at the cursor. That's your second clipboard.

> [*]iTunes - I'm no fan of Apple, but iPods & iPhones are popular, and while I was able to get it working in VirtualBox & VMware, that required a Windows license and more knowledge than most users have

Amarok, Banshee, GTKpod and lots of other native Linux programs can work with iPods. You might think that iPhones are popular, but in reality they don't have a lot of marketshare, and their internals are changing too quickly at the moment to be the target for open-source iPhone managers.

Maybe later. But I believe you can load music onto them the same as an iPod. Incidentally, I would consider anyone who's got an iPod or an iPhone to be an "Apple fan" :-)

---

### Post by cszikszoy on 2008-08-13
> **3rdalbum said:**
> Incidentally, I would consider anyone who's got an iPod or an iPhone to be an "Apple fan" :-)

Trust me, I'm anything but an Apple fan.  But when your girlfriend gives you an 80 gig iPod, you don't necessarily say "This is ****...".

And apple or not - it still works very well with amarok (i refuse to capitalize theirs stupid K!).  All cover art is transferred with the music, and playlists are no problem.

The iPhone on the other hand, that thing is more fascist than Mussolini.  Save yourself the trouble and wait for an android phone.

---

### Post by airjrdn on 2008-08-13
Thanks for replying.

For reference, I had previously been running 64bit Vista, and had no X-Fi issues there.

As for the Compiz issue, I haven't installed any extra plugins.  I checked a couple of the boxes available in the GUI (that I did install), but I don't remember which ones I selected and which were already selected.

I'll definitely give Glipper a try, I hadn't heard of it before.

Work bought the phone, I didn't. :)  After finding out that something as simple as ringtones have to be purchased twice (once as a song, and once as a ringtone), that just solidifies the Apple mindset IMO...enough so that I don't know if I'd plunk down the cash for one personally.  Most email/browser tasks are great, but them having the ability to uninstall stuff from "my" phone without my consent is just a little over the top for my taste.

---

### Post by Methuselah on 2008-08-13
> 
Cross Platform Apps - In Firefox for example, you use Tools->Options, and in Linux you use Edit-Preferences


This is due to firefox respecting platform conventions.
That's why it also looks different on Vista, Mac and Linux.
The average gnome program will have user preferences under edit->preferences rather than tools->options so linux firefox follows.
And no, I don't think tools is a more logical menu for changing user preferences.

Many of the others things you mentioned are possibly genuine hassles.
I haven't been affected by most of them though because my hardware is supported by vanilla hardy and I don't use samba nor iTunes etc.

---

### Post by Teamgeist on 2008-08-13
> **airjrdn said:**
> I'll definitely give Glipper a try, I hadn't heard of it before.

I suggest you use Parcellite since glipper seems to be not too well maintained and crashes every once in a while.

You can find a Parcellite .deb-Package on [www.getdeb.net](www.getdeb.net) which you can install by double-klicking on it.

direkt link: [http://www.getdeb.net/search.php?keywords=parcellite](http://www.getdeb.net/search.php?keywords=parcellite)

As for Flash crashing sometimes. This is because you are using a 64bits Operating System and there actually is no 64bit Version of Adobe Flash.
Since this is closed source software Ubuntu cannot do anything about it.

---

### Post by stchman on 2008-08-13
> **airjrdn said:**
> I've been using Ubuntu for about 3.5 weeks now, only booting into Windows for gaming a few times.  I wasn't really out to switch from Windows to Linux, I just wanted to play with it and see what happened.  So far, so good.  Some experiences have been good, some have been bad.  I've listed below the ones I can remember for sure.

For the record, I'm a Windows software developer, and have been (professionally) for over 10yrs.  Honestly, I think that makes switching a little more difficult in some ways than for an average user.  While I have deeply routed opinions on how some things should work, a basic user probably doesn't.  It's very important to me for instance, to group photos from my digital camera by the date the pictures were taken.  Given that I have over 15,000 photos in ACDSee, I'm not going to switch photo applications anytime soon, and getting them into a photo application just to figure out the date a picture was taken is simply not going to happen.

Where I do think a basic user is going to have issues though, is when applications specific to a piece of hardware they own don't work.  I was able to get iTunes working in both VirtualBox & VMWare for instance, but attempting to do an iPhone update hosed the phone.  The only way to get it working was by doing a "restore" in iTunes from a Windows machine.

In any case, these are some of the experiences I had.  Feel free to comment/ask questions.

The Good:

[LIST]
[*]Price - Ubuntu, and Linux is general, is free
[*]Stability - Ubuntu 8.04 has been solid.  I've had to kill Nautilus once, but that's it
[*]Safety - I can't imagine how hard it would be to code malware for Linux since no two machines have the same versions of software installed - (some sarcasm, some truth)
[*]Installing Software - If it's in the repository, it's great
[*]Cross Platform Apps - Since I already used Firefox, Thunderbird, VMware, VLC, Filezilla, GIMP, and Open Office, much of the switch was painless
[*]WINE - PSPad, my editor of choice since it has a built in FTP client, runs fine under WINE
[*]Compiz - It's just eyecandy, but it's still pretty cool
[*]Firefox & Thunderbird - Most extenions/addons work in both platforms
[/LIST]


The Bad:

[LIST]
[*]Drivers - Had to recompile the kernel, adding ALSA to get sound card to work
[*]Drivers - Doing Ubuntu updates often breaks sound, requiring killing X-Windows & working from terminal to do "make uninstall" & get working again
[*]Drivers - There don't seem to be any for my Olympus P400
[*]Drivers - When they get hosed, you don't immediately know it.  Sound for instance will work until I logout or reboot, then not work upon logging back in
[*]File Manager - Nautilus can't seem to show "Date Picture Taken" which is how many users group photos
[*]Installing Software - For non-repository software, you really have to pay attention to precisely what version of Ubuntu the HowTo steps are for
[*]Installing Software - For non-repository software, you often have to know exactly what version of X or Y you have installed before proceeding
[*]Burn Network Files - None of the CD/DVD Burning apps seem to be able to burn files from SMB Shares
[*]Seeing SAMBA Shares - Share's aren't seen in Nautilus.  If you know the share name, and type it in, it works
[*]Keyring Access - Some apps seem to have access to the password keyring, while others (VLC) don't.  I think that's why it can't play files from an SMB share
[*]Compiz - When docking windows at the edge of the screen, they often "bounce" above the top of the desktop, or to the desktop to the left
[*]Compiz - Clicking the titlebar on a window sometimes causing the window to move unexpectedly instead of just bring the window to the forefront
[*]Cross Platform Apps - In Firefox for example, you use Tools->Options, and in Linux you use Edit-Preferences
[*]Cross Platform Apps - In Firefox the address is highlighted if you simply click there in Windows, but isn't in Ubuntu
[*]Cross Platform Apps - In Filezilla in Windows, there's a dropdown arrow next to the site manager icon, and in Ubuntu, there isn't
[*]Clipboard - Sometimes it seems like the clipboard is cleared after pasting.  I haven't quite figured out the exact pattern that causes it though
[*]Text File work - Using only the Text Editor in Ubuntu, somehow single quotes got replaced with some funky character, and I had to use PSPad to fix the file
[*]Flash - Sometimes it works, sometimes it doesn't.  I'm running the non-free version
[*]iTunes - I'm no fan of Apple, but iPods & iPhones are popular, and while I was able to get it working in VirtualBox & VMware, that required a Windows license and more knowledge than most users have
[*]Numeric Keypad - Numeric keypad stopped working after no changes from me, but a couple of updates from Ubuntu
[*]Samba Shares - Couldn't browse SMB Shares even when typing them in.  Again, no changes by me, but after a couple of updates from Ubuntu
[/LIST]


For reference, here's the machine Ubuntu 8.04 64bit is installed on:
Case:     Antec Nine Hundred
PSU:      OCZ GameXStream 700W
MB:       EVGA NVIDIA nForce 680i SLI
CPU:      Intel Core 2 Quad Q6700
HS/Fan:   Arctic Cooling Freezer 7 Pro Cooler
Video:    (2x) EVGA GeForce 8800GTX
RAM:      (2x) DDR2 2GB (2x1GB) - 4G Total
HD:       Seagate 500GB Serial ATA/300, Maxtor 250G PATA
DVD:      Black NEC 18x DVD Multi Writer Burner
Sound:    Creative X-Fi Xtreme Gamer
Monitor:  Gateway FHD2400 24" LCD

As far as the sound card I blame Creative.  The X-Fi was released over 3 years ago and Creative still does not have a good driver for it.  My Audigy 2 works great OOB.

As far as iPod management, the program called Rhythmbox works well for iPods.

I use Flash 9 and it works about 95% of the time.  When it stops working I somply restart Firefox.

Remember SMB is a proprietary Windows file sharing protocol and Samba is a reverse engineered way to get Windows and *ix to share files.  I find that if I share a file on a *ix box Windows boxes see it very easily.  The other way around is not always the case.  I run Ubuntu in my home on all my PCs so I use NFS.

I have had no problems using Gedit for text file editing.  I find it far better than Notepad.

I find that the repository has pretty much everything I need.  If also find that if there is a Windows app I like, there is a Linux counterpart.

---

### Post by griz on 2008-08-14
I've been using Linux and Ubuntu specifically for a few years now.  Started with Red Hat, tried a few others, then settled on Ubuntu.  Currently have it on a desktop unit that works as a basic file and print server.  It has a 500G external HDD attached to it for backups and downloaded material.  I've got XUbuntu loaded on my Toshiba Satellite A200 laptop and love it.  It replaced Vista which just didn't work even though it came preinstalled.  

Ok, that's my background, I consider myself to be a slightly above average user, but no expert.  From my experience and from reading the posts in this and other forums, I see the biggest problem with Linux is the lack of support from hardware manufacturers and software developers.  The OP made mention of the problem that could be faced in writing malicious software due to different versions of software on different computers.  Not far off the mark.  I've noticed that Ubuntu appears to be working on more hardware OOTB, but can't talk about other distros.  My concern had always been that a user might have to try 3 or 4 different distros just to find one that would work with all their hardware.  Have to say though, Ubuntu now works with everything that I've thrown it at in the last 2 years.  Of course, I can't talk about the 64 bit versions either.  Anyway, from my experience, I'm having less problems on this laptop using Ubuntu than I did with Vista.  The Desktop used as a file server, can't compare, removed Vista straight away.  But, no probs so far.

Griz.

---

### Post by lordhaworth on 2008-08-14
In my experience, and i think this is fair, most of the problems you will ever have with ubuntu will be experienced within the first few weeks! It certainly takes some playing around with to get working the way you want it to properly. 

However once it is up and running it is great!

---

### Post by airjrdn on 2008-08-14
It makes sense that the applications are adopting the menu structures & differences of the host OS.  Just purely from a user's perspective, it's a minor difference that you notice.

Teamgeist - I ran the 64bit version of Vista Ultimate for a few months and never saw any of the Flash issues.  I did have some printer issues, actually worse than Ubuntu, but Flash seemed fine.

stchman - I've found that restarting Firefox makes it work too, it's just a hassle since I often have 15 or so tabs open and have to wait for them to reload just to watch a quick video clip.

It wasn't apps I was having to use other repositories for, it was drivers.  There are alternative apps for most things I use; IM for instance, but others are more difficult to switch to if you have a lot of data already.  In ACDSee, with 15K+ photos categorized, it may be tough to switch.  It will output the categorized info into XML, but I have to find/write a script to import that elsewhere, and even then, it may not go in fully.  Plus, it has options many others don't have, like and/or tag searches, the ability to write category info to different EXIF locations so uploaded photos to Fotki for instance, retain their tags.

griz - I've got a Windows fileserver with a little over 5TB in it that's been running fine for a few years or more now, but I also have two Linux fileservers; one running FreeNAS that's been there for nearly as long, and one running LVM on CentOS with just under 1TB.  It's been going for probably 6 months now.  I haven't had any issues with any of them really, but just for me personally, I don't put anything on the Linux ones where that's my only copy of the data.  I just don't have that comfort level with non-NTFS filesystems yet.  I'm sure that's unfounded, but I just have so much more experience with NTFS that I'm more comfortable with it.

---

### Post by Methuselah on 2008-08-14
> **lordhaworth said:**
> In my experience, and i think this is fair, most of the problems you will ever have with ubuntu will be experienced within the first few weeks! It certainly takes some playing around with to get working the way you want it to properly. 

However once it is up and running it is great!

I find this to be 100% accurate!

---

### Post by Methuselah on 2008-08-14
> 
stchman - I've found that restarting Firefox makes it work too, it's just a hassle since I often have 15 or so tabs open and have to wait for them to reload just to watch a quick video clip.


lol..I probably have close to 30!
It's very annoying to be forced to restart firefox.
There are places to bug adobe for flash fixes.
[http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform](http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform)

> 
griz - I've got a Windows fileserver with a little over 5TB in it that's been running fine for a few years or more now, but I also have two Linux fileservers; one running FreeNAS that's been there for nearly as long, and one running LVM on CentOS with just under 1TB. 


Just to be a little picky but FreeNAS is FreeBSD.

---

### Post by airjrdn on 2008-08-14
> **Methuselah said:**
> Just to be a little picky but FreeNAS is FreeBSD.

Not picky at all, I didn't know that.  I may have at one time, but it's been in place so long I've forgotten about it a few times. :)

---

### Post by griz on 2008-08-15
airjrdn:  My external HDD is NTFS format, only because that's how it came and I didn't want to change the format just in case I decide to plug it into another computer.  It has all my backups etc on it.  Just thought I'd point that out.

Griz

---

### Post by hashimoto on 2008-08-15
> **airjrdn said:**
> 
The Bad:

[LIST]
[*]Drivers - There don't seem to be any for my Olympus P400
[/LIST]


According to Open Printing database, Olympus P400 should work mostly. See:
[http://www.openprinting.org/show_printer.cgi?recnum=Olympus-P-400](http://www.openprinting.org/show_printer.cgi?recnum=Olympus-P-400)
It may need some digging and effort to get it up and running though. My fathers HPLJ1005 was/is a pain, too.

---

### Post by airjrdn on 2008-08-15
Thanks for the P400 link, I'll give it a shot.

On another note, I've subscribed to the big Ubuntu backup/restore thread, but I've not tested anything there yet.  I'm used to:

Image my machine
Try out something new/stupid
Restore image if necessary

And that thread indicates you can do restores from within Ubuntu, or from a liveCD, but I just haven't thought all the way through it.  I'd wonder if using a liveCD I'd have to go through some extra steps to make things writable on the HD, or if paths would change, I'd have to mount things from a command line, etc.  I've used some Linux imaging tools before, but they weren't as polished as the Windows ones.

Backups/restores are just something I've yet to mess with & test out I guess.

---

### Post by Irihapeti on 2008-08-16
In the last couple of weeks I've twice needed to restore my entire installation; one occasion was planned and the other was after I'd done something stupid.

In both cases I removed the entire existing installation (except for some data files on another partition) and then unarchived the backup to the drive. If the archiving is done with sudo in the first place, file permissions are preserved. You should be able to boot up normally.

The backups were done from within Ubuntu - no live CD was used. The restores were done from live CD but not Ubuntu ones. There are a number of rescue and lightweight OSs that are handy for this sort of thing, and I have several of them on hand. They even have GUIs.

One thing to watch is this: if you use an archiving program that's slightly unusual, as I did, do make sure you have a copy of the program *outside* of your backup archive. I forgot the first time. :oops: 

Fortunately, I was able to get online and download a copy that would run in my rescue OS. Now my backup script includes copying it to the DVD along with the archive.

Irihapeti

---

### Post by juhani on 2008-08-26
> **airjrdn said:**
> 
[*]Cross Platform Apps - In Firefox the address is highlighted if you simply click there in Windows, but isn't in Ubuntu


This can be changed through about:config, just set browser.urlbar.clickSelectsAll to true. I guess it has something to do with Firefox respecting traditions again.

---

### Post by airjrdn on 2008-08-26
That's good to know, thank you.

---

