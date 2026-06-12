---
title: "Wireless and video problems with vista"
date: 2008-07-11
forum: Windows
---

### Post by insane_alien on 2008-07-11
Hi, 

just yesterday i got a new laptop delivered. it's an inspiron 1525 with 4GB of RAM intell X3100 integrated drivers and a 2.4GHz core 2 duo. so not so shabby specs.

now, this came with vista(which i intend to use merely to familiarise myself with the OS as i frequently do tech support for friends family and neighbours and they are starting to get vista computers). and i'm having some strange issues.

These issues are only present in vista so it is not hardware that is the culprit.

1/ wireless connections only stay up for an hour and keys are lost upon disconnection. inconveinient and annoying.

2/ video playback under windows media player is absolutely terrible. it is jerky and frequently refuses to play. 

3/ it took roughly 1 hour for my usb mouse to become usable. the same again upon disconnection and reconnection. 

for me these problems are unacceptable. especially when i am told it has a windows experience rating of 3.5

besides these problems, i am much more impressed than last time i had vista on a local machine.though it still feels rather sluggish compared to ubuntu on the same machine. imo it runs about the same speed XP did on my 1.5GHz 512MB thinkpad but with worse video play back.

---

### Post by fiddledd on 2008-07-11
> **insane_alien said:**
> Hi, 

just yesterday i got a new laptop delivered. it's an inspiron 1525 with 4GB of RAM intell X3100 integrated drivers and a 2.4GHz core 2 duo. so not so shabby specs.

now, this came with vista(which i intend to use merely to familiarise myself with the OS as i frequently do tech support for friends family and neighbours and they are starting to get vista computers). and i'm having some strange issues.

These issues are only present in vista so it is not hardware that is the culprit.

1/ wireless connections only stay up for an hour and keys are lost upon disconnection. inconveinient and annoying.

2/ video playback under windows media player is absolutely terrible. it is jerky and frequently refuses to play. 

3/ it took roughly 1 hour for my usb mouse to become usable. the same again upon disconnection and reconnection. 

for me these problems are unacceptable. especially when i am told it has a windows experience rating of 3.5

besides these problems, i am much more impressed than last time i had vista on a local machine.though it still feels rather sluggish compared to ubuntu on the same machine. imo it runs about the same speed XP did on my 1.5GHz 512MB thinkpad but with worse video play back.

Firstly, as I understand it a 32 bit OS only fully supports 3 GB ram. If this is true you may be using 64 bit Vista, in which case the following might not mean much as I run 32 bit.

1: I can't comment on wireless as I don't use it.
2: WMP works fine for me with avis, mpegs, and also DVD playback. I use xvid codec for avis set to decode all avis (divx etc). You could try VLC ([http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)) for all video playback, that way you'll know the problem has nothing to do with hardware or drivers.
3: I don't use a USB mouse, but would suspect driver problem.

As for Vista, it came pre installed on this Laptop, and is fast and stable for me. To help you judge if your Laptop has a hardware or driver problem, mine boots up in < 30 seconds and shuts down in 5 secs. You can see in my sig that your Laptop is a higher spec than mine, so those times should be less for you.

I should probably add that I have disabled all services I don't use/need including System Restore and Shadow Copy. Readyboost and Superfetch are enabled though.

---

### Post by insane_alien on 2008-07-11
it is the 32-bit, but it does seem to manage to display 4GB whether that is used or not is a different story. it hasn't reached 3 GB of utilisation yet (though it has never been under 1 on vista).

1/ fair enough, can't expect everybody to know everything.

2/ VLC seems to go okay. only downside is that the remote control doesn't seem to work with it. oh well. wmp is still jittery for well everything. even a small 50x50 mpeg movie i made explicitly for testing it. although i would still expect it to handle DVD movies with zero jitter. its supposed to be able to play 1080p(though i neglected the bluray drive option, i do have 1080p content that i plan on playing through the HDMI output though).

3/ i tried installing the drivers that came with the mouse(even though it is just a generic usb mouse thats worked fine with everything.) didn't change anything.


my boot times are actually quite respectable 20 seconds usually. i'm very happy with it there. last time i tried it took 15 minutes to boot(albeit on a slower machine but still more than capable of running vista)

i'm going through and disabling unwanted services but there doesn't seem to be that much of a performance gain.

---

### Post by fiddledd on 2008-07-11
Apologies if you know this already. Most of the 1gb ram isn't actually used, it's cached for Superfetch. Linux does a similar thing with ram and releases it when needed. If you have the Superfetch  service enabled you'll see your HDD LED blinking for a few minutes after boot up, this is Superfetch doing it's thing. So if you use WMP straight after boot up you could possibly see jerky playback, though I've not seen this myself yet. BTW, I've only noticed a difference with Readyboost(also Readyboot)/Superfetch on startup times. Application loading times don't seem much different to me. So I guess you could disable Superfetch if it's causing you problems. Readyboost can be disabled if you don't use a USB stick to help Superfetch with faster memory for App loading etc.
I've not really helped at all with Wireless or USB Mouse, sorry about that. :)

---

### Post by dca on 2008-07-11
(1) could be a problem w/ the wifi NIC driver.  For instance, the manf supplied an XP only driver never tested w/ Vista and accidentally installed this driver w/o compatibility mode (and also administrator mode) set to a lesser Windows vers...
 
(2) sounds like memory issue, start WMP, do the 3-finger salute to get to TSKMGR (task manager) and see what processes are running at that time and how much virtual vs physical RAM and how much CPU cycles are being used...
 
(3) this wouldn't happen to be a wireless mouse would it?  Either way I don't think going into the 'mouse' settings in the useless control panel will help that much.
 
The bottom line on Vista is it's a dog.  If you are running Home Premium (versus Home Basic) be sure Aero is deactivated.  That's the RAM hog that allows you to do all the visual stuff that's been in Linux for years now...

---

### Post by rickyjones on 2008-07-11
If the USB devices are taking longer than a few seconds to be recognized and the problem goes away with, say, and Ubuntu live CD then I'm fairly confident that it is a driver issue.

Have you tried uninstalling the USB controller drivers from Device management? 

Sincerely,
Richard

---

### Post by dca on 2008-07-11
> **rickyjones said:**
> If the USB devices are taking longer than a few seconds to be recognized and the problem goes away with, say, and Ubuntu live CD then I'm fairly confident that it is a driver issue.

Have you tried uninstalling the USB controller drivers from Device management? 

Sincerely,
Richard

..that's a good one, too...  Even making sure there's no exclamation point next to the root USB hub controller or whatever in device manager...

---

### Post by insane_alien on 2008-07-12
okay, i've got the latest drivers for both the WNIC and the mousebut it hasn't helped. i've also tried rolling back the drivers a few versions and still n avail.

---

### Post by rickyjones on 2008-07-12
> **insane_alien said:**
> okay, i've got the latest drivers for both the WNIC and the mousebut it hasn't helped. i've also tried rolling back the drivers a few versions and still n avail.

Have you tried uninstalling the USB Host Controller and other related entries? Try doing that and reboot, it should then install the default Vista drivers. That might be where the problem lies.

-Richard

---

### Post by insane_alien on 2008-07-12
tried that, same results. tried my mates bluetooth mouse and that seems to work fine. might go get one, frees up a usb port and i'm always looking for new gadgets. though dealing with batteries for amouse may be annoying.

as for the wmp problem, it seems to be only local content that causes the jerky issues. streamed media over my network(even at high resolutions) is seamless as is content off a DVD. but even a low resolution media file off the harddrive is jerky, this goes for both the internal harddrive and my external. so i don't think a busy disk is the cause. but i can't think what else could possibly cause it.

the wireless problem seems to have cleared up but i have no idea what i done to fix it.

---

