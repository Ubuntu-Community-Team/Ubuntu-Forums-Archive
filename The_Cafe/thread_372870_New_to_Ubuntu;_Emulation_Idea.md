---
title: "New to Ubuntu; Emulation Idea"
date: 2007-02-28
forum: The Cafe
---

### Post by PatrickG on 2007-02-28
Hello!

I switched to Ubuntu earlier this year after some frustration with Windows and I'm loving it.

I play World of Warcraft with Cedega. I'm actually now running Feisty with a custom kernel and X Org's latest release. (So far, this has proven to be the best configuration for my system using an open source Radeon driver.)

Anyway, I was tinkering around and I noticed that the Windows install can run emulated within Cedega and despite the inefficiency, I was thinking about trying to install and run an entire emulated Windows XP installation within Ubuntu via Cedega.

At the very least, I imagined it might prove to be novel and at most I thought perhaps I would regain some of the improved performance of Windows gaming without maintaining an actual Windows partition. (I've been unable to get fglrx to work using any of the tutorials I've found; my card is a Radeon 9250 which I believe support has been discontinued on.)

I was wondering if anyone here runs an emulated Windows desktop. I realize there's probably some RAM that would be wasted in the process as well as some features that might not function properly but it just seems really novel to me.

I've used Wine, Crossover and Cedega. Thus far, Cedega seems to be the most robust for most of my purposes and I was thinking that perhaps a fully emulated Windows install, while being a RAM hog, would be the most robust option for using some Windows programs without actually maintaining a Windows partition. (I've also created guest logins with desktops that resemble OSX and Windoze for when friends use my computer as many of them seem lost when encountering any unfamiliar UI features.)

I LOVE Ubuntu. I feel that within the next year or two, any lost functionality or increased difficulty involved in running Ubuntu (ie. custom kernel updates, keeping track of software versions and driver versions for optimal hardware compatibility) will be negligible and I'm trying to sell friends and family on the superiority of Ubuntu as opposed to Vista for their future computer purchases. I think that within a year, courtesy of the Xorg enhancements under development as well as other advances, even the most casual of computer users will find Ubuntu to be easier, more system efficient and, obviously, MUCH more cost effective (even with paid MP3 software and such) than any option outside the Linux community.

Wireless cards, iTunes and gaming seem to be the biggest hurdles for people making the change and I believe that the day is almost here when those types of features are as universal and idiot proof in Ubuntu as they are in Windows and OSX. And when that day comes, Ubuntu's superior security and efficiency will turn the tides. (I doubt we'll see a DIRECT iTunes port but emulation that supports the iTunes store or a comparable Ubuntu native app will no doubt happen soon, IMO.)

But for right now, I'd like to be able to have access to Windows gaming and iTunes functionality at a mouseclick... and have the ability to escape its dysfunctionality for the comfort and customizibility of Ubuntu at another mouseclick.

Anybody else at a similar place?

---

### Post by tbroderick on 2007-02-28
check out vmware

---

### Post by bastiegast on 2007-02-28
Since Cedega is based off wine and wine is an open source implementation of a windows environment you cannot install windows XP in it. It would be like trying to install Windows XP while already in Windows XP.

---

### Post by PatrickG on 2007-02-28
Ah.

I wasn't too clear on the software architecture of the post Windows 3.11 systems. The GUI used to be an executable.

What about Bochs? Has anyone tried that?

---

### Post by SishGupta on 2007-02-28
I think the main confusion here is that you think that wine (or cedega, which is just modified wine) is an emulator.
wine: wine is not (an) emulator. 
Wine is a windows api layer for linux. Very basically it translates a windows programs system calls into linux system calls.

vmware is more like what you are looking for, but it won't run 3d games. It should run itunes however.

Currently the best option for 3d gamers is dual booting or wine.
I prefer wine over cedega as it is updated almost twice a month, and it is free so I don't have to steal it.

Bochs seems to be virtualization software (like vmware)

---

### Post by PatrickG on 2007-02-28
I tinkered with Wine but found that it needed more configuration than I was prepared for at the time with 3D games. Cedega offered configuration out of the box and while it doesn't entirely mesh with Linux philosophy in some respects, I suppose, I was happy to put $15 into development and I'll weigh out whether to continue giving $5 a month based on the level of development/support I see going on. If it meets my needs now, I suppose there's no need to continue the subscription.

Obviously since I play Warcraft, I have no problem supporting closed source commercial software so I'm not an absolutist on the issue.

I lost my Windows XP key code and getting a new one has been a headache. I payed $10 and was told to call back in half an hour. Later, I was told to call back in an hour. Then, I was told that the first two bits of advice I was given were unusual and that I should wait at least 24 hours.

I never played Warcraft on Windows but I know that City of Heroes utilized my graphics card far better in terms of effects than what I've seen with open source driver in Ubuntu (however, the RAM clogging MS TSRs did reduce performance). So the framerate and performance are better with my current Ubuntu spec but I can't access the full features of my graphics card for a fair comparison.

I'm in college and I mainly just want the smallest Windows XP installation possible that will run iTunes, Warcraft and any random software that professors decide I need to use that requires Windows/Mac. (I haven't been able to use clipboard features in Wine-run programs for instance which is important with Win-specific design software.)

---

### Post by SishGupta on 2007-02-28
If you are going to stick with cedega I would definitely continue with the subscription because in my experience, each time that WoW puts out an update it will often break cedega with wow. The subscription ensures that you get an update to cedega if WoW ever stops working with it.

I can definitely see why you would want to use cedega, there are a lot of positives with it and WoW.

What video card are you using? If you are using nvidia or ati then I would recommend getting the offical driver as you will be able to get all the effects out of your card, but perhaps at a loss of framerate. I find that wine in linux always does 3d a bit slower, and i assume this is due to api translation.

I am also in university and in IT no less so I am forced to use many development applications which are windows only. I have a dual boot setup so i can use windows and linux. I have a 10Gb partition for windows, and 40 for ubuntu.

---

### Post by PatrickG on 2007-02-28
I have an ATI Radeon 9250.

fglrx has been a headache and none of the tutorials I've found have worked.

The open source "Radeon" driver gives me a really nice framerate despite having less than a gig of RAM.

Once I get my Windows partition reinstalled, though, that may wind up being the way to go for WoW.

I have a 70 gig hard drive. Currently 60 gigs are going into Feisty and 10 gigs are set aside for a backup Edgy partition, both with working wireless support.

Since swap files tend to be slow anyway, I probably won't need a large one for Windows. Just guessing, I'll say that WoW is around 3 gigs. A ten gig Windows partition should be plenty if I manually disable/uninstall anything not needed for WoW and iTunes, I'm guessing. (And I'll do the burn and rip trick to get MP3s that I can carry over to Ubuntu so I won't need permanent storage space for music.) I'll look at the hard numbers before I do anything.

---

### Post by SishGupta on 2007-02-28
I feel ya man. I had ATI, then I switched to linux and when it was time to upgrade I went nVidia. ATI on linux is a hassle imo.

I forgot to mention that I use a second hard drive for neutral things like music and WoW. By having wow on a second drive I can use it in wine or windows. That way I can avoid double copies of files and installs.
Wow with BC is just under 7gb by the way.
If i remember correctly, a default windows install is about 4-5gb. There are some cool apps out there thought that really let you cut it down. I think on the torrent sites there is also a USB version of windows xp which i am sure could be installed to a HD and it would be incredibly small.

When you say you are doing the burn and rip trick...
Do you mean you are taking itunes tracks (what are they, mp4?) burning them to cd and then re-encoding them to mp3?
While this may be the only available method to un-DRM your music, I would suggest reading this article:
[http://en.wikipedia.org/wiki/Transcoding](http://en.wikipedia.org/wiki/Transcoding)

Transcoding audio will result in a loss of quality that may or may not be noticeable to you.

Anyway good luck with everything.

---

### Post by PatrickG on 2007-03-01
I knew about the diminished quality. I haven't really noticed a problem and since my car plays MP3s from a flashdrive, I need the conversion for that anyway. Anything I can buy as a vanilla MP3, I do.

OGGs are preferred but not that convenient to buy without a CD and not terribly useful without a CD player or a computer from what I've seen so far.

---

