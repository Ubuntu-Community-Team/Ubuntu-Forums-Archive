---
title: "VLC 2.0 will be released..."
date: 2012-01-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by forcecore on 2012-01-24
Looks like VLC 2.0 will be released before feature freeze, i hope any day it will arrive official repo.

---

### Post by Double.J on 2012-01-24
Thanks for this forcecore, I had no idea! 

I grabbed 2.0.0RC1 from ppa:videolan/stable-daily - only tested the basics - find media, play media, make playlist, play playlist, but no obvious glaring bugs :)

---

### Post by mc4man on 2012-01-24
the 2.0 stable is basically vlc-1.2 (twoflower) which is superior to the current stable release so hopefully it will show in PP.
One of the interesting things, though somewhat not intentional, is 1.2 does work in the sound menu to an extent. (shows, can open vlc, pause, change tracks, display album art) though it can't be minimized to the menu.

Whether it ever gets full sound-menu support who knows, probably not from the vlc/videolan side

---

### Post by kansasnoob on 2012-01-25
I'll bet this has something to do with these held packages:

```
The following packages have been kept back:
  libavformat53 libpostproc52 libswscale2

```

Maybe :confused:

---

### Post by mc4man on 2012-01-25
> **kansasnoob said:**
> I'll bet this has something to do with these held packages:

```
The following packages have been kept back:
  libavformat53 libpostproc52 libswscale2

```

Maybe :confused:
If you're showing held libav* shared lib packages it may be because you have some libav* -extra versions installed, the non extra upgraded, the extra haven't yet. Synaptic would tell you, search libav, scroll down

---

### Post by zika on 2012-01-25
In ~17 hours we will know how it looks like... ;)
At my place the reason for wait is mozilla-plugin-vlc...
Wait for new build or purge mpv and install it later? That is the question...
Of course, it was no brainier. It works just fine...

---

### Post by forcecore on 2012-01-25
I hope too it reaches to official repo because imagine Ubuntu 12.04.5 after 3-4 years with VLC 1.1.13.

---

### Post by cariboo on 2012-01-25
> **forcecore said:**
> I hope too it reaches to official repo because imagine Ubuntu 12.04.5 after 3-4 years with VLC 1.1.13.

Fortunately most of us here won't have that problem, by the time an Ubuntu version is released, we are champing at the bit to start testing the next version. :)

---

### Post by forcecore on 2012-01-25
> **cariboo907 said:**
> Fortunately most of us here won't have that problem, by the time an Ubuntu version is released, we are champing at the bit to start testing the next version. :)

...and mostly me too but i think of others who for example gets laptop with U12.04 and stays there and only knows how to install VLC with Software Center. My Ubuntu always is customized with UCK and needed PPA-s integrated so i have no problem.

---

### Post by kansasnoob on 2012-01-25
> **mc4man said:**
> If you're showing held libav* shared lib packages it may be because you have some libav* -extra versions installed, the non extra upgraded, the extra haven't yet. Synaptic would tell you, search libav, scroll down

Yes, I have both 'libavutil-extra-51' and 'libavcodec-extra-53' installed. Right now I'm going to wait a bit and see if things don't resolve themselves :)

---

### Post by zika on 2012-01-25
> **kansasnoob said:**
> Yes, I have both 'libavutil-extra-51' and 'libavcodec-extra-53' installed. Right now I'm going to wait a bit and see if things don't resolve themselves :)I'll start motion to expel You from testing department... [IMG]http://images.zaazu.com/img/thinking-idea-animated-animation-smiley-emoticon-000339-large.gif[/IMG][IMG]http://images.zaazu.com/img/Normal-people-scare-me-normal-people-scare-smiley-emoticon-001138-large.gif[/IMG][IMG]http://www.sherv.net/cm/emo/laughing/roflmao.gif[/IMG]

---

### Post by mc4man on 2012-01-25
> **kansasnoob said:**
> Yes, I have both 'libavutil-extra-51' and 'libavcodec-extra-53' installed. Right now I'm going to wait a bit and see if things don't resolve themselves :)
Well you could make all your installed libav packages the extra versions or wait until the extra updates.
(if you needed to install the dev libav packages then you'll need to wait or go back to the non-extra versions

Didn't see any mention [so reported a bug on]("https://bugs.launchpad.net/ubuntu/+source/libav-extra/+bug/921765") - seems launchpad has a new look (got a response in 2 min.

fixed in extra packages *(4:0.8.0.1)

Ot - see that from a terminal ffmpeg <whatever> is now recommending one uses avconv <whatever>, which is fine.
The message however seems to continue on with some of the same Libav vs. FFmpeg bs - 

"This program is not developed anymore and is only provided for compatibility." which is absolutely untrue...

---

### Post by t1497f35 on 2012-01-26
Anyone knows the location on launchpad of ppa:videolan/stable-daily ?

---

### Post by zika on 2012-01-26
> **t1497f35 said:**
> Anyone knows the location on launchpad of ppa:videolan/stable-daily ?
[https://launchpad.net/~videolan/+archive/stable-daily](https://launchpad.net/~videolan/+archive/stable-daily)
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

---

### Post by kansasnoob on 2012-01-26
All updated OK this AM, no more held packages :)

---

### Post by jfernyhough on 2012-01-26
Ack, the VLC 2 build kills my X when it tries to use hardware acceleration. VLC 1.1.3 works OK.

---

### Post by andrew.46 on 2012-01-27
For those who are not keen on PPAs the source is here:

[http://download.videolan.org/pub/videolan/testing/vlc-2.0.0-rc1/vlc-2.0.0-rc1.tar.xz](http://download.videolan.org/pub/videolan/testing/vlc-2.0.0-rc1/vlc-2.0.0-rc1.tar.xz)

Edit: There is a somewhat neglected guide somewhere on these forums that describes how to build from vlc from source.....

---

### Post by t1497f35 on 2012-01-28
It's a great release, though I can't find any longer the option to disable the subtitles by default.

---

### Post by andrew.46 on 2012-01-28
> **t1497f35 said:**
> It's a great release, though I can't find any longer the option to disable the subtitles by default.

Strictly speaking it has not been released yet :). Screenshot for the subtitle option...

---

### Post by t1497f35 on 2012-01-28
Thanks, that option is disabled as on your screenshot, but still when I start a movie with subtitles (e.g. built into an mkv container) it still shows the subs by default, until I go to Subtitles->Disable to get rid of them. I have to do so each time.

---

### Post by A_T on 2012-01-29
Is saving of bookmarks still broken?

---

### Post by mc4man on 2012-01-29
> **A_T said:**
> Is saving of bookmarks still broken?

I guess that would depend on how you're trying to save. If you set your bookmark(s), then save as a playlist, it has & continues to work fine. 
(this applies to all vlc versions since 1.1.3
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/620290](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/620290)

---

### Post by mc4man on 2012-01-31
It would appear, at least for the moment, that at least the 2.0 version can't retrieve audio cd info/album art from vlc's default freedb server.
(haven't tried the 1.1.13 yet

If so affected it can be changed to another server as in screen, in this case just using freedb.freedb.org

---

