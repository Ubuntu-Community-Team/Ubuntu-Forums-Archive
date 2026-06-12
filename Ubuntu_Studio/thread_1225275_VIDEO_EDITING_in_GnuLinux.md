---
title: "VIDEO EDITING in Gnu/Linux"
date: 2009-07-28
forum: Ubuntu Studio
---

### Post by manolomanolo on 2009-07-28
Hi to all.

I'm having some problems with video editing il Gnu/Linux. It doesn't seem to be a very great choice in this field.

**KDEnlive** produces video clips without any audio (maybe a problem of mine) :confused:

**LiVES** seems to have some packaging problems
[http://lives.sourceforge.net/index.php?do=downloads]("http://lives.sourceforge.net/index.php?do=downloads")

**Jahshaka** seems to be moved to CineFX but CineFX is not available/downloadable for Gnu/Linux
[http://www.cinefx.org/]("http://www.cinefx.org/")

**PiTiVi** is almost useless (no transitions, no effects etc etc)

**Cinelerra** will be transformed into Lumiera but they are taking very long time to code Lumiera: till then you should be happy with using Cinelerra with that very awful graphic interface :(

**Blender** does not seem to be very intuitive for basic video editing (haw can I add video/audio timelies?!?)

**Avidemux** easy to use but it has got no time line to mix video/audio tracks together with video/audio effects. Almost the same for **HandBrake**.

**Kino** does not seem to have a timeline as KDEnlive or Windows Movie Maker (I mean Kino has got a "Time Line" section but it doesn't seem to have the same meaning as in KDEnlive or Windows Movie Maker)


At the time of writing, it seems we can only hope that KDEnlive stops crashing in future releases, that [**OpenShotVideo**]("http://www.openshotvideo.com/") will finally become an "official version", that Cinelerra will become "Lumiera" or change that f*cking awful graphical interface and so on...

Any other option, please?
Regards.

---

### Post by Aphorism on 2009-07-28
Blender isn't a simple hobby application.  Look to Richard Querin's site for a relatively quick get-up-and-running series of screencasts.

While I encourage you to experiment with the other apps out there, nothing will even come within a hair of the power of Blender.

[http://blog.rfquerin.org/2009/01/26/how-i-edit-videos-using-blender-maybe-part-one/](http://blog.rfquerin.org/2009/01/26/how-i-edit-videos-using-blender-maybe-part-one/)
[http://blog.rfquerin.org/2009/02/14/really-basic-blender-video-editing-part-2/](http://blog.rfquerin.org/2009/02/14/really-basic-blender-video-editing-part-2/)
[http://blog.rfquerin.org/2009/07/23/blender-video-editing-screencast-no-3/](http://blog.rfquerin.org/2009/07/23/blender-video-editing-screencast-no-3/)

---

### Post by alphacrucis2 on 2009-07-29
I recently tried to edit (extract clips) from a VRO file created by a Panasonic DVD recorder on DVD RAM. Blender, Cinelerra and Kdenlive all failed miserably. Kino might have worked but was in the process of creating an insanely large DV file on import so I gave up on it. I tried Avidemux which is really a transcoder but all I wanted was some simple trimming and extracting. The only issue I had with a Avidemux was the audio sync which I had to adjust manually for each extracted clip. So Avidemux is a useful gui tool even if just to convert to a format that the other editors handle properly.

---

### Post by ssdt on 2009-07-29
I edit with Avidemux (if they are in the correct codec and file format) so you can also try those  because it looks like you only tried Cinerella (for me I didn't like it), LiVES (Tried it but seemed really hard to understand) Pitivi the same. I haven't tried Jahashna but think it will be the same.

If you need to convert the videos to Avi for Avidemux, you will need Handbrake.

---

### Post by manolomanolo on 2009-07-29
Avidemux easy to use but it has got no time line to mix video/audio tracks together with video/audio effects.

Neither HandBrake is able to mix and add effects

---

### Post by vinutux on 2009-07-29
kino is stable than other apps mentioned here

---

### Post by manolomanolo on 2009-07-29
> **vinutux said:**
> kino is stable than other apps mentioned here

Maybe it's stable, but **Kino** does not seem to have a timeline as KDEnlive or Windows Movie Maker. I mean Kino has got a "Time Line" section but it doesn't seem to have the same meaning as in KDEnlive or Windows Movie Maker, does it?

---

### Post by vinutux on 2009-07-29
> **manolomanolo said:**
> Maybe it's stable, but **Kino** does not seem to have a timeline as KDEnlive or Windows Movie Maker. I mean Kino has got a "Time Line" section but it doesn't seem to have the same meaning as in KDEnlive or Windows Movie Maker, does it?

Ok but [COLOR="Red"][new pitivi]("www.getdeb.net/app/PiTiVi")[/COLOR] does....but missing effects and translations.
[B][URL="www.getdeb.net/app/PiTiVi"]www.getdeb.net/app/PiTiVi
[/URL][/B]

[COLOR="YellowGreen"]Home page [/COLOR]- [**http://www.pitivi.org/wiki/Main_Page**]("http://www.pitivi.org/wiki/Main_Page")

[IMG]http://upload.wikimedia.org/wikipedia/en/thumb/4/48/PiTiVi_v0.13.0.1.png/800px-PiTiVi_v0.13.0.1.png[/IMG]

---

### Post by wkulecz on 2009-07-29
Blender is to a good Video Editor like the command line is to Gnome or KDE.  All the power you could ever want if you ever actually have enough time to figure it all out.

KDEnlive seems to have the most potential, but I've never been able to do anything but crash it until I tried it on Kubuntu 9.04.  Once I found a system it didn't crash on, it worked quite well.  I didn't do a lot with audio, but sync seemed OK at least for the 5-10 minute clips I was playing with.

I suspect I'll dual boot into Windows 7 for video editing, nothing on Linux can match the ~$70 Sony Vegas Movie Studio software on Windows :(
I'm still using an older version on Windows 2000, but the latest on Windows 7 RC1 will likely have me setting up a Win7 box for it once I upgrade to HD camcorder.

KDEnlive on Kubuntu 9.04 handled the 720P MJPEG from my Casio point and shoot without issues, but its not a real camcorder.  I've no HDV or AVCHD source to test at present.

--wally.

---

### Post by Aphorism on 2009-07-30
> **wkulecz said:**
> Blender is to a good Video Editor like the command line is to Gnome or KDE.  All the power you could ever want if you ever actually have enough time to figure it all out.

I suspect I'll dual boot into Windows 7 for video editing, nothing on Linux can match the ~$70 Sony Vegas Movie Studio software on Windows :(
I'm still using an older version on Windows 2000, but the latest on Windows 7 RC1 will likely have me setting up a Win7 box for it once I upgrade to HD camcorder.


A bit of an overstatement.  Richard Querin's links above have already disproved this point.  Unfortunately, the comments end up being inflammatory and probably dissuade people from learning an extremely powerful tool.

Blender blows away any 70$ editor.  Honestly, dedicate yourself to learning it and you will probably agree.  The nodal compositor is worth its weight in gold.  Your biggest issue appears to be codecs.  Perhaps myself or someone else can help you past that hiccup?

> **wkulecz said:**
> 
KDEnlive on Kubuntu 9.04 handled the 720P MJPEG from my Casio point and shoot without issues, but its not a real camcorder.  I've no HDV or AVCHD source to test at present.

Perhaps you should peruse the web and look at all of the innumerable problems with AVCHD and 24Pn pullup?  It isn't just in Linux.  In fact, it is all over in every platform.  Many of the solutions are interestingly wrapped around mplayer and ffmpeg.

There just isn't an end all for everyone, but don't mix up codec management with an application's ability to cut.  Anyone familiar with post production will spool off countless applications that live in the pipeline.

Hopefully we can work something out to help you out?

---

### Post by benoitcsirois on 2009-07-30
I have done some small video editing projects and used the following tools:

ffmpeg (CLI) for converting videos (I have an HD camera that outputs 1080x1950, 60fps, and that's too much for my old laptop, so I convert to MPEG, 720p, 30fps)

cinelerra for editing video. I found that the binary package from the repository they recommend here: [http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php) is very stable.

I have also tried avidemux, but I haven'e experimented much with it.

Pitivi seems cool, but doesn't support transitions.

---

### Post by wkulecz on 2009-07-30
> Blender blows away any 70$ editor. Honestly, dedicate yourself to learning it and you will probably agree.  Time is money, I want to do quality edits quickly without "dedication" to my tools.

> Perhaps you should peruse the web and look at all of the innumerable problems with AVCHD and 24Pn pullup?

I don't understand why 24P even exisits except to convert film to Blue Ray.  Putting it on digital video makes about as much sense to me as trying to make CDs sound like vinyl.  The artsy fartsy crowd demands it for reasons that escape me, I don't watch films because the 24 fps flicker and motion blur greatly annoy, at least on the small screen of DVD its tolerable.

1080/60p is my digital video holy grail, I fully intend to ignore 24p completely and certainly won't pay extra for it as "camcorder feature".

> Your biggest issue appears to be codecs
Whatever gave you that idea?  Probably the most impressive thing about KDEnlive it it appeared I could mix on the timeline any video I could play in Movie Player.  Sony Vegas can't edit many videos I can play in media player, so Linux might be ahead here.

--wally.

---

### Post by cotcot on 2009-07-30
I am doing video work that is sometimes quite complicated using blender VSE and cinelerra. Also AVCHD (after converting with mencoder command line). OK it took me some time to learn it and the learning curve is still going on. The more i know the more i appreciate.

---

### Post by binbash on 2009-07-30
You can get latest Lives package from getdeb.I use LIVES, blender and sometimes avidemux.KDEnlive has a lot of dependencies especially on minimal install so i never tried it.

---

### Post by blur xc on 2009-07-30
Blender has me intrigued- but I have some questions-

First off- I've only "produced" one video and I did it in windows movie maker.  It's kind of lame, and frustrating, but it's easy enough to use.  To capture the video, I plugged my ancient camcorder into a firewire port, and windows movie maker automatically started a capture dialog, and one option it had was to "split" the video into clips, where the camcorder started and stopped.  The video file stayed in one piece though...  From there, it was drag and drop, shorten, cut, etc, transition- add sound and export.  

So- how do you first capture the video from the device, and 2nd, how do you split up a video into clips?

I would really like to do my next video in linux, maybe using blender...

BM

---

### Post by paulmerchant on 2009-07-30
> **blur xc said:**
> 

So- how do you first capture the video from the device, and 2nd, how do you split up a video into clips?

I would really like to do my next video in linux, maybe using blender...

BM

It sounds like you are shooting on mini DV and your camera has firewire. In this case, you can use Kino (or, more specifically, dvgrab) to capture your video.

If I remember correctly, you can tell dvgrab to split your clips up by scenes as they are being imported. Then you can easily perform further cutting on those scene clips within Blender. Alternately, you could grab one big clip with dvgrab and, with some creative copying and pasting, simply cut on that big clip within Blender. It might be tedious. You could also use something like avidemux to cut up a big clip into smaller, more manageable clips to be brought into Blender.

Nice question. I'm interested in seeing other work flows that help with managing video editing projects in Blender.

---

### Post by wkulecz on 2009-07-31
> Alternately, you could grab one big clip with dvgrab and, with some creative copying and pasting, simply cut on that big clip within Blender. It might be tedious.

If editing a single large clip in Blender would be tedious, it means Blender would usually be a lousy editor for my purposes.  Having to deal with a multitude of smaller files (like the bad old days of Win9x where 2GB was the largest capture possible) is not something I'm willing to go back to.  Perhaps this helps understand why a long learning curve is a serious impediment -- I'd be rather PO'd to spend days going through tutorials only to learn it would force a work flow I can't tolerate.

For someone who wants to spend time editing instead of learning tools, KDEnlive seems the best bet right now, if they can solve the stability problems.  As I said I've tried on various systems and only on Kubuntu 9.04 has actually been usable.

I basically do two modes of editing: long files merging the best view from multiple cameras into a final output, or putting short clips together for presentations.  Since the short clips are in whatever format they are when they come to me, KDEnlive's ability to seamlessly mix codecs and resolutions on the time line has me greatly encouraged it could one day meet my needs.

--wally.

---

### Post by paulmerchant on 2009-07-31
> **wkulecz said:**
> If editing a single large clip in Blender would be tedious, it means Blender would usually be a lousy editor for my purposes.  Having to deal with a multitude of smaller files (like the bad old days of Win9x where 2GB was the largest capture possible) is not something I'm willing to go back to.

I've only experimented with using Blender as an NLE. Since Blender doesn't have a trimmer or any real media management, I felt that preparing short clips and organizing these clips ahead of time would improve the whole process. Again, there might be other work flows. I would love to hear about them.

---

### Post by cotcot on 2009-08-01
> **paulmerchant said:**
> I've only experimented with using Blender as an NLE. Since Blender doesn't have a trimmer or any real media management, I felt that preparing short clips and organizing these clips ahead of time would improve the whole process. Again, there might be other work flows. I would love to hear about them.

Trimming is possible in Blender with the node editor or with (soft or hard) cut strips on the timeline. The node editor takes somewhat time to learn and is slower. soft cut (K) and hard cut (shift K) allows you to use part of clips without modifying the source material.

---

### Post by manolomanolo on 2009-08-01
I think you all searching for Windows Movie Maker style video editor for Gnu/Linux should try OPEN SHOT VIDEO

[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

I suppose that's what all of those (including myself) wanted to read:

[http://www.openshotvideo.com/2009/07/it-is-time-for-linux-video-editor.html](http://www.openshotvideo.com/2009/07/it-is-time-for-linux-video-editor.html)

I'm trying it: I suppose it will do the job!!!

---

### Post by paulmerchant on 2009-08-01
> **cotcot said:**
> Trimming is possible in Blender with the node editor or with (soft or hard) cut strips on the timeline. The node editor takes somewhat time to learn and is slower. soft cut (K) and hard cut (shift K) allows you to use part of clips without modifying the source material.

Yes, of course, clips can be trimmed in Blender. A trimmer, however -- a feature in many NLE's that allows you, among other things, to quickly perform cutting tasks before adding media to a timeline -- is currently not one of Blender's features.

I don't think trimmers are critical features for everyone. You can always cut up clips on a timeline like you mention. However, with long projects, managing all of your media on a single timeline would become unwieldy. This is why I've seen some work flows involving Blender as an NLE that include the steps of cutting up and organizing clips into different files and folders before bringing them into Blender.

---

### Post by zelhar on 2009-08-01
I am trying to find the quickest way for doing a few simple edits like rotate, add captions etc. and then split the video at fixed size/intervals and export (i.e. email size, youtube size...). Does anyone know which app can do that in the most simple and elegant way ?

So far I've tried: Kino, pitivi, kdenlive, Open Movie editor, and I couldn't do it. I don't know why but for some reason when I tried to export the movie the programs crashed.

---

### Post by vinutux on 2009-08-01
> **zelhar said:**
> I am trying to find the quickest way for doing a few simple edits like rotate, add captions etc. and then split the video at fixed size/intervals and export (i.e. email size, youtube size...). Does anyone know which app can do that in the most simple and elegant way ?

So far I've tried: Kino, pitivi, kdenlive, Open Movie editor, and I couldn't do it. I don't know why but for some reason when I tried to export the movie the programs crashed.

Try **cinelerra**...**[.http://cinelerra.org/]("http://cinelerra.org/")**

---

### Post by Aphorism on 2009-08-02
> **zelhar said:**
> I am trying to find the quickest way for doing a few simple edits like rotate, add captions etc. and then split the video at fixed size/intervals and export (i.e. email size, youtube size...). Does anyone know which app can do that in the most simple and elegant way ?

Simple and elegant are subject to the audience at hand.

Blender can do all of that very simply and quite quickly.

[LIST]
[*]Rotate - For rotate, you can use Effect->Transform for a simple application.
[*]Captions - For captions, you can custom design them in Inkscape or another imaging app with alpha and layer them in with Effect->Alpha Over.  If you want, you can easily translate, rotate or both with the above effect.
[*]Splitting - Simple byproduct of selecting start and end frames when choosing render.
[/LIST]

Of course, both rotate and captions can be varied into infinite complexity with the compositor, but you may want to start simple.

Hope that helps...

---

### Post by zelhar on 2009-08-02
I installed cinelerra and I couldn't even get the imported clip inside a video track. This supposed to be one the simplest things to do yet I couldn't immediately find how, I couldn't drag it inside for example. I think cinelerra gets an F as well (or may be it's I who does ?)

I will try Blender later. But Aphorism, what I mean by splitting is an elegant way to save/export the project as a sequence of videos. It seems to me that you suggest to produce the sequence manually by each time selecting the consequetive interval. That could work too if it is easy to mark/find the ends of each interval.

i wish there was a video app similar to "Audacity" in audio editing.

---

### Post by vinutux on 2009-08-02
> **zelhar said:**
> I installed cinelerra and I couldn't even get the imported clip inside a video track. This supposed to be one the simplest things to do yet I couldn't immediately find how, I couldn't drag it inside for example. I think cinelerra gets an F as well (or may be it's I who does ?)

I will try Blender later. But Aphorism, what I mean by splitting is an elegant way to save/export the project as a sequence of videos. It seems to me that you suggest to produce the sequence manually by each time selecting the consequetive interval. That could work too if it is easy to mark/find the ends of each interval.

i wish there was a [COLOR="Red"]video app similar to "Audacity"[/COLOR] in audio editing.


PiTiVi - Not so similer to audacity but....simple one

install from here **[www.getdeb.net/app/PiTiVi]("www.getdeb.net/app/PiTiVi")**

---

### Post by manolomanolo on 2009-08-02
Does Blender have timelines as in OpenShotMovie editor? How to activate them?

In other words, will I get something like this:
[Open Movie Editor]("http://img148.imageshack.us/img148/7344/openshotmovieeditor.png")

using Blender that now it shows itself to me like that:
[Blender]("http://img205.imageshack.us/img205/8994/blender.png")

?

thanks.

---

### Post by ArmenianLeader4 on 2009-08-02
I don't know if anyone has posted this yet, but I've had no problem running Sony Vegas 9 Platinum using wine. Everything works well, except I can't export in specific codecs. Also, if you're on a low budget, Kino and Stopmotion seem to do everything you could need from a video editor.

---

### Post by kayosiii on 2009-08-02
> **zelhar said:**
> I installed cinelerra and I couldn't even get the imported clip inside a video track. This supposed to be one the simplest things to do yet I couldn't immediately find how, I couldn't drag it inside for example. I think cinelerra gets an F as well (or may be it's I who does ?)

Clips should be loaded into the into the Resources window using the open command (drag and drop works within the program but not from external resources. From the resources window they can be dragged and dropped onto the timeline - but Cinelerra is a 3 point editor so the better way of doing things is to drop onto the preview window and build your clips there (these clips have their section in the resources window).
Exported files can be split at label points automatically.

---

### Post by Aphorism on 2009-08-03
> **manolomanolo said:**
> Does Blender have timelines as in OpenShotMovie editor? How to activate them?
[...]
using Blender that now it shows itself to me like that:
[URL="http://img205.imageshack.us/img205/8994/blender.png"]Blender[/URL

You have predefined 'views' at the top.  Pull down the groupbox that says "SR: 2 - Model" and change it to "SR: 4 - Sequence".  That is the default layout.  You can customize it as much as you like of course.

Again, view the links I originally posted:
http://blog.rfquerin.org/2009/01/26/how-i-edit-videos-using-blender-maybe-part-one/
http://blog.rfquerin.org/2009/02/14/really-basic-blender-video-editing-part-2/
http://blog.rfquerin.org/2009/07/23/blender-video-editing-screencast-no-3/

> I will try Blender later. But Aphorism, what I mean by splitting is an elegant way to save/export the project as a sequence of videos. It seems to me that you suggest to produce the sequence manually by each time selecting the consequetive interval. That could work too if it is easy to mark/find the ends of each interval.

Just add a scene and change the render ranges.  It will remember them.  Once you have a scene, you can also render it from the command line by the name if you wish.

---

### Post by homy06 on 2009-08-04
Aphorism helped me out with blender. and yea, for the most part it's enough for me. My main purposes are for short films, so I need something robust. 

Don't believe the bad mouthing, get your codec in order (bc face it, any program would suck with bad codecs) then download blender and try out the sequencer.

---

### Post by kiddo on 2009-08-05
[SIZE="6"]Do not use the getdeb/jaunty versions of PiTiVi[/SIZE].

They are way too old. This was before 3 full-time paid developers started making PiTiVi rock. Use the PPA version instead. (See also [http://ubuntuforums.org/showpost.php?p=7735296&postcount=19](http://ubuntuforums.org/showpost.php?p=7735296&postcount=19))

Soon (this weekend?) I will be putting online the new website, which will reduce confusion with better instructions (and overview of the current status) than the pitivi wiki.

But yeah, no transitions/effets at the time being. That should come this autumn, if all goes well. In the meantime, you can still edit basic stuff (the website will have showcases of videos made with PiTiVi, when it's up).

---

### Post by manolomanolo on 2009-08-05
> **kiddo said:**
> [SIZE="6"]Do not use the getdeb/jaunty versions of PiTiVi[/SIZE].

They are way too old. This was before 3 full-time paid developers started making PiTiVi rock. Use the PPA version instead. (See also [http://ubuntuforums.org/showpost.php?p=7735296&postcount=19](http://ubuntuforums.org/showpost.php?p=7735296&postcount=19))

This link explains how to get the PPA version of PiTiVi:

[http://blogs.gnome.org/edwardrv/2009/05/21/pitivi-video-editor-01302-pre-release/]("http://blogs.gnome.org/edwardrv/2009/05/21/pitivi-video-editor-01302-pre-release/")

---

### Post by shane2peru on 2009-08-06
I really like kdenlive.  It was a low learning curve app, and worked very well.  However lately it is taking an eternity to process my videos.  I tried to get help on kdenlive irc, but that was about slower than processing my videos.  I think it has high potential, but is in need of some more development.  I have a 45min video recorded off my camcorder with mplayer and tv card, it is a 1.5GB file (high quality).  I wanted to edit it, just cut a little of the beginning and end, and output it to mpg file, it took over 8 hours of processing, and didn't finish!  I finally cut it.  I tried outputing to mpeg-2 at 1000k bit rate.  That seems a bit excessive to me.  I'm not sure where the problem is, but that just doesn't seem right.  I'm working on a Ubuntu 9.04 64bit, with a AMD Turion x2 ultra processor.  I'm trying a few others that were mentioned now.  I will let you know what I think.

Shane

PS my editing needs are simple, cut out a little here and there, and output to quality video, to be setup with dvdstyler and burned to dvd.

---

### Post by manolomanolo on 2009-08-07
> **shane2peru said:**
> 
PS my editing needs are simple, cut out a little here and there, and output to quality video, to be setup with dvdstyler and burned to dvd.

I suppose Avidemux is the best choice for you.

---

### Post by shane2peru on 2009-08-07
Well, I give OpenShot a [COLOR="Red"]-10[/COLOR]  It totally messed up my system.  I had the latest x264 installed from git, the latest ffmpeg installed from svn and it messed them up.  It didn't run once it was installed, and I don't see anyway to get it off my system.  That was a total mess.  I had my doubts about installing it because it installs from a python script.  

I have used Avidemux, and it is ok, but recently has been messing up the A/V sync on my videos.  So, hence my search for something new.

Shane

---

### Post by manolomanolo on 2009-08-07
> **shane2peru said:**
> Well, I give OpenShot a [COLOR="Red"]-10[/COLOR]  It totally messed up my system.

OpenShot 0.9.13 installed perfectly to me, using that python installer.

>   I had the latest **x264** installed from git,

What x264 means?

> I have used Avidemux, and it is ok, but recently has been messing up the A/V sync on my videos.

I have Avidemux 2.4.4 and it hasn't messed up anything at all. I know, it's frustrating but I suppose there's something wrong in your system since those programs generally work fine.

[QUOTE]So, hence my search for something new.[QUOTE]
I suppose you've been reading this discussion and so tried all the other programs such as: Open Movie Editor, Cinelerra, Kino, KDEnlive, etc

Shane

---

### Post by wkulecz on 2009-08-07
> I'm working on a Ubuntu 9.04 64bit, with a AMD Turion x2

While 64-bit would seem to be beneficial for video editing, at present I'd get off the bleeding edge.  KDEnlive on 32-bit Kubuntu 9.04 worked out of the box for me (had been crash-o'matiic on Ubuntu 6.06, 8.04 & 9.04).  Hard drives are cheap, I never install bleeding edge or non-standard software on a machine I need to have working afterwards, I dual boot into a test setup and try things there first.

> it took over 8 hours of processing, and didn't finish! I finally cut it. I tried outputing to mpeg-2 at 1000k bit rate. That seems a bit excessive to me  
Actually 1000k is very low bit rate for mpeg2, 4000k is more in line with the quality you might expect from a stand-alone DVD recorder box.  If you have two pass variable bit-rate encoding enabled it will be slower, and with that much compression slower still.

> with a AMD Turion x2 ultra 
Turion is a "notebook/economy" class CPU and not the best choice for video encoding.  You need all the CPU, cache, memory, and hard drive speed you can possibly afford for decently fast video encoding.

Open Shot looks interesting, but I'm waiting for a Ubuntu package before I bother with trying it.

--wally.

---

### Post by shane2peru on 2009-08-07
Let me clarify.  :)

My laptop as so well described above by wkulecz is what I put my videos on to be processed and I can walk away.  kdenlive worked fine on my desktop also with Ubuntu 9.04 64bit.  I do not mind testing some stuff on my laptop as it is my 'test' machine, and my desktop is my production machine.  However I really want to be able to process the videos on my laptop since that is the longest part.  After removing the x264, and ffmpeg from my system, and re-installing the git and svn versions.  And purging my system from kdenlive and re-installing, it seems to be working better.  It is giving me a Estimated 3 hour process time for the same 45min video.  I know the 1000k option before wasn't very high, I was trying lower, when I tried the 8000k option it took over 20 hours to process.  I think some of my settings in kdenlive had been botched somehow.  Purging, and re-installing it, and re-configuring it seemed to help.  

As for x264, I really don't know what it is, it was just in the tutorial I followed for upgrading to the latest ffmpeg.  

As for kino, I have never liked it, I don't really know what the dv format is, nor do I use it and every time I have ever tried it it takes an eternity just importing my file.  I want an editor that can use common formats, mpg, avi, etc.  I'm sure kino is very usefull for the people who use dv, but I'm not one of them.

Some of the others looked simple and usable for what I needed, like Open Movie editor (but it crashed) GopChop extra simple mpg editor worked fine.  And StopMotion crashed.  I so far think kdenlive is the best choice, and Avidemux for really simple stuff.

Shane

---

### Post by kiddo on 2009-08-07
x264 is a free/open source encoder (or codec?) implementation of H.264, one of the best codecs around in terms of image quality vs bitrate (but heavily patented and stuff. It's currently in a fierce battle against Ogg Theora for HTML5, see wikipedia).

Kdenlive taking 8 hours... well although I'd like to say that this is not normal on a powerful multicore system like a turion x2 (my quadcore renders H.264 at ~30 fps, so I expect mpeg2 rendering to be at roughly 3 times as fast, so it should actually take 1 hour for a 3 hours timeline, for example),... 

...but then this is kdenlive after all :popcorn: the same kdenlive that made my kernel panic systematically (read: I had to reset the computer by unplugging it) when I tried to render a 2-minutes-long timeline. Yeah, *kdenlive actually managed to instantly fill up my 4 gigabytes of RAM* and make the Linux kernel swap to death. That was a serious "WTF" moment.

But then I'm obviously biased towards PiTiVi of course ;)

---

### Post by shane2peru on 2009-08-08
:lolflag: :lolflag:

As it turns out, my video drivers were messed up and for some reason that was causing excessive processing times!!!  I'm re-running a video I did before on the laptop (after I fixed the dumb ATI drivers) and it is saying a mere 45 min!!  That is great.  I re-installed the proprietary drivers, and that fixed a lot of my problems.  Back up and running again!  

Shane

PS - and loving kdenlive, simple straight forward, and when the get the crashes worked out of it, it will be a top notch program.  It only crashes now and then on me, but for the minor editing I do, it is a great app!

---

### Post by chrisme52 on 2009-08-15
I installed kdenlive from the repos on 64bit 9.04 and has worked flawlessly. I was amazed how well it handled different formats with ease and worked perfect even with only 1 gb of ram!

It definitely is missing a few features but its perfect for chopping up video etc..

---

### Post by Dubstar_04 on 2009-08-16
See this:

[http://ubuntuforums.org/showthread.php?p=7794905#post7794905](http://ubuntuforums.org/showthread.php?p=7794905#post7794905)

Let me know what you think.

---

### Post by geovino on 2009-11-14
All I want to do is cut a 7 min section out of a mp4 file video. What is the best editor to use? I don't think any of the video editors in Linux are any good at this point. I guess I'll have a friend with windows do it for me. :(

---

### Post by manolomanolo on 2009-11-14
Hi geovino.

Which editor have you been testing before saying that no video editor for Gnu/Linux is good enough in your case?

Have you tried, KDEnlive? OpenShot Movie editor? Avidemux? Or any other?
Just in case, when did you try them? Check out for possible updates of your video editor apps and possibly try again. ;)

---

### Post by cotcot on 2009-11-15
> **geovino said:**
> All I want to do is cut a 7 min section out of a mp4 file video. What is the best editor to use? I don't think any of the video editors in Linux are any good at this point. I guess I'll have a friend with windows do it for me. :(

Easy job for Avidemux.

---

### Post by Allen3 on 2009-12-05
My frustration with Movie Editing with *Ubuntu Karmic Koala*, (version 9.10), is getting severe! My digital camera shoots .avi files. I have tried *Open Movie Editor* and it just plain didn't work at all! *Avidemux* plays the .avi file **without audio**! **Why is it that Linux doesn't have a decent movie editor!!!** Come on even *Windows Moviemaker* can do this! What I want to do is similar to *Moviemaker* in that I can put multiple clips together and edit them, insert graphics and other simple effects. Is their _any_ movie editor for *Ubuntu* that can do this with .avi files? I want one that doesn't have to resort to command line or anything like that. I _will not_ use or install anything that requires command line! It's about time the *Linux *OS get away from this primitive method of entry! So far movie editing is completely lame in *Linux Ubuntu*. Any modern operating system that cannot edit movies or play your music and Internet radio is not satisfactory. In fact it's downright ridiculous!

---

### Post by shane2peru on 2009-12-05
> **Allen3 said:**
> My frustration with Movie Editing with *Ubuntu Karmic Koala*, (version 9.10), is getting severe! My digital camera shoots .avi files. I have tried *Open Movie Editor* and it just plain didn't work at all! *Avidemux* plays the .avi file **without audio**! [B]Why is it that Linux doesn't have a decent movie editor!!!
I think a little more searching is in order, and little less ranting.  Have you tried kdenlive?  Very nice in my opinion, yes, it is still a little buggy, but going to be good.  I mean, after all, even Movie Editor was/is buggy.  There is also PiTiVi to look into, I have found it to be decent too.  As for Avidemux, there was a slight problem in that it doesn't work with pulse audio or something, it is a simple fix, just slips my mind at the moment.  If you are really interested I will find it and post it for you.


> **Allen3 said:**
> I _will not_ use or install anything that requires command line! It's about time the *Linux *OS get away from this primitive method of entry! 
Hmm, primitive, I think the word you were looking for there is powerful.  I will agree, that it isn't the most user friendly, however primitive isn't quite the choice I would have used.  I do agree though that GUI is the way to go for those who have no interest in using the powerful command line.

> **Allen3 said:**
> Any modern operating system that cannot edit movies or play your music and Internet radio is not satisfactory. In fact it's downright ridiculous!

I agree 100%, sure am glad that Ubuntu can do these things!  Of course it does require a little bit of patience and learning.  When your done ranting, and want to ask questions, we will be more than happy to help you resolve these issues.  Please open a new thread for individual things and state your problems, and what has been tried to fix them, and we will do our best to help out.

Shane

---

### Post by cotcot on 2009-12-05
> **Allen3 said:**
> My frustration with Movie Editing with *Ubuntu Karmic Koala*, (version 9.10), is getting severe! Any modern operating system that cannot edit movies or play your music and Internet radio is not satisfactory. In fact it's downright ridiculous!

Sure we can help you but not with this info. There are enough editors that can do what you want. Pick an editor try it and as soon as you cannot continue come back with a question and information. What is your camera type ? Any errors given by the editor ? In what step does the editor fail (loading the clip ?; putting the clip on a timeline ? Cutting the clip ? Render problem ?) ?

---

### Post by manolomanolo on 2009-12-05
> **Allen3 said:**
> *Avidemux* plays the .avi file **without audio**!
Go in the **Edit -> Preference -> Audio** menu. Try and change the selected audio driver.

> **Allen3 said:**
> **Why is it that Linux doesn't have a decent movie editor!!!** Come on even *Windows Moviemaker* can do this!
People here (and in everyday life too, I suppose) tries to help other people when they are able too. Complaining does not help you to get more people interested in your problem. Everyone knows that Gnu/Linux can get better and it will always do.

Somethimes changing the point of view can help: is it a Gnu/Linux problem or it's because of the minds of most of us polluted by
 **Next -> Next -> Next -> Ok/Cancel** procedures?

On the other hand if you say something like "I'll never do such a test or never try such a program" well, you're implicitly saying that you don't want to be helped after all.

So, for the next times, please be quiet and just try to show your problem without dedicating time and space with useless frustrations. ;)

---

### Post by kiddo on 2009-12-05
> **Allen3 said:**
> My frustration with Movie Editing with *Ubuntu Karmic Koala*, (version 9.10), is getting severe! My digital camera shoots .avi files. I have tried *Open Movie Editor* and it just plain didn't work at all! *Avidemux* plays the .avi file **without audio**! **Why is it that Linux doesn't have a decent movie editor!!!** Come on even *Windows Moviemaker* can do this! What I want to do is similar to *Moviemaker* in that I can put multiple clips together and edit them, insert graphics and other simple effects. Is their _any_ movie editor for *Ubuntu* that can do this with .avi files? I want one that doesn't have to resort to command line or anything like that. I _will not_ use or install anything that requires command line! It's about time the *Linux *OS get away from this primitive method of entry! So far movie editing is completely lame in *Linux Ubuntu*. Any modern operating system that cannot edit movies or play your music and Internet radio is not satisfactory. In fact it's downright ridiculous!

This is such an inflammatory troll that I don't even see how you managed to get courteous answers so far. A *good* video editor is among the most complex pieces of software you can possibly imagine (after the kernel and a 3D editor, maybe). Come back when you can write a professional-grade editor with one or two friends, on your spare time. Until then, steal the friendly urchin.

---

### Post by manolomanolo on 2009-12-06
> **kiddo said:**
> This is such an inflammatory troll that I don't even see how you managed to get courteous answers so far

I'm not sure the guy wanted to make mess here (a troll does make mess).
The guy just wanted to be helped but I suppose he/she could get a little bit better his/her way to communicate. That's all.

On the other hand, posts like yours do not help anyone either, IMHO.
Feel free to help the others, no need to add more flame. Trying to help the others will probably reduce their frustrations. On the other hand, pointing the finger is completely useless... ops, sorry... it's useful to make (flame) wars.

Karmic peace for everyone! ;)

---

### Post by Nixie Pixel on 2009-12-06
What version of Kdenlive are you using? The latest versions have resolved all my stability and audio issues.

---

### Post by vavoem on 2009-12-09
allen3 is actually right
all video editing in linux sucks
don't know how to improve it since i have no programming skills but still he's right it all is either complex buggy or lacks functionality.
I work with ubuntu since version 6 for all of my work, but can't help booting up xp for that single thing.
I would actually pay for a good piece of software and believe me i have tried them all.
Thats not a Rant but truth and a reason for people to skip ubuntu as a worthy windows replacement

---

### Post by mgmiller on 2009-12-09
If you haven't tried openshot recently, you haven't tried it at all.  It's now totally amazing.  

You can download a .deb to install it or you can add their ppa repository and have synaptic keep it up to date for you.  

I am using it in 64 bit 9.10 and I love it.  I have used all the others mentioned in this thread and they simply don't compare.  The current version even does chroma key(green screen) for goodness sake.  

Unlike kdenlive, it's a gnome app, so it "looks right".
Lots of transitions and effects.  
As many time lines for audio and video as you want. 
Easy drag and drop of files from nautilus directly into the program. 
It also outputs in many different formats from ipod to youtube to dvd, etc.

I have been looking for a decent Linux video editor for years and I finally found it.  The others are either insanely complex, feature poor, buggy or crash constantly.  This is the project that should become the default video editor in ubuntu.

[http://www.openshotvideo.com]("http://openshotvideo.com/")

---

### Post by edjski on 2009-12-29
> **mgmiller said:**
> If you haven't tried openshot recently, you haven't tried it at all.  It's now totally amazing.
I've installed it, but it won't start. Now, I'm completely comfortable with having to tweak things to make them work. I use Linux because I want to... But Openshot doesn't start -after following the directions step-by-step... And kdenlive, while it looks like it will actually edit video, ALSO does other strange things like randomly duplicating a clip, placing in on the timeline invisibly, etc. Its like having a calculator that correctly calculates but ALSO randomly inserts and deletes other numbers. Those additional "features" are not improvements!  
> 
You can download a .deb to install it or you can add their ppa repository and have synaptic keep it up to date for you.  

I am using it in 64 bit 9.10 and I love it.  I have used all the others mentioned in this thread and they simply don't compare.  The current version even does chroma key(green screen) for goodness sake.  

Unlike kdenlive, it's a gnome app, so it "looks right".
Lots of transitions and effects.  
As many time lines for audio and video as you want. 
Easy drag and drop of files from nautilus directly into the program. 
It also outputs in many different formats from ipod to youtube to dvd, etc.

I have been looking for a decent Linux video editor for years and I finally found it.  The others are either insanely complex, feature poor, buggy or crash constantly.  This is the project that should become the default video editor in ubuntu.

[http://www.openshotvideo.com]("http://openshotvideo.com/")
I hope I can get openshot to work.

---

### Post by mgmiller on 2009-12-29
> I've installed it, but it won't start

What version of Ubuntu are you running?  How did you install it?  did you use the .deb or the ppa.  If you used the .deb, I believe there are 4 dependency .debs that need to be installed first.  

Having tried it both ways, the ppa is really the best way to do it.

---

### Post by Aphorism on 2009-12-30
> **vavoem said:**
> allen3 is actually right
all video editing in linux sucks don't know how to improve it since i have no programming skills but still he's right it all is either complex buggy or lacks functionality. I work with ubuntu since version 6 for all of my work, but can't help booting up xp for that single thing. I would actually pay for a good piece of software and believe me i have tried them all.
Thats not a Rant but truth and a reason for people to skip ubuntu as a worthy windows replacement

Honestly, you are fueling the delusional fire again.

This type of rampant opinion makes me ill to the teeth.  First, you are an audience member. What type of audience are you?  There is no such thing as 'complex' - it is a relative statement.  And no you haven't tried them all...

Video editor eh? So you are looking for something that outputs a CMX3600 EDL?

Are you looking to uptake an EDL for finishing such as with Smoke?

Are you looking for effects work compositing such as Nuke?

The point is that Hollywood has been using Linux for feature film making for more than a few years now.  Final Cut and Avid, while only available on other platforms, don't output a single frame in a feature film pipeline, but you already know that because you are well informed, educated, and knowledgeable right?

So how about instead of spreading complete misinformation, you inform yourself and your ability set?  If you are seeking a _Free_ non linear video editor, there are more than a few out there that, I am guessing, will meet _your_ needs.  Some are lower case F free as well.

Don't troll a very important discussion with your worthless Windows versus Ubuntu spew.

---

### Post by JC Cheloven on 2009-12-30
my 2p:

I've used **_OpenShot_** to edit my christmas greeting movie, and found it to be fantastic. Only a bit of patiente needed, as it takes some time from hitting 'play' to actually starting the preview.

Kino is great for the specific task of retrieving video from a camcorder.

From the rest I've used (many of them), I'd only mention avidemux. I had some partial successes in the past with it.

---

### Post by babarosa on 2010-01-01
Hi,
did I miss to read it, but LIVES is also an option and it works very fine for me.

Get the latest version v1.1.8 from here [http://www.getdeb.net/updates/ubuntu/9.10/](http://www.getdeb.net/updates/ubuntu/9.10/)

Regards, Michael

---

### Post by isaacahloe on 2010-01-14
The new Openshot 1.0 is awesome. Haven't used anything better yet.

---

### Post by wkulecz on 2010-01-14
> The new Openshot 1.0 is awesome. Haven't used anything better yet.

Where do you get it?

In the repos? 

--wally.

---

### Post by redwoodguy on 2010-01-14
[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

It is the only video editor I have found that works right out of the shoot on Koala. I tried several others which were ridiculously buggy. This baby works! And installs in less than 2 minutes flat with no hitches. A no brainer.

---

### Post by a2z on 2010-01-19
> **vavoem said:**
> allen3 is actually right
all video editing in linux sucks


Not to me. I use kino,Cinelerra,and blender. Usually simultaneously.
I've even ventured into making video and or animation with Gimp. But Gimp isn't a vid editor.
Not always have they worked well for me though. I think sometimes there may be a bad install. Or kernel trouble. But as far as the programs are concerned, They usually perform quite well. But if you don't know what your doing with any of them, Things can get hectic.
Be patient, work it out....
Much respect to devs for their hard work!
Karmic rocks!

a2z

---

### Post by LuridCinema on 2010-01-21
Im a Indie filmmaker type meself and I made a feature movie on Sony Vegas ( the movie is titled" Cannibal Killer Clowns on Dope"  [http://killerclowntheater.com](http://killerclowntheater.com) )  I gave up on windoze and now that I have went thru some moments Im sold on Cinelerra. 

I first tried Cinelerra and it crashed and crashed and crashed.  I had my format settings off and imported the videos in a different format then tried to convert to a different format which caused problems.

I gave up on Cinelerra and tried KdenLive ... Crash city GRRRRR. I tried most every other Linux NLE and had no luck. I was ready to give up !!!

I finally gave Cinelerra one more try getting the install suggestions off Ubuntu forum somewhere and have been on track since. Cinelerra has a learning curve for sure and I see that I can do whatever I want w/ Cinelerra. If I had not learned basic editing on Vegas, I prolly would have given up on Cinelerra.  I now have found a workflow that works in Cinelerra for editing MOV files and rendering it to Quicktime for Linux and now I am able to use ffmpeg to rip the .mov files to whatever I want pretty well. 

I learned that Cinelerra does not like to convert from one format to another, so I get my files into cinelerra edit and THEN do conversions w/ ffmpeg and life is much easier. So you would not want to import in AVI and render to MOV. ( use ffmpeg for conversion works better ) It is important to get your settings correct before you import the video into the program and get your render settings correct and then you are off on the learning curve. 

  Ihave been playing w/ Cinelerra for maybe 3 months now and I getting more and more confident that I can master it for  HD movie work and use it for final editing for animation & FX work. I am also learning Synfig for animation and even FX work. I feel that with the team of Cinelerra, Synfig, Gimp and Audacity, I have some powerful tools at my disposal for FREE.

---

### Post by manolomanolo on 2010-01-26
Hi to all.

I am new to video editing. I used Gnome Subtitles to create my subtitles but now I don't know how to join those subtitles to my video file.

At the moment I found some programs ripping subtitles from an existing video or "attaching" the subtitle file to a video file by maintaining those file (subtitles and video) separated anyway.

My aim is to produce a .ogg video (or any other format)  which includes the subtitles. I mean, I want to share my video with other people passing them just one video file, and not a video file plus a separated subtitle files.

Is there any tool making this work?

Thanks for your time.
Regards.

---

### Post by kiddo on 2010-01-26
I think you want mkv as the container format if you prefer to embed subtitles dynamically/cleanly, but I'm not sure which app will do the job for you, perhaps try with avidemux or handbrake.

If you want to "hard burn" subtitles into the video image directly, not sure what tools will do it either (again, maybe avidemux/handbrake).

I'm not sure the ogg container format allows subtitle streams alongside video and audio streams, I'd be glad to be proven wrong though.

---

### Post by VertexPusher on 2010-01-27
I agree MKV is the best format for this. In the repository there's a graphical tool to merge multiple video, audio, and subtitle streams into one MKV file. A command line version exists as well.

The package names are mkvtoolnix and mkvtoolnix-gui.

---

### Post by Linuxforall on 2010-01-27
Open Shot is very good, its new and well made and emulates closest to Premiere.

---

### Post by manolomanolo on 2010-01-27
Unfortunately, I have been making some tests to show subtitles and the output is not reproducible by VLC and other players too. In fact, when selecting the subtitles using VLC I get a similar error "there is no way to fix this": the result is I can see the video but no subtitles.

Also Totem tries to find a suitable plugin but it is not able to find it and so I cannot even see the video.

The original video is reproduced withount errors with both VLC and Totem.

The output video is obtained using those commands:
```
kateenc -t srt -c SUB -l en -o subtitles.ogg input.srt
oggz merge -o final-video.ogv original-video.ogv subtitles.ogg
```

Is there any alternative way to do it with matroska or other tools?
Thanks.

---

### Post by Sem Nome on 2010-01-27
Hello friends. I'm new to Ubuntu, and I don't understand much about it yet. I'm also trying to edit videos with Cinelerra. I wanted to use a video in a little "movie" I'm making, but this video was shot upside down, with a photographic camera. Do you know if it's possible to turn it around, like we do with a picture?

Thank you!

---

### Post by kiddo on 2010-01-27
> **Sem Nome said:**
> Hello friends. I'm new to Ubuntu, and I don't understand much about it yet. I'm also trying to edit videos with Cinelerra. I wanted to use a video in a little "movie" I'm making, but this video was shot upside down, with a photographic camera. Do you know if it's possible to turn it around, like we do with a picture?

Thank you!

This is probably the "rotate" effect described in [http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_14.html](http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_14.html)

Otherwise, I don't know, I don't have the patience to use cinelerra :)

---

### Post by thatguruguy on 2010-01-27
Blender has a learning curve. But after cresting that curve, you go straight from the whole thing being incomprehensible to it all being easy and self-explanatory.

---

### Post by VertexPusher on 2010-01-28
> **manolomanolo said:**
> Unfortunately, I have been making some tests to show subtitles and the output is not reproducible by VLC and other players too. In fact, when selecting the subtitles using VLC I get a similar error "there is no way to fix this": the result is I can see the video but no subtitles.

Also Totem tries to find a suitable plugin but it is not able to find it and so I cannot even see the video.

The original video is reproduced withount errors with both VLC and Totem.

The output video is obtained using those commands:
```
kateenc -t srt -c SUB -l en -o subtitles.ogg input.srt
oggz merge -o final-video.ogv original-video.ogv subtitles.ogg
```Is there any alternative way to do it with matroska or other tools?
Thanks.
kate is a very obscure subtitle format, probably not supported by many players. With mkvmerge or mmg (GUI) you can embed the original SRT file. This works with all important players; I've used it for fansubs many times.

---

### Post by manolomanolo on 2010-01-28
> **Sem Nome said:**
> Hello friends. I'm new to Ubuntu, and I don't understand much about it yet. I'm also trying to edit videos with Cinelerra. I wanted to use a video in a little "movie" I'm making, but this video was shot upside down, with a photographic camera. Do you know if it's possible to turn it around, like we do with a picture?

Thank you!

I found **Transmageddon Video Transcoder** is able to easily rotate your video.
I think it is a good program and I expected it to integrate subtitles into the final output but it doesn't seem to do that.

I supposed it would, since it seems to be an advanced version of **Arista** which is supposed to create a unique file starting from a video file (ogg) and a subtitles file (srt), but I didn't manage to. 

> **VertexPusher said:**
> kate is a very obscure subtitle format, probably not supported by many players. With mkvmerge or mmg (GUI) you can embed the original SRT file. This works with all important players; I've used it for fansubs many times.

I did manage doing it using **MMG**!!! It is not into my "sound & video" application menu so I had to run it from command line... it is awesome!

Anyone knows how to merge those files with Arista?

---

### Post by loopduplicate on 2010-01-28
Blender is the best video tool ever!  It's so damn fun to use when you get used to it.  There's a million how-to videos out there.  That's the biggest problem because you have to sort through them all.

With Blender I can do all sorts of things with video like:
rotate, 
crop, 
stretch, 
skew, 
transcode, 
blend movies together like layers in GIMP or Photoshop
mix and cut audio
add subtitles
add graphics
add filters like blur, old movie effect, color correction, satufation, alpha blending
brightness/contrast
time stretch or shrink
deinterlace
mirror horizontally or vertically

there's a ton more too.

Also, Blender runs on Windows, Mac, and Linux so no matter what computer you are on, it is the same program.

And there's great keyboard shortcuts so you can work super fast when you get to know them.

The latest stable release is 2.49b.  But I use the latest builds that can be found at Graphicall.org because the new builds have some even better features.  There is a whole team of people working on a movie that is being made with Blender.  This includes paid developers that work on the video sequencer code.

Blender is for people who are serious about video.  Because you only have to learn it once and you know it is here to stay for a long time.

Loop Duplicate

---

### Post by VertexPusher on 2010-01-28
> **manolomanolo said:**
> I did manage doing it using **MMG**!!! It is not into my "sound & video" application menu so I had to run it from command line...
It does appear in the sound & video menu, but with a different name. Look for "MKV Files Creator" or something similar.

---

### Post by zsolt.trenyik on 2010-02-01
hi all, 
 
a use cinelerra for a few days, but I had to notice that it makes a joke with me. I have an audio track and a video track. when I work in the timeline, and playback my work from a point, audio runs slower than video. this means, that I cannot edit my video track connected to the specific points of the sound.
 
The problem is, based on the documentation, that I use alsa driver (preferences, ..., playback), however I had to set Esound (on port 7007, server name is empty), which would work via the Esound-compatible layer of PulseAudio. This sounds great! But, I set the preferences of my 9.04 Ubuntu to use PulseAudio, it runs fine, totem is able to use it. I installed the addon softwares for Pulseaudio, so I can monitor the daemon events, and see that totem connects etc.
 
I set the above things in cinelerra, and two may happen: either it crashes when I press play in the timeline (I started from terminal as user, to see dropped messages, but there was no error code or else) or if I start it with sudo, it starts to play the timeline, but there is no sound, and in the terminal I get the message that it cannot open sound device or similar.
 
I'm really confused, because until I can't solve this sync problem, cinelerra is just a desktop design element :(
 
I also played a lot of with the setting in the preferences-playback screen, realtime priority, play every frame etc, in every combination, but without any good result.
 
thanks for any advise. zsolt

---

### Post by zsolt.trenyik on 2010-02-01
sorry, my cinerella verison  is 2.1 (from the repository)

---

### Post by wildhostile on 2010-02-01
Hi zsolt.trenyik,

Maybe a codec/format problem.
What are the codecs/format of your videos.
midentify yourfile
or mplayer -identify
or right click on your video in nautilus, Properties -> Audio/Video
... to find it.

---

### Post by sheehanje on 2010-02-01
After reading through this whole 8 page long thread, I've settled on Blender.  I already use Ubuntu Studio for recording my band, but I wanted to start editing video to post live shows with simple titles and transitions.  I followed the following link provided earlier in this thread:

[http://blog.rfquerin.org/2009/01/26/how-i-edit-videos-using-blender-maybe-part-one/](http://blog.rfquerin.org/2009/01/26/how-i-edit-videos-using-blender-maybe-part-one/)

I also started looking into syncing with jack and ardour as shown in this video:

[http://www.youtube.com/watch?v=xvysT6Ak4y4](http://www.youtube.com/watch?v=xvysT6Ak4y4)

This works for me, and better than what I was able to do with windows.  I've even got a midi control surface working for triggering repetitive events.

Blender is daunting to look at, but with a little practice, it is the easiest solution to use in Linux for video editing, imho.

---

### Post by zsolt.trenyik on 2010-02-03
thanks for the tip, but my "video" are just series of still images, the audio is mp3 (I tried also with wav, and got the same result).

after some configuration, cinelerra behaves even more crazy. if I delete the audio track, create a new one, and drop onto it my sound file, it is duplicated (twice after each other) by default.

I would try mainactor, but I cannot get it (neither the demo nor some cracked version - (I work for an assossiation so nobody won't get money for the work...). I didn't find any documentation which type/size of marking the demo version places in the rendered picture, maybe it would be enough for me, it it was only in the corner... 

another problem: I downloaded cinelerra 4.1 for Ubi 9.04 (I have this one). just unzip it, and I had to get a ready-to-use version of the software. however, if I try to start it with sudo ./cinelerra, I get the message that it cannot execute binary file. strange...

---

### Post by cooper77z on 2010-02-04
Hi zsolt.trenyyik and friends,

I used to have those problems with cinelerra too, but I found this tutorial

[http://www.g-raffa.eu/Cinelerra/HOWTO/settings.html#_how_to_avoid_a_slow_playback_of_the_video_in_the_compositor](http://www.g-raffa.eu/Cinelerra/HOWTO/settings.html#_how_to_avoid_a_slow_playback_of_the_video_in_the_compositor)


Cinelerra for Grandma, and Cinelerra is quite usable for me now. You should check it out. That audio sync problem is easily fixed in the following manner"
**How to avoid a slow playback of the video in the Compositor**

  "By default Cinelerra plays every single frame of the video. That can cause the video playback to slow down a little. It can even fall behind audio. To avoid that, go to *Settings &#8594; Preferences &#8594; Playback*. Deselect *Play every frame*. During playback some frames will be dropped (not played) and the motion will appear a bit jerky but the video will be in synch with the audio. The motion will be jerky only in the *Compositor* preview and not in the final file since every single frame will be rendered." From Cinelerra for grandma.


I hope this helps. Cinelerra needs some helper programs to work right. She likes DV format and it's easy to make everything DV with winff. You can change DV back to mpeg with Kino if you want to use Devede to burn a DVD, but you have to inslall the correct Kino dependencies. Video editing with linux is totally do-able. Just read some how to's and doccumentation, especially if you use Cinelerra. Openshot is great too, but I can only get it to work right without audio sync issues under 9.04, so I use 9.04 Good Luck, and read through the How To's at Cinelerra for Grandma :)

---

### Post by zsolt.trenyik on 2010-02-04
hi cooper,

thanks for the tip. since I have some deadline in my calendar, I downloaded mainactor (after an hour I was even not able to make a still image e.g 4 sec long... any tip?), and looked for some information about this feautre in blender. but I will try what you advised above. cinelerra is ugly, but absolutely usabel expect some bugs.

the problem with this audio sync problem in cinelerra is similar to many things in the net: somebody writes a solution (maybe copied from the docs), and in the 99 percent of the cases you will read this one... but it doesn't work for you. 

thanks once again, I will step on with this in the evening.

---

### Post by zsolt.trenyik on 2010-02-04
do you use 2.1 ot the 4.1 version on 9.04? thanks.

---

### Post by LuridCinema on 2010-02-04
> **zsolt.trenyik said:**
> 

after some configuration, cinelerra behaves even more crazy. if I delete the audio track, create a new one, and drop onto it my sound file, it is duplicated (twice after each other) by default.




Maybe you need to check the "add new files at insertion point" when loading new files, otherwise you can duplicate things when you load files.  You have several options. One option is add new resources only and it adds the clip / audio to the media section where you cabn drag 7 drop it to the timeline


EDIT:

One other thing make sure the framerate is set correct, before you add media to the timeline sometimes that will create audio sync issues. I dont know if you tried that but it comes to mind

---

### Post by cooper77z on 2010-02-04
zsolt- I am using 2.1.1 If all you are doing is putting some digital photos together with some audio mp3s you should just install and use Openshot, especially if time is an issue. Or you can try editing online here [http://jaycut.com/](http://jaycut.com/) or youtube, or somewhere else online. There are lots of online video editors. I have never tried them though, so I don't know how well they work. Even if you have audio sync issues with Openshot it shouldn't be a big deal unless you are editing in a talking head. Cinelerra will probably take some time, and Openshot is really easy to learn and it's intuitive as well.

Video editing on a computer is difficult to learn on windows and mac too. It took me about a year to learn video editing on windows, and it took me nearly a year to learn on Linux. I learned Final Cut Pro on a Mac in about 2 months, but that was after taking 8 hours worth of classes. Don't be frustrated, video editing is difficult :)

---

### Post by zsolt.trenyik on 2010-02-05
hi all, thank for the tips, I wil try all. I worked 5 years long in a studio at the univesity (however, editing was mostly traditional, but sometimes nonlinear, too), the problem is not the editing but the quality of the software :( I don't want to set up an xp to do it... 

yesterday I tried Mainactor (blender has also many professional tutorials), in the first step without sound, because my wife slept already, it has a really nice interface and doc. it's strange, but cinelerra looks for the first sight more professional, but in the bug-counting topic it would be surely the winner.

I think video editing is not so difficult, but takes really much time, of course depending on what you want to get as a result :)

---

### Post by cooper77z on 2010-02-05
Before you give up on Cinelerra try this code: it sets the program up to work for beginners like us.

**Step 2: Adjust settings**

  The quickest way to adjust Cinelerra settings is downloading the configuration file I prepared just for you and saving it in the .bcast folder.

 
[LIST]
[*]  Make sure you have no instances of Cinelerra open.
[*]  Open a terminal
[*]  Copy and paste one of the following loooong commands, depending on your standard:
[/LIST]

 PAL:

 wget [http://www.g-raffa.eu/Cinelerra/HOWTO/Cinelerra_rc-PAL.tar.gz](http://www.g-raffa.eu/Cinelerra/HOWTO/Cinelerra_rc-PAL.tar.gz) && tar xvf Cinelerra_rc-PAL.tar.gz && mv PALCinelerraSettings/Cinelerra_rc .bcast/Cinelerra_rc && rm Cinelerra_rc-PAL.tar.gz

 NTSC:

 wget [http://www.g-raffa.eu/Cinelerra/HOWTO/Cinelerra_rc-NTSC.tar.gz](http://www.g-raffa.eu/Cinelerra/HOWTO/Cinelerra_rc-NTSC.tar.gz) && tar xvf Cinelerra_rc-NTSC.tar.gz && mv NTSCCinelerraSettings/Cinelerra_rc .bcast/Cinelerra_rc && rm Cinelerra_rc-NTSC.tar.gz

 This operaton creates in your home directory a directory called *PALCinelerraSettings* or *NTSCCinelerraSettings*. Inside, you have a *README* file that explains the changes I&#8217;ve made just for you.

 If you have time to waste, you can also perform this operation with no command lines. For instructions see the [Adjusting settings]("http://www.g-raffa.eu/Cinelerra/HOWTO/settings.html#_how_to_start_cinelerra_with_the_best_settings_for_grandma") page.


Then follow instructions for whatever you want to do from here: [http://www.g-raffa.eu/Cinelerra/HOWTO/index.html](http://www.g-raffa.eu/Cinelerra/HOWTO/index.html)

Cinelerra isn't as buggy as you think if you follow the instructions rather than just clicking around hoping to make it work right. You might want to increase the render quality a tad, but not too much. It's really easy to render video that outperforms my computer, a Dell Inspiron 1000 Laptop with like 700 megs of ram. I discovered that it's actually better to convert my MP4 video that my camcorder captures on SD Card over to Quicktime with 3175 bit rate via winff program rather than converting it to DV. I like Cinelerra better than Adobe Premiere now that I understand how to use Cinelerra.

EDIT::: Quicktime does not quite work right in the viewer screen on my computer, but mjpeg works flawlessly as far as splicing and overwrite mode. This line of code converts my MP4's to MJPEG 
mencoder -vf harddup -demuxer lavf -oac pcm -ovc lavc -lavcopts vcodec=mjpeg:vhq:vbitrate=6000 -noskip -mc 0 -o output.mov input.ext

---

### Post by zsolt.trenyik on 2010-02-08
hi all, I made some tests with mainactor. although it is a commercial software, it is far not perfect. I found in a blog that the version 5.5.19 is fairly usable (it just drops render error without any reason...). Can anyone share this in deb package (the shareware version, to test it)?

I guess I have 5.5.7 or something like, with a really awful bug: it cannot handle 2D text (label). maybe it was a developer release only :)

In other points its gui is clear-out, audio runs in sync with video part, and I would have even paid for it, but segmentation fault when working with these trivial parts, that doesn't make a professional image about it... (at least, this version)

thanks if somebody can provide it for download (in the mentioned post the author writes that this function in 5.5.19 is OK, but none of the above and below ones)

---

### Post by AlexanderDGreat on 2010-02-08
I'm gonna talk. I admit I didn't read what's been discussed here. I'm a newbie, and I can do tons of GIGS of High Definition Videos in Cinelerra, upload to YouTube without any problems, sometimes convert with FFWin, it crashed on me 5 out of 100 uses, I get on with my life, what's so hard with it? I'm using JJ 32 bit AMD64 laptop.

Basic Video Editing In Cinelerra Part 1:

[http://www.youtube.com/watch?v=-Q-NTYLiyKc]("http://www.youtube.com/watch?v=-Q-NTYLiyKc")

---

### Post by zsolt.trenyik on 2010-02-09
"I admit I didn't read what's been discussed here"

that's the first problem...

---

