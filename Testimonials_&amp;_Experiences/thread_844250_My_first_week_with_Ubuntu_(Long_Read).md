---
title: "My first week with Ubuntu (Long Read)"
date: 2008-06-29
forum: Testimonials &amp; Experiences
---

### Post by shadowake on 2008-06-29
Well I've been keeping an eye on Linux developments for quite some time, but never really 'took the plunge'. The only time I've ever used it was a live CD of knopix to restore some data from a dodgy hard drive.

Anyway with the newest versions of Fedora, Ubuntu and Suse being released and the screenshots looking so good I decided to give the whole Linux thing a go.

To be honest the other driving factor was the awful reliability of my machine running Vista. I caould run Crysis with the setting on full for hours without a single problem, but then run a much less demanding game like The Witcher or UFO: Alien Afterlight and it would hang or BSOD. Not to mention my anti-virus would randomly cause a BSOD (apparently a know issue with Kapersky and Vista yet a year on, even though you have to pay for it, still no fix).

So anyway back to Linux. I'd love to say the install of Ubuntu went smoothly and didn't take three days of hair pulling madness, but I'd be lying. I stuck the disk in and chose boot from CD. The first screen appeared and I hit install and then watched as the progress bar hung for 20mins... So I rebooted and tried again, same thing. After trawling the web I found that the 8800 can cause problems and to try noapic etc etc. Gave it a go and it did actually work. Great I thought, got to the actual setup and it didn't recognize me RAID0 array... Back to the web to find Linux doesn't like 'fake' RAID. Fantastic. I was trying to set up a dual boot with Vista which was already on RAID so I couldn't turn it off. Luckily I had a few spare drives in the loft so I went and dug out an 80GB SATA drive and stuck that in, and reinstalled to that. The install worked this time, but low and behold I could only boot to Vista (apparently the default install tried to write the boot data do my RAID disks and failed).

Feeling very disheartened I decided to call it a day. The next day and with some web browsing later I read that Fedora sometimes recognizes 'fake' RAID. So one massive 4GB odd download later I was ready to give it a go. Click install then... black screen... great. Back to the internet, apparently because I have NVidea graphics I have to choose the text installer. No problem, reboot and try again. This time it works, it even see's my RAID0 array properly, fantastic! Proceed to install on the extra disk (since it's in now anyway) and write the boot info onto the RAID disks, works a charm. Finally I think problems solved!... No... Kernal killed error... oh happy days. Look on the web 'eventually' find out it's due to my overclock. Fine, turn it down from 3.4GHz to 3.28GHz and it boots, then...black screen. Arrgh! Computer off, go to bed, try not to kill anyone.

Next day, after seriously contemplating just forgetting the whole Linux thing, against all odds, I decide to try once more. Grab my Ubuntu disk stick it in and hope and pray, surprisingly it goes to the install fine even though I forgot to add the noapic etc line (found this was because of my overclock too). Anyway install again, but this time make sure to go into the advanced options and put the boot data on the Linux drive. I follow a guide online to use easyBCD to get my system to dual boot Vista/Ubuntu as GRUB just didn't see the RAID drives properly.

Well... I'M GLAD I PERSISTED AS UBUNTU IS FANTASTIC!!!

OK it's not perfect, and took a lot of getting use to. I still don't have any sound from my XFi card despite following numerous guides but hey.

Heres a list of what has impressed me so far:

1. When I boot to Vista my hard drive churns away constantly until I shut down. I always just thought this was the drives themselves as the Western Digital Raptor's are notoriously noisy. When I boot into Ubuntu... COMPLETE SILENCE!!! Not a whisper, they are so quiet it's unbelievable! Even when I run something intensive.

2. First time I booted to Ubuntu, within 30 seconds a pop up told me there were 205 updates to be installed (Windows would take an eternity to tell you this). It then installed them ALL in just over 30mins and my net connection isn't the greatest. Not to mention this wasn't just OS updates but program updated as well! Would take best part of a working day to get this done on Vista.

3. Screenlets (had to download this but easy to find) - what can I say... BRILLIANT! So much better than Google gadgets or Vista's Sidebar. You can put them anywhere on your screen which is great, and you can download more at the click of a button!

4. Customization - You can change so much it's unreal. I love tinkering and 'making things my own'. Linux more than gives you enough to 'express' yourself. Downloaded some themes and the OS IMO now looks much better than Vista, even got transparent 'Vista glass' like menus :)

Well there you go, just thought I'd share my experience so far. Off to download Wine and some free games! Sure I'll be around this forum more frequently now, love Ubuntu and can't wait to fix my XFi problem, then it's bye bye Microsoft for good!!!

:guitar:

---

### Post by jukingeo on 2008-06-29
I hate to say this, but you are going to have one heck of a time getting that X-Fi to work.  I have the same card and I been on Ubuntu for a month now and it STILL isn't operating properly.  I currently have the OSS drivers set up on the card because the ALSA driver is only in Beta right now and it was only tested on Ubuntu 7.10.  To my knowledge, it doesn't work in 8.04 (Hardy).

As of now I have the current OSS driver installed and I have audio, but there are issues.  For one, I have Ubuntu Studio which configures most of it's audio programs through a low latency server program called Jack.  Jack runs on ALSA and I have yet to find a way to get it to talk to OSS.  So that being said, NONE of the audio editing software I got with Ubuntu Studio works.  Another issue with OSS is that it it doesn't work with flash or streaming audio, so that means no sound on the internet.  However, I do have my system sounds and I have most of my game sounds.  There are a few applications where I don't have sound with, but by and large I can play most of my games and they do have sound.  The games I usually play are Linux based games and console emulations such as Atari 2600, NES, SNES, Sega Genesis, and old DOS games.  I can also play MP3's that are on my system with no problem.

The solution that has been presented to me is either:

1) Revert back to Ubuntu 7.10 and load up the ALSA drivers 
2) Pull your X-Fi out of your system and go with a supported card. 

Here look at this list:

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

This list will tell you what sound devices are supported.

In terms of Creative sound devices, Sound Blaster Live or Audigy devices are known to work.

But as you see there are quite a few supported sound cards under the ALSA project.

There are other sound formats besides ALSA and OSS, but do yourself a favor and stick with ALSA.  Ubuntu is very heavily geared towards ALSA and if you want to do any kind of audio and video editing work, you are going to need ALSA.

Also, other Linux distributions are also favoring ALSA.  So unless you are really really attached to that X-Fi card...you are best pulling it out for something more compatible.  But hold on to it though...support for the card may be available in the future.

I can't wait though...more then likely I am going to change my card.

Sorry I don't have better news, but changing the card is probably your best option as of now.

Geo

---

### Post by starcannon on 2008-06-29
I don't own an X-Fi card, but have done some research on them, if you get it to work, it will be a headache, best bet is to replace it if you can (thanks Creative).

A list of known working cards is here:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

Theres lots of hardware that works excellent under Linux. The downside is if your bringing in an already built windows gaming machine it can be the case that you have something that is not yet well supported.

I have been using Ubuntu exclusively for 5+ years, my last big gaming machine build I took the time to build my idea of the perfect linux gaming box, its in my signature.

I'm not as big of an audiophile as many, and found that a good solid on board sound system was fine for me, as it is my integrated ac97 compliant sound chipset is capable of more than the speakers I own lol.

I'd say for the time being, whilst your learning your new found OS, perhaps start from default settings, remember the journey of a 1000 miles begins with the first step. Ubuntu is not hard to use, but its different than windows, so what may make sense there won't here and uva-ursi. Perhaps set your bios to a stock "performance" setting for now, learn your way around the linux file system, get your desktop just the way you like it etcetera, and once you have things working excellently with a stock configuration, then go back to hardware tweaking.

Speaking of hardware tweaking, if thats your bag, you will likely find a level of freedom previously unknown to you. Linux is all about letting you have it your way, though when you get into custom configurations, having it your way often means cutting your own path.

GL and welcome to Ubuntu!

---

### Post by wolfen69 on 2008-06-29
great news. welcome to the best os on earth.

---

### Post by grimdeath on 2008-06-29
oh, in case you are dual booting into vista, like I do, you CAN disable the constant churning sound from your hard drive. that sound is just windows indexing your computer so that search will work....yes it is still silly it does it that way, but hey, thats what your ubuntu boot is for right? :P

[http://4sysops.com/archives/how-to-disable-vista%E2%80%99s-desktop-search-indexing-windows-search/](http://4sysops.com/archives/how-to-disable-vista%E2%80%99s-desktop-search-indexing-windows-search/)

---

### Post by shadowake on 2008-06-30
> **grimdeath said:**
> oh, in case you are dual booting into vista, like I do, you CAN disable the constant churning sound from your hard drive. that sound is just windows indexing your computer so that search will work....yes it is still silly it does it that way, but hey, thats what your ubuntu boot is for right? :P

[http://4sysops.com/archives/how-to-disable-vista%E2%80%99s-desktop-search-indexing-windows-search/](http://4sysops.com/archives/how-to-disable-vista%E2%80%99s-desktop-search-indexing-windows-search/)

Nope indexing is already disabled, think it's just the sound of Windows!

No luck with the OSS or ASLA drivers for my sound card :( Need to keep it though as it's running my 7.1 speakers in Vista for movies etc.

Is it possible to use the on board sound from the mobo whilst having a sound card plugged in? If it is I could always just buy some cheap 2.1 speakers just to plug in to use with Linux? Is there some sort of command to disable the add in card or would it work anyway?

Thanks for the help guys :)

---

### Post by jukingeo on 2008-06-30
> **shadowake said:**
> Nope indexing is already disabled, think it's just the sound of Windows!

No luck with the OSS or ASLA drivers for my sound card :( Need to keep it though as it's running my 7.1 speakers in Vista for movies etc.

Is it possible to use the on board sound from the mobo whilst having a sound card plugged in? If it is I could always just buy some cheap 2.1 speakers just to plug in to use with Linux? Is there some sort of command to disable the add in card or would it work anyway?

Thanks for the help guys :)

You should get partial sound with OSS and this guide should get OSS to work with the X-Fi

[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

And this is the discussion I been a part of. I know the subject heading is AMD 64 bit processors, but the guide also applies to iX86 (32bit) machines:

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

After following this guide you should get some kind of sound on your system.  I will say though upfront that OSS doesn't like streaming audio, so you will not have sound on the internet.  You also will not have sound through anything that uses Jack Rack (for audio recording work).  Jack Rack is an ALSA based program and that is what it likes to see going into and out of it.

Now you should have SOME sound, like you should be able to play sound and movies on your hard drive.  You should also have system sounds and sounds within certain programs such as games and game console emulators.

In terms of on board sound, you are going to have to check the ALSA listing to see if it is supported.  More then likely internal sound is handled by Realtek audio and that isn't supported.  If you have a Yamaha sound chipset on board, THAT may be supported.  You just have to look at the list that both Starcannon and I provided here for you.

I am in the kind of the same boat as you.  At first I really didn't want to mess with my X-Fi card because it is working very well in Windows XP right now and I am still dual booting.  I was so petrified of ruining anything on Windows that I only dictated Ubuntu activities on a separate hard drive.

Because my needs are audio/video editing based I decided to look deeper into the X-Fi's ALSA drivers and what the problem is and I was also looking into other Linux distributions as well to see how they faired with the X-Fi.

As it turns out, the ALSA driver is in BETA stages and it only has been tested on a couple Linux distributions.   I believe it was tested only with Ubuntu 7.10 (Gutsy) and also OpenSuSE 10.3.  Outside of those you could be looking at a real pain in the butt to try to get the card to work with ALSA drivers here in Hardy.

I been looking into other distributions as well such as OpenSuSE's JackLab (which is based on OpenSuSE 10.2) and also 64Studio (yes they have a 32 bit variant).  While they will handle everyday tasks as well, but they are specifically formulated for audio/video editing work.

After poking around in both the JackLab and 64Studio forums, I have found that X-Fi users are experiencing problems there as well.

There is a common connection; Ubuntu (Studio), JackLab, and 64Studio use Jack Rack and as I said before, Jack likes ALSA and not OSS.

So the more I looked at my current situation the more I realized that the X-Fi has to go.

We don't know when Creative is going to finish the drivers for ALSA...it could still take years.

Now your situation isn't like mine in that I also have a professional recording piece of hardware made by Alesis called the IO-26.  Which is an 8 in 8 out device. Normally I only used this for heavy duty recording work in Windows, but this weekend I found out that the IO-26 can be configured through Windows with full 7.1 (8 channel) output configuration.

So that was a sigh of relief for me, because that means I could set Windows to use the Alesis IO-26 and I am at free liberty to disable and yank the X-Fi card out of my system.

How does this help you?  Well, you mentioned you have on-board sound.  Best thing to do is set up your Windows back on the on-board sound and sacrifice the lack of surround sound for the short period of time you find a replacement card.

If you are not doing heavy recording work, go to computer store websites (such as Tiger or Amazon) and find an audio card that you like.  From there go tot the ALSA site and see if your make and model is supported.   If you want something high end, I hear the Razer Barracuda is a really high end card like the X-Fi, but with the major difference that it has full Linux support.

If you do want to do some multi-channel recording work, but don't want to break the bank, you can check out Musician's Friend and the M-Audio Delta series.  They make them in different sized to handle your input and output needs.  They also offer midi interfaces as well to connect any midi musical instruments you may have.  So if you play one of those Casio keyboards, you can hook it up to the computer and take advantage of the all the wonderful free software that Linux has to offer.

I weighed my options and last night I made the decision that the X-Fi is leaving my system.

But remember, make sure the next card you look into is FULLY ALSA supported.   More and more of the newer Linux distributions are using ALSA now instead of OSS.

Good Luck!

Geo

---

### Post by shadowake on 2008-06-30
Thanks, found drivers for the onboard sound (it was realtek). Having problems removing the old OSS drivers now!

Please see [http://ubuntuforums.org/showthread.php?p=5293906#post5293906]("http://ubuntuforums.org/showthread.php?p=5293906#post5293906")

---

### Post by jukingeo on 2008-06-30
> **shadowake said:**
> Thanks, found drivers for the onboard sound (it was realtek). Having problems removing the old OSS drivers now!

Please see [http://ubuntuforums.org/showthread.php?p=5293906#post5293906]("http://ubuntuforums.org/showthread.php?p=5293906#post5293906")

Just be careful, according to the ALSA list Realtek isn't listed.  So it could be some kind of experimental ALSA driver.  I would read into it THOROUGHLY before trying anything like that.

Probably the best thing to do is put your Realtek back on to Windows and make sure it works.  Then disable the X-Fi and pull it for something that is more compatible with Linux.  Of course the card should also support Windows XP.   A high end card like the Razer Barracuda should support multiple outputs and surround sound.

Good Luck!

Geo

---

### Post by shadowake on 2008-07-02
Well formatted off and plugged some speakers into the onboard soundcard and guess what... Works right out of the box! :) Very happy! Ordered an extra set of cheap speakers just to use with Ubuntu and can still use my XFi for Vista (not that I'll be using it that much anymore)!

---

### Post by Martje_001 on 2008-07-02
Yes! Welcome!

---

### Post by steveneddy on 2008-07-30
[COLOR="Blue"]**Well... I'M GLAD I PERSISTED AS UBUNTU IS FANTASTIC!!!**[/COLOR]

I couldn't agree with you more!

---

