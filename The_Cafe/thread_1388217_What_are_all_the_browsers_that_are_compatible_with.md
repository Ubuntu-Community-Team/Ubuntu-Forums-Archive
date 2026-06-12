---
title: "What are all the browsers that are compatible with..."
date: 2010-01-22
forum: The Cafe
---

### Post by Psumi on 2010-01-22
HOSTS, Flash and javaScript?

I know Firefox, Midori and Arora and chrome and konquerer (supposedly) are, but what about others that are compatible with flashplugin-nonfree?

I just want to know because I'm going to try out lxde and see what browsers can run the lightest in that environment. Firefox takes up 80+ MB of RAM, Midori takes up 60+ MB and I want something even more lighterweight than that.

I also should let you know that, with flash, RAM usage on firefox does not increase much (if at all), but does increase by 50% cpu usage.

---

### Post by mkvnmtr on 2010-01-22
Check out the latest Firefox from the Ubuntuzilla repository. My memory usage seems to be about half of what it was before the update. You can also get the latest Seamonkey there. It does everything that is important to me that Firefox does. I also like Midori and Opera. Chromium does not do much for me.

---

### Post by juancarlospaco on 2010-01-22
I was testing Arora, it dont work with http**S** websites, simply fail.
Dillo works nice with SSL, but no Javascript.

Also tested NoScript, but FlashBlock seems better, it just block the OverBloated Flash.
*Its not Browser fault, its Flash fault.*

---

### Post by mikkie on 2010-01-22
Well, if you like Firefox, you should try it compiled with PGO optimizations. It should be pretty fast and lightweight then.

---

### Post by Psumi on 2010-01-22
> **mikkie said:**
> Well, if you like Firefox, you should try it compiled with PGO optimizations. It should be pretty fast and lightweight then.

Got one that is already compiled? I don't think I should be forced to compile something when it can be readily available.

I'm using firefox 3.6, and yes, it does have RAM usages of 80+ MB.

> **juancarlospaco said:**
> Also tested NoScript, but FlashBlock seems better, it just block the OverBloated Flash.
*Its not Browser fault, its Flash fault.*

Sorry, I need flash, can't watch Homestarrunner without it.

---

### Post by juancarlospaco on 2010-01-22
> **Psumi said:**
> 
Sorry, I need flash, can't watch Homestarrunner without it.

No but FlashBlock dont block Flash, but blocks Flash ADs, 
i mean you click and play only the Video, and not all the ADs.

---

### Post by lovinglinux on 2010-01-22
> **Psumi said:**
> I also should let you know that, with flash, RAM usage on firefox does not increase much (if at all), but does increase by 50% cpu usage.

Flash will increase CPU usage on all of them, specially with single core CPU. It is not a browser issue, but a flash issue. You might want to try the Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). 

Firefox works like a charm here.

---

### Post by Psumi on 2010-01-22
> **lovinglinux said:**
> Flash will increase CPU usage on all of them, specially with single core CPU. It is not a browser issue, but a flash issue. You might want to try the Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). 

Firefox works like a charm here.

Sadly though, I don't use compiz, don't have propietary video drivers (even though I use ATI), and since that GPU fix is only for youtube, it won't affect me, furthuremore, I can't use the embedded player, because I don't want to go around clicking each thing, which is annoying. I don't have mplayer, nor will ever use it due to it not being what I want in a media player (I use totem or parole, both being based on gstreamer.) (even if I did use mplayer, I'd use smplayer, which is the only one that I'd use, as it has a repeat function and no playlist editor (even if it does, it replaces the playlist with opened files, which I need), as I don't like playlists.)

So in short, I can't optimize flash at all really.

---

### Post by Psumi on 2010-01-22
And for those who do not believe me... here's a shot when running [this video]("http://www.youtube.com/watch?v=Nn1uPQ3zXMw") on youtube, even after the GPU adobe fix:

[img]http://i46.tinypic.com/2u7spoj.png[/img]

Firefox 3.6 of course, using Ubuntuzilla.

---

### Post by Psumi on 2010-01-23
I also just tried that greasemonkey script, and it gives me the "click here to download plugin" thing, lovinglinux. I have mplayer installed, so it should work, right?

---

### Post by lovinglinux on 2010-01-23
> **Psumi said:**
> I also just tried that greasemonkey script, and it gives me the "click here to download plugin" thing, lovinglinux. I have mplayer installed, so it should work, right?

Screenshot?

---

### Post by Psumi on 2010-01-23
> **lovinglinux said:**
> Screenshot?

Here you go: [http://i46.tinypic.com/4u8g8m.png](http://i46.tinypic.com/4u8g8m.png)

---

### Post by lovinglinux on 2010-01-23
> **Psumi said:**
> Here you go: [http://i46.tinypic.com/4u8g8m.png](http://i46.tinypic.com/4u8g8m.png)

You need a plugin like gecko-mediaplayer. It doesn't work with external players.

---

### Post by Psumi on 2010-01-23
> **lovinglinux said:**
> You need a plugin like gecko-mediaplayer. It doesn't work with external players.

Great, ANOTHER gnome-dependency... JUST what I need...

It still has the CPU at 25+% though, and 40+% when focused.

---

### Post by k64 on 2010-01-23
[apt:/flashplugin-installer](apt:/flashplugin-installer)

---

### Post by Psumi on 2010-01-23
> **k64 said:**
> [apt:/flashplugin-installer](apt:/flashplugin-installer)

already have it when I installed flashplugin installer. Please read the whole topic.

---

### Post by john_spiral on 2010-01-23
> **Psumi said:**
> HOSTS, Flash and javaScript?

I know Firefox, Midori and Arora and chrome and konquerer (supposedly) are, but what about others that are compatible with flashplugin-nonfree?

I just want to know because I'm going to try out lxde and see what browsers can run the lightest in that environment. Firefox takes up 80+ MB of RAM, Midori takes up 60+ MB and I want something even more lighterweight than that.

I also should let you know that, with flash, RAM usage on firefox does not increase much (if at all), but does increase by 50% cpu usage.

You can't beat Opera for lightness, also has fash non free compatibility. 

I had a 233mhz machine running Slitaz with Opera as the browser and Adobe flash plugin installed, ran alright.

Otherwise Google Chrome might be another option, I know it also supports flash non free.

---

### Post by Psumi on 2010-01-23
> **john_spiral said:**
> You can't beat Opera for lightness, also has fash non free compatibility. 

I had a 233mhz machine running Slitaz with Opera as the browser and Adobe flash plugin installed, ran alright.

Otherwise Google Chrome might be another option, I know it also supports flash non free.

Just tried opera 10.10, it used up 90% of my CPU when on a flash object (such as youtube.) And I have 1.6 GHz. It also used more real RAM than firefox did (shooting RAM up to 180 MB instead of 130 MB total usage.)

---

### Post by Skripka on 2010-01-23
> **Psumi said:**
> Just tried opera 10.10, it used up 90% of my CPU when on a flash object (such as youtube.) And I have 1.6 GHz. It also used more real RAM than firefox did (shooting RAM up to 180 MB instead of 130 MB total usage.)

How much RAM do you have anyway?  I know you want lightweight, but RAM is meant to be used-and the only thingslighter than Webkit browsers are things like elinks.

---

### Post by Psumi on 2010-01-23
> **Skripka said:**
> How much RAM do you have anyway?  I know you want lightweight, but RAM is meant to be used-and the only thingslighter than Webkit browsers are things like elinks.

512 MB, 496 Usable, see this post for more information: [http://ubuntuforums.org/showpost.php?p=8711201&postcount=468](http://ubuntuforums.org/showpost.php?p=8711201&postcount=468)

on a normal gnome day, I use about 200+ MB depending. On this LXDE, only about as much as I specified in that post.

---

### Post by lovinglinux on 2010-01-23
> **Psumi said:**
> 512 MB, 496 Usable, see this post for more information: [http://ubuntuforums.org/showpost.php?p=8711201&postcount=468](http://ubuntuforums.org/showpost.php?p=8711201&postcount=468)

on a normal gnome day, I use about 200+ MB depending. On this LXDE, only about as much as I specified in that post.

Although the Flash tweaks on my tut helped my situation, I only "solved" my flash issues after upgrading my processor from single core P4 to Core2 Duo. Nevertheless, I have a notebook, with an AMD Sempron and only 256 Mb of RAM and it runs well. It uses a lot of CPU, but at least it doesn't stutters. I guess some old CPUs cannot handle the extra load of the crappy flash code.

---

### Post by earthpigg on 2010-01-23
how closely have you looked at chrome?

it runs blazing fast on my netbook.

---

### Post by Psumi on 2010-01-23
> **earthpigg said:**
> how closely have you looked at chrome?

it runs blazing fast on my netbook.

Netbooks are dual-core according to GNOME System Monitor, this is a single-core NON-HT I have (so it can't even emulate another core.)

---

### Post by lovinglinux on 2010-01-23
> **Psumi said:**
> Netbooks are dual-core according to GNOME System Monitor, this is a single-core NON-HT I have (so it can't even emulate another core.)

I'm afraid that will be a major problem. It's flash fault of course, but single core users are the ones suffering the most.

---

### Post by Warpnow on 2010-01-23
Chromium is as light as I've found for decent flash support.

---

### Post by Psumi on 2010-01-23
> **Warpnow said:**
> Chromium is as light as I've found for decent flash support.

[http://www.srware.net/forum/viewtopic.php?f=18&t=1031](http://www.srware.net/forum/viewtopic.php?f=18&t=1031)

Give me a deb package for iron then. I won't compile it, I hate compiling. I won't use chromium or chrome either until it has the same patches as Iron does.

---

### Post by lovinglinux on 2010-01-23
> **Psumi said:**
> [http://www.srware.net/forum/viewtopic.php?f=18&t=1031](http://www.srware.net/forum/viewtopic.php?f=18&t=1031)

Give me a deb package for iron then. I won't compile it, I hate compiling. I won't use chromium or chrome either until it has the same patches as Iron does.

Kind of hard to make you happy, isn't it? :)

---

### Post by Psumi on 2010-01-23
> **lovinglinux said:**
> Kind of hard to make you happy, isn't it? :)

Yes, I'd rather not be spied upon by anyone but my ISP (As it's Charter, and when do they give a dam about what I do?)

Don't go spouting nonsense like I can configure chrome not to spy on me, I know some things in chrome that can't be turned off by a user normally.

---

