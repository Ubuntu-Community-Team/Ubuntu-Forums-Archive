---
title: "Audio skips or stutters in Lucid"
date: 2010-05-03
forum: System76 Support
---

### Post by gruntlips_ on 2010-05-03
Hi,

Installed 10.04 on my serval and everything seems to work great, except for one thing - audio stuttering.

Again, this is the same problem I had in 9.10 and I have it again in 10.04. When I play mp3 files or video in banshee, rhythmbox, mplayer, or vlc the sound skips/stutters randomly during the song (every 30 sec to 1 minute). I haven't noticed any spikes in memory usage during playback when the stuttering occurred and my total system memory being used was pretty reasonable (<20%) during the time when bashee was doing this. I installed the following codecs and programs after the 10.04 install:

sudo apt-get install ubuntu restricted extras
sudo /usr/share/doc/libdvdread4/install-css.sh
sudo apt-get install mplayer smplayer
sudo apt-get install vlc vlc-plugin-pulse

The stuttering started right away after a fresh install of 10.04 and has persisted since. When I had this probkem in 9.10, I removed pulse audio by following the instructions from vortex pusher [http://ubuntuforums.org/showthread.php?t=1368141&page=2](http://ubuntuforums.org/showthread.php?t=1368141&page=2) (below). If I do this the stuttering stops, suggesting pulse audio is the source of the problem.

sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio

However, I don't like this solution for a few reasons. 1) Pulse is part of ubnuntu, canonical clearly does not seem like it is getting rid of it, and it seems reasonable that I should be able to make my OS work correctly, especially on a fresh install. 2) Pulse is nicely integrated with my desktop allowing me to easily control volume using the fn keys and other sound aspects from the applet on the top panel. This works out of the box and I like this. It is convenient and user-friendly. When I removed pulseadio in 9.10, I installed the ALSA mixer applet but it was clunky and annoying in comparison. 3) Sounds simply sounds better with pulse (minus the stuttering). It is louder, richer, and fuller. I don't have to screw around with command line settings for gain etc. 4) Skype video cam works out of the box with 10.04 with the default pulse audio settings. I don't have to mess with anything to make it go. For me, that is huge, and I don't want to push over the apple cart. 5) After removing pulse audio in 9.10, my top panel developed some random annoying behavior such as moving around the applets every time I booted up or not loading the networks applet at all unless I logged out and logged back in.

I have read about tweaking the default-fragments and default-fragment-size-msec default values in the file /etc/pulse/daemon.conf at [http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio+guide](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio+guide). I have experimented with different values and this seems to reduce the stuttering somewhat, but not eliminate it. The guide suggests values are sound card specific. Which brings me to my question for the past 6 months:

### How can I fix this audio stuttering while keeping pulse intact? ###

I am hoping someone from system76 might know of a solution or at least help me troubleshoot. I emailed the system76 tech support after posting this issue here previously but haven't heard anything. I am wondering if the issue involves some way my serval sound card, an HDA Intel Realtek ALC268, is interacting with pulse and if system76 has encountered this before.

I don't want this to be perceived as a rant but audio functioning correctly is a big deal, and is something, at this stage in ubuntu's development, should simply just work (with minor tweaking, of course [*grin*]).

Any suggestions on how I can fix this?

I appreciate it!

- Chris

My specs:
10.04
Serval System76 laptop (serp4)
Core2 Duo 2.5o GHz
nVidia GeForce 8600M GT
HDA Intel Realtek ALC268
4GB ram

---

### Post by Wheel_nut on 2010-05-03
I have the same symptoms on a ThinkPad X21 with a clean installation of Lucid 10.04.

Audio stutters with ALL sound including the start-up tune.

---

### Post by gruntlips_ on 2010-05-03
Wheel_nut, I feel your pain.

---

### Post by Wheel_nut on 2010-05-03
Hi Gruntlips, I wish I could understand the techspeak enough to try one of the options you have described.

I hope there is an update to fix this soon. 

Would a downgrade to a previous release .... or a previous Kernel fix this more easily?

---

### Post by gruntlips_ on 2010-05-03
I am not sure if that would help since I don't know what is causing this. I had this problem in 9.10 and 10.04 so it is not specific to lucid. Maybe there is a way to configure pulse that I am just not doing correctly.

- Chris

---

### Post by bandersen on 2010-05-04
bump, same!

---

### Post by isantop on 2010-05-04
gruntlips_:
Are you getting a skipping-type error, like a skipping CD, or is it more like a pop? Also, can you hear it happening all the time, or only during playback? Does it change with different volume levels, or is it always constant?

---

### Post by gruntlips_ on 2010-05-04
Skipping sound, not popping. It happens during audio playback on any of the music players, video playback on mplayer or vlc, within firefox, while watching youtube for instance, in skype (I think), and also during startup sometimes.  It does not happen all the time, but only during playback. It is intermittent and the frequency of the stuttering is not constant. It occurs at all volume levels with the skipping being louder at higher volume. Do you have a similar problem?

- Chris

---

### Post by bandersen on 2010-05-04
i have had the exact same problem for a while BUMPBUMP

---

### Post by gruntlips_ on 2010-05-05
Thomasaaron, I know you are always swamped but I was hoping you might have some advice for fixing this audio problem. It is not as though there is a lack of "solutions" floating around here on the forums, but there does not appear to be any kind of consensus and many involve beheading pulse in some fashion or another. Have you guys noticed this issue on system76 computers?

Thanks! I feel like if I can figure this audio problem out then 10.04 on my serval will simply rock.

- Chris

---

### Post by ArnoDF on 2010-05-05
I had the same problem but also with video. Totem seemed to work without  problems but vlc and exaile are a real pain; increasing the buffer in  vlc didn't help. As you suggested the problem is caused by pulseaudio  and I've been able to solve the problem with audio with the tool that  has saved me from many problems in the past:
```
sudo dpkg-reconfigure pulseaudio
```


This may be to soon to tell but reconfiguring pulseaudio also seems to  solve the video problem

Hope this helped for you, chrz

---

### Post by mbuller10 on 2010-05-05
same problem bump lots of people have this problem bump to Canonical

---

### Post by thomasaaron on 2010-05-06
Hi, gruntlips_.

I think this is a pulseaudio bug. Here's a pretty good (though unresolved) post on it. If I'm correct, the problem should eventually be fixed by upstream devs.

```
touch ~/.pulse-a11y-nostart
echo autospawn = no|tee -a ~/.pulse/client.conf
killall pulseaudio 
```

See if that fixes it. If not, it's easy enough to undo, and we'll keep pecking at it. So far, I've not noticed this problem, but we can certainly do some additional testing tomorrow or Monday.

---

### Post by bandersen on 2010-05-06
I fixed my problem by removing my pci sound card, and going back to my board for sound.

---

### Post by gruntlips_ on 2010-05-06
Thanks ArnoDF, bandersen, and Thomasaaron.

Thomasaaron, I was wondering what exactly those commands do. It seems like they kill pulse. Is this the current working solution? I was hoping to avoid that, but if this is the only solution then so be it. Also, you mentioned a posting for this bug but didn't provide a link. I was hoping you wouldn't mind sharing that so we could follow this bug.

Based on the fact that this only appears to be affecting certain users and bandersen's fix of going back to his onboard sound, could the issue perhaps lie in how pulse interacts with certain sound cards?

I think this problem has been kicking around for at least 6 months and I'm surprised there hasn't been a bigger push to fix this. While not a deal-breaker for me for using ubuntu, sound skipping in all my video and audio applications is pretty damn annoying. I am a fan of the 10.04 additions and enhancements, but I would definitely take sound that works over most of them.

I'll try your suggestions thomasaaron and post what happens. Thanks again.

- Chris

---

### Post by Samsonite71 on 2010-05-07
I have the same problem with audio studders. Been trying to resolve this by googling for a few days but it seems like the only solution is to disable pulseaudio.

Anyway, it is a problem, lots of posts around this floating around and it all seems to come down to this.

---

### Post by mbuller10 on 2010-05-07
I spent many hours over several days googling until I came across this,

[http://rightfootin.blogspot.com/2009...rs-pauses.html](http://rightfootin.blogspot.com/2009...rs-pauses.html)

This was an old post for 9.04 so I modified it a little I added 

tsched=0 to the line #load-module module-alsa-source device=hw:1,0 

although I don't think that did anything

and changed

realtime-priority = 5 to 8

then did 

sudo dpkg-reconfigure pulseaudio

then restarted

this greatly reduced the stuttering and the severity of the stuttering

---

### Post by thomasaaron on 2010-05-07
> Thomasaaron, I was wondering what exactly those commands do. It seems like they kill pulse. Is this the current working solution? I was hoping to avoid that, but if this is the only solution then so be it. Also, you mentioned a posting for this bug but didn't provide a link. I was hoping you wouldn't mind sharing that so we could follow this bug.

Sorry, I forgot to post it. It's here...
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/311853](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/311853)

I don't know if killing pulse and keeping it from respawning is the only fix, but it's the only one I've found so far... if it works, that is.

You might try  mbuller10's fix as well.

---

### Post by gruntlips_ on 2010-05-07
OK, in detail based on mbuller10's post and his link.

1) I have several files in /etc/pulse. One is system.pa and appears to be the pulse settings for when ubuntu is loaded in system mode. I have another file called default.pa for when ubuntu is loaded in per-user mode. In the default.pa there is a line for load-module module-alsa-source device=hw:1,0 but it is commented out. So adding an argument to this would not do anything (unless mbuller10 uncommented the line and just made a typo in their post). See below:

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

However, There is nothing below for using model-hal-detect in default.pa.

In the system.pa there is a line for load-module module-hal-detect but I think when I boot up it is into per-user mode so I wonder if this program ever runs. Nevertheless I added tsched=0 to the load-module module-hal-detect lone below:

## Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

2) audio, pulse-access, and pulse-rt groups do not exist so I am ignoring this step.

3) Because there is no pulse-rt group I did not add the following lines to /etc/security/limits.conf

@pulse-rt       -       rtprio          99
@pulse-rt       -       nice            -20

4) Changed realtime priority from 5 to 8 in /etc/pulse/daemon.conf

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 8

; exit-idle-time = 20
; scache-idle-time = 20

5) Ran sudo dpkg-reconfigure pulseaudio which, I assume, is equivlent to pulseaudio -k ; pulseaudio -D?

6) Restart!

7) Sacrificed a young goat to the ubuntu gods. My office mates are not amused...

And...

No real change. Still skips, maybe slightly less but enough to make you want to get out a walkman. Video stutters as well too.

OK, on to disabling pulse.

---

### Post by gruntlips_ on 2010-05-07
Thomasaaron, according to that bug post (and I am horrible at deciphering these things) I think Daniel Chen says this bug is supposed to be fixed in the current version of pulseaudio. However, that does not seem to be true. Perhaps it might be worth investigating the sound card driver system76 uses. According to Cliff10^6 on this post, "there is something wrong with the Intel Realtek ALC889A sound Driver which is updated in the new kernel" and suggests switching to a generic kernel. My card is the Intel Realtek ALC268 but it could have a similar problem. This is largely beyond me, so I am pointing this out mostly to generate discussion.

In any case, your three commands above worked. I disabled pulse and they problems go away and pulse does not respawn. Now, I cannot seem to:

1) Change change my volume controls with the fn F7,F8
2) Find a config menu in preferences for alsa and an applet for the top panel so I can switch inputs, outputs etc
3) Change the loudness. When under pulse I could keep the volume around 1/2 and it was plenty loud. Now, I put it up all the way and it is not loud enough.

Any suggestions on how to restore this functionality?

Thanks,

- Chris

---

### Post by mbuller10 on 2010-05-07
> **gruntlips_ said:**
> Thomasaaron, according to that bug post (and I am horrible at deciphering these things) I think Daniel Chen says this bug is supposed to be fixed in the current version of pulseaudio. However, that does not seem to be true. Perhaps it might be worth investigating the sound card driver system76 uses. According to Cliff10^6 on this post, "there is something wrong with the Intel Realtek ALC889A sound Driver which is updated in the new kernel" and suggests switching to a generic kernel. My card is the Intel Realtek ALC268 but it could have a similar problem. This is largely beyond me, so I am pointing this out mostly to generate discussion.

In any case, your three commands above worked. I disabled pulse and they problems go away and pulse does not respawn. Now, I cannot seem to:

1) Change change my volume controls with the fn F7,F8
2) Find a config menu in preferences for alsa and an applet for the top panel so I can switch inputs, outputs etc
3) Change the loudness. When under pulse I could keep the volume around 1/2 and it was plenty loud. Now, I put it up all the way and it is not loud enough.

Any suggestions on how to restore this functionality?

Thanks,

- Chris

That's basically what I did, and what all the other threads say to do but that stops volume buttons hot keys misc games and app to all stop working so I don't want to disable pulse, the solution I posted did help reduce the skipping to about once every 3 songs I play with rhythmbox

---

### Post by gruntlips_ on 2010-05-07
mbuller10,

Yea, I agree with you completely. That was the reason behind my original post - fix stuttering audio without disabling pulse. The solution to remove pulse is not a great solution. It works, but it is kind of like when your driver side door doesn't open anymore and you wind up crawling in every morning from the passenger side while trying to avoid spilling coffee everywhere.

I posted here because it seems that since everyone is not experiencing this problem, it is logical that tinkering with the pulse software or audio driver might solve the problem. If I do a fresh install on my machine, sudo apt-get restricted-extras, and the sound skips straight away and someone else does the same thing on a different machine and it does not skip, then a strong candidate what is going wrong is that ubuntu does not get along with my hardware somehow. System76 sells computers whose components are made to work with ubuntu. Well, perhaps my sound card does not (or at least, hasn't since 9.04). I would be happy to let them use my computer as a guinea pig to try and figure this out.

---

### Post by gruntlips_ on 2010-05-08
Here is a helpful and related post. It seems that the consensus is removing pulse is the thing to do. In this post are some helpful hints about restoring some of the sound functionality that ubuntu ships with in without pulse.

[http://art.ubuntuforums.org/showthread.php?t=1313253&page=14](http://art.ubuntuforums.org/showthread.php?t=1313253&page=14)

- Chris

---

### Post by akwala on 2010-05-08
The stuttering/skipping started happening on my System76 Serval after upgrading to Lucid.

According to the following comment on [Bug #476652]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/476652"), the problem is most likely fixed in kernel v. 2.6.34: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/476652/comments/50](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/476652/comments/50)

Also see:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/571464](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/571464)

---

### Post by mbuller10 on 2010-05-08
So I guess we just wait for the new kernel to be released?

---

### Post by nightawk on 2010-05-09
Same problem here. Everything worked fine under 9.10, but sound and video playback is erratic (to say the least) under Lucid. Have just repeated a clean install in case I'd inadvertently introduced some kind of conflict, but it's as bad as ever. The only pattern I can detect is that video will often play OK for around 50 secs before the stuttering starts. Lucid feels very polished in other ways, it's a shame this gremlin has crept in.

---

### Post by thomasaaron on 2010-05-10
It would be interesting to see how many of you upgraded vs. did a fresh install. I'm not seeing this on our shop Serval.

---

### Post by gruntlips_ on 2010-05-10
I did a fresh install of both 10.04 and 9.10 and had the problem right away. I installed a few codecs etc first in both cases (see original post).

---

### Post by mbuller10 on 2010-05-10
When I use VLC and under tools audio preferences change the output to OSS no more video or audio skipping under VLC, by the way I did a fresh install and this is the only partition I have

---

### Post by gruntlips_ on 2010-05-10
Thomasaaron, how do I reverse the commands you gave to disable pulse so I can mess around with this some more?

You wrote:

touch ~/.pulse-a11y-nostart
echo autospawn = no|tee -a ~/.pulse/client.conf
killall pulseaudio

Thanks,

- Chris

---

### Post by akwala on 2010-05-10
> **thomasaaron said:**
> It would be interesting to see how many of you upgraded vs. did a fresh install. I'm not seeing this on our shop Serval.
Mine was a 9.10 ->10.04 upgrade.

---

### Post by isantop on 2010-05-10
> **gruntlips_ said:**
> Thomasaaron, how do I reverse the commands you gave to disable pulse so I can mess around with this some more?

You wrote:

touch ~/.pulse-a11y-nostart
echo autospawn = no|tee -a ~/.pulse/client.conf
killall pulseaudio

Thanks,

- Chris

To keep fiddling, run
```
rm ~/.pulse-a11y-nostart
rm ~/.pulse/client.conf

```
then reboot your machine to undo these changes.

EDIT:
I've got a Serval (Serp6) in the shop here, and I'm not getting any skipping at all. In fact, this is probably the best sound I've ever heard from a laptop. That said, the concensus here seems to be to try a fresh install. There are so many things that could go wrong with an update, and thanks to our default partitioning scheme, you shouldn't need to backup your data. (But you should, for those just-in-case moments.)

---

### Post by gruntlips_ on 2010-05-10
Isantop, I did do a fresh install. There are multiple folks posting here about this problem and I think akwala had done the upgrade. I did a fresh install to 9.10 and 1.04 and had the problem both times.

So, if you cannot replicate this on your serval in the shop then perhaps the issues is with how my card interacts with ubuntu? Or perhaps the driver? Is there something I can post from any of my config files etc. to assist with figuring this out?

Thanks for the tip on kicking it back to pulse. If you want to see what I did that started this whole thing look at the first post in this thread.

Thanks.

- gruntlips

---

### Post by mbuller10 on 2010-05-11
with all the latest updates no more stuttering skipping HURRAYYY

---

### Post by akwala on 2010-05-11
> **mbuller10 said:**
> with all the latest updates no more stuttering skipping HURRAYYY
Can you list what you updated and the versions?

---

### Post by mbuller10 on 2010-05-11
I just went to update manager and installed all the latest updates. Last update was 

Upgraded the following packages:
libgdata-common (0.5.1-1) to 0.5.2-0ubuntu1
libgdata6 (0.5.1-1) to 0.5.2-0ubuntu1
nvidia-current (195.36.15-0ubuntu2) to 195.36.15-0ubuntu3
nvidia-current-modaliases (195.36.15-0ubuntu2) to 195.36.15-0ubuntu3

---

### Post by akwala on 2010-05-11
> **mbuller10 said:**
> 
Upgraded the following packages:
libgdata-common (0.5.1-1) to 0.5.2-0ubuntu1
libgdata6 (0.5.1-1) to 0.5.2-0ubuntu1
nvidia-current (195.36.15-0ubuntu2) to 195.36.15-0ubuntu3
nvidia-current-modaliases (195.36.15-0ubuntu2) to 195.36.15-0ubuntu3

Thx, mbuller10. I had the latest libgdata* but my nvidia-current* needed to be updated. Unfortunately, I don't see/hear any change after the update. The issue persists.

After less than a minute of playing w/ stutters/skips, the error described in this thread occurred (not sure if it's related):
[http://ubuntuforums.org/showthread.php?t=1479352](http://ubuntuforums.org/showthread.php?t=1479352)

---

### Post by isantop on 2010-05-11
> **gruntlips_ said:**
> Isantop, I did do a fresh install. There are multiple folks posting here about this problem and I think akwala had done the upgrade. I did a fresh install to 9.10 and 1.04 and had the problem both times.

So, if you cannot replicate this on your serval in the shop then perhaps the issues is with how my card interacts with ubuntu? Or perhaps the driver? Is there something I can post from any of my config files etc. to assist with figuring this out?

Thanks for the tip on kicking it back to pulse. If you want to see what I did that started this whole thing look at the first post in this thread.

Thanks.

- gruntlips

No problem about the tip. It may come in handy for someone else as well.

I have checked the other thread out, and it could be the issue. Go ahead and play some audio until you notice the problem, take note of the time in the clock (upper right), then open the System76 Driver (System > Administration > System76 Driver). Open the support tab and click create. Then attach the file to a reply here with the time you took down.

---

### Post by mbuller10 on 2010-05-12
okay the fix I posted before I modified a little, because after installing wine the sound problems came back

Here's what I did and it hardly ever skips

-install all the latest updates

-sudo gedit /etc/pulse/default.pa

and added tsched=0 to 

load-module module-detect

- sudo gedit /etc/pulse/daemon.conf
 
changed realtime-priority = 5 to realtime-priority = 8

---

### Post by akwala on 2010-05-12
> **mbuller10 said:**
> 
-sudo gedit /etc/pulse/default.pa

and added tsched=0 to 

load-module module-detect

This seems to have fixed it for me. Thanks!

Hopefully it'll stay fixed.

---

### Post by gruntlips_ on 2010-05-13
Isantop,

OK, this is the line I get from my syslog when the stuttering occurs. I do not know what this means.

May 13 00:09:36 coldwater-laptop pulseaudio[1420]: ratelimit.c: 4 events suppressed

I changed realtime priority as below is daemon.conf:

; realtime-scheduling = yes
; realtime-priority = 8

; exit-idle-time = 20
; scache-idle-time = 20

I added tsched = 0 to default.pa at the following line:

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect tsched=0
.endif

Ran sudo dpkg-reconfigure pulseaudio 

I still have the stuttering after I do this. I do not see any errors in the log related to pulseaudio. I attached it anyway.

- Chris

---

### Post by gruntlips_ on 2010-05-13
I found this in the user.log though when it stutters. This might be the culprit although I don't know what it means.

---

### Post by akwala on 2010-05-13
> **gruntlips_ said:**
> 
I still have the stuttering after I do this. I do not see any errors in the log related to pulseaudio. I attached it anyway.

Adding the "tsched=0" is a workaround, I think. Looks like this is an ALSA issue that still needs to be fixed. (BTW, the lines beginning w/ ';' in /etc/pulse/daemon.conf are commented out, so the realtime* values are not in play in your case -- same applies to me.)

I did hear stuttering again when I launched projectM (visualizer) when the audio was playing. Not yet sure what to attribute this to, but it suggests that the stuttering/skipping will most likely recur.

---

### Post by mbuller10 on 2010-05-13
it didn't stay fixed :( skipping is back

---

### Post by akwala on 2010-05-13
> **mbuller10 said:**
> it didn't stay fixed :( skipping is back
Mine is back too, same as before.

---

### Post by mbuller10 on 2010-05-13
I'm on the verge of going back to Karmic, I knew it was to early to install a new release

---

### Post by gruntlips_ on 2010-05-13
Karmic has the same problem. You will have to go back to 9.04 but who knows, it might be the pulse or alsa packages so it wouldn't matter what version you are using. I just want to fix this problem once and for all.

---

### Post by mbuller10 on 2010-05-14
Just reinstalled karmic, not having any issues, I had sound issues a while ago when karmic first came out but after installing the 230+ something updates and using the latest iso from the ubuntu website no more sound issues

---

### Post by ToneDispenser on 2010-05-15
Hi Folks,


Here's what I do:

```

sudo apt-get remove pulseaudio pulseaudio-module-x11 gstreamer0.10-pulseaudio libsdl1.2debian-pulseaudio pulseaudio-utils

sudo apt-get install libsdl1.2debian-alsa

```

after next boot, everything should be fine... byebye pulseaudio :P

I really don't understand this. Ever since pulseaudio came with ubuntu installations it caused trouble with certain apps or overall playback. Why is it being installed if users keep reporting crappy behavior again and again? It just sux if you install an OS and the first thing you have to do is fix something :(   I'm using ubuntu since 2004 and it has come a long way. I love it. Pulseaudio is the only nuisance and it's been around for the last three releases! That's annoying and it's a turn-off for first-timers...

---

### Post by msrinath80 on 2010-05-15
It's just a specific case here and there. For instance on my Lemur, pulseaudio has been nothing but flawless (fingers crossed).

---

### Post by gruntlips_ on 2010-05-15
I disagree msrinath80. Based on the number of hits on this thread and the number of posts and bug reports in general on pulseaudio problems it seems to be an issue for a lot of people. Canonical should resolve this because it is a black eye for ubuntu. If they have time to make a microblogging client, then they have time to make sure sound works out of the box.

- gruntlips

---

### Post by ToneDispenser on 2010-05-16
Mabye I did PulseAudio wrong with my last post. The following thread has a lot of information on the PulseAudio issue and states that it has been poorly integrated in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by akwala on 2010-05-16
I installed the latest dev ALSA driver -- repo: ppa:ubuntu-audio-dev/ppa.

$ cat /proc/asound/version
 Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 15 2010 for kernel 2.6.32-22-generic (SMP).


The problem persists.


Please report your findings on the appropriate bug reports, for instance...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545065](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545065)

---

### Post by KRopa on 2010-05-16
Hello gruntlips_, Wheel_nut, mbuller10, thomasaaron et al., and thanks for keeping this thread active.  I have been reading with interest prior to upgrading to Lucid, since I experienced issues with PulseAudio when using Ubuntu Studio 9.10, and had disabled it in favor of ASLA to resolve the issues.  PulseAudio also seemed to be the source of one of the several large memory leaks in the system, which I worked around by disabling visual effects, screen saver, and PulseAudio in turn... and stopped using the "hibernate" function.

Today I did a fresh install of Lucid on my Serval (serp5) and am lucky to report that PulseAudio hasn't turned up any issues so far.  Check my signature for information about my hardware configuration.

I was able to listen to MP3s and other audio formats for more than half an hour without encountering skips or stutters.  Video playback is fine too, for local files as well as YouTube and other Web video, though there is some problem blocking all Hulu videos, apparently related to the flash plugin as reported elsewhere.  I have also had success using Audacity to do some audio editing with little perceived latency and no issues with skipping, and without removing PulseAudio.

I'm sorry I don't have any solutions or suggestions to report, but wanted to post in response to a question of whether certain hardware setups are more prone to the problem than others.

---

### Post by SilverDragon on 2010-05-17
Hey everyone. I think I read through the entire thread and I don't think anyone mentioned how they are listening to their music.

I am also having the skipping and stuttering in Lucid which was not apparent in Karmic but only when listening through the laptop's speakers. (It might have been there but I tend to use headphones in the dorms)

When I listen through the headphone jack or use my Total Bithead USB headphone Amp/DAC the the music plays like it should.

I was wondering if anyone else had tried listening through headphones.

p.s. OP, Sweet laptop :)

edit: I just wanted to mention I always do a fresh install.

---

### Post by johnnyhop on 2010-05-17
Hi all, likewise I read through the entire post.  My PCI sound device is a C-Media Electronics CM8738 driver=C-Media PCI.  I use Lucid Kubuntu and my sound server remains OSS.  Pulse is present, but not configured as far as I can tell.  Did want to mention I do have the audio problems as described with online streaming particularly on you tube, sound will stop need to close and reopen Firefox and audio might last for to duration of the clip.  Momentary stuttering at varying intervals usually in excess of 30 seconds when playing mp3's in VLC :(but no problem with .flac files.  Didn't have this problem with Karmic or previous, been using Kubuntu since Fiesty.

---

### Post by mbuller10 on 2010-05-18
I'm just gonna wait 6 months for lucid to become stable, or I'll wait maybe.... nevaaaaa. Long Live Karmic, by the way if you uninstall pulse audio and do that switharoo with alsa then the volume control and a bunch of games Wesnoth SMC etc will not work

---

### Post by cybersamen on 2010-05-19
ok, i have used lucid for about 2 weeks now, started my linux experience with karmic 2 month's ago.
My trouble with the sound started when i installed wine.
After hour's of testing, reading and headache i uninstall wine.
After all it's a beta release, and possibly causing trouble
There the problems are gone, playing music on the 2 hour with rhythmbox without skipping or other problems with gstreamer audiosink plugin.

So perhaps that is an solution, don't know....probably just lucky
;-)

Regards
Roar

---

### Post by gruntlips_ on 2010-05-19
SilverDragon, I have the problem through headphones and through the front mic. 

Cybersamen, I uninstalled wine and the stuttering persists.

Mbuller10, I had this issue in karmic too so I think i will stick it out with lucid. I like almost everything else about 10.04.

I emailed the following to system76. Maybe they can help us out. Note the error I get in the log files when pulse is active. Can't figure out what it is though or how to fix. It is up on launchpad but it is not assigned and does not have a priority. Could be a red herring but who knows.

Hi,

I have been posting on your forum these last few weeks about sound stuttering in lucid on my serval. It appears that a significant number of us are having problems with pulse and that there is no ready solution. I am asking if it would be possible for you guys to post a guide on how to properly do the following in 10.04, either on the message board or in the system76 knowledge page.

1) Fully disable pulse and install whatever replacement alsa packages are required
2) Setup up alsa so that one can change the volume controls with the fn F7,F8
3) Install an alsa and an applet for the top panel so one can switch inputs, outputs etc,
4) Change the loudness or gain. When under pulse I could keep the volume around 2/3 and it was plenty loud. Under alsa, it is up all the way and it is not loud enough.

There are various instructions scattered across the message boards on how to do this but they offer conflicting advice and/or are out of date. This would be a huge help to many of us with this issue using your computers.

I am attaching the user log for when I watch video with pulse and it stutters. It seems I get a lot of the following statements:

May 19 14:11:38 coldwater-laptop pulseaudio[1478]: ratelimit.c: 5 events suppressed
May 19 14:40:07 coldwater-laptop pulseaudio[1424]: pid.c: Daemon already running.
May 19 14:45:32 coldwater-laptop pulseaudio[1402]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
May 19 14:45:32 coldwater-laptop pulseaudio[1402]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
May 19 14:45:32 coldwater-laptop pulseaudio[1402]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
May 19 14:46:04 coldwater-laptop pulseaudio[1402]: ratelimit.c: 8 events suppressed
May 19 14:46:30 coldwater-laptop pulseaudio[1402]: ratelimit.c: 1112 events suppressed
May 19 14:48:33 coldwater-laptop pulseaudio[1402]: ratelimit.c: 1300 events suppressed

However, this goes away with pulse disabled and the stuttering stops and I am not sure what it means.

I have to say that I have had a serval for the last several years and have really enjoyed the experience. However, not having working sound is a deal-breaker for me when it comes to buying a new computer from you guys. I hope you can help me figure this out.

Thank you very much for your assistance. I really appreciate it.

---

### Post by benjaminchodroff on 2010-05-20
Same problem - lucid, vlc and other programs stutter when starting to play an mp3. Usually this lasts for the first 2 seconds, then it goes away. I'd rather not kill pulse...

---

### Post by R0bb0b on 2010-05-22
I had the same problem on 9.10 and was looking forward to 10.04, mostly in hopes that this problem was fixed.  I guess you could say that I have been looking for a solution for almost 6 months and to still see that an answer is still not available is frustrating, especially since this was such an anticipated release.

I guess I will go back to 9.04 until I get a new sound card.  Does anyone have a list of known sound cards that do work correctly?

---

### Post by drcabana on 2010-06-06
Sound was working just fine for me in Karmic.  I had waited until yesterday to upgrade, figuring initial bugs would have been worked out by then.  Hah! I can't get through a whole song on last.fm without very noticeable skipping. 

This is just sad.

---

### Post by Bas232 on 2010-06-07
Weird thing is, the problem isn't when you play with Audacious.
But it is present with all other players.

---

### Post by isantop on 2010-06-07
Bas232 seems to have a point. It is only some players in which this problem occurs, indicating that it has something to do with how that particular application interacts with the Ubuntu Multimedia System.

It also seems to be fairly random. On our test machines, a Serval 4 (Serp4) and a Serval 6 (Serp6), we get completely clear audio playback for extended periods of time. Both of these are running the latest System76 Driver, and are fully updated.

Try enabling proposed and backports. They may contain an update that could fix this for people experiencing this issue.

---

### Post by gruntlips_ on 2010-06-11
I have this problem in VLC, rhythmbox, mplayer, VLC, movie player, and internet video applications. I am running the latest system76 driver and installed 10.04 on a clean install. I have posted on two of the bugs on launchpad concerning audio stuttering but haven't received any responses, suggestions, or fixes.

I would not describe this issue as "fairly random" based on this thread's poll and the number of bug posts, related threads, and random blogs, complaints, etc. about PA found on the internet. 

Right now pulseaudio does not work on my serval - plain and simple. It hasn't worked in 9.10 and it certainly doesn't in 10.04. And there appears to be no solution. The extent of the support I have received from system76 has only been to ask me (repeatedly) if I have done a clean install or not. If it works on your test machines and not on mine, surely there must be some reason why this is the case?

[Deep breath] I'll try this backport thing. How exactly, do I enable proposed and backports?

- gl

---

### Post by thomasaaron on 2010-06-11
gruntlips_,

Sorry. It is difficult to work on this issue when we can't reproduce it. However, I don't think it is a hardware issue, as the issue seems to be happening throughout Ubuntu-dom. (New word?)

Can you use the System76 driver to create some fresh logs after the next occurrence, and attach the logs to the thread. We'll have a new look at it and see if we can find any new info on it.

---

### Post by gruntlips_ on 2010-06-11
Thomasaaron, I am posting what I emailed directly to system76 support on 5/19. The log is attached. I am attaching the user log for when I watch video or audio with pulse and it stutters. It seems I get a lot of the following statements:

May 19 14:11:38 coldwater-laptop pulseaudio[1478]: ratelimit.c: 5 events suppressed
May 19 14:40:07 coldwater-laptop pulseaudio[1424]: pid.c: Daemon already running.
May 19 14:45:32 coldwater-laptop pulseaudio[1402]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
May 19 14:45:32 coldwater-laptop pulseaudio[1402]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
May 19 14:45:32 coldwater-laptop pulseaudio[1402]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
May 19 14:46:04 coldwater-laptop pulseaudio[1402]: ratelimit.c: 8 events suppressed
May 19 14:46:30 coldwater-laptop pulseaudio[1402]: ratelimit.c: 1112 events suppressed
May 19 14:48:33 coldwater-laptop pulseaudio[1402]: ratelimit.c: 1300 events suppressed

However, this goes away with pulse disabled and the stuttering stops and I am not sure what it means. Are there sound specific log files I can log at to diagnose things? Perhaps to see if my sound card is being used properly etc.?

Also I am willing to do a fresh install of 10.04 to work through step by step and see exactly when the problem first occurs and what the logs say etc. if that is helpful.

- Chris

---

### Post by kfriesen on 2010-06-14
Hello, I have being following this thread for about 2 weeks now and decided I would like to put in my 2 cents.

I have being having problems with pulse audio stuttering since 10.04 came out, which makes me think its a problem with a change in pulse, not with system 76 hardware. It was so annoying i had to use my wifes Vista laptop to watch movies. And it always made be feel dirty when i was done. (Vista not the movies) :P

I am completely fine with removing pulse. I prefered not to but i saw no other way. But, like other people I lost my keyboard volume buttons, Is there a way of getting this function back with ALSA?

If interested, I did a fresh install of Lucid 64bit on a Serval Performance Serp 4. I never do upgrades, they always give me problems.

---

### Post by ikeurb on 2010-06-15
I followed these steps and it solved my issue. The audio on my sytem seemed to repeat segments of audio clips as well.


touch ~/.pulse-a11y-nostart
echo autospawn = no|tee -a ~/.pulse/client.conf
killall pulseaudio

---

### Post by ikeurb on 2010-06-15
I wonder if turning off PulseAudio under System -> Prefrences -> Startup Applications would do the trick as well.

I'd try it but have already done the previous suggestion to killall pulseaudio

---

### Post by edevers on 2010-06-21
I downloaded an older version of Skype from [http://skype-old-version.blogspot.com/2010/03/skype-old-version.html]("http://skype-old-version.blogspot.com/2010/03/skype-old-version.html") and Skype sound in Ubuntu 10.04 is fine!

---

### Post by BreuJa on 2010-06-30
> **thomasaaron said:**
> 
```
touch ~/.pulse-a11y-nostart
echo autospawn = no|tee -a ~/.pulse/client.conf
killall pulseaudio 
```

Hello thomasaaron,

many thanks for this. I had trouble since I upgraded from 9.10 to 10.04. Thought I would lose my mind. Tried thousand things, but each "fix" introduced new similar problems. Your soulution seems to disable pulseaudio at all, however, I really don't care. Currently I consider pulseaudio as a pile of crap. I want to listen to music and that's what I can do now without any trouble at all.

I even thought about dropping ubuntu. Sound not working is just a no-go. However, I am astonished about how many people have trouble with sound in 10.04 but there is no real fix.

Kind regards.

EDIT:

I don't have a clue about System76. I just own a custom Desktop system.

---

### Post by thinman1189 on 2010-07-03
I was having the same problem with pulseaudio on my serp4 running lucid. I removed pulse and now rely on alsa. Lost some features but now I can use skype and *gasp* listen to music.

---

### Post by Neobuntu on 2010-07-04
Hello! Way to drive people away!

Thanks for the geeky commands (seriously). FINALLY! I just today realized, the popping I was getting, was audio issues and not anything getting into my audio! AFTER MUCH TIME WASTED! Now I wonder if they will work after reboot.

Call me Mr. Negative; but this sucks!

---

### Post by betrunkenaffe on 2010-07-05
gruntlips: System->Software Sources->Updates tab

You'll find backports and proposed there.

Have you tried the reinstall suggested? I know I've previously ran into issues with Ubuntu after a fresh install which disappeared when I reinstalled my OS.

I snagged this piece of info for  you from a Red hat bug

> This probably means that you need to browse a little in syslog for outher PA
related output, which might give us a hint which msg might get repeated that
often that it is suppressed. Please grep for "pulseaudio" in syslog and attach
this here.

and also

> If you run PA in a terminal, is the output any more interesting? (to do that
set autospawn=false in ~/pulse/client.conf, then stop pa with pulseaudio -k,
and then run PA in the terminal as pulseaudio -vvvvv) 

You can find more information about the pulseaudio config here [http://linux.die.net/man/5/pulse-daemon.conf]("http://linux.die.net/man/5/pulse-daemon.conf")

I didn't find any information on how to disable the rate limiting (which is suppressing the logs), they managed it in Red Hat by installing a package.

Correction: I think it's a module as per a bug report on Ubuntu. Don't know what else will be disabled but you could disable modules and see what happens.

---

### Post by kfriesen on 2010-07-05
I was able to get my keyboard volume buttons working again by installing the packages from: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by jellyfisharepretty on 2010-07-17
I have this problem with a fresh install of Lucid.  The Problem pappeared suddenly a while ago in 9.10 (I suspect an update caused it), so I decided to try a fresh install of 10.04.  No luck though. 

The only sound I can get working properly is my (Logitech) USB headset, which is in fact a USB sound card I guess.  My PCI Audigy 2 stutters horribly, even though I've tried some of the suggested fixes.

---

### Post by chrone on 2010-07-21
> **jellyfisharepretty said:**
> I have this problem with a fresh install of Lucid.  The Problem pappeared suddenly a while ago in 9.10 (I suspect an update caused it), so I decided to try a fresh install of 10.04.  No luck though. 

The only sound I can get working properly is my (Logitech) USB headset, which is in fact a USB sound card I guess.  My PCI Audigy 2 stutters horribly, even though I've tried some of the suggested fixes.

me too, the only working audio is from usb speaker. :(

i've tried to set "default-sample-rate" to 44100 with no luck at all in /etc/pulse/daemon.conf, it just minimize the skipping.

this is bad! :(

---

### Post by ikeurb on 2010-07-22
I fixed my sound skipping issues by doing two things:
 
1.) Running the following commands in a terminal to stop PulseAudio from running and from restarting upon reboot.
 
```

touch ~/.pulse-ally-nostart
echo autospawn =no|tee -a ~/.pulse/client.conf
killall pulseaudio

```
 
2.) Create a file in your home folder called > .asoundrc And add the following code...
 
NOTE: You may have to increase the buffer size.
 
```

pcm.dsp {
    type plug
    slave.pcm "dmixer"
}
pcm.!default {
    type plug
    slave.pcm "dmixer"
}
ctl.!default {
        type hw
        card 0
        }
pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
            pcm "hw:0,0"
            period_time 0
         #   period_time 84000
         #   period_size 2048
         #   buffer_time 340000
              rate 44100
         #   rate 48000
              period_size 1024
         #    buffer_size 2052
              buffer_size 4096 # this is the size of buffer I use
        #   buffer_size 8192
        #   buffer_size 16384
        }
        bindings {
            0 0
            1 1
        }
    }
    ctl.dmixer {
        type hw
        card 0
    }
 
 

```
 
 
I hope this helps.

---

### Post by brunofin on 2010-07-30
> **ikeurb said:**
> I fixed my sound skipping issues by doing two things:
 
1.) Running the following commands in a terminal to stop PulseAudio from running and from restarting upon reboot.
 
```

touch ~/.pulse-ally-nostart
echo autospawn =no|tee -a ~/.pulse/client.conf
killall pulseaudio

```
 
2.) Create a file in your home folder called  And add the following code...
 
NOTE: You may have to increase the buffer size.
 
```

pcm.dsp {
    type plug
    slave.pcm "dmixer"
}
pcm.!default {
    type plug
    slave.pcm "dmixer"
}
ctl.!default {
        type hw
        card 0
        }
pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
            pcm "hw:0,0"
            period_time 0
         #   period_time 84000
         #   period_size 2048
         #   buffer_time 340000
              rate 44100
         #   rate 48000
              period_size 1024
         #    buffer_size 2052
              buffer_size 4096 # this is the size of buffer I use
        #   buffer_size 8192
        #   buffer_size 16384
        }
        bindings {
            0 0
            1 1
        }
    }
    ctl.dmixer {
        type hw
        card 0
    }
 
 

```
 
 
I hope this helps.

What's up guys, I had the same problem and I could fix it thanks to those commands. But now I can only play sounds from one application at time. That means I can't play World of Warcraft and listen to my songs :( Is there a way to fix that, or if not, how can I undo the commands?

Thanks all, and sorry my bad english. :D

EDIT:

The following command will make it go back as it was:

```

rm .pulse-a11y-nostart ~/.pulse/client.conf .asoundrc

```

---

### Post by chrone on 2010-07-30
> **brunofin said:**
> What's up guys, I had the same problem and I could fix it thanks to those commands. But now I can only play sounds from one application at time. That means I can't play World of Warcraft and listen to my songs :( Is there a way to fix that, or if not, how can I undo the commands?

Thanks all, and sorry my bad english. :D

EDIT:

The following command will make it go back as it was:

```

rm .pulse-a11y-nostart ~/.pulse/client.conf .asoundrc

```

i've managed to get it fix by updating alsa-driver, alsa-lib, and alsa-tools from the [www.alsa-project.org](www.alsa-project.org). bring back the pulseaudio do not kill it.

try this following: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

### Post by mojo risin on 2010-08-06
My normal sound output(songs etc) is okay, but when I record something using my head set mic, it stutters badly.
I have updated my alsa only yesterday to the most recent version but it did not change the problem with the stuttering mic.

---

### Post by isantop on 2010-08-06
> **mojo risin said:**
> My normal sound output(songs etc) is okay, but when I record something using my head set mic, it stutters badly.
I have updated my alsa only yesterday to the most recent version but it did not change the problem with the stuttering mic.

Do you mean that the recording has stuttered, and sounds choppy during playback? Or do you mean that after recording, the Audio playback is choppy?

You can check this by recording something, then playing it back. If it stutters in the same place every time, it's the recording that's choppy. If it stutters in odd places, it's the playback.

It could also be that the playback *while* recording is stuttering.

---

### Post by fredknex on 2010-08-08
> **chrone said:**
> i've managed to get it fix by updating alsa-driver, alsa-lib, and alsa-tools from the [www.alsa-project.org](www.alsa-project.org). bring back the pulseaudio do not kill it.

try this following: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

thanks for the link, i just ran all the commands and everything is good to go. 1.0.23 no skips on rhythmbox or vlc yet. so if not fixed its at least a LOT less frequent.


-- i also lost sound in my browsers (chrome/firefox). they dont show up under sound preferences at all.

---

### Post by mojo risin on 2010-08-09
> **isantop said:**
> Do you mean that the recording has stuttered, and sounds choppy during playback? Or do you mean that after recording, the Audio playback is choppy?

You can check this by recording something, then playing it back. If it stutters in the same place every time, it's the recording that's choppy. If it stutters in odd places, it's the playback.

It could also be that the playback *while* recording is stuttering.Mine is the same as this bug [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620)
it has a work around for skype but it is not really a solution.

---

### Post by yarddad on 2010-08-09
The sound and video problems were not able to be resolved so I went back to 9.10 Karmic where it works great! I'm hoping the next release works better. I bet there are alot of folks who did the same.The problem was most prevalent in skype. Music playback was fine. I tried the fixes from many posts and it just was not up to par with 9.10.

---

### Post by jellyfisharepretty on 2010-08-14
In my case, sound even skips in Karmic... Or a clean install of Lucid.

I've tried removing PulseAudio, ALSA, OSS, reinstalling PulseAudio all without success.  And yet my soundcard works just fine in Windows XP, just as it used to work fine in Karmic a few months ago.

I'm going to try Fedora Core.  The latest version also uses PulseAudio, I believe.

---

### Post by jellyfisharepretty on 2010-08-14
Ok...

Sound worked flawlessly in the Fedora Core LiveCD, just before install I tested it by playing an .ogg file.

*But*, after installing Fedora, the same symptoms show up.  I notice the skipping gets worse if there is some CPU usage (any usage, really). This is very frustrating problem.  I am starting to think it has something to do with the recent Linux kernel versions both Ubuntu and Fedora use.

I wonder if it's worth trying a vanilla, older-version kernel.

---

### Post by mullens101 on 2010-08-18
Chrone, thanks for the tip ... I had the skipping issue on my Gigabyte Mobo running Lucid (uses ATI Azalia which is intel).  I have tried MANY other fixes, mostly dealing with module parameters or config files with no luck.

Updating ALSA to 1.23 appears to have resolved the issue (or as fredknex said, if it's not completely resolved, it's alot better than it was)

On a side note, just installed Guayadeque music player and LOVE it ... does embedded lyrics, embedded cover art and everything I want for max iPhone compatibility.  (No, I'm not developer, just happy user ... hadn't heard of Guayadeque before the other day)  So ... if you have to clean up a large collection of music, MusicBrainz Picard is great (with the albumart plugin) and Guayadeque seems to be a great player, especially for large collections (16,000 tracks or so).  I had been using Songbird mainly for embedded lyrics but slow performance and no linux support caused me to drop it.

---

### Post by chrone on 2010-08-18
> **mullens101 said:**
> Chrone, thanks for the tip ... I had the skipping issue on my Gigabyte Mobo running Lucid (uses ATI Azalia which is intel).  I have tried MANY other fixes, mostly dealing with module parameters or config files with no luck.

Updating ALSA to 1.23 appears to have resolved the issue (or as fredknex said, if it's not completely resolved, it's alot better than it was)

On a side note, just installed Guayadeque music player and LOVE it ... does embedded lyrics, embedded cover art and everything I want for max iPhone compatibility.  (No, I'm not developer, just happy user ... hadn't heard of Guayadeque before the other day)  So ... if you have to clean up a large collection of music, MusicBrainz Picard is great (with the albumart plugin) and Guayadeque seems to be a great player, especially for large collections (16,000 tracks or so).  I had been using Songbird mainly for embedded lyrics but slow performance and no linux support caused me to drop it.

glad you could make it. ;)

---

### Post by HandeH on 2011-11-03
> **mullens101 said:**
> ...
Updating ALSA to 1.23 appears to have resolved the issue (or as fredknex said, if it's not completely resolved, it's alot better than it was)
...

My friend's Compal JFL92 (ALC268) has been suffering from this issue for a couple of months (at least). Does updating ALSA really work?

---

### Post by isantop on 2011-11-03
We haven't had any reports of this issue since the upgrade to 11.04 came out. Are you running the latest version of Ubuntu?

---

### Post by HandeH on 2011-11-06
It is running Lucid Lynx and does not matter if you boot with the current kernel or the older ones (e.g. 2.26.32-24 or newer). 

The issue is experienced also with 11.04 and 11.10 live CDs, but the playback audio is working with 10.04.2 live CD. All 32-bit. 

I think, an interesting thing is that in 10.04.2 live CD there is the same versions of the following packages than in the up to date and broken installation: 
alsa-base
alsa-utils
bluez-alsa
gstreamer0.10-alsa
libasound2
libasound2-plugins
linux-sound-base
pulseaudio.

---

### Post by HandeH on 2011-12-09
I just turned to a workaround: I bought an external USB sound card (A-Link SU51).

---

### Post by HandeH on 2012-03-14
Still a problem in Precise 12.04-beta1. A bug report: 
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/882566](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/882566)

---

### Post by Rodney9 on 2012-03-28
I am having this skip/stuttering problem on Xubuntu 11.10 64bit, very frustrating. Gets worse when I plug in my USB speakers.

Rodney

---

### Post by HandeH on 2012-04-07
> **Rodney9 said:**
> I am having this skip/stuttering problem on Xubuntu 11.10 64bit, very frustrating. Gets worse when I plug in my USB speakers.

Rodney

Hi Rodney, 
if you are still using Xubuntu/Ubuntu, you can try a workaround found here: 
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/882566/comments/6](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/882566/comments/6)

It helped for me. Now I'm able to listen to music through the native sound card of my Compal JFL92 (Serval?) and do not have to use an external USB sound card in Lucid 10.04. Also the 12.04 (beta 2) now turned out to be usable OS for this Compal :popcorn:

Before trying that workaround you can just try to make a change in your BIOS settings: AHCI configuration = Disabled.

---

### Post by andrewdied on 2012-05-02
I'm also seeing the issue in ubuntu 12.04 (64 bit) on my serp4. I'd seen it in older ubuntu releases as well. One interesting bit is I only see it in gnome -- if I log into kde instead video/sound (like from [http://www.watchtheguild.com](http://www.watchtheguild.com)) plays 100% normally. This was a fresh install from CD for 12.04. 

The "killall pulseaudio" set of instructions does certainly kill pulseaudio. What do I turn on to get sound again? Alsa is installed.

Update: After I rebooted with pulseaudio killed, the stuttering came back and I can't change the sound volume with the F7/F8 keys or the sound icon in the top right of the gnome desktop.

---

