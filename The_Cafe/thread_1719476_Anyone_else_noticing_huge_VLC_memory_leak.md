---
title: "Anyone else noticing huge VLC memory leak?"
date: 2011-04-01
forum: The Cafe
---

### Post by akand074 on 2011-04-01
Hey guys, just recently (as of maybe 3 or 4 days ago?) VLC has been having a massive memory leak. It's only happened to me when I skip through a video on occasion but my RAM usage jumps to ~98% and my whole system becomes almost unusable. I close VLC and then within a few seconds it drops back to ~18% of my 6GB of RAM. I run VLC again and everything is fine.

I'm not really looking for a solution, it's not really a big deal to me right now so I posted in these forums. I'm just wondering if anyone else is getting this? Might have been due to an update. I'm using the VLC right from the repositories in Maverick. I was pretty surprised the first time it happened.

---

### Post by youbuntu on 2011-04-01
Windows VLC did a few strange, crashy tricks on me when I opened videos recently, but not Schminux :).

---

### Post by beew on 2011-04-01
That happens in Lucid when VLC goes full screen without fail, never notice that in Maverick.

---

### Post by wolfen69 on 2011-04-01
VLC has been great for me.

---

### Post by Dayofswords on 2011-04-01
this happened to me in lucid once, could not figure out what i did... other than that, things have been great.

---

### Post by akand074 on 2011-04-01
This happened only twice I think.. maybe three times and now that I think about it, it's when I closed a movie and am clicking through it to find out where I was. So when I skip through a video frequently in a short period of time that happened.

VLC has been amazing for me otherwise, have been using it exclusively for years, I'm not looking for a fix because these kinds of things tend to go away on their own through updates. It was just my first issue with VLC I've had worth mentioning.

---

### Post by Legendary_Bibo on 2011-04-01
VLC can't play any video correctly for me. They all stutter.

---

### Post by beew on 2011-04-01
> **Legendary_Bibo said:**
> VLC can't play any video correctly for me. They all stutter.

Probably because it uses only single core for decoding (mplayer from ppas use multi-core) But ffmpeg-mt has been merged to the main trunk in March so I expect h264 playback will get better for vlc in future releases.

Also vlc doesn't work with vdpau apparently, so it performs far poorer than mplayer or XBMC(vdpau enabled)in hd video playback if you have a Nvidia card.

---

### Post by KiwiNZ on 2011-04-01
If it's occurring in full screen mode trying reducing to 'Windowed' before skipping this may help.

---

### Post by akand074 on 2011-04-03
> **KiwiNZ said:**
> If it's occurring in full screen mode trying reducing to 'Windowed' before skipping this may help.

No this has only happened in windowed mode. I should try to see if I can reproduce it. Then again, my current uptime is 16d 2h 37m and there has been like 3 sets of updates that recommended a restart. That could have something to do with it.

---

### Post by NightwishFan on 2011-04-03
I have had this happen to me before. I am not sure what caused it because the OOM killer caught the process before I could figure out too much. This was on Lucid I think.

---

### Post by Aquix on 2011-04-03
You use skins? I have noticed that some skins can make the computer freeze for a bit. I have no idea why though.

---

### Post by Myone on 2011-04-06
I have the same issue in Lucid since VLC got updated from 1.1.7 to 1.1.8.
Ocassionally VLC starts using up to 99% memory, resulting in an unstable system.

Since the frequency of those memory leaks seems to be rising,
i use Mplayer as a part-time solution until VLC will be fixed.
Alternately one could compile VLC 1.1.7 manually.

---

### Post by stuntgp2000 on 2011-04-07
Yes, happened to me a few times on Ubuntu 11.04 and thought it was due to something else. And few moments ago the same happened to me on Fedora 14 x64 when I was using nothing but VLC 1.1.8. So it's definitely VLC 1.1.8 which is causing it.

---

### Post by akand074 on 2011-04-07
I actually just checked and I'm only running 1.1.4, I suppose that's the default in Maverick. Perhaps fixed and then reintroduced in 1.1.8? Then again, I've yet to have the problem again. Though I haven't had the need to skip through a video frequently recently.

EDIT: I just tried to reproduce it using a few videos and I couldn't. These things tend to come and go for me which is why I never bother searching for a fix.

---

### Post by Myone on 2011-04-09
EDIT 10-04-2011: Still not fixed, unfortunately.

---

### Post by leviathan8 on 2011-04-09
I'd suggest that you'd better use mplayer.

---

### Post by hellslinger on 2011-04-16
Just in case some VLC devs run into this, I'd like to add a +1 here for VLC memory leak on X86_64 Natty Beta. I added some MP3s to a playlist and when it got to a third song during playback, my machine with 6 GB of RAM slowed to the point where my mouse cursor was unresponsive. htop revealed 2 vlc processes that were using 7 GB of ram and swap was being used.

VLC kicks ***. Many thanks for great, free software.

---

### Post by NightwishFan on 2011-04-16
> **hellslinger said:**
> VLC kicks ***. Many thanks for great, free software.

I am pretty sure this is an isolated and probably resolved issue.

---

### Post by frankbooth on 2011-04-16
> **hellslinger said:**
> Just in case some VLC devs run into this, I'd like to add a +1 here for VLC memory leak on X86_64 Natty Beta. I added some MP3s to a playlist and when it got to a third song during playback, my machine with 6 GB of RAM slowed to the point where my mouse cursor was unresponsive. htop revealed 2 vlc processes that were using 7 GB of ram and swap was being used.


Been having the exact same problem, also using 64bit natty.

---

### Post by Immerse on 2011-04-16
Yeah, same problem here.
I had to turn the computer off to get control back.

+1 for a fix :)

---

### Post by gragnar on 2011-04-16
uname -a
Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

Vlc plays some files (Codec: MPEG-4 Video (XVID))

but for example another file that looks like it could be Windows Media coded did not play but just started eating up memory.

Am now playing 2 Codec: MPEG-4 Video (XVID) files at the same time with no problem each using just under 200 MB virtual.

It could be the audio codecs, I can just confirm that it depends on the file i am trying to play.

g!

---

### Post by akand074 on 2011-04-17
It actually happened again the other day, oddly enough, this time I had just had a movie paused and minimized while I was doing other things then out of nowhere my computer went almost completely unusable until I shut off vlc.

---

### Post by NightwishFan on 2011-04-17
I am going to try leaving VLC on and paused all day.

---

### Post by akand074 on 2011-04-17
> **NightwishFan said:**
> I am going to try leaving VLC on and paused all day.

Perhaps I should too! I'll try to remember what I had playing to keep the conditions the same. These things are so hard to reproduce though I wonder what causes them. Something must be triggering it that has nothing to do with something the user is doing or anything that can be controlled.

---

### Post by NightwishFan on 2011-04-17
I will keep you guys posted and try a few things out. I am on Debian though so it is likely compiled differently.

---

### Post by baytuni on 2011-04-17
+1 here. It happens occasionally and cannot reproduce it at will.

DistroRelease: Ubuntu 11.04
Package: vlc 1.1.9-1ubuntu1
ProcVersionSignature: Ubuntu 2.6.38-8.42-generic 2.6.38.2
Uname: Linux 2.6.38-8-generic x86_64
Architecture: amd64
Date: Sun Apr 17 17:59:26 2011
InstallationMedia: Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
ProcEnviron:
 LANGUAGE=en_US:en
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage: vlc
UpgradeStatus: Upgraded to natty on 2011-04-11 (6 days ago)

---

### Post by NightwishFan on 2011-04-17
Has not gained a megabyte overnight, even through a suspend/resume. I think it must be a specific problem or it is only in the Ubuntu build.

---

### Post by Artemis3 on 2011-04-20
I think this happened to me once when i started playing games and left a vlc video paused. So when i need to leave VLC minimized (say, a long playlist), i make sure to leave it stopped. I currently have a VLC running in this state for like two weeks (watching episodes from time to time), and it currently shows 59m of ram used (v1.1.7); 64 bits, nvidia stock driver.

---

### Post by David Tomic on 2011-04-24
This has been happening pretty frequently to me as well.  Ubuntu 11.04 x64.

I've got 8GB of RAM in this system, and it normally sits on ~2.5GB used.

When VLC decides to go crazy the RAM shoots up to 100% usage [very quickly], and then my swap space starts getting eaten up as well.

If the swap space fills up completely, then the whole system basically becomes completely unresponsive, and I need to do a hard reset in order to get it running again.

If I can catch it before that happens though, and manage to kill the VLC process, then my memory usage drops back to normal, but any swap space that's been eaten up stays like that until the next time I reboot.

I've basically had to give up on using VLC until this gets resolved ...

---

### Post by baytuni on 2011-04-24
David Tomic described the problem beautifully.

---

### Post by David Tomic on 2011-04-24
FWIW ... I've just found a LP bug report for what looks like the same problem.

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/743323](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/743323)

It hasn't actually been confirmed yet though, so if there's any more information you're able to add to the ticket, it might help with getting it identified/resolved faster.

---

### Post by Cas07 on 2011-04-24
This memory leak problem with VLC was fixed a last year in Maverick but it seems to be a regression with Natty. 

I have had this a few times recently but as I know that its VLC chomping through all my ram then into my swap, I get to console or alt-f2:
> 
pkill -9 vlc 


Note:You have being really patient with the slow desktop refreshing.

Afterwards I clear the swap back to ram:
> sudo swap off -a
sudo swap on -a

---

### Post by solitaire on 2011-04-30
I upgraded my laptop from 10.10 to 11.04 yesterday and had this problem twice!
I'm running the 32bit
I've 1Gb ram and 1Gb swap.

---

### Post by manzdagratiano on 2011-04-30
I am a fellow victim, put to shame in front of my Fiancee, to who I continually preach the Ubuntu, while watching a movie through HDMI.

---

### Post by sandyd on 2011-04-30
Its happened before here on gentoo as well.

For some videos, VLC doesn't play anything - it just sits there, and begins gobbling up CPU and RAM. It doesn't get far though, since im using a PaX enabled kernel (which subquentially killed the vlc process).

For other videos, it just eats up Gigabytes of RAM. I don't understand how my 1080p friday video can use less memory than a 480p movie.:confused:

However, it hasn't happened once since I upgraded to VLC 1.1.9

---

### Post by psyentist88 on 2011-05-02
I am having the same problem as David Tomic since I updated my Ubuntu 10.10 system to 11.04 (x64).

---

### Post by Legendary_Bibo on 2011-05-02
So I added the VLC PPA and updated to 1.1.9 and now it works flawlessly. Mplayer is generally smoother at play back, but VLC is better than mplayer at playing 1080p videos.

---

### Post by ivanovnegro on 2011-05-03
Ok, Im onboard, i saw this now twice on my system, Kubuntu Natty 32 bit with latest VLC 1.1.9 from repos. The last time it happened I had to make a hard reboot of my system.

---

### Post by NightwishFan on 2011-05-03
Well, if you notice this bug, make sure to give us some details. I can no longer reproduce it after many times using vlc so ill need some outside info.

What type of codec/container of the file the bug occured with, what version of vlc. What video and audio output plugin, what graphics card etc..

---

### Post by ivanovnegro on 2011-05-03
Ok, version 1.1.9 like said yet.
It was an MP3 file, I paused it, later I seeked forward and noticed that my system was going crazy, looked at the system monitor and VLC increased the memory usage drastically, wanted to exit/kill VLC but the system freezed totally, I was out of RAM and even the Swap was used to the maximum.
I use an Intel integrated graphics card on an HP 6730s notebook with 1.9 GB of RAM.
Audio output in VLC is set to standard (I suppose Pulse, not sure), video output also set to standard, just what I always had and never had any issue before at least not that I am aware of it.

---

### Post by NightwishFan on 2011-05-03
> **ivanovnegro said:**
> Ok, version 1.1.9 like said yet.
It was an MP3 file, I paused it, later I seeked forward and noticed that my system was going crazy, looked at the system monitor and VLC increased the memory usage drastically, wanted to exit/kill VLC but the system freezed totally, I was out of RAM and even the Swap was used to the maximum.
I use an Intel integrated graphics card on an HP 6730s notebook with 1.9 GB of RAM.
Audio output in VLC is set to standard (I suppose Pulse, not sure), video output also set to standard, just what I always had and never had any issue before at least not that I am aware of it.

I did not mean just you specifically. However I am interested in this bug. :)

Cross referenced with mine, I believe I had a video, but it likely had mp3 audio. I also have an Intel integrated so that is another similarity. Again I too was using the pulseaudio output. The seeking is interesting. Vlc always have trouble seeking compared to gstreamer based players, so perhaps that might have something to do with it. *goes off to do research*

Well apparently this issue might have something to do with pulseaudio.  Perhaps try using the alsa plugin for now? And see if we can't reproduce this using that.

---

### Post by ivanovnegro on 2011-05-03
> **NightwishFan said:**
> I did not mean just you specifically. However I am interested in this bug. :)

Cross referenced with mine, I believe I had a video, but it likely had mp3 audio. I also have an Intel integrated so that is another similarity. Again I too was using the pulseaudio output. The seeking is interesting. Vlc always have trouble seeking compared to gstreamer based players, so perhaps that might have something to do with it. *goes off to do research*

Well apparently this issue might have something to do with pulseaudio.  Perhaps try using the alsa plugin for now? And see if we can't reproduce this using that.

Thanks, will test it, just wanted to change to Alsa to see.
Tried also SMPlayer, no issues, especially seeking is great, without to increase the CPU, what VLC also does in my case.

---

### Post by akand074 on 2011-05-03
> **NightwishFan said:**
> Well, if you notice this bug, make sure to give us some details. I can no longer reproduce it after many times using vlc so ill need some outside info.

What type of codec/container of the file the bug occured with, what version of vlc. What video and audio output plugin, what graphics card etc..

I haven't had it in a while either. Then I updated to Natty and haven't had it on there either. Not sure if it'll eventually come up. I think most of the time it happened to H264 with an MKV container. Might have also happened to a VC1 codec once.

---

### Post by ivanovnegro on 2011-05-03
Hm, I cannoth reproduce it again right now, changed the output, at the moment its still ok.

---

### Post by maximus5 on 2011-05-03
+1
identical problem. I've been trying everything to reproduce it at will..but cant..happens to me almost on a daily basis..though I spend much of the day with VLC and Avidemux, searching through and re-encoding videos. Avidemux is ruled out as its not always open when RAM & SWAP hit 100%. Wish I could figure out how to reproduce at will..it's getting annoying!

Natty 64bit, VLC 1.1.9
Dual mon on ATI Radeon HD5670, proprietary drivers
Default audio and video outputs with VLC.

---

### Post by Wirshlitza on 2011-05-03
Ubuntu 10.04 here, VLC 1.0.6. The only time VLC starts eating my memory, is when I turn off my WiFi connection on my laptop! It doesn't start immediately, but that is the only time it happens. Playback stops (whatever it's playing), and RAM usage starts going up, and up, and up, until all is gone, and then eats swap, until it's gone to. By that time VLC alone crashes, and memory drops back to normal. Also, CPU jumps to 100% during this time.

I'm using HP Compaq Presario CQ62, Intel Celeron 1.6GHz, 2G RAM, integrated graphics.

Perhaps this could be of some sort of use when tracing this leak? Besides this, VLC works flawlessly, sometimes hours on end.

---

### Post by El_Belgicano on 2011-05-04
+1 vlc leaking.
It all happens randomly, sometimes shifting backward and forward a lot goes fine, sometimes just playing an avi fills my 4g RAM in the blink of an eye, vlc exits and everything returns to normal.

(using 1.0.6 in Lucid at the moment, but I'm planning on using the lucidbleed ppa to get 1.1.9)

Something I came across while googling: [***LINK***]("http://www.andymillar.co.uk/blog/2010/03/17/limiting-vlc-memory-usage/")
```
#!/bin/bash
source /etc/profile
ulimit -v 1048576
vlc
```
or:```
. /etc/profile; ulimit -v 1048576 && vlc $*
```
Could this be (half) a solution at least to avoid the unstable behavior of the computer while vlc is eating memory??
Any comment on these commands could be nice, someone using them maybe?

Thanks

---

### Post by handy on 2011-05-04
Never.

---

### Post by TeoBigusGeekus on 2011-05-04
Could [this]("http://www.h-online.com/security/news/item/VLC-Media-Player-vulnerable-to-buffer-overflow-exploits-1237404.html") be related?

---

### Post by akand074 on 2011-05-04
> **TeoBigusGeekus said:**
> Could [this]("http://www.h-online.com/security/news/item/VLC-Media-Player-vulnerable-to-buffer-overflow-exploits-1237404.html") be related?

Probably the best explanation we've got so far. Could be this.

---

### Post by red_five on 2011-05-11
Running Maverick x86_64 here, Core 2 Duo 2.4GHz, 8GB RAM and 16GB swap. All I have to do to replicate the issue is load up VLC 1.1.8 and fill the playlist with lots of video clips. Within a minute or 2 it chews through 8GB RAM and starts on my swap, which brings the whole laptop to a dead stop. If I kill VLC just before it reaches max RAM usage, it clears itself up just fine. I don't even have to be playing anything, just load lots of video clips (could be music files as well, haven't tried), sit back and wait for the fireworks.

---

### Post by Warpnow on 2011-05-11
And...the people on the Oneiric board are all suggesting VLC be default...

---

### Post by Oxwivi on 2011-05-11
> **Warpnow said:**
> And...the people on the Oneiric board are all suggesting VLC be default...
VLC?! No way! Subtitle support sucks on VLC, MPlayer FTW!

---

### Post by El_Belgicano on 2011-05-11
Upgraded to 1.1.9, and still getting the fireworks fill up the ram.

---

### Post by akand074 on 2011-05-11
> **Oxwivi said:**
> VLC?! No way! Subtitle support sucks on VLC, MPlayer FTW!

I honestly love VLC. I always use it as a default for all my videos. I just find it simple and clean and runs every video well. I have a source built MPlayer fully built with all the codecs/libraries you can imagine as a backup though. Mplayer is great, don't get me wrong (better than VLC even in terms of functionality) but I still prefer VLC. Totem in gnome 3 is getting pretty nice. I can't wait until 11.10.

> **El_Belgicano said:**
> Upgraded to 1.1.9, and still getting the fireworks fill up the ram.

I haven't had the issue since natty. Though I haven't really been watching enough videos I suppose to run into the problem.

---

### Post by ivanovnegro on 2011-05-11
Im subscribed to the VLC issue on Launchpad and the problem is known, the devs want to fix it as soon as possible and yes, Pulse is the problem, as a workaround switch to Alsa.

---

### Post by Exile09 on 2011-05-15
> **ivanovnegro said:**
> Im subscribed to the VLC issue on Launchpad and the problem is known, the devs want to fix it as soon as possible and yes, Pulse is the problem, as a workaround switch to Alsa.

I found this topic before finding this: [http://forum.videolan.org/viewtopic.php?f=13&t=90153](http://forum.videolan.org/viewtopic.php?f=13&t=90153)

I was also having this problem but I've switched the audio in VLC to Alsa and had no problems so far. I'll post here if I have any more trouble.

I had this problem on 64 bit versions of 10.10 and 11.04 btw.

---

### Post by ivanovnegro on 2011-05-15
> **Exile09 said:**
> I found this topic before finding this: [http://forum.videolan.org/viewtopic.php?f=13&t=90153](http://forum.videolan.org/viewtopic.php?f=13&t=90153)

I was also having this problem but I've switched the audio in VLC to Alsa and had no problems so far. I'll post here if I have any more trouble.

I had this problem on 64 bit versions of 10.10 and 11.04 btw.

The problem is also that the dev version 1.2 seems to have problems with Pulse on all distros that uses this as default, that was a message of today. They are still considering to switch to Alsa.

---

### Post by Exile09 on 2011-05-15
Hmm I think there's something else to this.

I have 'ASLA AUDIO OUTPUT' set in my vlc audio settings and I'm still having problems with this.

This problem is so serious I completely run out of ram and swap and end up with a near impossible to use machine (until I kill the power or have a lot of patience and try and kill the process). My hard drive has taken a battering just working out what this is, I couldn't even open a terminal to find out what was going on!

And this is just with a 128k audio stream!

---

### Post by ivanovnegro on 2011-05-15
> **Exile09 said:**
> Hmm I think there's something else to this.

I have 'ASLA AUDIO OUTPUT' set in my vlc audio settings and I'm still having problems with this.

This problem is so serious I completely run out of ram and swap and end up with a near impossible to use machine (until I kill the power or have a lot of patience and try and kill the process). My hard drive has taken a battering just working out what this is, I couldn't even open a terminal to find out what was going on!

And this is just with a 128k audio stream!

You should report this on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/743323"), hell that sounds really bad if it happens also with Alsa.

---

### Post by timZZ on 2011-05-15
On my IBM machine yes! but it is quite old now.

---

### Post by Exile09 on 2011-05-16
> **ivanovnegro said:**
> You should report this on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/743323"), hell that sounds really bad if it happens also with Alsa.

Thanks for the link. I reported this and I got an answer I wasn't expecting!

[QUOTE=Rémi Denis-Courmont]All VLC 1.1.x versions are affected by this bug (memory leak and audio stops) by default. In VLC 1.2.x development as of today, this problem is "fixed", but audio sync is quite poor. In versions 1.0.x and older, VLC will use ALSA by default; this might work if the PulseAudio ALSA plugin is installed and configured adequately, or it might not work (as you saw @Alex C). This option is also available in versions 1.1/1.2 from the preferences, just no default.

We have asked for help from the PulseAudio guys but did not get much (so far). This is surprising, given none of the professional PulseAudio guys care about VLC (and the main author is busy wiith systemd), and the hobbyist PA guys are busy.

We have asked for help from Ubuntu and got nothing. This is also not surprising as the Debian/Ubuntu multimedia maintainers are busy hobbyists, and are not (a priori) audio/PulseAudio specialists.

For the time being, and unfortunately also for the foreseeable future, I can only recommend using ALSA adn hope it works.
[/QUOTE]

That is really bad news :icon_frown:

---

### Post by blackbird34 on 2011-05-22
> **manzdagratiano said:**
> I am a fellow victim, put to shame in front of my Fiancee, to who I continually preach the Ubuntu, while watching a movie through HDMI.

   hahaaaaaa =)  Me too, well nott my fiancée but three friends... bloody leak. I'm never pausing anything in that player again. Pian, it's the best one around...

---

### Post by Shabakthanai on 2011-05-22
> **akand074 said:**
> Hey guys, just recently (as of maybe 3 or 4 days ago?) VLC has been having a massive memory leak. It's only happened to me when I skip through a video on occasion but my RAM usage jumps to ~98% and my whole system becomes almost unusable. I close VLC and then within a few seconds it drops back to ~18% of my 6GB of RAM. I run VLC again and everything is fine.

I'm not really looking for a solution, it's not really a big deal to me right now so I posted in these forums. I'm just wondering if anyone else is getting this? Might have been due to an update. I'm using the VLC right from the repositories in Maverick. I was pretty surprised the first time it happened.

[COLOR="DarkRed"]I am and have been having similar problems.  A friend who has been one of the better helpers for kubuntu users has recently removed Kubuntu because he says this memory problem is related to Nepomuk and perhaps Strigi.  I don't know, because I am not so experienced, however I have removed Maverick, installed and removed Mint 10, and now am having an occasional problem with Natty right now.  It caused me to enter this chat for the first time.  

I am not sure that is the problem, however, (and I envy your system), I also have a pretty powerful system that gets bogged down using Kubuntu related systems.  It happens when watching a movie and having any other tasking project working at the same time.  Additionally, I recently had personal folders opening by the Rekonq browser which doesn't make any sense.  I was typing in search informations and expected google, at the least, or the site I wanted at best.  Seeing my private material exposed when I am attempting an Internet search is and was disquieting.

It looks like Kubuntu is trying to make things happen instantly using the new procedures for finding information.  It concerns me, in that, if it causes access to personal files when surfing the Internet, it seems insecure when on the Internet.  I am probably paranoid for no cause, however, I do not want to trade my privacy for speed.  And I love the faster operations.

I tried PCLOS and did not like it because it seemed like they were making moral decisions for me.  I don't view porn or steal video, but because those are natures that PCLOS seems to prefer to control, it also inhibits the proper usage of the system while they are being moral monitor.

I really like the special effects that Kubuntu provides, and am grateful for being able to use such a fine system for such a long time, but I hate it when the computer takes over memory to provide services I do not want or need and causes me to have to hard-shut-down to get control of my computer back.  That is what seems to be happening with the Kubuntu related OS's that I have tried to use lately.

Most cutting edge technology is desirable to me, but not technology that takes control of my computer.  It seems that if I install a relatively current edition of Ubuntu KDE it only takes about a month before I am having to remove the OS because of memory abuse.

If this finally drives me away from Kubuntu, I would like to thank them for the years I have enjoyed, and hope the new stuff ends up practical and useful for other users.[/COLOR]

---

### Post by ivanovnegro on 2011-05-23
@Shabaktanai: I dont understand really your problem, if you dont like these services just disable them, thats all and you could speed up your system. I dont see anything security related here.
Also you could use another Ubuntu spin if you like.
The memory leak in VLC is not only a primary Ubuntu problem even if it is realted somehow. The devs of VLC are working on the issue.

---

### Post by tjeremiah on 2011-06-10
A new version has been released. VLC 1.1.10 (for Natty only).

---

### Post by lovinglinux on 2011-06-11
I am not sure if it is the same problem, but I have been experiencing weird issues with VLC more than once, while watching a DVD. Suddenly the video freezes and VLC goes crazy, using a lot of CPU and memory.

I actually use smplayer, but sometimes some DVDs don't work with it, so I use VLC then.

---

### Post by NightwishFan on 2011-06-11
That is the problem exactly. In some cases that is libdvdcss2, but since the dvd was working I am thinking it is not css. Are you using the pulse plugin?

---

### Post by lovinglinux on 2011-06-11
> **NightwishFan said:**
> That is the problem exactly. In some cases that is libdvdcss2, but since the dvd was working I am thinking it is not css. Are you using the pulse plugin?

I don't think so. I just installed vlc package.

BTW, when that happens, the system becomes unusable until I manage to kill vlc. But then, if I start the movie from where I stopped, it plays normally. It is really weird.

---

### Post by ivanovnegro on 2011-06-11
> **lovinglinux said:**
> I am not sure if it is the same problem, but I have been experiencing weird issues with VLC more than once, while watching a DVD. Suddenly the video freezes and VLC goes crazy, using a lot of CPU and memory.

I actually use smplayer, but sometimes some DVDs don't work with it, so I use VLC then.

VLC 1.1.10 came out recently and it seems they fixed the issues we were talking about here, I did not try it yet.

---

### Post by fremantle on 2011-06-12
which version is it in natty repo?

---

### Post by NightwishFan on 2011-06-12
> **fremantle said:**
> which version is it in natty repo?

1.1.9-1ubuntu1.1

---

### Post by akand074 on 2011-06-12
I haven't had the issue since I've installed Natty (using 1.1.9). Though, I've very recently been getting minor lag when fullscreen/cancel full screen for a few seconds. If it's fixed in 1.1.10 then the problem should be gone in 11.10's repots. If the problem ever comes back I may add the VLC ppa but otherwise I should be good. 

For curiosity's sake, has anyone had the issue in the stable release of Natty (i.e not during beta/pre-beta when I read some complaints here).

---

