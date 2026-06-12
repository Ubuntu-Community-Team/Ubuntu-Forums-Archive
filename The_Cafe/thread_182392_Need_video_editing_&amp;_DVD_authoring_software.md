---
title: "Need video editing &amp; DVD authoring software"
date: 2006-05-26
forum: The Cafe
---

### Post by futz on 2006-05-26
Besides games and my accounting software, video editing is one of the last things I really need windows for anymore.

I'm a WRC (World Rally Car) fan and since I live in North America, there is no TV coverage anymore, so I have to bittorrent download every rally in three parts. Then I put the parts back together, add a bit of a title and transcode to mp2. Then I author for DVD and burn it so I can enjoy it on a nice big screen.

I could shoot these files over to one of the windoze boxes and use my usual Premiere Pro 1.5 and TMPGEnc DVD Author to do the job, but I'd like to try doing it in  Linux for a change. Anyone got any good recommendations?

I've tried avidemux - after a bit of tinkering I gave up. Maybe I'm missing something, but it seems pretty clumsy and difficult to use. Even after reading the so called "documentation" I'm still pretty lost. 

Yes, I am spoiled by Premiere Pro. It's the best video editor in the whole world. I've tried many others (including Vegas), but nothing even comes close. Premiere Pro is the best.

I played with QDVDAuthor a bit too. Same results as above, only worse. I can't even get started with this thing. Way too weird.

---

### Post by meng on 2006-05-26
Simple video editing: kino
More in-depth video editing: cinelerra

If you're using really cool features on Premiere Pro, then you'll want cinelerra. If you're just doing some trims and subtitles, then kino is fine (although a little unstable).

DVD authoring: dvdstyler

I have also found QDVDAuthor to not function as advertised. However, dvdstyler 1.31 requires an older version of mjpegtools: 1.6.2-0.8 works.

---

### Post by futz on 2006-05-26
[QUOTE=meng]Simple video editing: kino[/quote]
I have kino installed, but have rarely been able to get it to import anything.

> More in-depth video editing: cinelerra
I was just looking at that in another tab. I'm going to install and try it out. There are ubuntu packages available, so that makes it easy.

> If you're using really cool features on Premiere Pro, then you'll want cinelerra. If you're just doing some trims and subtitles, then kino is fine (although a little unstable).
Mostly pretty simple stuff, but occasionally I need to diddle with sound - add some compression or whatever...

> DVD authoring: dvdstyler
Thanks. I'll have a look at that one.

---

### Post by Red.Heron on 2007-12-17
I have kino and cinelarra both installed, but I can't seem to import a still image and expand that to a few seconds of footage... the documentation only seems to cover pre-existing video.

Any authoring packages out there that might help?

---

### Post by Jhongy on 2007-12-17
I've been doing a fair bit of video editing in Ubuntu. I can offer my experience and findings.

I use cinelerra CV. Works just fine -- be sure to glance at the documentation, or follow a tutorial for your first video. The install section of the Cinelerra CV manual tells you how to install it on Gutsy from their Ubuntu repository.

You have to make a minor system setting change for it to work properly -- a popup window will tell you about it.

Using Cinelerra CV is pretty easy -- I pull the mpeg files from my camcorder, dump them into Cinelerra, view them in the viewer, splice them into the timeline, add effects (deinterlace), and then render. 

The only thing that is tricky is to make sure you set the correct project options (NTSC or PAL) before you start, and don't worry about the displayed aspect ratio if you're using widescreen -- the resolution is still the same as normal PAL (the pixels are just rectangular), the aspect gets fixed when you use ffmpeg later.

Despite all of Cinelerra's rendering options, pretty much all videos you create in cinelerra, you would render into quicktime4linux format (two's coplement audio, DV video), which you can then play with (convert to mpeg2 for DVD or XViD for internet) using ffmpeg, which is well documented and the same as on Windows (be sure to replace ubuntu's ffmpeg with the one from the medibuntu repository though, as the default one is crippled).

To create a nice DVD with menus, I've used QDVDAuthor -- easy to use and works great (although have a look in its settings to see the list of command-line tools it needs, and apt-get install them).

For the actual burning to DVD, nothing beats K3B. Far easier/better than Nero on Windows. It's in the repos as well.

Hope this helps.

J

EDIT: Here's a great tutorial that helped me begin to get to grips with Cinelerra CV: [http://www.robfisher.net/video/cinelerra1.html](http://www.robfisher.net/video/cinelerra1.html) . I still have a long way to go though!

---

### Post by Jhongy on 2007-12-17
> **Red.Heron said:**
> I have kino and cinelarra both installed, but I can't seem to import a still image and expand that to a few seconds of footage... the documentation only seems to cover pre-existing video.

Any authoring packages out there that might help?

After you drag the image onto the video track in Cinelerra, it will only be one frame long. You should be able to zoom in on the timeline, and use the middle button to drag it and expand it in length.

---

### Post by mips on 2007-12-17
[http://www.kdenlive.org/](http://www.kdenlive.org/)

---

### Post by forrestcupp on 2007-12-17
> **Jhongy said:**
> 
The only thing that is tricky is to make sure you set the correct project options (NTSC or PAL) before you start, and don't worry about the displayed aspect ratio if you're using widescreen -- the resolution is still the same as normal PAL (the pixels are just rectangular), the aspect gets fixed when you use ffmpeg later.

Good advice.  I found this out the hard way.  Once you start working on a project in Cinelerra, you can't change it from PAL to NTSC.  Make sure to set that first.

> **mips said:**
> [http://www.kdenlive.org/](http://www.kdenlive.org/)
+1
If you need to do complex stuff, Cinelerra is the only way to go.  But if you don't need all of those features, please don't use Kino; use KDEnlive.  It's pretty amazing and it has a lot of potential.  But again, if you are used to using all of those features in Premiere, you may be better off with Cinelerra.  You should give KDEnlive a shot, though.  To me, Kino was just unusable.

In the Windows world, I personally like Vegas better than Premiere.  But everyone has their own preference.

---

