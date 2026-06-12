---
title: "iPhone/iPod Touch music player with linux support!!!"
date: 2008-09-23
forum: The Cafe
---

### Post by Guillaume86 on 2008-09-23
Hi everybody, 

Some of you own an iPhone or an iPod Touch i bet, and you can't upload music from Ubuntu since you upgraded to 2.0 firmware -_-. I have great news for you ( for all the poeple who doesn't like iTunes actually ), an app is going to be released soon on Cydia, it's called pwnPlayer, i'm in touch with the developper (Errrick) and he's doing a great job on that, his player is going to be far better than the official one.

You'll be able to upload music on your device via wifi ( sftp or samba share for exemple ) and listen to it with that player.
The player will have extra features like lock screen controls, search in library, etc
For more information and a video please visit: [http://www.pwnplayer.com/](http://www.pwnplayer.com/)
Some very cool features are coming like plugin support(!!!) sharing library with other devices via wifi etc
The author hope the linux community will pay interest in his work, I do :)

PS: if somebody want to make a planet post about this, feel free to do it ;)

---

### Post by tom-ubuntu on 2008-09-24
Great stuff  :-) Looking forward to that.

Any idea on a release date?
Do you know if it works with 2.1 as well?

Cheers

---

### Post by Vadi on 2008-09-24
That's nice.

Next audio player I'm buying will be an iAudio from Cowon, most likely. They advertise Linux support, and their players look great :)

Go to [http://www.cowonglobal.com/](http://www.cowonglobal.com/), click on MP3, you'll find that all models do that ;)

---

### Post by Octagonal on 2008-09-24
All well and good but this requires a jailbroken ipod touch or iphone.  From the latest info I've read iphone 3G and 2nd Gen Ipod Touches still cannot be jailbroken.
So in order to even think about using this soon, you'd need an ipod touch first gen or a non 3G Iphone, which would have to be jailbroken.

---

### Post by zavius on 2008-09-24
I can't speak for the new touches but I can say 100% that the 3G is jailbroken. I've had mine cracked for days after 2.1 came out.

Problem now is that there doens't appear to be any movement on the new ipod hashing scheme. Hopefully sometime soon but theres little to no information out there about it.

---

### Post by Crafty Kisses on 2008-09-24
That looks pretty good, I was looking into openMOKO.

---

### Post by styfle on 2008-09-24
Wow the Lock-Screen gesture controls are tight.

---

### Post by Octagonal on 2008-09-24
You're right Zavius, I read on [http://blog.iphone-dev.org/](http://blog.iphone-dev.org/) and I read unlocked as jailbroken for the 3g iphone.  So it looks like we are still waiting for 2nd gen touches to be jailbroken but everything else looks good.

---

### Post by Guillaume86 on 2008-09-25
iPhones 3G are jailbreakable :)

Actually with Apple DNA, there is no other choice than jailbreak to make a really usefull app (background listening, double tap on home controls etc). And with the features that are comming (seeqpod download, library sharing over wifi, ...) it would never have been accepted in the App Store :).

edit: release very soon, within 2 weeks i think from what errick said he had still to do( and of course no problem with 2.1...)

---

### Post by Guillaume86 on 2008-10-26
PwnPlayer has been released on Cydia, good news for all the linux user!

---

### Post by zmjjmz on 2008-10-26
> **Guillaume86 said:**
> PwnPlayer has been released on Cydia, good news for all the linux user!

Do I have to add a special repo?

(By the way, if anyone doesn't want to use Beta software (PwnPlayer is Beta 5) but still wants half-decent music playback on their iPhone/iPod Touch, they can install dTunes)
EDIT: No special repos, I'm installing it now.

---

### Post by init1 on 2008-10-26
Yeah, but you have to Jailbreak it. I'd rather keep mine legal for now.

---

### Post by Guillaume86 on 2008-10-26
> **init1 said:**
> Yeah, but you have to Jailbreak it. I'd rather keep mine legal for now.

Jailbreak is completely reversible if it's what you're afraid of...

---

### Post by zmjjmz on 2008-10-26
> **Guillaume86 said:**
> Jailbreak is completely reversible if it's what you're afraid of...

...
And completely legal.
Oh, and it's not like you lose the Appstore. The Appstore and all your music and videos are still there.

EDIT: Right, I like PwnPlayer but I have a few issues:
A) Being a Linux user, I have to use filesystem playback.
I was pretty sure I had the music on there already, but PwnPlayer didn't find it, so I put it in /var/mobile/Media/Music 
Now, I have a bunch of tracks from 8bitpeoples, and these don't play at all. I can select one to play and it just skips over all of them.
It could be due to the unusual naming scheme, but other songs have worse names yet play fine. Can anyone help me on this?

Note: This happens with dTunes too.

---

### Post by MaindotC on 2008-10-26
> **Vadi said:**
> That's nice.

Next audio player I'm buying will be an iAudio from Cowon, most likely. They advertise Linux support, and their players look great :)

Go to [http://www.cowonglobal.com/](http://www.cowonglobal.com/), click on MP3, you'll find that all models do that ;)

This player looks pretty good.  Why are pmp's only coming with FM radios, and not AM?

---

### Post by Guillaume86 on 2008-10-27
> **zmjjmz said:**
> ...
And completely legal.
Oh, and it's not like you lose the Appstore. The Appstore and all your music and videos are still there.

EDIT: Right, I like PwnPlayer but I have a few issues:
A) Being a Linux user, I have to use filesystem playback.
I was pretty sure I had the music on there already, but PwnPlayer didn't find it, so I put it in /var/mobile/Media/Music 
Now, I have a bunch of tracks from 8bitpeoples, and these don't play at all. I can select one to play and it just skips over all of them.
It could be due to the unusual naming scheme, but other songs have worse names yet play fine. Can anyone help me on this?

Note: This happens with dTunes too.

First try to rename the files, then try to get the syslog, it's beta there's some special characters problems, but I'm afraid it's something else if it happens for all the album (unusual encodage). The pwnPlayer forum is there: [http://forum.pwnplayer.com/](http://forum.pwnplayer.com/) for bug report

---

### Post by zmjjmz on 2008-10-27
> **Guillaume86 said:**
> First try to rename the files, then try to get the syslog, it's beta there's some special characters problems, but I'm afraid it's something else if it happens for all the album (unusual encodage). The pwnPlayer forum is there: [http://forum.pwnplayer.com/](http://forum.pwnplayer.com/) for bug report

I'm completely lost as to why these songs don't work, because comparing the Audio/Video properties to songs that do work don't give me anything useful.

---

### Post by myusername on 2008-10-27
the only bad thing is that it requires jailbreak. i tried pwnplayer last night and its kinda slow and buggy. hopefully it will get better since its just a beta

---

### Post by Guillaume86 on 2008-10-28
> **zmjjmz said:**
> I'm completely lost as to why these songs don't work, because comparing the Audio/Video properties to songs that do work don't give me anything useful.

If you can send me a song I can try to find out what's goin on, you got a link to one of the songs?

---

### Post by stevenyu on 2008-10-29
Hi Guys

I am planning to upgrade my ipod 60gb classic to either 120gb classic or the 32gb ipod touch with the latest v2 firmware.

I did few search on the net, it seems a lot of people is having problem mounting the new firmware ipod under linux, can any of you confirm this?

Thanks in advance!!!

---

### Post by Guillaume86 on 2008-10-29
> **stevenyu said:**
> Hi Guys

I am planning to upgrade my ipod 60gb classic to either 120gb classic or the 32gb ipod touch with the latest v2 firmware.

I did few search on the net, it seems a lot of people is having problem mounting the new firmware ipod under linux, can any of you confirm this?

Thanks in advance!!!

iPod touch has SSH, over wifi, no problems to mount that (at least after jailbreak). You can also mount it via usb without jailbreak but you'll only access to the userspace files.

---

### Post by stevenyu on 2008-10-29
Is there a software like itune which allow user to manage their music collection, and auto sync it between the ipod and the HDD?  and support audio cd rip?

---

### Post by zmjjmz on 2008-10-29
The songs are on 8bitpeoples.com
Oy, stevenyu, google "gtkpod ipod touch"
I personally think you should get an older 80GB iPod and install Rockbox, but it won't "sync" (you need to put the music on manually).
There's a CD ripping program that comes with Ubuntu that you can use, but it rips to ogg by default so if you want to put the files on an iPod without Rockbox you'll need to make sure they're in mp3 format.

---

### Post by stevenyu on 2008-10-29
> **zmjjmz said:**
> I personally think you should get an older 80GB iPod and install Rockbox, but it won't "sync" (you need to put the music on manually).


This is my current format already, maybe this is still the best way of using iPod under Linux.

---

### Post by zmjjmz on 2008-10-29
> **stevenyu said:**
> This is my current format already, maybe this is still the best way of using iPod under Linux.
Well Rockbox is awesome.
So yes, it is one of the best ways use an iPod.
Ever.

---

### Post by Guillaume86 on 2008-10-30
> **zmjjmz said:**
> Well Rockbox is awesome.
So yes, it is one of the best ways use an iPod.
Ever.

On new firmwares iPod Touch/iPhones you can auto sync a folder mounted via ssh (over wifi) and read the files with pwnPlayer, you just need a little script running on your linux. It's in my opinion a very nice way to sync a mp3 player...

---

### Post by zmjjmz on 2008-11-01
I think that the iPod Touch is more of an MID than an iPod, which falls under the category of a PMP.
By the way, have you been able to work out some of that music?

---

### Post by Guillaume86 on 2008-11-01
> **zmjjmz said:**
> I think that the iPod Touch is more of an MID than an iPod, which falls under the category of a PMP.
By the way, have you been able to work out some of that music?

It's working on my device, I've tested with Modelness on The Slaphappy Bee III EP

---

### Post by zmjjmz on 2008-11-01
> **Guillaume86 said:**
> It's working on my device, I've tested with Modelness on The Slaphappy Bee III EP

That's really odd.
I'll try redownloading it then, see if that works.
EDIT: That works...?
Maybe they just updated the songs or something. Solved.

---

### Post by Guillaume86 on 2008-11-02
> **zmjjmz said:**
> That's really odd.
I'll try redownloading it then, see if that works.
EDIT: That works...?
Maybe they just updated the songs or something. Solved.

Computer science is not really an exact science :)

---

### Post by init1 on 2008-11-02
> **zmjjmz said:**
> ...
And completely legal.

I was under the impression that it violated the EULA, but I can't find any sites that confirm that.

---

### Post by areskz on 2009-01-03
Has someone managed to establish a connection with iPhone/iPod Touch within Linux **without **using wifi? 

In Windows they have iPhone Tunnel Suite, that allows to connect to an iPhone via usb cable, using ssh. 

How can we use ssh and connect without wifi?

---

### Post by juanmoreno92 on 2009-01-03
VLC has been ported to the iPhone if anyone is interested.

---

### Post by Guillaume86 on 2009-01-05
> **areskz said:**
> Has someone managed to establish a connection with iPhone/iPod Touch within Linux **without **using wifi? 

In Windows they have iPhone Tunnel Suite, that allows to connect to an iPhone via usb cable, using ssh. 

How can we use ssh and connect without wifi?

the iphone linux project have something to connect via usb without ssh, i succeed to compile and use it some time ago, try a google search

---

### Post by Jota37 on 2009-11-09
Pwnplayer is gone, and might come back in the future, author says.

Anyway, I just found this, which might help in the near future and NOT require jail-breaking, from what I've understood:

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/]("http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/")

So, according to the developer, the hash has been reverse-engineered "enough":
> The new hash has been reverse engineered enough to bring near full functionality to Linux

Right now, it helps jail-broken devices by allowing them to use USB intead of WiFi, if I understood the info correctly.

I'll keep watching that, but it seems like full support, or at least as good as it is for my 1st gen nano, is coming soon. For some values of soon, of course. :-)

Only then I'll think of buying a Touch.

---

