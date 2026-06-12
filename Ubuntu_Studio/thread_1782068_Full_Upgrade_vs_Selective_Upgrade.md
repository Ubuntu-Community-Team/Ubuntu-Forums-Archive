---
title: "Full Upgrade vs Selective Upgrade?"
date: 2011-06-14
forum: Ubuntu Studio
---

### Post by Jonatello on 2011-06-14
Hello, everyone :) Today I'll be receiving my brand new System76 Serval and for the first time will be able to really dig into the Ubuntu experience myself. I know I'll have some learning curves ahead, but at least I've had various chances to dabble over the past year or so (rescued my girlfriend's dying laptop with ubuntu and gave it new life) while planning my own migration. 

There's such a sea of information out there, I was hoping maybe some of you could help me understand the important factors regarding one of my first big decisions when the machine arrives.

I'm looking at this page: [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

I need to figure out whether it's best for me to do Full Upgrade, Selective Upgrade, or something else that I haven't considered.

I'm a graphic/web designer by trade (will probably eventually need to run LAMP), a music producer by passion (migrating from FL/Audition workflow to probably some Audacity/LMMS/Ardour combo), and also looking forward to more dabbling in video, etc. I will also surely be using the computer for regular things like email, web browsing, skyping with family, etc. 

What would yall say are the major determining factors in choosing my approach to installing ubuntu studio (full/selective) or other route?

---

### Post by Pablo_F on 2011-06-14
If you do the full upgrade you risk installing some programs that are a bit buggy, or not very intuitive or  not very useful, or a mixture between (this is subjective, of course).

OTOH, the full upgrade will install very useful software very easily.

So, basically, it depends on your tolerance to suboptimal software and your prefered way of installing, the time available, etc. 

Note that, in general, unused apps don't hurt.

---

### Post by Jonatello on 2011-06-14
> **Pablo_F said:**
> If you do the full upgrade you risk installing some programs that are a bit buggy, or not very intuitive or  not very useful, or a mixture between (this is subjective, of course).

OTOH, the full upgrade will install very useful software very easily.

So, basically, it depends on your tolerance to suboptimal software and your prefered way of installing, the time available, etc. 

Note that, in general, unused apps don't hurt.

Thanks, Pablo. The computer will be coming with 11.04, which is Unity. I noticed that the full version of Ubuntu Studio stays away from Unity. If I were to go the selective route, would I run into problems conflicting with Unity?

Besides having extra suboptimal software (not a big deal, since I'm assuming I could remove anything I don't want) are there any other concerns or possible disadvantages with the full install? Is is still useful for general needs, web stuff, etc?

---

### Post by Flaggmann on 2011-06-14
I did FULL install of ubuntu 10.10 first because I had the ISO DVD to start with. Whe it asked for audio/video/graphics install components I selected full all three 2D & 3d Graphics as well as full audio and video editing. Once installed, I did basic config of browsers and email etc. and added open office, seamonkey, chromium and LAMP as well as Icecast/Icecast2 streaming servers for audio. ( with jack audio you can patch the output of a player's playlist looped continuously directly to streamer for accessiblity by any PC on your private home network)

Once configured, I selected the update window, but did not update, just let it sit until the UPGRADE button appeared; then chose to UPGRADE so I didn't have to download both all the updates and then all the upgrades; this way it just did it all at once.

Once completed I finished configuring alsa and jack (see previous post on disabling pulseaudio  "Helpful info re audio troubles") then go System --> Preferences --> Startup Applications  and remove that which you aren't using to free up mem and cpu resources to help speed things in the OS up a bit.

I am reasonably happy with 11.04, but it seems a bit sluggish compared to 10.10 and definitely the browsers are quite slow loading especially noticeable in FF 4.0. There is a Flash-Aid plugin that someone here told me about and that straightened out flash video problems for all browsers just by using it as a tool in FF.

I am ex Eng Tech and aud/videogfx production type and find the packages pretty good on linux. GIMP, raster gfx editor is excellent replacement for photoshop, Inkscape is good vector gfx editor replacement for Illustrator; Audacity, after you install the lame plugins for mp3 is excellent editor for audio. OpenOffice is pretty good replacement for costlier windows office packs.

As they have stated elsewhere in the studio forum the video editling NLE W/S packages are fair to decent but not pro/prosumer grade yet, some that were close have been dropped for support and others have come to replace them; you might say it is a work in progress. I have used FCP , Premiere, leitch's products as well as avid NLE's and of course they are smooth and pro versions, but I found I have to keep a windows box offline loaded with Video Studio, Pinnacle Studio/Liquid, Premiere/Photoshop Elements
to be able to come close to a final product that one could do with any one of the costlier pro NLE packages. Each one has a different set of filters and effects, but combined they all have close to a complete set available in the better versions. I also found a open source converter package that will convert any video format file to swf for web use directly. Premiere elements will do flv but not swf. The only problem with having to do it this way is it takes some extra rendering steps and with each re-render process the quality is affected. Everything I do now is in HD so that the final result is reasonably good quality product for web sites etc.
Some of the video open source products as well as the openoffice base products don't have enough users/devs yet so they aren't quite as feature rich and user friendly yet
as their windoze equivalents (like MS Access). The databases, like mysql and postgresql
are pretty decent but the report design capabilities are lacking; as are the report capabilities in OpenOffice Base. The MS Access version allows customizing reports that are needed over and over and include page and font formatting and layout as well as logo watermarking etc. but these are not built into base yet, as their aren't enough people using/developing it yet. The word proc and spreadsheet are nice but there are more folks using it.

OpenOffice has a directly compatible presentation package with powerpoint as well.

Hope this helps out in deciding which way you want to go....cheers

---

### Post by dawiba on 2011-06-14
[QUOTE=Jonatello]The computer will be coming with 11.04, which is Unity. I noticed that the full version of Ubuntu Studio stays away from Unity. If I were to go the selective route, would I run into problems conflicting with Unity?[/QUOTE]

I originally installed regular Ubuntu 11.04 and then installed some of the Ubuntu Studio packages and have been fine so far.

[QUOTE=Jonatello]Besides having extra suboptimal software (not a big deal, since I'm assuming I could remove anything I don't want) are there any other concerns or possible disadvantages with the full install?[/QUOTE]

Only that if you install the Studio packages and then decide you no longer want a specific program and try to uninstall that program, you'll end up having to uninstall the Studio package it came in, so you may be stuck with some programs that you don't use. Like Pablo says though, in general, unused apps don't hurt.

---

### Post by Pablo_F on 2011-06-14
> If I were to go the selective route, would I run into problems conflicting with Unity?
It has absolutely nothing to do. If you don't like Unity select "ubuntu classic" in the login screen. 

> Is is still useful for general needs, web stuff, etc?

You have to know two things:

1) Ubuntustudio IS ubuntu. There are no different repos. ubuntustudio metapackages do not change almost anything in your system, they just install some programs for audio and video work. There are more programs that are not in the ubuntustudio metapackages but they are in the ubuntu official repos. So, yes.

2) The most important thing in the audio side is the jack sound server. This confuses new users as you end up with two sound servers, pulseaudio and jack. Pulseaudio is for desktop use, jack is for pro audio use. Both use the alsa drivers which support your audio card (hopefully) but they are very different beasts. In general, you need to know if a given application is a jack client or a pulseaudio client (or if it uses plain alsa). You will realise, don't worry just yet.

Cheers, Pablo

---

### Post by Pablo_F on 2011-06-14
> you'll end up having to uninstall the Studio package it came in, so you may be stuck with some programs that you don't use.

This is confusing, but AFAIK, there is no problem. You can safely uninstall the ubuntustudio metapackages, which already did their job.

---

### Post by dawiba on 2011-06-14
> **Pablo_F said:**
> This is confusing, but AFAIK, there is no problem. You can safely uninstall the ubuntustudio metapackages, which already did their job.

To give an example of what I mean, after having installed ubuntustudio-audio-plugins, try uninstalling just Aeolus and nothing else. I can't do it. If you know how I can do it, I'd be pleased to know :D

---

### Post by Pablo_F on 2011-06-14
> after having installed ubuntustudio-audio-plugins, try uninstalling just Aeolus and nothing else. I can't do it. If you know how I can do it, I'd be pleased to know

If you remove aeolus, ubuntustudio-audio-plugins package will be removed but it does not matter because it already did its job of installing the actual programs. 

It is just a convenient way of installing a lot of programs by marking them as dependencies. It does nothing else.

Cheers, Pablo

---

### Post by dawiba on 2011-06-14
> **Pablo_F said:**
> If you remove aeolus, ubuntustudio-audio-plugins package will be removed but it does not matter because it already did its job of installing the actual programs.

Having just tried this, I offer my apologies. You are correct :)

I seem to remember in a previous version of Ubuntu/UbuntuStudio, when I tried to uninstall just one particular program (it was probably Aeolus) that Synaptic wanted to uninstall a whole host of other stuff, including Ardour. Not so this time :)

Thanks for pointing that out, my computer is a lot lighter now :)

---

### Post by Jonatello on 2011-06-15
> **Pablo_F said:**
> It has absolutely nothing to do. If you don't like Unity select "ubuntu classic" in the login screen. 



You have to know two things:

1) Ubuntustudio IS ubuntu. There are no different repos. ubuntustudio metapackages do not change almost anything in your system, they just install some programs for audio and video work. There are more programs that are not in the ubuntustudio metapackages but they are in the ubuntu official repos. So, yes.

2) The most important thing in the audio side is the jack sound server. This confuses new users as you end up with two sound servers, pulseaudio and jack. Pulseaudio is for desktop use, jack is for pro audio use. Both use the alsa drivers which support your audio card (hopefully) but they are very different beasts. In general, you need to know if a given application is a jack client or a pulseaudio client (or if it uses plain alsa). You will realise, don't worry just yet.

Cheers, Pablo

Thanks Pablo, this was a very helpful reply. So if I just install the audio programs I want, plus jack, I should be all set? 

Does jack cause any side problems in the system or is it safe?

Oh, and just because I'm still so fuzzy on things (and I promise I've been googling up a storm, not just taking advantage of you good people)...at what point would I be lacking or disadvantaged if I didn't use jack?

---

### Post by jejeman on 2011-06-15
> Does jack cause any side problems in the system or is it safe?No problems. It's a daemon which is started by user, so if you are not using it, it does nothing.
> at what point would I be lacking or disadvantaged if I didn't use jack? 
If you don't install jack you can't use programs that only runs with it. Also if you need to do something in realtime you need jack.

---

### Post by Jonatello on 2011-06-17
> **jejeman said:**
> No problems. It's a daemon which is started by user, so if you are not using it, it does nothing.

thanks. does that mean it automatically turns off and switches back to pulseaudio when i'm not using a given music software, o do i need to manually turn it off/switch?

---

### Post by jejeman on 2011-06-17
It does automatically, (at least thats how it is on my systems.)

---

### Post by Jonatello on 2011-06-17
> **jejeman said:**
> It does automatically, (at least thats how it is on my systems.)

cool. lol i'm such a noob with this. just trying to make sure i don't mess up anything.

---

