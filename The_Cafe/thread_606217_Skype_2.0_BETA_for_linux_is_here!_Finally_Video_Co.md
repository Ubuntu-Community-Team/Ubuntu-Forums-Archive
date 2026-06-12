---
title: "Skype 2.0 BETA for linux is here! Finally Video Conference!"
date: 2007-11-07
forum: The Cafe
---

### Post by Kosimo on 2007-11-07
Skype finally offers video conference for linux users.

Strongly recommended to give it a try.

Get a nice .deb from here:

[http://www.skype.com/intl/en/download/skype/linux/beta/]("http://www.skype.com/intl/en/download/skype/linux/beta/") 



It works for you?

Good luck!


EDIT: "kripkenstein" made a wiki where you can find useful information about webcams compatibility in Skype Linux. Check it and don't forget to contribute to enlarge it!
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by wieman01 on 2007-11-07
Oh man... that's good news indeed. Thanks for posting the news, we'll have a crack at it this weekend.

---

### Post by Kosimo on 2007-11-07
> **wieman01 said:**
> Oh man... that's good news indeed. Thanks for posting the news, we'll have a crack at it this weekend.

I was waiting this day for a while...

;)

---

### Post by wieman01 on 2007-11-07
Do you know what sort of cameras are generally supported?

---

### Post by Kosimo on 2007-11-07
> **wieman01 said:**
> Do you know what sort of cameras are generally supported?

At the moment I'm using an old Logitech Quick Cam Express and is loaded with Skype. But I'm having problems with the video signal, don't know if some issue of my camera or this first bugged version of the 2.x series.  Anyway honestly I don't really care. I'm really happy now to see that skype is working to bring me videoconference with every mac/windows/linux skype machine.

I'll tell you later how can I manage a video call, now at 01:55 here in europe everybody is sleeping!

---

### Post by wieman01 on 2007-11-07
> **Kosimo said:**
> At the moment I'm using an old Logitech Quick Cam Express and is loaded with Skype. But I'm having problems with the video signal, don't know if some issue of my camera or this first bugged version of the 2.x series.  Anyway honestly I don't really care. I'm really happy now to see that skype is working to bring me videoconference with every mac/windows/linux skype machine.

I'll tell you later how can I manage a video call, now at 01:55 here in europe everybody is sleeping!
Alright, have a good night & keep us posted, dude. Look forward to it as well.

---

### Post by loell on 2007-11-07
> **wieman01 said:**
> Do you know what sort of cameras are generally supported?

from the forum announcement.
> 
Known Issues with Compatibility for 2.0.0.13
* Using uvc webcam driver with new Logitech cameras can cause a split video effect which does not recover until you restart video.
* Using uvc webcam driver with ATi fglrx graphics card driver results in a memory leak and potential crash currently.
* gspca webcam driver can crash sometimes during webcam initialisation (which can also happen during the call).
* Using a display driver with only a single Xv port means you can only see video in one direction currently.
* Using a display driver with no Xv support will not work at all.
* ATi fglrx driver versions before 8.42.3 may crash your X server and lock up video during the call.
* ATi fglrx driver version 8.42.3 may crash your X server and lock up video at the beginning of the call.

Issues in orange are fixed already for the next release.
I'll update these issues as we isolate more.

---

### Post by SomeGuyDude on 2007-11-07
Awesome. My built-in webcam worked flawlessly. I was concerned after I couldn't get it to work with YouTube.

---

### Post by Kingsley on 2007-11-07
The video works flawlessly with the built-in web cam on my HP dv6000t laptop.

---

### Post by boom2k1 on 2007-11-08
Does anybody have any idea how I can get my Logitech Clicksmart 310 to work in Skype?

In Camorama I can capture pictures with my webcam,
although in skype option it detects my logitech Clicksmart 310 (/dev/video0), it actually remains a black screen when I press the "Test" button. Does anybody know how to fix it? Thanks.

---

### Post by graabein on 2007-11-08
I could have needed this last year when my girlfriend studied abroad! I had to boot into Windows to get the webcam working. 

Good news though.

---

### Post by toupeiro on 2007-11-08
I don't usually say this but...


omgwtfw00t!!!!!111one

I'm one download away from no more XP Guest OS.

---

### Post by FG123 on 2007-11-08
HOLY HELL!

About damn time. :)

---

### Post by toupeiro on 2007-11-08
Working flawlessly with Logitech Quick Cam Ultra Vision and 7.10!!

Damnit I'm so happy I think I'm going to the pub.  Later!

---

### Post by FG123 on 2007-11-08
Damnit, no 64-bit version, still. Have to force a whole bunch of libs with getlibs, unless anyone else has a better idea.

---

### Post by funpop on 2007-11-08
any gutsy .deb ? or did you use the feisty one ?

---

### Post by FG123 on 2007-11-08
Just use the Feisty one, it works fine.

---

### Post by graabein on 2007-11-08
> **toupeiro said:**
> I don't usually say this but...


omgwtfw00t!!!!!111one

I'm one download away from no more XP Guest OS.

> **toupeiro said:**
> Working flawlessly with Logitech Quick Cam Ultra Vision and 7.10!!

Damnit I'm so happy I think I'm going to the pub.  Later!

LOL!!

---

### Post by FG123 on 2007-11-08
Funny...

Works fine for my Gutsy 64-bit setup, although I had to use getlibs for several things but no biggie. Video works fine as well as sound playback and record.

Completely broken for my father's Debian Etch 32-bit setup. Although we've confirmed sound playback is possible on the setup and the camera works fine in Ekiga, Skype plays no sound, shows no video, and records no audio. Useless POS.

---

### Post by BatPenguin on 2007-11-08
> **toupeiro said:**
> Working flawlessly with Logitech Quick Cam Ultra Vision and 7.10!!

Damnit I'm so happy I think I'm going to the pub.  Later!

Hey, can you confirm that EVERYTHING in that webcam is working out-of-the-box on Gutsy? Including microphone? Plug in and it works? 

Also: could EVERYBODY who has a webcam that works good with Skype now and is easy to setup (either out-of-the-box or just a simple .deb or something) please reply to this thread with the exact name of their cam and instructions (if any) for setting it up.

I'm sure there's plenty of us who've been waiting for this day and would really like to just buy a new cam and get this working.

I think this thread is appropriate for something like this but if you disagree I guess we could make a new thread for "Skype supported webcams" but I think it's important to have a clear list of cams that work, let's make the list here...ok?

Thanks.

---

### Post by FG123 on 2007-11-08
Logitech Quickcam Zoom.

All I had to do was modify the "Sound in" device in the "Sound devices" options menu, to point to USB device instead of Default. Everything else worked fine.

---

### Post by funpop on 2007-11-08
doesnt work for me, all i get is  <1 fps, all green display. same with kopete. its not skype's fault, there is no great driver for my cam: Trust WB-3400T

the only thing that gets better pics out of it is the app videoview from this site: 
[http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)



](*,)
[http://www.linux-projects.org/downloads/sn9cxxx-unlimited.html](http://www.linux-projects.org/downloads/sn9cxxx-unlimited.html)

---

### Post by lisc998 on 2007-11-08
Does it come with the SMS feature? That's what I really miss when I'm on Linux.

---

### Post by Kosimo on 2007-11-08
> **lisc998 said:**
> Does it come with the SMS feature? That's what I really miss when I'm on Linux.

Not at the moment, but It will come very soon. Linux team in Skype is working very hard to improve their client.

---

### Post by FG123 on 2007-11-08
> **Kosimo said:**
> Not at the moment, but It will come very soon. Linux team in Skype are working very hard to improve their client.
They better be, that's what we're paying them for!

/shakes fist

Oh wait...

---

### Post by kripkenstein on 2007-11-08
> **BatPenguin said:**
> 
Also: could EVERYBODY who has a webcam that works good with Skype now and is easy to setup (either out-of-the-box or just a simple .deb or something) please reply to this thread with the exact name of their cam and instructions (if any) for setting it up.

A list of webcams that work with Skype on Ubuntu is a great idea. How about a Wiki page for it, though, instead of just this thread? I suggest this page that I just made:

**[Ubuntu Wiki page about Webcams on Skype]("https://wiki.ubuntu.com/SkypeWebCams")**

Please contribute information to this page :)

---

### Post by Kosimo on 2007-11-08
> **kripkenstein said:**
> A list of webcams that work with Skype on Ubuntu is a great idea. How about a Wiki page for it, though, instead of just this thread? I suggest this page that I just made:

**[Ubuntu Wiki page about Webcams on Skype]("https://wiki.ubuntu.com/SkypeWebCams")**

Please contribute information to this page :)

Very nice idea, let's contribute it!

---

### Post by BatPenguin on 2007-11-08
> **FG123 said:**
> Logitech Quickcam Zoom.

All I had to do was modify the "Sound in" device in the "Sound devices" options menu, to point to USB device instead of Default. Everything else worked fine.

Wow, really? That's MY webcam and I've had endless problems getting it to work at all. Could you please post what you did with it either here and/or at that new wiki page? Just simply plug-in and it works? No extra driver? The reason I was hoping to hear about other people's cameras is that I wasn't having any luck with the Zoom in other programs...

Btw, kripkenstein, that wiki page for SkypeWebCams looks great. Hopefully many people will contribute!

---

### Post by orduek on 2007-11-08
I just checked it and saw that i can send video and see myself but can't see the other person - only gets a white screen.

any ideas?

---

### Post by cheeki on 2007-11-08
Thanks for the info...it is all working perfectly with my MSI camera. All I can say is at last! Wonder what made them finally get there finger out umm, highly anticipated linux enable devices with webcams perhaps? Whatever it is, I'm very please the linux version with webam support  is finally here :)

---

### Post by obavjestenja on 2007-11-08
i runing gusty gibbon wit ati radeon xpress 200 card and in the begining my camera isn't  work  but i instaled envy with latest ati driver and my camera work now.
:guitar:

---

### Post by frodon on 2007-11-08
Just great, i'm going to try this out as soon as i get home, i'm pretty sure my logitech quikcam communicate will just work our of the box as usual.

---

### Post by Knoob on 2007-11-08
Logitech Quickcam Pro 4000

All I had to do was modify the "Sound in" device in the "Sound devices" options menu, to point to USB device instead of Default. Everything else worked fine.

btw, i'm using Feisty Fawn (7.04)

---

### Post by sixela on 2007-11-08
Installed and everything looks fine, my contacts are coming up.
My webcam however doesn't show any picture.
It is showing up correctly as a Logitech quickcam, but when I hit the test button all I get is a black screen. Working fine in Ekiga though.

My camera btw is a Logitech quickcam for notebooks.

Anyone else having similar problems? Help? Would love to get this working and ditch windows for good.

---

### Post by kripkenstein on 2007-11-08
Ok, I did my best to add the webcams mentioned so far to the [Wiki page]("https://wiki.ubuntu.com/SkypeWebCams").

People with webcams, add your results to the page and earn our undying gratitude :)

---

### Post by LizardKing73 on 2007-11-08
Oh hell yeah!!!!!!
Finally video on Linux, installed and my cam works. Will definately give this a try over the weekend.
Thanks Kosimo :D

---

### Post by toupeiro on 2007-11-08
> **BatPenguin said:**
> Hey, can you confirm that EVERYTHING in that webcam is working out-of-the-box on Gutsy? Including microphone? Plug in and it works? 

Also: could EVERYBODY who has a webcam that works good with Skype now and is easy to setup (either out-of-the-box or just a simple .deb or something) please reply to this thread with the exact name of their cam and instructions (if any) for setting it up.

I'm sure there's plenty of us who've been waiting for this day and would really like to just buy a new cam and get this working.

I think this thread is appropriate for something like this but if you disagree I guess we could make a new thread for "Skype supported webcams" but I think it's important to have a clear list of cams that work, let's make the list here...ok?

Thanks.

Yes, everything worked.  I didn't have to do anything because the mic on my webcam is my system default MIC, which is what Skype defaults to, but if you need to configure it within skype, it can be done in the options -> sound settings.  There will be a dropdown for mics and you select the one associated with your webcam.

Again, I have the [Quick Cam: Ultra Vision]("http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/238&cl=us,en")

---

### Post by abhiroopb on 2007-11-08
FINALLY video for skype...

Unfortunately I have a webcam problem

I have a Logitech Quickcam 3000 Pro

and when I connect it I see this (after typing lsusb)

```

us 005 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 046d:08b0 Logitech, Inc. QuickCam 3000 Pro [pwc]
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 1241:1503 Belkin 
Bus 002 Device 004: ID 09da:022b A4 Tech Co., Ltd 
Bus 002 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 0000:0000  

```

so it has been detected. But in skype it says no devices found and the green light on top of the cam remains switched on perpetually.

Initially (a while back) I had tried setting up my webcam and I had fiddled around with the pwc....unfortunately I can't remember exactly what I had done. But I remember the video had flickered on and off for a bit. 

Then recently I used virtualbox to install win xp and so I thought I'd try video calling using the skype in the guest os. I tried again to install pwc and it didn't work. I really don't know now what it is that I have done and tried, as installing pwc required patching and then recompiling the kernel. This worked fine but I still couldn't make the pwc driver for some reason, it kept giving error.

If this seems like too much effort I don't mind getting a new cam as the one I have is quite old anyway. But if I do buy a new cam I want it to work out of the box, so if there is one that is guaranteed to work out of the box (e.g. it is made for linux) then I don't mind getting it, otherwise I'd like to try and fix my current cam.

Thanks!

---

### Post by bash on 2007-11-08
Could you maybe also specify with which version of Ubuntu the Webcams worked? So that that can be added to the wiki.

But besides that: Omg that I actually still see the day the skype video comes to Linux.

---

### Post by hellmet on 2007-11-08
How do I install it on 64 bit Gutsy?

---

### Post by meborc on 2007-11-08
> **ubun-two said:**
> Could you maybe also specify with which version of Ubuntu the Webcams worked? So that that can be added to the wiki.

But besides that: Omg that I actually still see the day the skype video comes to Linux.

i thought it would take at least a year more :) i'm so happy i could cry... oh wait... i don't have a webcam :(

checking the wiki now... will buy a webcam this weekend... thanks for the good news, and people, keep on contributing to the wikipage!

---

### Post by loell on 2007-11-08
be sure to buy a webcam that uses a gspca driver , and not those webcams that uses the uvc drivers ;)

---

### Post by BatPenguin on 2007-11-08
Alright: happy to confirm that Logitech Quickcam Zoom works for me as well now. Must've been a problem with previous programs (Kopete) that I didn't get it working but now it works fine. Just had to select the right video input (I have 2 tv cards so it was picking one of those by default) and the right mic (supposedly I have several...anyway, USB mic works). So as long as settings in Skype are correct, I didn't have to do anything other than just plug the cam in.

There was some flickering in the picture on the receiving end (just calling desktop to laptop here) but I think it's safe to say that this thing is working now at least pretty well (I'll of course keep testing).

This is great! Now we just need somebody to port this thing to the N800 already...just imagine what a great Skype device that thing (and N810) is now with video Skype. Getting one very soon...:)

---

### Post by SunnyRabbiera on 2007-11-08
This is VERY good news, skype was one of the roadblocks for many people going over to linux

---

### Post by sefs on 2007-11-08
Logitech quickcam express here but all I get is a black screen when I click the test button.

```

Bus 005 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

```

Do i need to install drivers for the cam to work before I use in skype?

When I go into skype options and video devices it has logitec quickcam usb (/devvideo0/) selected

What else do I need to do to get this baby up and running

---

### Post by Cuppa-Chino on 2007-11-08
delight and pain....

got it to install but unable to choose my webcam.... shows only my tv-card as an option at the moment whereas kopete, ekiga all show both tv-card and webcam (creative webcam nx pro -- spca driver very generic)

any ideas

---

### Post by user1397 on 2007-11-08
My results:

Video WORKED when someone with a webcam called me; as in, the video screen automatically popped up and I could see movement.

I don't have a webcam right now, so I can't test that out yet...I might soon though

---

### Post by wersdaluv on 2007-11-08
Wooohooo!!!

I just had it installed. My Logitech Quickcam Orbit just showed a black box in test (am on 7.10). I hope, it works in an actual call.

---

### Post by Kosimo on 2007-11-08
> **sefs said:**
> Logitech quickcam express here but all I get is a black screen when I click the test button.

```

Bus 005 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

```

Do i need to install drivers for the cam to work before I use in skype?

When I go into skype options and video devices it has logitec quickcam usb (/devvideo0/) selected

What else do I need to do to get this baby up and running

I'm having the same issue with the same webcam.

In the wiki, it says that is supported. Do we may need to install something else?

---

### Post by zzelinski on 2007-11-08
Well, a bittersweet upgrade, for sure. My webcam works, my video works, I can see their video, and hear them well in my USB headset...but they hear choppy, fractured audio! Even in the test call, choppy fractured audio (or recording, I guess). Any ideas?

---

### Post by user1397 on 2007-11-08
> **zzelinski said:**
> Well, a bittersweet upgrade, for sure. My webcam works, my video works, I can see their video, and hear them well in my USB headset...but they hear choppy, fractured audio! Even in the test call, choppy fractured audio (or recording, I guess). Any ideas?well u can't really count on it too much, it's like the second day of the beta version of skype 2.0, so its gonna be a while till they iron out all the bugs...:(

---

### Post by kodoku on 2007-11-08
Microsoft LifeCam works!! WHOOOOOOOOOHOOOOOOOOOOOOOO!!!!!

---

### Post by loell on 2007-11-09
it seems that the logitech quickcam express have a different subtypes and device ID, i better put my device ID that works , in the wiki.

---

### Post by Kosimo on 2007-11-09
> **loell said:**
> it seems that the logitech quickcam express have a different subtypes and device ID, i better put my device ID that works , in the wiki.

:^^   ut on the wiki says that it works out of the box.

---

### Post by kripkenstein on 2007-11-09
> **Kosimo said:**
> :^^   ut on the wiki says that it works out of the box.
The wiki is written by human beings, just like you and me :) It can contain mistakes.

Meanwhile the wiki now notes that the Quickcam may NOT work easily for everyone. Hopefully someone will figure this out and update the wiki, perhaps with directions to get it to work, etc.

---

### Post by loell on 2007-11-09
> **Kosimo said:**
> :^^   ut on the wiki says that it works out of the box.

yeah, it works out of the box with the device ID ,

```
Bus 002 Device 002: ID 046d:0928 Logitech, Inc. Quickcam Express
```

if you have a quickcam express too, and didn't work, please post your device ID, for everybody's  benefit. :)

---

### Post by loell on 2007-11-09
> **kripkenstein said:**
> The wiki is written by human beings, just like you and me :) It can contain mistakes.

Meanwhile the wiki now notes that the Quickcam may NOT work easily for everyone. Hopefully someone will figure this out and update the wiki, perhaps with directions to get it to work, etc.

eh? its not a mistake, quickcam express have different kinds of device ID's ,

---

### Post by kripkenstein on 2007-11-09
> **loell said:**
> eh? its not a mistake, quickcam express have different kinds of device ID's ,
I'm sorry, I didn't mean to imply that it was a mistake. I meant that the wiki might not be 100% accurate, it is a work in progress, written by us the users.

Hopefully we'll get more device ids and fill in the blanks.

---

### Post by loell on 2007-11-09
> **kripkenstein said:**
> I'm sorry, I didn't mean to imply that it was a mistake. I meant that the wiki might not be 100% accurate, it is a work in progress, written by us the users.

Hopefully we'll get more device ids and fill in the blanks.

no offense taken :), i googled more, it turns out that true model name of the webcam with that device ID is actually **quickcam express II**
;) , editing back the wiki now..


oops its already been edited, can you put the true model name in there?

---

### Post by kripkenstein on 2007-11-09
> **loell said:**
> no offense taken :), i googled more, it turns out that true model name of the webcam with that device ID is actually **quickcam express II**
;) , editing back the wiki now..
Great :)

---

### Post by Kosimo on 2007-11-09
> **kripkenstein said:**
> The wiki is written by human beings, just like you and me :) It can contain mistakes.

Meanwhile the wiki now notes that the Quickcam may NOT work easily for everyone. Hopefully someone will figure this out and update the wiki, perhaps with directions to get it to work, etc.

I know that dude ;)

My intention was to remark that someone with quickcam express had it working

---

### Post by Kosimo on 2007-11-09
> **loell said:**
> yeah, it works out of the box with the device ID ,

```
Bus 002 Device 002: ID 046d:0928 Logitech, Inc. Quickcam Express
```

if you have a quickcam express too, and didn't work, please post your device ID, for everybody's  benefit. :)

How can I figure out that information?

---

### Post by loell on 2007-11-09
> **Kosimo said:**
> How can I figure out that information?

plug the webcam, and invoke ```
lsusb
``` in the terminal/console

copy and paste the output here.

---

### Post by Kosimo on 2007-11-09
> **loell said:**
> plug the webcam, and invoke ```
lsusb
``` in the terminal/console

copy and paste the output here.



Ok, So...

This Quickcam express is not working:

```

Bus 003 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

```

---

### Post by loell on 2007-11-09
thanks :) , you are the second post that confirms this, the other one is in page 5 of this thread, this is the quickcam express , the on that only works out of the box is **quickcam express II**

would you know what driver you're using? if not you can just ```
lsmod
``` , lets see what driver its using.

---

### Post by kripkenstein on 2007-11-09
> **Kosimo said:**
> Ok, So...

This Quickcam express is not working:

```

Bus 003 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

```
Thanks, added to the wiki (and moved stuff around there).

---

### Post by Kosimo on 2007-11-09
> **loell said:**
> thanks :) , you are the second post that confirms this, the other one is in page 5 of this thread, this is the quickcam express , the on that only works out of the box is **quickcam express II**

would you know what driver you're using? if not you can just ```
lsmod
``` , lets see what driver its using.

```
lsmod
Module                  Size  Used by
quickcam               73124  0 
videodev               29312  1 quickcam
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev
usbhid                 29536  0 
hid                    28928  1 usbhid
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
af_packet              24840  4 
isofs                  36412  1 
udf                    87204  0 
vmnet                  44596  13 
vmblock                16288  3 
vmmon                 945260  0 
binfmt_misc            12936  1 
ipv6                  273892  18 
radeon                125472  2 
drm                    83348  3 radeon
acpi_cpufreq           10568  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
ac                      6148  0 
sbs                    19592  0 
battery                11012  0 
container               5504  0 
dock                   10656  0 
video                  18060  0 
button                  8976  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  2 
vfat                   14080  1 
fat                    54300  1 vfat
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  2 parport_pc,lp
joydev                 11328  0 
snd_intel8x0           34972  3 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
pcmcia                 41388  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wbsd                   18056  0 
mmc_core               28420  1 wbsd
ipw2200               149320  0 
snd                    54660  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
yenta_socket           27532  1 
ieee80211              35656  1 ipw2200
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
pcspkr                  4224  0 
iTCO_wdt               11940  0 
psmouse                39952  0 
serio_raw               8068  0 
rsrc_nonstatic         14080  1 yenta_socket
iTCO_vendor_support     4868  1 iTCO_wdt
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  4 
8139too                27776  0 
ata_generic             8452  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ata_piix               17540  4 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 quickcam,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```


Le'ts hope future versions fix that for me ;)

---

### Post by Kosimo on 2007-11-09
> **kripkenstein said:**
> Thanks, added to the wiki (and moved stuff around there).

By the way, I noticed in the official skype linux forum about your wiki ;)

Have a look [here]("http://forum.skype.com/index.php?showtopic=101464")

---

### Post by kripkenstein on 2007-11-09
> **loell said:**
> thanks :) , you are the second post that confirms this, the other one is in page 5 of this thread, this is the quickcam express , the on that only works out of the box is **quickcam express II**

would you know what driver you're using? if not you can just ```
lsmod
``` , lets see what driver its using.

loell, you know about this stuff :) , can you perhaps add a line to the wiki about how to figure out using lsmod what driver you are using? I already added a line about how to use lsusb.

---

### Post by loell on 2007-11-09
> **kripkenstein said:**
> loell, you know about this stuff :) , can you perhaps add a line to the wiki about how to figure out using lsmod what driver you are using? I already added a line about how to use lsusb.

added , just make the necessary corrections please ;) , thanks.

---

### Post by Kosimo on 2007-11-09
> **loell said:**
> added , just make the necessary corrections please ;) , thanks.

There is anything on my "list" that you can figure out about my driver? :D

---

### Post by Kosimo on 2007-11-09
Video driver:

```
 lsmod | grep videodev
videodev               29312  1 quickcam
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

```

---

### Post by kripkenstein on 2007-11-09
> **loell said:**
> added , just make the necessary corrections please ;) , thanks.
Ok, did some organizing after your addition. Wiki is starting to look useful now :)

---

### Post by loell on 2007-11-09
> **Kosimo said:**
> There is anything on my "list" that you can figure out about my driver? :D

unfortunately,** quickcam** driver is an aging driver. it really needs to be in the spca based driver, don't loose yet, maybe we or someone can figure out this in the next days, or perhaps report it to skype devs :)

---

### Post by bash on 2007-11-09
Anybody got a Logitech Quickcam Connect? Now that Skype has Vid4Lin (tm) :D I thougth about getting myself a webcam. And that one looks nice.

/edit:

According to the Webcam Hardware wiki that webcam is at least supported out of the box. So I might get it anyways. A confirmation from someone who got it working with skype would still be nice thogh

---

### Post by pesalomo on 2007-11-09
> **FG123 said:**
> Funny...

Works fine for my Gutsy 64-bit setup, although I had to use getlibs for several things but no biggie. Video works fine as well as sound playback and record.

Completely broken for my father's Debian Etch 32-bit setup. Although we've confirmed sound playback is possible on the setup and the camera works fine in Ekiga, Skype plays no sound, shows no video, and records no audio. Useless POS.


What libraries did you get? Besides those needed for running the program (which are showed using ldd), how did you make video work? Mine doesn't detect any v4l devices...

---

### Post by elasticrock on 2007-11-09
Skype has worked so far with the test call and testing the video (I just had to change the audio in device as mentioned in previous posts). I'm using a Logitech Quickcam Notebooks Deluxe and running Gutsy.

---

### Post by beercz on 2007-11-09
Anyone got a creative webcam working with skype yet?  (I have yet to try it)

Edit:

winnie-the-poo has on the [skype for linux]("http://forum.skype.com/index.php?showtopic=101297&st=280") forum (post #286).

I have followed his instructions and it works fine.

Thanks winnie-the-poo

---

### Post by hellmet on 2007-11-09
I reiterate !! How do I install it on a 64bit gutsy pc?

---

### Post by rsambuca on 2007-11-09
> **hellmet said:**
> I reiterate !! How do I install it on a 64bit gutsy pc?

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by NeillHog on 2007-11-09
Camera: Logitech Quickcam Messenger
Bus 005 Device 008: ID 046d:08da Logitech, Inc.
Kubuntu 7.10

Deinstalled old Skyoe.
Installed newest version.

Plugged in camera and went to options -> video devices.
Camera had been recognised and video worked.
Loud speakers also worked and test call worked except that I could not hear myself.

In options -> sound devices tried changing sound in from default to USB device 046d:08da and then neither the video or microphone worked.

Changed "sound in" to "Intel ICH5 (hw:ICH5,0)" and now the video and microphone both work.

Rang a friend and he could see and hear me.

The call dropped a few times killing Skype. Only seemed to happen with the video switched on.

So to summarise. Everything seems to work relatively well except the built in microphone. 

Hope that helps some one.
Neill

---

### Post by jespdj on 2007-11-09
Oh no.... :(

Finally there is Skype for Linux with video, and now the microphone on my laptop doesn't work because of [bug #147682](https://bugs.launchpad.net/dell/+bug/147682)... :cry: Skype is pretty useless when the microphone doesn't work...

---

### Post by Cuppa-Chino on 2007-11-09
as I posted earlier, I am having problems getting skype to recognise my webcam (as it is not dev/video0)

```
desktop:~$ lsmod | grep videodev
videodev               31360  4 zc0301,cx8800,cx88xx,gspca
v4l2_common            21888  6 zc0301,tuner,cx8800,cx88xx,compat_ioctl32,videodev
v4l1_compat            15364  1 videodev

```

how do I force skype onto video 1

```
desktop:~$ ls -l /dev/ | grep video
crw-rw---- 1 root   video    10, 175 2007-11-09 17:54 agpgart
crw-rw---- 1 root   video    81,  64 2007-11-09 17:54 radio0
crw-rw---- 1 root   video    81, 224 2007-11-09 17:54 vbi0
crw-rw---- 1 root   video    81,   0 2007-11-09 17:54 video0
crw-rw---- 1 root   video    81,   1 2007-11-09 17:54 video1

```

fyi it does not appear in the pulldown menu in skype but it does in feature there?

fyi my webcam is bog standard creative that works with gspca

I have check config.xml in .Skype folder but cannot find setting for video device there anywhere? any ideas where that setting is stored, so I can force video1

----------------

also forcing webcam /dev/video1 as standard device in System-->Preferences-->Multimedia has no effect

---

### Post by daynah on 2007-11-09
Just wanna point out that that's the Human theme.

Go Ubuntu and...

GO BROWN GO!

EDIT: Whoa. So, my cam works in options (despite the usual issue of me being upside down, skype can't help it). But uh... I Don't know how to send my upside down self to other people. I'm sure there's a big huge "VIDEO CALL" button right on my forehead, but I can't find it. Any help?

---

### Post by Vn Tutor on 2007-11-09
Skype brings happiness to Linux users including me. After a long time, Skype has finally offered a new feature - video conference - for Linux users. I have downloaded a Debian package. This package is used to install on Ubuntu Feisty but I have installed and tested successfully in Ubuntu Gutsy. Then, I also have a post about it on my blog. :)

---

### Post by hellmet on 2007-11-09
> **rsambuca said:**
> [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)
Thanks.. Worked like charm!

---

### Post by rsambuca on 2007-11-09
> **hellmet said:**
> Thanks.. Worked like charm!

No prob!   But don't thank me, thank Cappy for excellent work!

---

### Post by loell on 2007-11-09
@ **Cuppa-Chino  ** 

you can try linking , see if it can work,  if the webcam is in **/dev/video1** 

you can

```
sudo ln -s /dev/video1 /dev/video0
```


oh, :( but then your   /dev/video0 seems to be occupied already :(

---

### Post by beercz on 2007-11-09
> **beercz said:**
> Anyone got a creative webcam working with skype yet?  (I have yet to try it)

Well, I tried.

According the the options in Skype, my camera is listed (correctly) as OV511 + USB Camera (/dev/video0).

However when I do the video text the small window remains black.

When I engage in a Skype call and I activate my video the person on the other end just sees a small black window rather than me.

Any one else experienced similar?

---

### Post by Atreus12 on 2007-11-09
Are either the client or the protocol open source?

---

### Post by davey.moore on 2007-11-09
I am experiencing exactly the same as you.
This is my webcam:


scofield@scofield-laptop:~$ lsmod | grep videodev
videodev               29312  1 stk11xx
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

---

### Post by beercz on 2007-11-09
> **davey.moore said:**
> I am experiencing exactly the same as you.
This is my webcam:


scofield@scofield-laptop:~$ lsmod | grep videodev
videodev               29312  1 stk11xx
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

Here's mine:

ianpc% lsmod | grep videodev
videodev               27136  2 ov511
v4l2_common            24192  1 videodev
v4l1_compat            14340  1 videodev

---

### Post by spamaverter on 2007-11-09
Okay, it's official.  There really isn't much of an excuse to *not* switch to Ubuntu now... if only SightSpeed would make a Linux version... Works more or less for me - the window of me sometimes disappears, but I can get it back by hiding/unhiding it.  The webcam mic kinda works but makes a horrible clicking sound repeatedly, so I just use the normal mic input.

I am using:
Ubuntu 7.10
Logitech QuickCam Fusion: 046d:08ca (using uvcvideo driver)

I'm not sure if this matters, but when I couldn't get QuickCam Fusion to work in Ekiga (before I downloaded Skype), I did the following:

sudo modprobe uvcvideo trace=15

I also changed Ekiga's video plug-in from V4L to V4L2

Hope this helps someone else - again - I'm not sure if the steps above are required - it *might* work out of the box.

---

### Post by the8thstar on 2007-11-09
Hello guys,

Has anyone tried it with the MICROSOFT VX-6000 or VX6000 cam?

---

### Post by amitaibar on 2007-11-10
Did anyone with ov511 USB camera got skype to work?
It is working fine with kopete, amsn,ekiga butit doesn't work in skype.
My camera is Creative WebCam 3
Thanks

---

### Post by lognok on 2007-11-10
ok, tested 2.0 beta on my family's ubuntu-box with a Logitech quickcam communicate stx and I can send and receive video to a windowsXP-box. I can receive sound but not transmit any and 1min max of playtime, then it crashes.
Tried three times and it crashed all the times within 1 min..

Bus 001 Device 004: ID 046d:08d7 Logitech, Inc. 
videodev               29312  1 gspca

---

### Post by Mr. Knuffke on 2007-11-10
I have the same issue that has been mentioned several times in this thread.  I'm running Gutsy on a 64 bit Athalon.  Using a Logitech Quickcam Communicate.  The webcam works in every other program that I have had the good sense to try out, but skype 2.0 beta does not recognize the cam.  It tells me there is no device detected in the video options.

Any one not have this problem in a similar set up (specifically using a 64 bit computer with skype 2.0 beta and actually having the webcam recognized)?

---

### Post by conphara on 2007-11-10
This is a great day. Finally something "ordinary" comes our way; video conferencing. 
On my laptop I had to choose Realtek audio instead of HD Intel for the other person being able to receive audio. Other than that the audio was VERY clear, almost phoneline quality. My own video did go white a few times, while the receiver's video was working in the lower left corner, both on Ubuntu. Another time it was the other way around. Don't really know what caused that, but when I turned down the background light the video came back on again. I guess my webcam doesnt like too far lit rooms.
Room for improvements: I really like to have some video controlling bars like in ekiga and an adjuster for fps.
Other than that the Skype layout is really good, very Gnome like.

Can somebody tell. The Windows driver for my webcam (Trust Webcam WB-1400T) does speed up the fps and it always seems to be low using Ubuntu, which results in a very choppy videostream. Any way to adjust this other than raise the brightness?
Also the webcams in the Mac notebooks - when you look at IChat conferencing, it uses the h264 codec instead of h263, so the quality, is it only software related or are the webcams just that expensive and good in quality? Are there any opensource apps that uses the h264 codec in videostreaming?

---

### Post by mendieta on 2007-11-10
Agreed, it is a good day. ** Many thanks to the Skype team**. They always said they were working on this, they took unfair heat from some users, and they delivered. 

It's working mostly fine here, but it crashes some times. Still, this is just a Beta. It will only get better.

I always prefer open source software, but I realize Skype is one of the killer apps under Linux: it's mostly a trio: Firefox, OpenOffice and Skype IMHO. (Of course, there is also Amarok, k3b, Digikam, there is a full stack, I'm just thinking of the three biggest hits). But I digress.

Cheers!

---

### Post by pickarooney on 2007-11-10
I tested with my webcam in the settings screen and can see myself. However, I have no idea how to start a video conference to share the picture with someone else!

Please help

---

### Post by mendieta on 2007-11-10
> **pickarooney said:**
> I tested with my webcam in the settings screen and can see myself. However, I have no idea how to start a video conference to share the picture with someone else!

In my case, I had to make the camera available in the options (see the screenshot):

---

### Post by pickarooney on 2007-11-10
that's enabled but there's still no options other than start a chat, call or send a file to a contact

---

### Post by mendieta on 2007-11-10
Ok, with this configuration, the next call I made I had video both ways (before I had a similar config but I wouldn't get my video to stream)

---

### Post by tony.morse on 2007-11-11
At last, I'm so glad it's here but it's not working properly for me...

I have a logitech quickcam messenger.  I can skype with someone and see them fine, or just do chat with no video.  I can even put my camera on and we can all see me but that only works for about a minute and reliably crashes, i.e. skype quits.  I can re-load it and it will work fine for about a min again and so on.  This seems to be listed in the wiki as a problem?  anyone got a clue why this is happening?

BTW the mic works fine contrary to what the wiki says

---

### Post by YannickDefais on 2007-11-12
> **conphara said:**
> 
Also the webcams in the Mac notebooks - when you look at IChat conferencing, it uses the h264 codec instead of h263, so the quality, is it only software related or are the webcams just that expensive and good in quality? Are there any opensource apps that uses the h264 codec in videostreaming?

The development version of Ekiga does use H.264. It works with any webcam. I've tested it and the quality is really good. You'll get it in Ekiga 3.0. Resolution is currently up to 704x576, and FPS up to 30.

We hope to get it in Ubuntu 8.04.

For those willing to test it (it's still under heavy development):
[http://wiki.ekiga.org/index.php/Talk:Additional_Information](http://wiki.ekiga.org/index.php/Talk:Additional_Information)
(This how-to was done with AMD64 system in mind, few adjustments in ./configure are necessary for a 32 bits build) 

The roadmap to Ekiga 3.0
[http://wiki.ekiga.org/index.php/Roadmap_to_3.00](http://wiki.ekiga.org/index.php/Roadmap_to_3.00)

Regards,
Yannick

---

### Post by maluka on 2007-11-12
the camera on my macbook pro doesn't work in skype beta but it does work in amsn, kopete, cheese etc.

---

### Post by aikishugyo on 2007-11-12
I'm delighted that SkyPe with video for linux is out. Problem is getting a webcam. Here in Japan Yodobashi and other large (huge) retail outlets sell lots of relabelled stuff (Elecom, Sanyo) as well as a fair range of Logitech, Microsoft, and Creative products. However, technical information to be had is: ZERO.

I've obviously read this thread and others, looked at the pwc, uvc, spca driver pages on the web to check compatibility, and checked what webcams are available locally.

What I'm not clear about, first of all, is whether to choose a uvc or an spca-based webcam (assuming I don't want to use pwc, as it doesn't appear very popular). A poster here mentioned spca is better, but no reason given. The SkyPE Beta announcement lists issues with both drivers. I gather that uvc is v4l2 (which SkyPE does not support) but that there is a v4l compatibility layer(?); and spca is v4l. The crunch is that on the spca web pages, M.Xhaard gives much better quality marks to the uvc webcams. From what I can see of the cameras, the uvc ones listed all have between 1.3 and 2 megamixels, while the spca ones tend to have around 300 kilopixels only(!).

So I am confused: should I stick with "lower quality" and find an spca webcam (Logitech QC Communicate STX is a possibility), or can I go with a "higher quality" uvc one (Logitech QC Fusion 2007 model, Orbit AF, Pro 9000, Communicate deluxe, Creative Optia AF and Pro, and Microsoft NX-6000 are all possibilities).

Any comments much appreciated.
Cheers, G.

---

### Post by FG123 on 2007-11-12
From my experiences and from what I've read here and elsewhere:

Logitech Quickcam Pro - yay!
Logitech Quickcam Messenger - damn!

If you want older cams, rememember - eBay.

---

### Post by YannickDefais on 2007-11-12
> **aikishugyo said:**
> I'm delighted that SkyPe with video for linux is out. Problem is getting a webcam. Here in Japan Yodobashi and other large (huge) retail outlets sell lots of relabelled stuff (Elecom, Sanyo) as well as a fair range of Logitech, Microsoft, and Creative products. However, technical information to be had is: ZERO.

I've obviously read this thread and others, looked at the pwc, uvc, spca driver pages on the web to check compatibility, and checked what webcams are available locally.

What I'm not clear about, first of all, is whether to choose a uvc or an spca-based webcam (assuming I don't want to use pwc, as it doesn't appear very popular). A poster here mentioned spca is better, but no reason given. The SkyPE Beta announcement lists issues with both drivers. I gather that uvc is v4l2 (which SkyPE does not support) but that there is a v4l compatibility layer(?); and spca is v4l. The crunch is that on the spca web pages, M.Xhaard gives much better quality marks to the uvc webcams. From what I can see of the cameras, the uvc ones listed all have between 1.3 and 2 megamixels, while the spca ones tend to have around 300 kilopixels only(!).

So I am confused: should I stick with "lower quality" and find an spca webcam (Logitech QC Communicate STX is a possibility), or can I go with a "higher quality" uvc one (Logitech QC Fusion 2007 model, Orbit AF, Pro 9000, Communicate deluxe, Creative Optia AF and Pro, and Microsoft NX-6000 are all possibilities).

Any comments much appreciated.
Cheers, G.

Hi,

You're wrong about pwc: this driver is part of the Linux kernel, which means a good support for any kernel and quality of code. I'm personnaly in touch with the author (he is working with the Ekiga team). pwc support both v4l and v4l2 API.

uvc is based on a industry standard and is considered by the FSF itself as a good free driver. Support should be good.

spca is popular but this driver report sometimes a wrong information about its capabilities (but shouldn't hurt with skype AFAIK). The author is not willing to fix it (it cause a smaller capture in ekiga using the QCIF standard resolution).

Regards,
Yannick

---

### Post by aikishugyo on 2007-11-13
> **YannickDefais said:**
> You're wrong about pwc: this driver is part of the Linux kernel, which means a good support for any kernel and quality of code. I'm personnaly in touch with the author (he is working with the Ekiga team). pwc support both v4l and v4l2 API.

Hi Yannick, thanks for setting me straight, much appreciated. I don't see anything but the Logitech Orbit/Sphere supported (but not whether AF---I see new MP is not supported) from the models I can get locally. Hence my conclusion as "not popular".

> **YannickDefais said:**
> uvc is based on a industry standard and is considered by the FSF itself as a good free driver. Support should be good.

OK, that is good news for me, thanks for the information.

> **YannickDefais said:**
> spca is popular but this driver report sometimes a wrong information about its capabilities (but shouldn't hurt with skype AFAIK). The author is not willing to fix it (it cause a smaller capture in ekiga using the QCIF standard resolution).

Hmm, I won't enter into such a discussion :-) <self-censored zipperlips>

Based on availability and support, I will try a uvc version, and report back.

Cheers, Gernot

---

### Post by YannickDefais on 2007-11-13
> **aikishugyo said:**
> 
Based on availability and support, I will try a uvc version, and report back.

Cheers, Gernot

[http://www.fsf.org/resources/hw/cameras](http://www.fsf.org/resources/hw/cameras)

Regards,
Yannick

---

### Post by beercz on 2007-11-13
> **aikishugyo said:**
> I'm delighted that SkyPe with video for linux is out. Problem is getting a webcam. Here in Japan Yodobashi and other large (huge) retail outlets sell lots of relabelled stuff (Elecom, Sanyo) as well as a fair range of Logitech, Microsoft, and Creative products. However, technical information to be had is: ZERO.

I've obviously read this thread and others, looked at the pwc, uvc, spca driver pages on the web to check compatibility, and checked what webcams are available locally.

What I'm not clear about, first of all, is whether to choose a uvc or an spca-based webcam (assuming I don't want to use pwc, as it doesn't appear very popular). A poster here mentioned spca is better, but no reason given. The SkyPE Beta announcement lists issues with both drivers. I gather that uvc is v4l2 (which SkyPE does not support) but that there is a v4l compatibility layer(?); and spca is v4l. The crunch is that on the spca web pages, M.Xhaard gives much better quality marks to the uvc webcams. From what I can see of the cameras, the uvc ones listed all have between 1.3 and 2 megamixels, while the spca ones tend to have around 300 kilopixels only(!).

So I am confused: should I stick with "lower quality" and find an spca webcam (Logitech QC Communicate STX is a possibility), or can I go with a "higher quality" uvc one (Logitech QC Fusion 2007 model, Orbit AF, Pro 9000, Communicate deluxe, Creative Optia AF and Pro, and Microsoft NX-6000 are all possibilities).

Any comments much appreciated.
Cheers, G.
Does [this page]("https://wiki.ubuntu.com/SkypeWebCams") help? (Link from earlier in the thread)

---

### Post by aikishugyo on 2007-11-13
Yes thanks for tips Yannick, and beercz thanks for the wiki page again (it's a permanent open tab for the last few days, heh!).

I took the advice that the uvc drivers would be well-supported, and went and bought a Logitech QC 9000 Pro which I found is supported under linux.  I installed linux-uvc from reps, but could not get luvcview to get anything other than some blue lines on a cyan background. So I downloaded and compiled the SVN version from Berlios. Then tried ekiga and the v4l2 drivers: it works, very nice indeed!. But in skype 2 beta all I get is the same crazy screen as in luvcview (screenshot below):

[http://www.aikishugyo.dnsdojo.org/pics/QCpro9000skype.png](http://www.aikishugyo.dnsdojo.org/pics/QCpro9000skype.png)

The thread here on Mandriva indicates that the Pro 9000 *does* work with SkyPE beta:

[http://www.linuxquestions.org/questions/mandriva-30/logitech-quickcam-pro-9000-uvc-driver-596901/](http://www.linuxquestions.org/questions/mandriva-30/logitech-quickcam-pro-9000-uvc-driver-596901/)

<scratches head> I'm going to see if I have to forcefully change the video size that the camera gives to SkyPE....

---

### Post by YannickDefais on 2007-11-13
> **aikishugyo said:**
> Yes thanks for tips Yannick, and beercz thanks for the wiki page again (it's a permanent open tab for the last few days, heh!).

I took the advice that the uvc drivers would be well-supported, and went and bought a Logitech QC 9000 Pro which I found is supported under linux.  I installed linux-uvc from reps, but could not get luvcview to get anything other than some blue lines on a cyan background. So I downloaded and compiled the SVN version from Berlios. Then tried ekiga and the v4l2 drivers: it works, very nice indeed!. But in skype 2 beta all I get is the same crazy screen as in luvcview (screenshot below):

[http://www.aikishugyo.dnsdojo.org/pics/QCpro9000skype.png](http://www.aikishugyo.dnsdojo.org/pics/QCpro9000skype.png)

The thread here on Mandriva indicates that the Pro 9000 *does* work with SkyPE beta:

[http://www.linuxquestions.org/questions/mandriva-30/logitech-quickcam-pro-9000-uvc-driver-596901/](http://www.linuxquestions.org/questions/mandriva-30/logitech-quickcam-pro-9000-uvc-driver-596901/)

<scratches head> I'm going to see if I have to forcefully change the video size that the camera gives to SkyPE....

Well, Skype is very far away from free software. I advice you to ask about your problem in the Skype forum. There is some section dedicated to Linux and video... As Skype is very well closed and patented, they can't look at how Ekiga does it. You probably get better chance dealing with their devs directly..

Regards,
Yannick

---

### Post by frodon on 2007-11-13
Yes, the best way to get your problem being taken in consideration is in this thread :
[http://forum.skype.com/index.php?showtopic=101297](http://forum.skype.com/index.php?showtopic=101297)

---

### Post by aikishugyo on 2007-11-13
Will do (and yes, I've been following that thread too). I'll post back here with any solutions---seems it could also be an SDL problem since the controls for luvcview don't appear.

---

### Post by little_penguin on 2007-11-13
It's brilliant news! Video at last, my Logitech Quickcam Pro 9000 works great with it.

ID 046d:0990
uvc driver

---

### Post by aikishugyo on 2007-11-13
> **little_penguin said:**
> It's brilliant news! Video at last, my Logitech Quickcam Pro 9000 works great with it.

ID 046d:0990
uvc driver

Feedback: I did not get any help on other forums (yet) but good news: the QC 9000 Pro works fine on 2 other machines, to the problem I have with video is confined to my desktop i386 with nvidia card (Ge6200).

1. perfect SkyPE 2 Beta on Toshiba LX/290DR with nVidia (Geforce Go 6600TE/6200TE) i386 architecture.

2. perfect SkyPE 2 Beta on AMD64 with nVidia G70 (GeForce 7800 GTX) i386_64 architecture.

*Update:* Added to Wiki.

---

### Post by aikishugyo on 2007-11-14
Problem with garbage in luvcview and SkyPE with V4L on i386 solved:

In response to my problem, I can happily announce that after a kernel upgrade today on my Debian Sid machine, to
2.6.22-3-686-bigmem #1 SMP Mon Nov 12 09:52:20 UTC 2007 i686 GNU/Linux,
and the installation of the uvcvideo module, all works as expected! As I noted in another post, I had no problems on an Ubuntu AMD64 Gutsy system with GTX 7800 nVidia cards, nor on a i386 laptop with Go 6600/6200TE card. 

So now I have two i386 (one of which is running Debian Sid) and one x86_64 machines running SkyPE 2 beta successfully with the Logitech QC 9000 Pro.

---

### Post by meborc on 2007-11-14
ok... tried with "creative notebook live cam" (don't know the exact model)... everything works just fine until i try to call someone

i can see myself in a tiny box for just a fraction of a second (that means the cam works... i also can see myself when testing under settings)... and then skype crashes with a "illegal intruction" error message in terminal

:( anyone encountered this before?

---

### Post by YannickDefais on 2007-11-14
> **aikishugyo said:**
> Problem with garbage in luvcview and SkyPE with V4L on i386 solved:

In response to my problem, I can happily announce that after a kernel upgrade today on my Debian Sid machine, to
2.6.22-3-686-bigmem #1 SMP Mon Nov 12 09:52:20 UTC 2007 i686 GNU/Linux,
and the installation of the uvcvideo module, all works as expected! As I noted in another post, I had no problems on an Ubuntu AMD64 Gutsy system with GTX 7800 nVidia cards, nor on a i386 laptop with Go 6600/6200TE card. 

So now I have two i386 (one of which is running Debian Sid) and one x86_64 machines running SkyPE 2 beta successfully with the Logitech QC 9000 Pro.

Great!

please, can you test it against Ekiga? I'm maintaining this page to help users:
[http://wiki.ekiga.org/index.php/Tested_hardware](http://wiki.ekiga.org/index.php/Tested_hardware)

It use V4L2 right?

Regards,
Yannick

---

### Post by aikishugyo on 2007-11-14
> **YannickDefais said:**
> Great!

please, can you test it against Ekiga? I'm maintaining this page to help users:
[http://wiki.ekiga.org/index.php/Tested_hardware](http://wiki.ekiga.org/index.php/Tested_hardware)

It use V4L2 right?


Yannick, yes, I already did---somewhere in an earlier post where I explained the problem I said it works fine with V4L2 apps like Ekiga, aMSN, and with mplayer and VLC using that app layer. After the kernel upgrade and new uvc module install on Debian sid (2.6.22-3-686-bigmem) it also worked fine with V4L apps like luvcview and SkyPE.

I had no troubles under Gutsy AMD64 (2.6.22-14-generic) with the uvcvideo module, either with V4L2 or V4L apps.

Cheers!

---

### Post by lnxpwr on 2007-11-16
> **boom2k1 said:**
> Does anybody have any idea how I can get my Logitech Clicksmart 310 to work in Skype?

In Camorama I can capture pictures with my webcam,
although in skype option it detects my logitech Clicksmart 310 (/dev/video0), it actually remains a black screen when I press the "Test" button. Does anybody know how to fix it? Thanks.


Boom2K1,
have the same problem with both of my cams (Trust 120 spacecam and Logitech Quickcam Express). Let me know if you get a solution.
thx

---

### Post by Andypoo on 2007-11-17
Just for those who are here but not monitoring the Skype thread.

If you have a uvc or gspca camera on 64-bit Ubuntu and can not get Skype to see the device in options at all (ie. it is not in the list), then you may need to upgrade to the latest uvc/gspca source.

Unfortunately, the bundled versions of uvc/gspca with Ubuntu are quite old and do not have compat_ioctl32 support (which is a kernel module included in the video device subsystem to allow webcams on 64-bit systems to talk to 32-bit applications).

Also, with regards the QCP9000, this is a relatively new camera, so you may also need to upgrade uvc for support on this on 32 or 64-bit systems.

Andy from Skype.

---

### Post by styven on 2007-11-17
Hurrah!

Sound and video working in Skype 2.0 beta.
Ubuntu Gutsy, Logitech Quickcam pro5000 for both audio and video in skype.

Sadly the screen grab does not show the test screen but it will show the device listed.

Steve.

---

### Post by rduch on 2007-11-17
I am using  a Logitech QuickCam Pro 9000, Kubuntu Gutsy and I have no option with Skype for video. I am assuming that somehow the camera is not recognized as being there. The camera does work with Kopete so I know the system has found it. 
Voice connection to another skype user has been confirmed. How do I troubleshoot this? I have read this entire thread and maybe I just don't recognize the answer. It seems that all video configuration problems have been solved by clicking the video button in the Options menu. I do not have a video button to click.

Thanks in advance...Rene

---

### Post by mendieta on 2007-11-18
> **rduch said:**
>  It seems that all video configuration problems have been solved by clicking the video button in the Options menu. I do not have a video button to click.

Thanks in advance...Rene

Weird, Are you sure you are running the beta ? Maybe you have an older version around and you are running this one? If you go to the "About" option in the menus, what version do you see? 2.0.0.13 ?

---

### Post by rduch on 2007-11-18
You nailed it!. I did not have an older version on my computer. I just downloaded it yesterday from the Skype site. I naturally assumed that it was the latest version. What I failed to consider was that the new version is a beta and the normal download button would not get a bete but the last stable version. Will unload stable and reload beta. Thanks a heap!

Rene

---

### Post by mendieta on 2007-11-18
Hey I'm glad, hope it works well for you. Cheers !

---

### Post by rduch on 2007-11-18
Well, not quite...The video button is now available but the test screen returns only a blank black screen. I cannot make outgoing calls at all now. I get an error message "Call failed: Problem with audio playback". I checked all the options to be sure that they were set up as before. What may be my next step?


Edit: Now calls are going through, but still no video. All I did was to try different audio configurations and I ended up back where I started. The only difference is that I now can make a call.

rene@ubuntu:~$ lsusb
Bus 004 Device 004: ID 046d:0990 Logitech, Inc. 
Bus 004 Device 003: ID 058f:6362 Alcor Micro Corp. 
Bus 004 Device 002: ID 03f0:2112 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

rene@ubuntu:~$ lsmod
Module                  Size  Used by
uvcvideo               47748  0 
snd_usb_audio          79872  0 
snd_usb_lib            16768  1 snd_usb_audio
compat_ioctl32          1408  1 uvcvideo
snd_hwdep               9220  1 snd_usb_audio
videodev               28288  1 uvcvideo
v4l1_compat            14468  2 uvcvideo,videodev
v4l2_common            17536  2 uvcvideo,videodev

Maybe this data will help....Rene

---

### Post by styven on 2007-11-18
> **rduch said:**
> Well, not quite...The video button is now available but the test screen returns only a blank black screen. I cannot make outgoing calls at all now. I get an error message "Call failed: Problem with audio playback". I checked all the options to be sure that they were set up as before. What may be my next step?


Edit: Now calls are going through, but still no video. All I did was to try different audio configurations and I ended up back where I started. The only difference is that I now can make a call.

rene@ubuntu:~$ lsusb
Bus 004 Device 004: ID 046d:0990 Logitech, Inc. 
Bus 004 Device 003: ID 058f:6362 Alcor Micro Corp. 
Bus 004 Device 002: ID 03f0:2112 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

rene@ubuntu:~$ lsmod
Module                  Size  Used by
uvcvideo               47748  0 
snd_usb_audio          79872  0 
snd_usb_lib            16768  1 snd_usb_audio
compat_ioctl32          1408  1 uvcvideo
snd_hwdep               9220  1 snd_usb_audio
videodev               28288  1 uvcvideo
v4l1_compat            14468  2 uvcvideo,videodev
v4l2_common            17536  2 uvcvideo,videodev

Maybe this data will help....Rene

Have you selected your webcam in the dropdown as shown in the screenshot i recently posted.
I too had nothing until i did this for both audio and video in the options menu.
In your case you should see under where it says select webcam.....
UVC Camera (046d:0990) 
Select this and hopefully it will work.

Steve.

---

### Post by rduch on 2007-11-18
Yes, it is my only selection for a webcam. Is is labeled as
 "UVC Camera (046d:o990) (/dev/video0)"

---

### Post by aikishugyo on 2007-11-18
> **rduch said:**
> Yes, it is my only selection for a webcam. Is is labeled as
 "UVC Camera (046d:o990) (/dev/video0)"

First, check if luvcview works for you. Then you will at least know that v4l is working and not only v4l2. What do you get?

Second, since my x64_86 GG worked fine with the 9000 Pro (see my posts a page or two back) probably the error on your side is quite simple to fix. Are you on a i386 or x86_64 system?

---

### Post by rduch on 2007-11-18
> First, check if luvcview works for you. Then you will at least know that v4l is working and not only v4l2. What do you get?

What is luvcview? I do not find it in the repositories. I'll google it and try it. It does work with kopete.

> Second, since my x64_86 GG worked fine with the 9000 Pro (see my posts a page or two back) probably the error on your side is quite simple to fix. Are you on a i386 or x86_64 system?

I am on a i386 system. I'm sure that it's simple configuration issue as well. Just got to find it.

Rene

Installed luvcview; the camera works just fine.

---

### Post by aikishugyo on 2007-11-19
OK, so now you know v4l is working---I can also confirm the webcam working on my AMD64 system, and I saw confirmations from others that it works on their i386 systems. Just to be safe, can you purge skype, get rid of any directories where preferences might be saved, and install it again? Then attach the camera, check what is the lsusb output (or dmesg or /var/log/messages): should have attachment to /dev/video0 or something like that. In Skype make sure you select the same device in video before you test it. See how that goes...

---

### Post by rduch on 2007-11-19
> **aikishugyo said:**
>  Just to be safe, can you purge skype, get rid of any directories where preferences might be saved, and install it again? Then attach the camera, check what is the lsusb output (or dmesg or /var/log/messages): should have attachment to /dev/video0 or something like that. In Skype make sure you select the same device in video before you test it. See how that goes...

Purged skype through Synaptic, deleted the .skype folder in my home folder. Re-installed skype with dpkg -i in terminal. Opened and reset all my preferences. Got audio and no video. Attaced is the end of my dmesg file and my lsusb output.

[294478.924158] usb 4-2: USB disconnect, address 4
[294486.959234] usb 4-2: new high speed USB device using ehci_hcd and address 6
[294487.218639] usb 4-2: configuration #1 chosen from 1 choice
[294487.219459] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
rene@ubuntu:~/Downloads$ lsusb
Bus 004 Device 006: ID 046d:0990 Logitech, Inc. 
Bus 004 Device 003: ID 058f:6362 Alcor Micro Corp. 
Bus 004 Device 002: ID 03f0:2112 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by tezzaa on 2007-11-19
Hi,

I have 7.10 Gutsy Gibbon installed and want to download skype.

Is it best to download from this link:[http://www.skype.com/intl/en/download/skype/linux/beta/choose/]("http://www.skype.com/intl/en/download/skype/linux/beta/choose/")
(apparently the Fiesty Fawn version works OK with Gutsy Gibbon)
or should I install it using this method :

**Skype for Linux Repositories**
Using Skype's apt repository

1. As the root user, add this line to the end of your /etc/apt/sources.list file:

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free2. 

Then run apt-get update to sync to the latest repository and 
apt-get install skype to install the latest version of Skype on your computer.

Terry
(a total newbie)

---

### Post by beercz on 2007-11-19
For those with the black screen problem using ov51x cameras - this link may be helpful (post #60 by SebTV):

[http://forum.skype.com/index.php?showtopic=100897&st=40](http://forum.skype.com/index.php?showtopic=100897&st=40)

I have got an ov511 +USB based webcam, not quite the one that SebTV uses,  I don't have the file ov51x-jpeg-core.c (I only have ov511.c) therefore I cannot apply SebTV's patch.

I think SebTV's solution is getting close though.

Can anyone modify the patch for an ov511 based camera?

---

### Post by banda on 2007-11-20
@beercz
thanks for providing the link..
but in order to install the patched version of the driver that sebtv provided i will have to remove the driver i already have installed.. unfortunately i do not yet know of a way to do this .. 
i will be very glad if you could point me in the right direction .. thanks :)

> 
Bus 001 Device 005: ID 041e:405f Creative Technology, Ltd
(its a creative vista webcam model number -  vf0330)

$ lsmod | grep videodev
videodev               29312  2 ov51x_jpeg
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

---

### Post by KingWilliam on 2007-11-20
neat-o, my cheap-*** LabTec webcam is supported :D

---

### Post by rduch on 2007-11-20
Her's an update of my efforts to get video working since my last post. 
Looking through the Skype website for solutions I noticed on the download page that the required files for beta 2.0 included QT4.2.1+ and D-bus 1.0.0. I checked in my Adept Manager and found that I had QT 3.something installed but not 4.etc. I installed 4.* and removed and re-installed Skype, but no luck. The next item was D-bus 1.0.0. Now there are several D-bus associated files listed in my Adept Manager, all seemingly to address some particular issue. Some state that they will not do the regular D-bus job (or so it seems to me). Can someone clarify which D-bus file is required for Skype? I have all the main, security multiverse and universe repositories accessed. Do I need to go to an outside source for the correct file?

Thanks again for all the help....Rene

Edit: Found out that I had d-bus as required.....anybody with any other ideas?

---

### Post by estebe on 2007-11-22
Hi, I’ve tried Skype 2 with a Logitech Quickcam Chat for skype.

```
[I]lsusb
Bus 002	Device 002	ID 046d:092e	Logitech Inc.

lsmod | grep videodev
videodev		29312		2	gspca,bttv
v4l2_common	18432		4	tuner,tvaudio,bttv,videodev
v4l1-compat		15364		2	bttv, videodev[/I]
```

I can send the video signal, the others can see me but I can not see myself and the others. Also when I click test on options my video is too dark and I can not change anything like sharpness…
Any idea?

---

### Post by jespdj on 2007-11-22
> **Atreus12 said:**
> Are either the client or the protocol open source?
NO and NO.

---

### Post by tuque on 2007-11-24
Rduch, If you find a fix please let me know.
I'm having the same difficulty with a Logitech Quickcam Pro 9000 (046d:0990) and Gutsy with Skype.
Uvc is installed but doesn't work in Skype, just displays static. Also fails to work in Canorama with the error message, "could not connect to video device (/dev/video0) "

lsmod | grep videodev
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev

The camera works in Cheese (although the image is poor, blurred) so I guess V4l2 is running ok.
Rather puzzling as others report this camera works without issues. It's bound to be something simple that I have or haven't done but for now it's got me beat.

---

### Post by masmre on 2007-11-25
stk11xx working whit new 1.2.0 release.
Asus a6km laptop.
[http://sourceforge.net/project/showfiles.php?group_id=178178&package_id=205527&release_id=556245](http://sourceforge.net/project/showfiles.php?group_id=178178&package_id=205527&release_id=556245)

---

### Post by diego1188 on 2007-11-25
Downloaded skype 2.0 today. Tested with my cheap Trust wb1200p webcam, which works with all the other apps; the webcam was recognized, but I only got a black test window. 
Tried many times, also tried disabling compiz, but had no luck. 
Then I installed the ow511 source driver, I tried once more and it worked (slow framerate and 100% cpu, but at least it worked).
This is the webcam:
[http://www.trust.com/products/default.aspx?item=13405](http://www.trust.com/products/default.aspx?item=13405) 
Product ID is 093a:2468, I guess it uses gspca driver (but how can I find out that? :confused:).

---

### Post by Whoopie on 2007-11-26
Hi,

don't miss [http://forum.skype.com/index.php?showtopic=102838](http://forum.skype.com/index.php?showtopic=102838)

With skype_video_hijacker, I got my Quickcam Messenger working.

The preview doesn't work, so you should test it with a real  video call.

Best regards,
Whoopie

---

### Post by MarcRJacobs on 2007-11-27
Just downloaded the new Skype 2.x.  I have been using Linphone with a M$ Lifecam NX-6000 on my Toshiba P105-S9337 running Kubuntu 7.10.  It's been great.  Can anyone tell me why this cam won't work in Skype, but does in Linphone?  It's not a hardware, or palette issues (as has been discussed), because Linphone has perfect colors and a good frame rate.  Any ideas?
Thanks

---

### Post by neocon2005 on 2007-11-28
Hello Folks:
Got the Logitech Quickcam Express (device id 046d:0870) working with Skype. I don't know what driver (quickcam?) I am using though. Teach me how to find it and I will post it.

I followed the instructions on [URL="http://forum.skype.com/index.php?showtopic=102838"]http://forum.skype.com/index.php?showtopic=102838
[/URL]

Download source code using
```
svn checkout http://gstfakevideo.googlecode.com/svn/trunk/ gstfakevideo
```

Make sure dependencies are satisfied with
```
sudo apt-get install libgstreamer0.10-dev pkg-config
```

Then
```
cd gstfakevideo
make
sudo make install
```

If your webcam is at [COLOR="Red"]/dev/video0[/COLOR] then [COLOR="Red"]sudo mv /dev/video0 /dev/video1[/COLOR]

Fire up skype with ```
gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace
``` and enjoy Skype with video!!! And my preview works too! Plus I tested on a remote machine as well :)

YMMV with other webcams but give this procedure a shot!

Alas! It crashes randomly!

> **Kosimo said:**
> I'm having the same issue with the same webcam.

In the wiki, it says that is supported. Do we may need to install something else?

---

### Post by aikishugyo on 2007-11-28
I'd like to offer this tip for those of you with problems involving stiping, interlacing, and the like: where you can see that the camera is working, but something in the resolution is screwed up (this may also appear as a green screen, or even a black screen if you mess up the editing of the file I mention below).

From the SkyPE forums, there was the suggestion to edit the ~/.Skype/<username>/config.xml (after backing it up. This is the procedure I used.

1. Prepare by making a backup of the config.xml file (e.g., config.xml.orig)

2. Start SkyPE, go to video options, and tick the "start automatically" type button. I assume from the intro that your camera is already detected, so take note of the device name.

3. Now quit (not just close) SkyPE, and edit the config.xml file, looking for an XML structure <Video> ... </Video>. Initially it would not be there, but if you followed step 2, there should be one, with a single line <AutoSend>1</AutoSend> inside it.

4. Now, add a line ```
<Device>/dev/videoN</Device>
``` in the structure, where N is the number of your device seen in SkyPE video options (usually 0).

5. Now open SkyPE again and check that it still "works" as before. A wrong devicename will be fatal.

5. Quit SkyPE again, and add another line, ```
<Fps>10</Fps>
``` to the video section of the config file (see below for more). This is kind of a minimum requirement I expect, although you could use 5 instead of 10. Then you have other more serious graphics problems anyway :-) Restart SkyPE and check that it still works! Then quite SkyPE again and we'll get to the real meat of the deal.

6. Run "luvcview -L" which should output the capabilities of your graphics card. If you don't have luvcview already, either download it from the author's site (gspca driver site), or add a Hardy universe line to the apt repos and install it from there. Now, the output should read something like this, with the exact lines and IFR numbers supported dependent on your graphics card/X layer and so on (below is from a twin nVidia 7800GTX card on a 2-year-old AMD64 platform, I doubt that will be matched by many laptops out there, hehe):

```
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
/dev/video0 does not support read i/o
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
        Time interval between frame: 1/5, 

```

SkyPE I think (is this true?) need the YUV supported mode, and if it assumes in its own twisted little way something different than what your card supports, you are *screwed* by the pooch. I have 4 machines that I tested SkyPE on, and on one it was fine (the above one), on another I got video but the lower part was frozen, and in another two I got interlacing. Well, no longer :-)

7. Now, be conservative (as you can see, 10 for the inverse of frame speed is fairly conservative), and take, for example, the YUV resolution of 176x144 as a starting point (if you have an older laptop, for example like one of my Toshiba models from 2000 that originally ran Windows ME, gulp, you might try less, but I pretty much think you won't need to), and add the following lines to your config.xml video section:```
<CaptureWidth>176</CaptureWidth>
<CaptureHeight>144</CaptureHeight>
```
Start up SkePE again and see if that works. I hope it does, else go back a couple of steps to where it does work, and try a lower resolution and/or frame speed setting.

8. Now, if that all works, you may experiment with different settings, maybe writing scripts to choose SkyPE to start up with different configurations depending on who/where you are calling to and from which location you are connected from, etc. Because, of course, the bandwidth requirements are quite different. Obviously, with the current state of SkyPE for linux doing unknown things with its selection criteria for video modes, someone on a Windows machine will have a different default bandwidth use compared to someone using the same camera on a linux system... so you have to do this setting manually for now.

I hope this helps, cheers,
   Gernot

---

### Post by wieman01 on 2007-11-29
Funny... latest Skype BETA version works great on Kubuntu Gutsy. No more crashes with a Logitech webcam. Things are improving, guys.

---

### Post by mendieta on 2007-11-30
> **wieman01 said:**
> Funny... latest Skype BETA version works great on Kubuntu Gutsy. No more crashes with a Logitech webcam. Things are improving, guys.

Uou, I have a logitech, consistently crashing after one minute of use with Skype beta, and now I see your post. Which beta version are you running ? I thought they only released one so far: 2.0.0.13

Is there an apt repository to install the betas? 

Thanks !

---

### Post by Warpnow on 2007-11-30
awsome. Im going to get it.

---

### Post by wieman01 on 2007-12-01
> **mendieta said:**
> Uou, I have a logitech, consistently crashing after one minute of use with Skype beta, and now I see your post. Which beta version are you running ? I thought they only released one so far: 2.0.0.13

Is there an apt repository to install the betas? 

Thanks !
Sorry, I have to revise my statement... it constantly crashes in Feisty and is rock-stable using the same device in Gutsy. But the version number has not changed indeed. Sorry for the confusion.

---

### Post by mendieta on 2007-12-01
> **wieman01 said:**
> Sorry, I have to revise my statement... it constantly crashes in Feisty and is rock-stable using the same device in Gutsy. But the version number has not changed indeed. Sorry for the confusion.

No problem ! Thanks a lot for letting us know! Indeed, it seems like this bug is going to be fixed in the next beta, according to a skype staff member:

[http://forum.skype.com/index.php?showtopic=101447&st=0](http://forum.skype.com/index.php?showtopic=101447&st=0)

Cheers!

---

### Post by rsambuca on 2007-12-05
A new update has been released today.  You can get details of fixes and download it here.

[Skype 2.0 Beta for Linux update]("http://share.skype.com/sites/garage/2007/12/skype_20_beta_for_linux_update.html")

---

### Post by xhilyn on 2007-12-05
Thanks for the info. I have just installed the new beta and it looks like my 1 min crashing bug has been squished. So the new one works brilliantly for me, I'm well chuffed. I hope everyone else is as lucky. I'm using a Logitec QuickCam Connect and the onboard mic works as well. Great stuff.

xhi

---

### Post by MarcRJacobs on 2007-12-05
The Feisty Fawn (7.04) link is broken on the Skype linux beta download page ([http://www.skype.com/intl/en/download/skype/linux/beta/choose/](http://www.skype.com/intl/en/download/skype/linux/beta/choose/)).  Where did you get yours?  I want one too. Thanks

---

### Post by xhilyn on 2007-12-05
Hi. Yeah thats where I got it from and the link woks ok for me in Firefox. I checked it on two different computers and the link worked fine on both.
Sorry I can't help further.

xhi

---

### Post by meborc on 2007-12-05
so you guys use the feisty version on gutsy? or you use the static pack?

---

### Post by rsambuca on 2007-12-05
> **meborc said:**
> so you guys use the feisty version on gutsy? or you use the static pack?

Feisty deb seems to work in Gutsy.

---

### Post by meborc on 2007-12-05
> **rsambuca said:**
> Feisty deb seems to work in Gutsy.

thanks... i hope this version will work for me... i have a strange crash just when i start a video call... if i chat or just stay online everything is OK...

but as soon as i video-call someone, the program just closes

does everyone have the same video/call quality between linux-linux and linux-windows/mac ? or are there abnormalities?

EDIT: just checked, the same bug still exists... as soon as i video-call someone, the skype window closes :S

---

### Post by rsambuca on 2007-12-05
> **meborc said:**
> thanks... i hope this version will work for me... i have a strange crash just when i start a video call... if i chat or just stay online everything is OK...

but as soon as i video-call someone, the program just closes

does everyone have the same video/call quality between linux-linux and linux-windows/mac ? or are there abnormalities?

EDIT: just checked, the same bug still exists... as soon as i video-call someone, the skype window closes :S

Close Skype and then open it from a terminal window.  Then test it on a video call. It should give some error message.

---

### Post by meborc on 2007-12-07
> **rsambuca said:**
> Close Skype and then open it from a terminal window.  Then test it on a video call. It should give some error message.

sorry for late reply :) i did start skype from terminal, but forgot to include the error message

the error i got was:
```
Starting the process...
Illegal instruction

```

after which the skype closes... there are no other messages when starting skype from the terminal... only these 2 lines

btw - i'm running fluxbuntu RC (gutsy based) latest updates...

ps. tried starting skype with sudo (just to be sure) and yes, i get the exact same error
pps. the cam i use is logitech quick cam (works perfectly with motion etc)

---

### Post by mendieta on 2007-12-09
Good news here ! The latest beta (2.0.0.27) solves the well known gspca crash after 1 minute of use, with my camera ([logitech stx]("http://ubuntuforums.org/showthread.php?t=487401")).

Many thanks to the skype team!

---

### Post by ronmarley1 on 2007-12-11
Just to add a bit here...  I have Skype version 2.0.0.27 and am able to video call with the Logitech QuickCam for Notebooks Pro.  All seems to work well.

EDIT: Maybe I spoke too soon...  I rtied it with another teacher here at school, who did not have a camera.  Video from my desktop to hers worked well.  I tried it last night from home, and sending video from me was fine, but I was not able to receive video.  I tried just running Metacity, instead of Compiz, and it did not improve.  So, the final result is...  it sorta works for me.

---

### Post by Atow on 2007-12-12
Calls work flawlessly on HP v5000 laptop.

1 minor issue is that you cannot have teamspeak open and make a skype call. it gives an error about ur audio device.

i dont have webcam so yeah

---

### Post by pablovp on 2007-12-15
Hi

I have a LG LIC-200 webcam, it's using the gspca driver.

The cam works on ekiga, but on skype it shows only a black screen when i click the test button.

Anyone solved this problem?

---

### Post by MarcRJacobs on 2007-12-16
Hi

I have a Microsoft LifeCam NX-6000  webcam.

This cam also works perfectly on ekiga, but on skype it shows only a black screen when i click the test button.

Anyone solved this problem?

---

### Post by Kosimo on 2007-12-16
> **MarcRJacobs said:**
> Hi

I have a Microsoft LifeCam NX-6000  webcam.

This cam also works perfectly on ekiga, but on skype it shows only a black screen when i click the test button.

Anyone solved this problem?

Have a look to the dedicated wiki (first post on this 3rd)
then search for your camera and find out the current status (if one)
If you can't find your camera, would be nice if you can add your information.

Cosimo.

---

### Post by MarcRJacobs on 2007-12-16
Hi Cosimo;
Thanks for the reply.
Sorry, I can't find the wiki "(first post on this 3rd)".  I guess I don't understand your instruction.  Can you please provide a link?
Thanks

---

### Post by meborc on 2007-12-16
i guess he ment this - [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) (first post on this thread)

---

### Post by Kosimo on 2007-12-17
> **meborc said:**
> i guess he ment this - [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) (first post on this thread)

Exactly ;)

---

### Post by HumanAnarchist on 2007-12-23
Is it possible to record the video in skype, if so, how can I do it?

-ha-

---

### Post by Hark3n on 2007-12-26
Good news everyone.

Just bought myself a Logitech Quickcam Express Plus, as recommended by the wiki, and it work flawlessly.

Only problem is that it went nearly completely dark halfway through the call to my brother.

After the call the video settings in Skype showed it at normal brightness again.

Anybody know what could be the problem.

Regards,
E

---

### Post by cytg on 2007-12-28
havent tried it yet, just wanna pitch in a 

HURRA! finally!  Merry friggin christmas to you too :)

---

### Post by xurizaemon on 2008-01-01
I grabbed the "Feisty" deb from Skype but it core dumped (I'm on Gutsy, they don't offer a Gutsy deb, and the feisty d/l is labelled "debian" anyway). 

It core dumped when trying to display the EULA screen. (Gotta love it.)

I purged that download, installed the 1.4 version from Medibuntu. Worked fine.

On a hunch, I then download the "dynamic" version and installing it in /opt - worked fine also. So then I removed skype and skype-common from medibuntu, and reinstalled the Feisty deb from Skype. And that one works now too.

(I suspect it was just the EULA screen that had issues? By installing Medibuntu and/or the dynamic version, I must have agreed to Skype's current EULA, and skipped that phase when reinstalling their Feisty deb. 

So there may be a cleaner workaround, like echo "yes" > ~/.all_my_words_are_belong_to_skype ...

---

### Post by Bossieman on 2008-01-01
I just ordered a QuickCam 9000 Pro that should work perfect with Skype according to the wiki. But now i read this thread and I see that people have problem with it?!? :confused:

Can someone tell me how it actually works? Is it just to plug in and start skype or do i have to install some drivers?

---

### Post by Bossieman on 2008-01-02
Well, the cam just arrived. I plugged it in and started up Skype2 beta and I had video and it all worked. 
Microphone doesnt work as far as I know.

---

### Post by Bastardbugger on 2008-01-02
To get the mic' working on the Logitech Quickcam Pro 9000 with Skype;

In Skype,  Options, Sound Devices, select the "Sound in" box and scroll to and select "USB Device 0x46d:0x990 (hw:U0x46d0x990,0)"

That is the USB mic on the webcam.

---

### Post by Bossieman on 2008-01-02
Thanks Bastardbugger, ill try that.
Now I noticed that videocall actually doesnt work for more than 10 seconds. How do you people fix this with the 9000? Any speciall drivers?

---

### Post by DrSpirograph on 2008-01-03
> **xurizaemon said:**
> (I suspect it was just the EULA screen that had issues? By installing Medibuntu and/or the dynamic version, I must have agreed to Skype's current EULA, and skipped that phase when reinstalling their Feisty deb. 

So there may be a cleaner workaround, like echo "yes" > ~/.all_my_words_are_belong_to_skype ...
It seems to be a combination of having an existing profile setup when the EULA is displayed.

I also got the core dump, so then I moved my ~/.Skye directory and it started up fine (including EULA).

So I moved the ~/.Skype directory back, and edited ~/.Skype/shared.xml, I changed
```
<Installed>1</Installed>
```to
```
<Installed>2</Installed>
```
that got rid of the EULA and Skype worked fine after that.

---

### Post by lilies34 on 2008-01-07
> **Kingsley said:**
> The video works flawlessly with the built-in web cam on my HP dv6000t laptop.

works perfectly with my toshiba laptop too! :popcorn:

---

### Post by mendieta on 2008-01-13
Guys, Version 2.0.0.27 fixes the 50 secs gspca driver crash. I can confirm with my STX Camera, and I updated the wiki, only for my camera:

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

I am planning to update the comments for all gspca based cameras unless someone objects. Please let me know ...

---

### Post by wjston on 2008-01-14
> **Bossieman said:**
> Thanks Bastardbugger, ill try that.
Now I noticed that videocall actually doesnt work for more than 10 seconds. How do you people fix this with the 9000? Any speciall drivers?

Go to your home folder>press Ctrl_H and this should show all hidden folders in your home folder. Navigate to the .Skype folder and then the folder with the config.xml file in it. Right click on the file and choose>open with> then choose either a text editor or Bluefish editor or some other editor that will allow you to add information. Add the part that I highlighted in red or a Height and Width that works for you. This hopefully will help.

<Video>
<AutoSend>1</AutoSend>
[COLOR="Red"]<CaptureHeight>600</CaptureHeight>
<CaptureWidth>800</CaptureWidth>
<Device>/dev/video0</Device>
<Fps>25</Fps>[/COLOR]
</Video>

---

### Post by mendieta on 2008-01-14
> **mendieta said:**
> Guys, Version 2.0.0.27 fixes the 50 secs gspca driver crash. I can confirm with my STX Camera, and I updated the wiki, only for my camera:

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

I am planning to update the comments for all gspca based cameras unless someone objects. Please let me know ...

Done!

---

### Post by Bossieman on 2008-01-15
> **wjston said:**
> Go to your home folder>press Ctrl_H and this should show all hidden folders in your home folder. Navigate to the .Skype folder and then the folder with the config.xml file in it. Right click on the file and choose>open with> then choose either a text editor or Bluefish editor or some other editor that will allow you to add information. Add the part that I highlighted in red or a Height and Width that works for you. This hopefully will help.

<Video>
<AutoSend>1</AutoSend>
[COLOR="Red"]<CaptureHeight>600</CaptureHeight>
<CaptureWidth>800</CaptureWidth>
<Device>/dev/video0</Device>
<Fps>25</Fps>[/COLOR]
</Video>

Thanks, I will try this.

---

### Post by wjston on 2008-01-15
> **Bossieman said:**
> Thanks, I will try this.

The height and width settings may vary depending on your video card. I am using an Nvidia FX5200. The best way to find out what resolutions your card/camera are capable of is to launch luvcview by typing luvcview -L in a terminal (you may have to install it). Also, make sure your camera is located at /dev/video0 (This may be different if you have one or more TV capture cards). You can verify this by going into the Skype options>VideoDevices and checking the location under the "Select Web Camera" option.

---

### Post by Bossieman on 2008-01-15
> **wjston said:**
> The height and width settings may vary depending on your video card. I am using an Nvidia FX5200. The best way to find out what resolutions your card/camera are capable of is to launch luvcview by typing luvcview -L in a terminal (you may have to install it). Also, make sure your camera is located at /dev/video0 (This may be different if you have one or more TV capture cards). You can verify this by going into the Skype options>VideoDevices and checking the location under the "Select Web Camera" option.

```
leif@Znote-6224W:~$ luvcview -L
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
/dev/video0 does not support read i/o
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
        Time interval between frame: 1/5, 
leif@Znote-6224W:~$ 
```

So I guess 960x720@10fps should work?

EDIT: Just tried 960x720@10 fps, skype dies after about a minute. Then I tested 320x240@30fps for about 10 minutes and it worked perfectly.

---

### Post by wjston on 2008-01-15
> **Bossieman said:**
> 

EDIT: Just tried 960x720@10 fps, skype dies after about a minute. Then I tested 320x240@30fps for about 10 minutes and it worked perfectly.

Great news. I would try higher settings until you find the one that best works for your video card and bandwidth. Just to let you know, my Skype has not froze once since I added the info to my config.xml file that I posted for you. Prior to this, I was unable to video conference for more than 10 seconds like you. Happy Skyping.

---

### Post by LostinSpacetime on 2008-01-25
Hello everybody :).
I have a (probably basic) question. First to my problem.
My webcam (Logitech Quickcam Messenger) works fine on my system (Ubuntu Feisty Fawn) and after using gstfakevideo, I can use it even in Skype. My problem, is that the picture is far to dark and the auto exposure doesn't work with the driver I have. It looks like the driver used is usbvideo, but I couldn't figure out how/if one can adjust the brightness with this driver. But I found out, that there is a far better driver for this webcam, namely the quickcam-usb driver. After downloading the source, and a "sudo make install" everything seemed to be ok. sudo modprobe quickcam did its job.
Now to my question. In my case I have (at least) two drivers which can handle the webcam. It looks like the device is still using the usbvideo driver. How can I change that???

Please help!!

---

### Post by erolerten on 2008-01-26
Hi Everyone

I also have a problem with my Logitech Quickcam Messenger. 

After a while during the video call, the LED on the camera starts blinking and skype crashes after couple of seconds.

So far I had been using the 2.0.0.13 after trying the 2.0.0.27 I will let you know the result.

---

### Post by mendieta on 2008-01-26
> **LostinSpacetime said:**
> 
Now to my question. In my case I have (at least) two drivers which can handle the webcam. It looks like the device is still using the usbvideo driver. How can I change that???

Please help!!

Hi Lost ! :-)

I think you simply need to blacklist the module you don't want to use. See for instance the instructions here:

[http://ubuntuforums.org/showthread.php?t=489679](http://ubuntuforums.org/showthread.php?t=489679)

You'll also need to reboot after blacklisting. Hope this helps!

---

### Post by LostinSpacetime on 2008-01-27
Hi mendieta, thx for answering. Actually I already tried that, but it didn't work, because usbvideo is built into the kernel. I know I could recompile now the kernel without it, but I would like to avoid that if somehow possible.

---

### Post by mendieta on 2008-01-27
> **LostinSpacetime said:**
> Hi mendieta, thx for answering. Actually I already tried that, but it didn't work, because usbvideo is built into the kernel. I know I could recompile now the kernel without it, but I would like to avoid that if somehow possible.
Hi

Are you sure it is compiled monolithically? It sure looks like a module (see the .ko extension):

```

grisell: ~> find /lib/modules/2.6.22-14-generic/ -iname "*usbvideo*"
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/usbvideo
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/usbvideo/usbvideo.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo

```

I can actually insert the module:

```
 
grisell: ~> sudo -i
[sudo] password for mendieta:
root@grisell:~# modprobe usbvideo
root@grisell:~# lsmod |grep usbvideo
usbvideo               28676  0
compat_ioctl32          2304  1 usbvideo
videodev               29568  2 usbvideo,gspca
usbcore               139912  9 usbvideo,snd_usb_audio,snd_usb_lib,usbhid,gspca,usblp,ehci_hcd,uhci_hcd

```

So, now I see it loaded, and listed as a videodev (my driver is gspca)

I can also remove the module:

```

root@grisell:~# rmmod usbvideo
root@grisell:~# lsmod |grep usbvideo
root@grisell:~# lsmod |grep gspca
gspca                 608208  0
videodev               29568  1 gspca
usbcore               139912  8 snd_usb_audio,snd_usb_lib,usbhid,gspca,usblp,ehci_hcd,uhci_hcd

```

I think you'll fix this soon if you play a bit with these commands. It could be that the blacklisting is not working. You may search the forums for that. Or maybe you are having a different issue ...

---

### Post by LostinSpacetime on 2008-01-28
Hmm.. U r right!!..  I also can load and unload usbvideo. However, even if not loaded, when I plug the webcam in,  the module is loaded automaticlly.. and blacklisting it doesn't help at all. Also, the module isn't listed in the /etc/modules file. I'm a little confused. :confused:

---

### Post by mendieta on 2008-01-29
> **LostinSpacetime said:**
> Hmm.. U r right!!..  I also can load and unload usbvideo. However, even if not loaded, when I plug the webcam in,  the module is loaded automaticlly.. and blacklisting it doesn't help at all. Also, the module isn't listed in the /etc/modules file. I'm a little confused. :confused:

I recall problems when trying to blacklist ipv6 some time ago, and now I found this interesting post:
[http://www.beranger.org/index.php?page=3k&fullarticle=2256](http://www.beranger.org/index.php?page=3k&fullarticle=2256)

Maybe one of the solutions posted there works for you ? Otherwise, I'd probably rename the offending module temporarily, you can always rename to the original name ... hope this helps!

---

### Post by Marianne_S on 2008-02-03
I have a philips spc 315 nc - and it works in skype beta (somehow it didn't last month - but now it does) - how do i register it in the [wiki]("https://wiki.ubuntu.com/SkypeWebCams") ?

---

### Post by mendieta on 2008-02-03
> **Marianne_S said:**
> I have a philips spc 315 nc - and it works in skype beta (somehow it didn't last month - but now it does) - how do i register it in the [wiki]("https://wiki.ubuntu.com/SkypeWebCams") ?

Hi Marianne

You need to look for "edit" somewhere in the page. It will ask you to login, you need an account is in launchpad, which is the system used to report bugs:

[https://launchpad.net/+login](https://launchpad.net/+login)

You probably even have an account there :-) 

Cheers, and thanks for contributing!

---

### Post by Thinker-Philosopher on 2008-02-06
FYI, Skype Beta 2.0.0.43 just came out (checked today, and haven't seen it posted anywhere).

---

### Post by Bossieman on 2008-02-06
> **Thinker-Philosopher said:**
> FYI, Skype Beta 2.0.0.43 just came out (checked today, and haven't seen it posted anywhere).

Thanks for the info!

---

### Post by project4 on 2008-02-06
I just installed skype 2.0.0.43 on my HP pavilion dv6373 (dv6000 series) and seems to be working fine... webcam was immediately recognized... just did a test video from the options menu. 

Still have to do a real video call though...

---

### Post by MattK358 on 2008-02-07
ThinkPad T61 built in webcam was instantly recognized, downloaded .deb, let GDebi update me from 1.4 to 2.0 and it just...worked.

---

### Post by sml on 2008-02-07
WOW!! This is the process ....
1. Skype was running.
2. Plugged in my brand new USB2.0 Logitech Quickcam Communicate STX.
3. Connect to a friend and turn on video and IT WORKS PERFECTLY!?!?

Is this really linux? haha

---

### Post by Pekkalainen on 2008-02-07
I have no one to do videocalls with atm so can anybody tell me if the 100% cpu problem is fixed?

---

### Post by Dropbear on 2008-02-07
Finally got my sony eyetoy to work with the 2.0.0.43 beta.
just followed the instructions at the bottom of this page [http://forum.skype.com/index.php?showtopic=100897&st=40]("http://forum.skype.com/index.php?showtopic=100897&st=40")
the inbuilt mic works as well
:guitar:

---

### Post by Pekkalainen on 2008-02-09
> **sml said:**
> WOW!! This is the process ....
1. Skype was running.
2. Plugged in my brand new USB2.0 Logitech Quickcam Communicate STX.
3. Connect to a friend and turn on video and IT WORKS PERFECTLY!?!?

Is this really linux? haha


Welcome to the world of *real* Plug & Play ;)

---

### Post by homersbrain on 2008-02-19
I cannot get it to run. A license agreement window pops up for a moment and disappears instantly. When I run it through the terminal, it reports ABORTED - CORE DUMPED. I'm running feisty. Anyone else had this problem?

---

### Post by Kosimo on 2008-02-19
I'm having a strange bug in this last version:

I can't pick up the calls that I receive!  But I can make calls with no problems at all.

---

### Post by Cappy on 2008-02-20
> **homersbrain said:**
> I cannot get it to run. A license agreement window pops up for a moment and disappears instantly. When I run it through the terminal, it reports ABORTED - CORE DUMPED. I'm running feisty. Anyone else had this problem?

Sounds like the old qt bug. You should try the statically linked version. I think the other way is to use a different qt version but I don't remember off the top of my head which one.

> **Kosimo said:**
> I'm having a strange bug in this last version:

I can't pick up the calls that I receive!  But I can make calls with no problems at all.

I had this happen to me when I had skype logged in on two computers. I couldn't answer calls.

---

### Post by savantelite on 2008-02-20
This makes me want the eeePC that much more.

---

### Post by CarpKing on 2008-02-20
It was nice of them to switch the "Show Myself" to X11 for those of us who only have one Xv port.  This just keeps getting better!

---

### Post by allan25 on 2008-02-22
Yes very sweet. Unlike my old Vista installation, I installed this last night under Kubuntu 7.10, plugged in my 18 month old Creative notebook webcam (unsupported under Vista) which I most often used in collaboration with my Gomeetnow conferencing software and it all worked fine. Good thing is that I don't have to make any configuration changes at all .

---

### Post by tdrusk on 2008-02-25
sweet action. I just bought my gf a webcam for her b-day and it works with it!

---

### Post by chiliroose1979 on 2008-02-28
My problem is still a "Black preview window". The webcam working nicely with other linux applications such as ekiga, xawtv, camorama, ...

Distro: ubuntu 7.10, Gutsy, linux-headers 2.6.22-14
Notebook: Fujitsu Amilo Pro V3515
Graphic card: VIA Technologies, Inc. Chrome9 HC IGP
Skype: 2.0.0.43 and the new 2.0.0.43-1
Cam: Creative Live!CAM Notebook

under vesa driver skype finds no Xv ports available and with compiled openchrome i get this log about video overlay:

Skype Xv: Xv ports available: 1
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 60
Skype Xv: No suitable overlay format found

i tried xorg.conf options "VideoOverlay" and "TexturedVideo" but no luck so far.
Maybe anyone here had any luck with a similar configuration?
what about the new X11 overlay in skype, why it doesnt fit? what do i have to change?
meantime solved through gstfakevideo & vesa ... can't get X11 with vesa to be used in someway. any clue would be nice;)
Thanks in advance,)

---

### Post by allan25 on 2008-02-29
Well there is another application with voice over IP functionality is the Gnome software -Ekiga, which has full support for the SIP and H.323 protocols. Currently I am testing it with my Rhubcom conferencing appliance on linux  platform. :KS

---

### Post by mjones41 on 2008-03-01
Yep works out of the box with my Creative VF0250 excellent, now just waiting for Pidgin to follow suit.

:guitar:

---

### Post by tdrusk on 2008-03-02
can someone please video conference with me so I can see if this works. I'm still waiting for my lady to get a laptop and I want to get all the kinks worked out.

---

### Post by Lady Owl on 2008-03-05
> **allan25 said:**
> Well there is another application with voice over IP functionality is the Gnome software -Ekiga, which has full support for the SIP and H.323 protocols. 
There's just the problem that "everybody" else is using skype... :-?

---

### Post by hrimhari on 2008-03-12
> **homersbrain said:**
> I cannot get it to run. A license agreement window pops up for a moment and disappears instantly. When I run it through the terminal, it reports ABORTED - CORE DUMPED. I'm running feisty. Anyone else had this problem?

I solved this problem by removing my old ~/.Skype folder as per a suggestion in [http://ubuntuforums.org/showpost.php?p=3946169&postcount=195](http://ubuntuforums.org/showpost.php?p=3946169&postcount=195)

---

### Post by rsambuca on 2008-03-13
Just an FYI - Version 2.0 has been officially released today.  A few bug fixes included.

---

### Post by allan25 on 2008-03-17
I still prefer gizmoproject along with [www.rhubcom.com]("http://www.rhubcom.com") Turbomeeting. The skype client for Linux still needs more improvement, but I'm glad they finally got this done.:)

---

### Post by GlorytheWIz825 on 2008-05-11
I am using a Logitech Orbit AF webcam and the split screen problem is still occurring. Shouldn't this have been fixed already? My Skype version is  2.0.0.68. Any tips on how I can go about fixing it or should I simply wait for the next release?

Thanks!

---

### Post by mendieta on 2008-05-11
> **rsambuca said:**
> Just an FYI - Version 2.0 has been officially released today.  A few bug fixes included.

Awesome, hope to see it in the 8.04 repositories soon!

---

### Post by smbtol on 2008-05-11
> **GlorytheWIz825 said:**
> I am using a Logitech Orbit AF webcam and the split screen problem is still occurring. Shouldn't this have been fixed already? My Skype version is  2.0.0.68. Any tips on how I can go about fixing it or should I simply wait for the next release?

Thanks!

Since upgrading to Ubuntu 8.04 I don't have the splitting problem anymore. I have a Logitech Fusion webcam.

---

### Post by GlorytheWIz825 on 2008-05-13
Thanks for the advice to the poster above. I upgraded to Hardy yesterday and the split screen problem is now gone. :)

---

### Post by hanzomon4 on 2008-05-17
How do you start a video call, macbook pro with working isight-cam

---

### Post by mendieta on 2008-05-17
> **hanzomon4 said:**
> How do you start a video call, macbook pro with working isight-cam

Go to the **Options** menu, and make sure the camera is detected in **Video Devices**. Select it, and decide whether the camera should be started automatically or manually during the calls. Enjoy!

---

### Post by gameryoshi600 on 2008-05-17
nice but i am going to wait till its final released.

---

### Post by meborc on 2008-05-18
> **gameryoshi600 said:**
> nice but i am going to wait till its final released.

2.0 is a final... or stable release... it is NOT a beta anymore... the thread started way back so that's why the title...

go check from skype.com if you have doubts :)

---

### Post by Ub1476 on 2008-05-18
I'm more anxious for Ekiga 3;)

Will be released in June I think.

---

### Post by meborc on 2008-05-18
> **Ub1476 said:**
> I'm more anxious for Ekiga 3;)

Will be released in June I think.

true... ekiga rocks... but the fact it is not cross-platform really makes it useless to me :(

for video - skype... for talking with a group of people - teamspeak

---

### Post by taikonaut on 2008-06-15
delete me

---

### Post by vaibshah on 2008-06-17
Hello!
I am new with the Ubuntu environment. How do I instal thel Skype on my  ubuntu computer?

I already downloaded skype-debian_2.0.0.72-1_i386.deb from the skype website. But the other steps seem to be not working. 
Can somebody please give me stepbystep guide.

Thanks ahead!!


> **Kosimo said:**
> Skype finally offers video conference for linux users.

Strongly recommended to give it a try.

Get a nice .deb from here:

[http://www.skype.com/intl/en/download/skype/linux/beta/]("http://www.skype.com/intl/en/download/skype/linux/beta/") 



It works for you?

Good luck!


EDIT: "kripkenstein" has created a wiki where you can find useful information about webcams compatibility list. You can check before buy it or just contribute to enlarge it.
Check it here:  [https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by Kosimo on 2008-06-17
> **vaibshah said:**
> Hello!
I am new with the Ubuntu environment. How do I instal thel Skype on my  ubuntu computer?

I already downloaded skype-debian_2.0.0.72-1_i386.deb from the skype website. But the other steps seem to be not working. 
Can somebody please give me stepbystep guide.

Thanks ahead!!

Hello, and welcome to the Ubuntu Community ;) 

The installation procedure is very simple: If you downloaded this .deb file (let's say in the Desktop) so you only need to double click that file, and then hit the button (Install) located at the top, right. Then It ask to insert your password. Once you type it, it'll start installing skype. Once installed you'll find skype in (Applications > Internet)

Pretty simple.
Good luck! And please feel free to asking if you get in trouble

---

### Post by vaibshah on 2008-06-17
Thanks for the quick reply!

That double clicking I did. But it gave the message Error: dependency is not satisfiable: libasound2

what does this mean?

Infact my main concern now, is to install Logitech QuickCam Pro9000 which seems to be difficult due to missing stuff on my Ubuntu 6.06. I don't get to run the commands I see on the forums.

Any clues?

Thanks ahead!

---

### Post by Kosimo on 2008-06-17
> **vaibshah said:**
> Thanks for the quick reply!

That double clicking I did. But it gave the message Error: dependency is not satisfiable: libasound2

what does this mean?

Infact my main concern now, is to install Logitech QuickCam Pro9000 which seems to be difficult due to missing stuff on my Ubuntu 6.06. I don't get to run the commands I see on the forums.

Any clues?

Thanks ahead!

Ooooops....
You're using Ubuntu 6.06 witch is a quite "old" release and doesn't automatically installs all needed dependencies.    You're using this version for any particular reason? Otherwise you can give it a try to the very last release: Ubuntu Hardy Heron 8.04 witch will solve this problem (appart of having an update software)  

If you want to upgrade your operating system just open Terminal (Application > Accessories > Termina)  And type: 

```
sudo apt-get update (it asks for password, type it and then intro)

sudo apt-get dist-upgrade 
```

---

### Post by vaibshah on 2008-06-17
Hi!
Well, no special reason for using this version. We just got it with the computer. And I am actually building an application with some CNC machines. The operating system has some application already installed on it. 

If I upgrade the OS, will it harm any applications installed already? or not? For e.g. I have installed LabVIEW on it, and also, some other tools came with this for free, which are critical to my application.

Best regards!

> **Kosimo said:**
> Ooooops....
You're using Ubuntu 6.06 witch is a quite "old" release and doesn't automatically installs all needed dependencies.    You're using this version for any particular reason? Otherwise you can give it a try to the very last release: Ubuntu Hardy Heron 8.04 witch will solve this problem (appart of having an update software)  

If you want to upgrade your operating system just open Terminal (Application > Accessories > Termina)  And type: 

```
sudo apt-get update (it asks for password, type it and then intro)

sudo apt-get dist-upgrade 
```

---

### Post by vaibshah on 2008-06-17
Well, executed the commands!

Thanks. 
But not sure if my OS is already a new version or not, because the System>About Ubuntu still shows 6.06 version.

Anyways, now, how do I go ahead?

---

### Post by lswest on 2008-06-17
> **vaibshah said:**
> Well, executed the commands!

Thanks. 
But not sure if my OS is already a new version or not, because the System>About Ubuntu still shows 6.06 version.

Anyways, now, how do I go ahead?

Can you post the results of ```
uname -a
``` please?

Also, you can try installing the package again, if it succeeds, chances are it worked ;) (lastly, did you reboot before checking the "about Ubuntu" section?)

---

### Post by Kosimo on 2008-06-17
> **vaibshah said:**
> Well, executed the commands!

Thanks. 
But not sure if my OS is already a new version or not, because the System>About Ubuntu still shows 6.06 version.

Anyways, now, how do I go ahead?

Here an official ubuntu webpage witch tells you exactly how to upgrade your system,  in another easy way:  

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by vaibshah on 2008-06-17
Thanks for the link!

Can you please give me step-by-step guide for installing skype. The setup still gives the same error of libasound2

Best regards!

---

### Post by vaibshah on 2008-06-17
Hi!

Installation had no error, and even after rebooting it shows Ubuntu 6.06.

Also,

uname -a  gives
$ uname -a Linux lakos150-desktop 2.6.15-magma #1 Fri Jun 9 20:51:19 EEST 2006 i686 GNU/Linux


Thanks!


> **lswest said:**
> Can you post the results of ```
uname -a
``` please?

Also, you can try installing the package again, if it succeeds, chances are it worked ;) (lastly, did you reboot before checking the "about Ubuntu" section?)

---

### Post by HumanAnarchist on 2008-06-18
Maybe the upgrade failed, it looks like you have a custom version of Ubuntu, but you can try to install the dependencies manualy, just search for it in Synaptics or at google, sometimes files that are asked for as dependencies are included in other packages so they don't show up in synaptic search (stupid) 

What guy did you get the machine from? Why is it so special?

---

### Post by vaibshah on 2008-06-18
Hi! 
Thanks for the message.

We got these machines with our custom made CNC machines. So probably they have this 'special' ubuntu with no other features.

Can you tell me please how do I go step by step through synaptic manager, to install these dependencies. For eg, to install our previous features, I reloaded the synaptic package manager after selecting the dependencies which were needed and it installed them. 

Not sure which dependencies are needed this time, for my Logitech QuickCam Pro 9000 camera or for Skype (libasound2).

Thanks!

> **HumanAnarchist said:**
> Maybe the upgrade failed, it looks like you have a custom version of Ubuntu, but you can try to install the dependencies manualy, just search for it in Synaptics or at google, sometimes files that are asked for as dependencies are included in other packages so they don't show up in synaptic search (stupid) 

What guy did you get the machine from? Why is it so special?

---

### Post by HumanAnarchist on 2008-06-18
First install skype after you've satisfied the dependencies. 

```


sudo apt-get install libasound2

```

If that's the only dependency you needed, skype shold be installed. 

Then you can get on to make the webcam work. Your webcam seams to be supported: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) but the driver is not included in Ubuntu 6.06.... so you must install it from source... It's not hard, but you need some more programs, like subversion and build-essensial, I think that is enough.

Then do this:

```

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
sudo make install

```

If that worked well, your cam should work with skype... (cross fingers:))

---

### Post by vaibshah on 2008-06-18
Hi!

Thanks for the reply!

Well, I have already tried to install the libasound2 and it continues with the same error.

Also, subversion command doesn't work in my system. earlier the command didn't work, and then, it started giving timed out error, i.e. it couldn't connect with the svn.berlios.de server.

Today finally, I upgraded to Ubuntu 8.04 and now, don't know if my webcam is going to work just out of the box (as others say) or I will have to do some more struggle. :)

(fingers crossed :) )


> **HumanAnarchist said:**
> First install skype after you've satisfied the dependencies. 

```


sudo apt-get install libasound2

```

If that's the only dependency you needed, skype shold be installed. 

Then you can get on to make the webcam work. Your webcam seams to be supported: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) but the driver is not included in Ubuntu 6.06.... so you must install it from source... It's not hard, but you need some more programs, like subversion and build-essensial, I think that is enough.

Then do this:

```

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
sudo make install

```

If that worked well, your cam should work with skype... (cross fingers:))

---

### Post by Kosimo on 2008-06-18
> **vaibshah said:**
> Hi!

Thanks for the reply!

Well, I have already tried to install the libasound2 and it continues with the same error.

Also, subversion command doesn't work in my system. earlier the command didn't work, and then, it started giving timed out error, i.e. it couldn't connect with the svn.berlios.de server.

Today finally, I upgraded to Ubuntu 8.04 and now, don't know if my webcam is going to work just out of the box (as others say) or I will have to do some more struggle. :)

(fingers crossed :) )

Good!  
Now, have a look at the first page of this topic, where you can find a Wiki  with useful information about Webcams compatibility on Skype.

Good luck!

---

### Post by reginr on 2008-06-19
[QUOTE=toupeiro;3729548]Working flawlessly with Logitech Quick Cam Ultra Vision and 7.10!!

What is your Linux box setup?

Thanks :)

---

### Post by vaibshah on 2008-06-20
Hey!!

I upgraded the system to 8.04 and then did some reloading and installed the updates (automatic, not specifically some special package, except monodevelop which is used for my own application).

Then, Just connected the QuickCam 9000 and it worked without any settings. First, I tried to see it in Ekiga and it worked. 

Then, I installed Skype by just double clicking on the .deb setup. Yesterday it didn't work because there was an error of broken package of some another application I installed.

Now, skype works, but the video is completely junk. Looks like from some old science fiction where there is some grain on the screen and not a specific video. :lolflag:

Now I will check out the other comments on this thread and will see if they had the same problem or not. At least, now I find my system in that level.

Thanks!

 
> **Kosimo said:**
> Good!  
Now, have a look at the first page of this topic, where you can find a Wiki  with useful information about Webcams compatibility on Skype.

Good luck!

---

### Post by Kosimo on 2008-06-22
Hey guys... There is a new version for linux:   Version 2.0.0.72


I'm looking at the changelog. But I strongly recommend an update!

---

### Post by Kosimo on 2008-06-22
here the changelog for 2.0.0.72:

- feature: Show 'Edited by' on chat messages if they were edited later.
- feature: Added notifications for role changes in group chats
- feature: Add displaying new chat guidelines for public chat.
- bugfix: Video degraded slowly over time
- bugfix: Workaround for crashes with messages that contain Tab characters on Qt 4.4.0.
- bugfix: Fix for pressing Escape in Quickfilter for Qt 4.4.
- Localizations updated: Bulgarian, French, Lithuanian, Polish, Turkish language updates.

---

### Post by dixon on 2008-06-22
What about pulseaudio? Is it fixed in the new release?

---

### Post by JohnSearle on 2008-06-22
> **dixon said:**
> What about pulseaudio? Is it fixed in the new release?

I'm using the newest version right now... and no it's not.

- John

---

### Post by Mr_B on 2008-06-22
I need HELP! I have to admit that I am somewhat of a n00p but I am not afraid of the terminal window. I have Ubuntu 8.04 and a "Logitech Quickcam for Notebooks Pro" on a Sony Vaio Laptop. I have Skype 2.0.0.72 installed and Camorama and EasyCam2 and "svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk"

Lauchcam2 (Easycam2) sees the usb camera as "Bus 005 Device 007: ID 046d:08c3 Logitech, Inc." and when I run the EasyCam driver installation, I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-19-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15 sword-text-arasvd gtkhtml3.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mkdir: cannot create directory `/lib/modules/2.6.24-19-generic/kernel/drivers/usb/media-back': File exists
cp: cannot stat `/lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/*': No such file or directory
cd: 1: can't cd to /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video': File exists
rm -f *.o *.ko .*.cmd .*.flags *.mod.c
rm -rf .tmp_versions

```

After the installation, when I click on Properties, Webcam in EasyCam, I get a popup window: Error (camorama); Could not connect to video device (/dev/video0). Please check the connection.

I already spent several hours on this an I need help... Please.

---

### Post by jrusso2 on 2008-06-22
I just installed Skype a few days ago on Gutsy and every time I start my webcam it crashes it.

---

### Post by HumanAnarchist on 2008-06-25
> **Mr_B said:**
> I need HELP! I have to admit that I am somewhat of a n00p but I am not afraid of the terminal window. I have Ubuntu 8.04 and a "Logitech Quickcam for Notebooks Pro" on a Sony Vaio Laptop. I have Skype 2.0.0.72 installed and Camorama and EasyCam2 and "svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk"

Lauchcam2 (Easycam2) sees the usb camera as "Bus 005 Device 007: ID 046d:08c3 Logitech, Inc." and when I run the EasyCam driver installation, I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-19-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15 sword-text-arasvd gtkhtml3.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mkdir: cannot create directory `/lib/modules/2.6.24-19-generic/kernel/drivers/usb/media-back': File exists
cp: cannot stat `/lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/*': No such file or directory
cd: 1: can't cd to /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video': File exists
rm -f *.o *.ko .*.cmd .*.flags *.mod.c
rm -rf .tmp_versions

```

After the installation, when I click on Properties, Webcam in EasyCam, I get a popup window: Error (camorama); Could not connect to video device (/dev/video0). Please check the connection.

I already spent several hours on this an I need help... Please.

Never heard about easycam, but if your cam is supported, it should be enough to do 'make' and 'sudo make install' to get the latest uvc drivers going.

---

### Post by Kosimo on 2008-08-02
HI guys!
It's been a while since the last skype version 2.0.0.72. 
Does anyone know how is the develop going on Skype linux team?

---

### Post by Dustin2128 on 2011-06-16
> **Macskeeball said:**
> Yeah, it reminds me of spam comments I get on my blog, which seem to be automated based on keywords in the article titles.
That's most likely exactly what it is- no posts. Why people would spam ubuntu forums though... beyond me.

---

### Post by frodon on 2011-06-16
Useless necromancing.

Thread closed

---

### Post by frodon on 2011-06-16
Unnecessary necromancing.

Thread closed

---

