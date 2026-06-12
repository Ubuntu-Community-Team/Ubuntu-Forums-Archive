---
title: "[SOLVED] options for using vst/vsti in ubuntu/linux"
date: 2008-11-09
forum: Ubuntu Studio
---

### Post by otz070 on 2008-11-09
I want to be able to get my vst/vsti working in linux/ubuntu studio (I use 64bit)
Generally most of the vsts that I use are free, as I know that pay for from big companies are generally not supported

so far I have found the method using audacity vst
but this uses no gui and can be glitchy

I was wondering what other options I have for getting vsts to work (preferably with the gui though)

---

### Post by Stochastic on 2008-11-09
There are three other methods that I'm currently aware of (of course I don't know how much 64-bit compatibility each has) for VST in Linux:

1) FST - from what I've read, this is the method to use if you want to use VSTs in Ardour. Website: [http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)

2) dssi-vst - this is a wrapper for dssi that allows you to run VST plugins.  See the dssi website for more info (dssi-vst is in the list at the bottom of the page): [http://dssi.sourceforge.net/](http://dssi.sourceforge.net/)

3) JOST - this is a very intriguing new package.  Seriously take a look at this: [http://www.anticore.org/jucetice/?page_id=4](http://www.anticore.org/jucetice/?page_id=4)

On top of all that, I'd recommend taking a read through the Linux-VST database if you haven't already seen it; it's a listing (similar to wine-app-db) of the various VSTs that reportedly work/don't work on Linux: [http://ladspavst.linuxaudio.org/](http://ladspavst.linuxaudio.org/)

Please report back with your successes/failures on 64-bit!

---

### Post by babarosa on 2008-11-09
Another possibility is this:

Use Reaper with Wine to do mixdowns using vst effects and vst-instruments (I only use a sf2-player and pre-record it's midi-tracks with muse). In this case latencies are not an issue.

[http://www.servimg.com/image_preview.php?i=4&u=12842335](http://www.servimg.com/image_preview.php?i=4&u=12842335)

It works very well on my system.

---

### Post by otz070 on 2008-11-09
ok thanks using the last link I found this [http://lmms.sourceforge.net/home.php](http://lmms.sourceforge.net/home.php) (It supports vst!!!) I'm going to give it a try

other things I found are that many of the vsts that I already use will work on linux:D

and also I seem to be having a problem installing wineasio

---

### Post by otz070 on 2008-11-09
(last link was from Stochastic)
Got beat to post

---

### Post by Stochastic on 2008-11-09
Actually wikipedia's section on linux vst info is quite extensive/comprehensive: [http://en.wikipedia.org/wiki/Virtual_Studio_Technology#GNU.2FLinux_support](http://en.wikipedia.org/wiki/Virtual_Studio_Technology#GNU.2FLinux_support) and lists a few more options out there.

---

### Post by otz070 on 2008-11-09
I could also use some help in this thread which is [http://ubuntuforums.org/showthread.php?t=975010](http://ubuntuforums.org/showthread.php?t=975010) (about my usb interface)

Just trying my best to get everything working:D 


ok jost website doesn't seem to load tonight mabye try tommorow

trying dssi-vst got tar.gz 
unpacked to desktop
how do I get installed (I think I use make?)
Thanks:D

---

### Post by otz070 on 2008-11-09
stuck here

need help to install wineasio (sudo apt-get?) not sure but tried awhile ago and kept getting errors need solution 

how to install dssi-vst file is on my desktop right now

and took a look at the wiki page on vst and seen I need vst sdk so which one(s) do I download?:confused:

Thanks:D (Sorry If I'm being a pain I'm new at this)

---

### Post by otz070 on 2008-11-09
ok (still need stuff from my previous though)

but got lmms and has 64bit support with vst:D
now just to dig into my vst archive and test them out I'll post the results here as simple yes or no to save space but anyway I'm happy for a little while:D



(lmms has multicore support for upto 16 cores! the only daw I have ever seen that has this kind of support! And yes they do exist there are currently two that I know of boards that support quad quad cores 4x4=16 cores I want one but I'll have to settle for a dual quad:( for my workstation, those boards start around 1k$)

---

### Post by otz070 on 2008-11-09
(Finally figured where the thanks button is!:D)

Heres what I got from lmms 

linux has 64bit support but get deb has an older version than the one I used with wine and it severly lacks features compared to the new version 
as for the new version it has only 32bit support with wine 
I got several vsts to work with this but only the guis showed up and when playing It played general midi instead of the actual vst (I'm pretty sure that I had something configured wrong though)

lmms has a neat little vst translation tool within and I am curious to see If it is only for wine or if it exists within the newest (current beta) for hardy 64 though this will probably be through dssi

But either way If I can get anything working for now that uses my favorite vsts and loads fast I'll be happy 

(But I'll alwalys be wanting more:D)

 (Right now for windows I use Traction 2 which unfortuantly takes forever to load at the start, and this is with the check for new turned off. So when Inspiration strikes by the time the system is ready Inspiration is gone:()

---

### Post by Stochastic on 2008-11-09
as for the Steinberg SDK, here's where it is now: [http://www.steinberg.net/en/company/3rd_party_developer.html](http://www.steinberg.net/en/company/3rd_party_developer.html) but they keep moving it around so you may need to do a google search if you come back to this thread in 6months.  You also need to make an account on their site and agree to the terms before you get it.  Oh, and I'm pretty sure you want version 2.3 for best results on Linux.

The lmms get deb issue you're having I dont' fully understand, are you saying that you're not using the LMMS that's in Ubuntu's repositories?

As for your other queries, I think they're a little off topic for this thread (it's hard to keep track of them all).  Proper forum etiquette is to keep each issue to its own thread.

---

### Post by otz070 on 2008-11-11
> As for your other queries, I think they're a little off topic for this thread (it's hard to keep track of them all). Proper forum etiquette is to keep each issue to its own thread. I apologize for that.

> The lmms get deb issue you're having I dont' fully understand, are you saying that you're not using the LMMS that's in Ubuntu's repositories?

The lmms issue is sort of rather not so much an issue but rather a work around (I'm using it in xp pro as a alternative to traction 2 until the ver.4 is available for hardy) sorry for the confusion

So the real problem is just with installing dssi and wineasio
I have both packages on my computer but cannot get them installed mostly due to lack of know how.:confused: 

Again sorry for the confusion next time I'll try to keep posts more on topic and organized.

---

### Post by otz070 on 2008-11-11
I am going to mark this thread as solved as It really is It is just going too off topic and there have been recently posted more revelant topics to what I am looking for any way the inital topic was [COLOR="Indigo"]Options[/COLOR] not [COLOR="Red"]installitaion issues[/COLOR] so the [COLOR="Purple"]options[/COLOR] are here so really the thread is solved 

Time to move on.
Apoligezing again.

---

