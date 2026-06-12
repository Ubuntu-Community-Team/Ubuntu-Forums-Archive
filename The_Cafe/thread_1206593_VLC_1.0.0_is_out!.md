---
title: "VLC 1.0.0 is out!"
date: 2009-07-07
forum: The Cafe
---

### Post by jsmidt on 2009-07-07
Go [get it]("http://www.videolan.org/vlc/")!  As [Matt Asay]("http://news.cnet.com/8301-13505_3-10280845-16.html?tag=mncol;title") writes:

Here are a few of the features now available in VLC 1.0.0:

    * Live recording
    * Instant pausing and frame-by-frame support
    * Finer speed controls
    * New HD codecs (AES3, Dolby Digital Plus, TrueHD, Blu-ray Linear PCM, Real Video 3.0 and 4.0, ...)
    * New formats (Raw Dirac, M2TS, ...) and major improvements in many formats
    * New Dirac encoder and MP3 fixed-point encoder
    * Video scaling in full screen
    * RTSP Trickplay support
    * Zipped file playback
    * Customizable toolbars
    * Easier encoding GUI in Qt interface
    * Better integration in Gtk environments
    * MTP devices on Linux
    * AirTunes streaming

---

### Post by chozoboy on 2009-07-07
So can I buy a Blu-ray version of say "The Dark Knight", pop it in my laptop's BD/DVD/CD drive and play the movie?

---

### Post by Short__Error on 2009-07-07
:O cant wait to get this :|

---

### Post by Yvan300 on 2009-07-07
Is it updated in the repos yet or do i have to add a ppa, if so what is it?

---

### Post by RiceMonster on 2009-07-07
hmmm... I'll give it a try and see if it makes me want to switch out of Mplayer (hightly doubt it), but I'll probably just use it for DVDs.

---

### Post by Arup on 2009-07-07
Only C.Korn's ppa has it. Sadly no vdpau support yet as I had hoped for.

---

### Post by northwestuntu on 2009-07-07
> **Arup said:**
> Only C.Korn's ppa has it. Sadly no vdpau support yet as I had hoped for.

well why did they even waste the time of releasing it without that?

---

### Post by sertse on 2009-07-07
vlc mozilla plugin still hasn't have a gui yet? Move along then...

---

### Post by Muffinabus on 2009-07-07
Excellent, thanks for the heads up!

---

### Post by Sealbhach on 2009-07-07
> **chozoboy said:**
> So can I buy a Blu-ray version of say "The Dark Knight", pop it in my laptop's BD/DVD/CD drive and play the movie?

I doubt it. There's all that DRM encryption to deal with.

.

---

### Post by .Maleficus. on 2009-07-07
> **Arup said:**
> Only C.Korn's ppa has it. Sadly no vdpau support yet as I had hoped for.
No VDPAU?  Then no reason for me to switch from Mplayer.

---

### Post by Pasdar on 2009-07-07
Thx, installed it.

---

### Post by jerrrys on 2009-07-07
so far working fine in 804...

---

### Post by Sealbhach on 2009-07-07
How did you install it?

.

---

### Post by jerrrys on 2009-07-07
[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by Nevon on 2009-07-07
```
nevon@loltop:~/workspace$ vlc
VLC media player 1.0.0 Goldeneye
[0x95a5140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Segmentation fault
nevon@loltop:~/workspace$ cvlc
VLC media player 1.0.0 Goldeneye
[0x9673898] dummy interface: using the dummy interface module...
Segmentation fault
```

---

### Post by jsmidt on 2009-07-07
> **Arup said:**
> Only C.Korn's ppa has it. Sadly no vdpau support yet as I had hoped for.

I believe you, but how do you know this?   Also, does anyone have a blue-ray player who could tell us if it really works?

---

### Post by Arup on 2009-07-07
> **jsmidt said:**
> I believe you, but how do you know this?   Also, does anyone have a blue-ray player who could tell us if it really works?

No vdpau option in video configuration.

---

### Post by reyfer on 2009-07-07
My video card is an Nvidia GeForce 6800 XT, not supported by vdpau, so VLC not having it is of no consequence to me :)

---

### Post by mamamia88 on 2009-07-08
it's about time they got to 1.0  don't numbers below 1 usually mean they are beta?  vlc has always seemed more than beta

---

### Post by Warpnow on 2009-07-08
I fail to understand why people would use mplayer over VLC. It doesn't seem much to me like they're different than each other, so much as VLC is simply easier to use. 

What advantage does mplayer offer? I've never liked it much, mostly because its never worked well for me. The few files it seems to play correctly seem to crash more often than play.

---

### Post by ghindo on 2009-07-08
> **RiceMonster said:**
> hmmm... I'll give it a try and see if it makes me want to switch out of Mplayer (hightly doubt it), but I'll probably just use it for DVDs.What advantages does MPlayer have over VLC?

---

### Post by .Maleficus. on 2009-07-08
> **Warpnow said:**
> I fail to understand why people would use mplayer over VLC. It doesn't seem much to me like they're different than each other, so much as VLC is simply easier to use. 

What advantage does mplayer offer? I've never liked it much, mostly because its never worked well for me. The few files it seems to play correctly seem to crash more often than play.
> **ghindo said:**
> What advantages does MPlayer have over VLC?
[VDPAU]("http://en.wikipedia.org/wiki/VDPAU").  Much, much smoother decoding of HD content.  Since all of my videos are 720p, VLC doesn't really cut it.

---

### Post by ghindo on 2009-07-08
> **.Maleficus. said:**
> [VDPAU]("http://en.wikipedia.org/wiki/VDPAU").  Much, much smoother decoding of HD content.  Since all of my videos are 720p, VLC doesn't really cut it.I think VLC supports hardware acceleration.  I'd look around for it, but the wiki and documentation is down due to the high traffic on the site.

---

### Post by stwschool on 2009-07-08
Been using VLC for ages since back in my windows days. It really is a useful piece of software, plays anything, what more can I ask?

---

### Post by CaseSensative on 2009-07-08
[INDENT]  ```
sudo apt-get update
``````

sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```[/INDENT]

---

### Post by moster on 2009-07-08
> **ghindo said:**
> What advantages does MPlayer have over VLC?

How about putting subtitles BELOW actual movie. Who wants to look at movie with subtitles on it when there is plenty of black around it in full screen. Mplayer can do that.

Can someone tell me if this VLC version got that right so I can finally try it?

---

### Post by Arup on 2009-07-08
> **ghindo said:**
> I think VLC supports hardware acceleration.  I'd look around for it, but the wiki and documentation is down due to the high traffic on the site.

VDPAU is different from hardware acceleration, all the decoding work is handed over to GPU thereby freeing your CPU, its a boon for those with older slower CPUs.

---

### Post by munky99999 on 2009-07-08
> **CaseSensative said:**
> [INDENT]  ```
sudo apt-get update
``````

sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```[/INDENT]

The repos havent been updated yet. Building from source also has quite the problem because the repos for 1 of the dependencies is QT 4.5 while QT 4.5.1 is minimum required. The latest is 4.5.2.

120 meg source for the 4.5.2... and it's still building lawl. Been a good 10 hours building.

FUN!

---

### Post by RiceMonster on 2009-07-08
> **ghindo said:**
> What advantages does MPlayer have over VLC?

> **Warpnow said:**
> What advantage does mplayer offer? I've never liked it much, mostly because its never worked well for me. The few files it seems to play correctly seem to crash more often than play.

I use the command line version, and I've never had any problem with it at all. I just like that it's simple and offers great keyboard control. Also, I find that it plays whetever I throw at it without problems (except DVDs, though, because it doesn't have menu support). Mplayer is the only video player that has never messed up soft subtitles either. In some .mkv files, I've had to mess around with VLC to get them to not overlap or  something, but Mplayer never does this. Plus, with mplayer I don't have to install qt.

---

### Post by Shijojoy on 2009-07-08
Dear friends, anyone can help me to get deb file for VLC 1.0.0

thanks in advance

---

### Post by Insane_Homer on 2009-07-08
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D
```

Software Sources add:
> deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main

```
sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

---

### Post by Clean3d on 2009-07-09
> **Nevon said:**
> ```
nevon@loltop:~/workspace$ vlc
VLC media player 1.0.0 Goldeneye
[0x95a5140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Segmentation fault
nevon@loltop:~/workspace$ cvlc
VLC media player 1.0.0 Goldeneye
[0x9673898] dummy interface: using the dummy interface module...
Segmentation fault
```

Segfaults here too. Rather disappointing, that.

---

### Post by paok4 on 2009-07-09
i will try this ...

---

### Post by ghindo on 2009-07-09
> **Arup said:**
> No vdpau option in video configuration.> **.Maleficus. said:**
> [VDPAU]("http://en.wikipedia.org/wiki/VDPAU").  Much, much smoother decoding of HD content.  Since all of my videos are 720p, VLC doesn't really cut it.Looks like [VDPAU work is underway]("http://www.jbkempf.com/blog/post/2009/04/19/Decoding-video-in-VLC-using-VAAPI-and-nVidia"), but is a compile-time option.> **RiceMonster said:**
> Plus, with mplayer I don't have to install qt.AFAIK there is a command-line interface for VLC as well.

---

