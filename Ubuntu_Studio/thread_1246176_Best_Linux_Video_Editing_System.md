---
title: "Best Linux Video Editing System"
date: 2009-08-21
forum: Ubuntu Studio
---

### Post by markekeller on 2009-08-21
It's been almost a year since I've done any video editing in Linux, so I'm wondering what program is currently the best for that sort of thing.  Back when I was editing footage, Cinelerra was heading the pack, but some other programs were catching up.

I need to be able to do basic video sequencing, as well as chroma-keying, compositing, and (maybe) video stabilization.  A program that works fast and doesn't crash a lot is a plus.  Anyone know what's the best application for that purpose, currently?

---

### Post by brunolabs on 2009-08-21
IMO Cinelerra keeps "heading the pack". ;)

---

### Post by decoherence on 2009-08-21
[Smoke!]("http://usa.autodesk.com/adsk/servlet/index?siteID=123112&id=5561833")

Newer versions of Blender also have some [powerful video editing capabilities.]("http://www.blendernation.com/tutorials/blender-3d-beginner-tutorial-the-blender-sequence-editor/")

But something tells me you'll want to stick with Cinelerra

---

### Post by metalf8801 on 2009-08-21
I've been told that cinelerra is the best as in it can do the most and its a professional software but its not very users friendly   
Cinelerra's home page:[http://www.heroinewarrior.com/cinelerra.php](http://www.heroinewarrior.com/cinelerra.php)

I've also heard good things about kdenlive which I think you can get using Add/Remove 
here's a video about kdenlive: [http://www.youtube.com/watch?v=1eHEAfNFJ0k&feature=related](http://www.youtube.com/watch?v=1eHEAfNFJ0k&feature=related)
Kdenlive homepage [http://kdenlive.org/](http://kdenlive.org/)

I hope this helps 
Dan

---

### Post by macunixfan on 2009-08-21
Cinelerra is the most like Final Cut Pro. But you can also try PiTiVi which I think just released a new version. It's more like Windows Movie Maker though.

---

### Post by brunolabs on 2009-08-22
> **metalf8801 said:**
> I've also heard good things about kdenlive which I think you can get using Add/Remove

Does it work without problems under GNOME?

---

### Post by cotcot on 2009-08-22
What you ask is stuff for cinelerra or blender VSE.

---

### Post by brevardo on 2009-08-24
I have Cinelerra and it appears that it will be able to do exactly what I want. the only problem is that it seems to be very confusing when just trying to do simple things. All that I want to do is load an image file to track 1 and then load an audio file to track two. the problem that I'm having is that the image file will only play for .2 of a second. how do I duplicate it ( or drag it ) or set it to play for 10 minutes. It was very easy to do this in Windows Movie Maker. Any suggestions?

---

### Post by joey-elijah on 2009-08-24
For simple things it's worth using OpenShot. it has loads of transitions, effects, non-linear editing, previews etc. 

[IMG]http://lh3.ggpht.com/_AuTEvUYi4Ms/Sj3DOZDU35I/AAAAAAAAAr4/X0GUw4SZxqw/s576/Spiral%20Wipe.png[/IMG]

[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

---

### Post by wildnfree on 2009-08-30
OpenShot is fast becoming the leading Non-Linear Video Editor.

It is fast, stable, and very easy to use. OpenShot is just about to have its first beta release when we have got the packaging fully tested. Though it has been capable of some awsome results in alpha state.

Some effects like Chroma-Key are not in it yet, but will be added shortly after the first beta release.

---

### Post by Cresho on 2009-09-02
heroens version of cinelerra are betas.  THey have audio and video sync issues when you toss certain files into the timeline.

cinelerra akira from cinelerra cv are the best.  They have none issues minus your video driver.

One thing i had to do on nvidia powered workstation is to create a script to color calibrate cinelerra.  xv or opengl does not use the nvidias driver for xvideo. to color correct.  It uses the desktop's colors which should not be.

here is my script to correctly fix this issue.

```
#!/bin/bash

xgamma -gamma .7;
Cinelerra;
xgamma -gamma 1.0
```

after cinelerra closes, it corrects your desktop again.

---

### Post by Stochastic on 2009-09-02
OpenShot should NOT be used by the average Ubuntu user just yet.  It requires versions of libraries that aren't even released yet, nevermind supported by Ubuntu.  The installer grabs development snapshots of those libraries and deletes any other version of those libraries currently installed on your computer.  This could lead to major issues on your computer.  Don't use it until it can be run against a stable release of it's libraries (probably at least a few months away).

As for the OP's feature set, I too say Blender or Cinelerra is the way to go.

---

### Post by Cresho on 2009-09-03
Blender for HD is not yet mature enough though I have dabled weeks with it.  In 720p, my max render for video time is 30 minutes at a time.  This should not be.  also, 60fps is not supported.  when dropping files into the timeline, it comes out of sync  and yes i adjusted the paramaters for the ones who know what im talking about.  It has issues and not mature enough.  It is tough getting some kind of suggestions from the developers.  I tried contributing but it was impossible.

Cinelerra cv is the best!  it has a slight learning curve but once you understand it, it is the best video editor surpassing vegas video you can get your hands on.  If you are creative, you can also come up with some videos that are just awesome.

---

### Post by todaymueller on 2009-09-03
Open shot looks fantastic :D The screen shots promise a much better editor than kino .

---

### Post by Ubuntiac on 2009-09-03
Just to clear up a couple of things people seem to miss:

1. Blender - while my favourite FOSS app - does *not* have "powerful editing features". It has weak, barely passable editing features mixed with powerful *compositing* and *3d* features. The two are not the same. That said, if you can get around the sound sync issues, it's still pretty decent for basic stuff.

2. Openshot - Is basically Kdenlive with a different Gnome interface. Under the hood, it's still ffmpeg, mlt etc. Worth noting though is that the main mlt dev also works on kdenlive, not openshot, so my guess is better milage from Kdenlive for this reason. That said, Kdenlive is not exactly stable unless you're primarily working with mpeg based formats (eg m2t / dv). That said it does *not* require (or even benefit from) you running KDE over Gnome (other than matching icons etc). It only requires the kdelibs package, not the whole kde desktop.

Anyway, in summary, I'm not fussed which video editing app anyone's pushing, as long as you're doing *something* to help further the cause of one of them. Right now we have a problem of everyone wanting to wait for an app that works perfectly for them first before contributing. All the apps out there currently need help to really get to a usable, functional and stable state. Whichever one gets there first (OK, maybe 2, one for entry level, one for pro) will dominate eventually just as Gimp / Inkscape do, but they're all suffering from chicken and egg syndrome at the moment (ie no finished app without help, no help without a finished app). So please, before replying to my comments here, just ask yourself if you're currently contributing to *any* FOSS video app's progress.

---

### Post by Cresho on 2009-09-03
Though I love openshot, its pretty useless due to mlt and kernel version in my hardy.  After splitting videos, my final render comes out of sync with audio/video.  KDEnlive suffers the same fate.

Still looking forward to testing the later versions.  Cinelerra cv has no issues at the moment.

---

### Post by Ubuntiac on 2009-09-03
> **Cresho said:**
> Though I love openshot, its pretty useless due to mlt and kernel version in my hardy.  After splitting videos, my final render comes out of sync with audio/video.  KDEnlive suffers the same fate.

Still looking forward to testing the later versions.  Cinelerra cv has no issues at the moment.

If it's a problem on both OpenShot and Kdenlive then the bug probably lies with either FFMPEG or MLT. I'd ask Dan (the MLT dev) and he'll likely be able to either fix it, or point you to the FFMPEG bug tracker.

---

### Post by Ubuntiac on 2009-09-03
Just something interesting to add:

Blender just released 2.49b which fixes a couple of bugs in the VSE, but more interestingly (finally) adds support for importing the following parts of EDL:

# audio, video edits
# fades, wipes, speed changes (video only)
# importing from multiple reels

**Import dialogue:**
[IMG]http://www.graphicall.org/ftp/ideasman42/edl_import_ui.png[/IMG]

**Project imported from Final Cut Pro**
[IMG]http://www.graphicall.org/ftp/ideasman42/edl_in_blender_px.png[/IMG]

---

### Post by Cresho on 2009-09-03
> **Ubuntiac said:**
> If it's a problem on both OpenShot and Kdenlive then the bug probably lies with either FFMPEG or MLT. I'd ask Dan (the MLT dev) and he'll likely be able to either fix it, or point you to the FFMPEG bug tracker.

its an mlt and kernel version issue.  I read tons on this subject.  If i split the file in kdenlive, its renders fine and i mean splitting the audio from video.  cinelerra cv is flawless.  ill give dan a ring.

here is my blender getup

[IMG]http://forums.steves-digicams.com/attachments/sanyo/130257d1224927072-editing-avchd-using-video-cards-hd3850-hd3870-hd3650-blender-video.jpg[/IMG]

---

### Post by joey-elijah on 2009-09-04
> **Ubuntiac said:**
> 
Anyway, in summary, I'm not fussed which video editing app anyone's pushing, as long as you're doing *something* to help further the cause of one of them. Right now we have a problem of everyone wanting to wait for an app that works perfectly for them first before contributing. All the apps out there currently need help to really get to a usable, functional and stable state. Whichever one gets there first (OK, maybe 2, one for entry level, one for pro) will dominate eventually just as Gimp / Inkscape do, but they're all suffering from chicken and egg syndrome at the moment (ie no finished app without help, no help without a finished app). So please, before replying to my comments here, just ask yourself if you're currently contributing to *any* FOSS video app's progress.

I try to help as best i can with bug reports etc though i'd seriously love to do more.

I think the same issue with Video Editors will move on to Audio Editors; Linux needs a user-entry "garageband". Something that combines LMMS with Audacity via Jokosher's interface.

---

### Post by Ubuntiac on 2009-09-04
> **joey-elijah said:**
> I try to help as best i can with bug reports etc though i'd seriously love to do more.

Awesome. It doesn't take doing much, just doing something. There are loads of people using open source. The key to opening the floodgates is getting more users to contribute. Just a small percentage of users contributing equals a large contribution.

Just to show I'm not being hypocritical here, I've done a lot of bug triaging on Kdenlive and it's builder wizard as well as some artwork, and filed a stack of bugs on Blender. I'm interested in helping Lumiera more, but thus far (as I'm not a coder) haven't really found any way of helping beyond advocacy and putting in an entry for their logo design (which wasn't as good as the one that won, anyway!).

As with most people, I'd love to help more, it's all about finding a need that matches my skills (design, artwork, copywriting and marketing).

---

### Post by Cresho on 2009-09-05
Im looking forward to lumiera myself. They are the same folks who did cinelerra.

---

### Post by cotcot on 2009-09-06
> **Cresho said:**
> Im looking forward to lumiera myself. They are the same folks who did cinelerra.

Me too.
Any idea about the amount of developers ?

---

### Post by Cresho on 2009-09-11
Not sure about the developers but I tried installing it on a 64bit system and it has a few issues.  especially that nobug program.  Doesnt seem to like my 64bit system.

---

### Post by ongandrew on 2009-09-13
Offtopic:
ei cresho what os are you using i have seen the screenshot of your desktop at page 2 of this thread i was wondering where to get a theme like that am using ubuntu 9

---

### Post by Mazza558 on 2009-09-13
> **joey-elijah said:**
> 
I think the same issue with Video Editors will move on to Audio Editors; Linux needs a user-entry "garageband". Something that combines LMMS with Audacity via Jokosher's interface.

LMMS will have proper audio support in 2010 - e.g being able to add, edit, slice audio tracks and samples like you would in Audacity. :)

---

### Post by theZoid on 2009-09-13
> **wildnfree said:**
> OpenShot is fast becoming the leading Non-Linear Video Editor.

It is fast, stable, and very easy to use. OpenShot is just about to have its first beta release when we have got the packaging fully tested. Though it has been capable of some awsome results in alpha state.

Some effects like Chroma-Key are not in it yet, but will be added shortly after the first beta release.

thanks...I like this Openshot....:P  

EDIT:  is there a repo we can add for updates?  this would be totally cool :)

---

### Post by mr.matt.numberguy on 2009-09-13
This looks like an older thread but I figured I would post my experience that might help others choose. I am a new linux user (mint). First I tried kino but couldn't create title pages. Next I tried Avidemux but couldn't do anything -- seems like it is more of a converter than an editor. Next I tried PiTiVi but again I couldn't create a Title page. All of these were available from the Package Manager (I'm tentative to venture from it after crashing my Kubuntu from "self-installed" software). Anyhow, OpenShot screenshots showed it had a Title page maker. I downloaded the two deb package files from their site (version 0.9.22) and first installed the dependencies, then OpenShot (easy double-click from Nautilus). OpenShot fired right up no problems. I was easily able to make a title page, insert and trim two videos, add simple fade transitions, and create an mpeg4 video. The video quality was great in my opinion (as viewed in VLC). I next tried to create an mpeg2 video. That was tricky only because I didn't know what combination of video/video codec settings to use. I think they will improve that in the future to only allow "logical" combinations. I'm not an AV expert. I ended up choosing MPEG video with MPEG2VIDEO codec. Previously I chose MPEG2VIDEO "video" and MPEG2VIDEO "codec" and my output file didn't have audio. Not exactly logical. This "beta" program did more for me than the other 3 I tried. I gave a small donation and wish them well. The program had very few extra files I had to install (no Mono) so I was pleased with that. Good luck!

---

### Post by theZoid on 2009-09-13
> **Stochastic said:**
> OpenShot should NOT be used by the average Ubuntu user just yet.  It requires versions of libraries that aren't even released yet, nevermind supported by Ubuntu.  The installer grabs development snapshots of those libraries and deletes any other version of those libraries currently installed on your computer.  This could lead to major issues on your computer.  Don't use it until it can be run against a stable release of it's libraries (probably at least a few months away).

As for the OP's feature set, I too say Blender or Cinelerra is the way to go.

I've installed Openshot without issue on my Ubuntu 9.04 x64 installation.  I installed the required dependencies as provided by the site which are shown in the attached screenshot.  Are those dependencies replacing existing files on my system?  I don't see any problems so far...how can I check this?  These dependencies were selected specifically for Ubuntu 9,.04 x64 by the dev team....hasn't the development team tested this?  thanks

---

### Post by ajju31 on 2009-09-13
Have been using openshot and Cinepaint for video and image editing recently.Promising as it sounds never straightforward/simple are the linux editing tools.

Cinepaint is good to render a frame sequence to generate changing patterns .....I seem to be struggling to generate simple text on a black background with after effects like typewriter ,Text dissolving in/out ....

With cinepaint i don't seem to have any option for text filters except for worm like effect ....Please help.

My requirement is simple....Open any editor ,type text , go to filter and "choose slide from left to right in a typewriter style".....None of the tools provide me with a straightforward option .Solution anyone?

---

### Post by jukingeo on 2009-09-13
> **mr.matt.numberguy said:**
> OpenShot (easy double-click from Nautilus). OpenShot fired right up no problems. I was easily able to make a title page, insert and trim two videos, add simple fade transitions, and create an mpeg4 video. The video quality was great in my opinion (as viewed in VLC). I next tried to create an mpeg2 video. That was tricky only because I didn't know what combination of video/video codec settings to use. I think they will improve that in the future to only allow "logical" combinations. I'm not an AV expert. I ended up choosing MPEG video with MPEG2VIDEO codec. Previously I chose MPEG2VIDEO "video" and MPEG2VIDEO "codec" and my output file didn't have audio. Not exactly logical. This "beta" program did more for me than the other 3 I tried. I gave a small donation and wish them well. The program had very few extra files I had to install (no Mono) so I was pleased with that. Good luck!

I have high hopes for OpenShot myself.   As you pointed out, I got further with OpenShot than with any other program.   As of now the only other video editing program I have on my machine is Cinelerra.   While it is the better of the two programs, it is pretty hard to work things out in it and in the midst of learning Cinelerra, I said, "There has to be an easier way".

I am testing OpenShot right now and apparently I have not been met with as stellar results as you have.  I have had a few problems with the program, but it is still a night and day difference compared to other editors out there that simply do not work at all or just often crash.

I really only have two issues with OpenShot:

1) Export has a tendency to produce pixelated video output...even on high settings.  I am not sure if this is my fault or the fault of the program, but  it sounds like the video turned out fine on your end...so I would appreciate it if you could enlighten me to your settings for an OpenShot export.

2) OpenShot DOES have audio/video sync problems and it has been determined as being a bug.  They are working on the problem though.

So it does look like OpenShot is ALMOST there.  I am hoping the issues are fixed soon because I would rather use this program than try to learn Cinelerra.   Don't get me wrong, I DO like Cinelerra, but it is a VERY serious video editor...something what you would need for movie or music video work.  I am just making simple videos and want something that edits FAST!

Thanx,

Geo

---

### Post by cbstryker on 2009-09-14
I would like to know what is the best editor to use to work with AVCHD (.m2ts or .mts) video. I've tried most of what was mentioned here (except for Jahshaka, Cinelerra, OpenShot and Smoke). I'm most experienced in After Effects CS4 and Premier CS4. So any suggestions?

---

### Post by jukingeo on 2009-09-14
> **cbstryker said:**
> I would like to know what is the best editor to use to work with AVCHD (.m2ts or .mts) video. I've tried most of what was mentioned here (except for Jahshaka, Cinelerra, OpenShot and Smoke). I'm most experienced in After Effects CS4 and Premier CS4. So any suggestions?

It depends on what you want to do.   If you just need to do basic editing, some have had good results with Kino.  For some reason it doesn't work on my system.

If you want to take it to the next level and want to edit/make family videos or create basic music videos with title screens, transitions and wipes then for KDE you would use Kdenlive and for Gnome, Openshot is the new kid on the block.

If you want to make precise in sync video with music that hits with the scenes on screen (advanced music video) or if you are doing professional cinema quality movies, then the only clear cut choice here is Cinelerra.  

Naturally by reading that you might think, "Ok, I will go with Cinelerra and the world is my oyster?"  Well, the answer to that would be yes and no.  Cinelerra has a very difficult learning curve and some tasks that would seem easy in other editors take a long time in Cinelerra.  Yes it is powerful, but with it's power also comes that long learning curve.  It might take a very long time before you produce that first video.   Unless you have some guides or help from someone else, you will get lost very fast in Cinelerra.  It isn't as intuitive as the other programs of which you can 'figure out' in a short time and start making video right away.  But that said and out of the way, if you take the time to become a master with Cinelerra, then yeah it is probably the best out there for Linux.

Geo

---

### Post by cbstryker on 2009-09-15
> **jukingeo said:**
> If you want to make precise in sync video with music that hits with the scenes on screen (advanced music video) or if you are doing professional cinema quality movies, then the only clear cut choice here is Cinelerra.

Ok, I've quickly tested out installing CinelerraCV on a virtual machine at school (I'm taking Network Engineering) and it seems alright. Learning it shouldn't be a problem for me, I am familiar with Combustion and other editors.

But when I tried to import an AVCHD file (.m2ts) it said it could identify the type of file and was assuming raw PCM. 

I know, I know, we all hate AVCHD, I do too. It's a backwards standard imo, but converting every-single-clip from my HD camera is just not an option. I do a lot of filmimg (vacations, dirtbiking, friends weddings, etc) and I practically generate 5 - 6 GB of video a month (and that's only at 1440x1080 7mbps setting on my camera) so that's WAY to much to deal with. Although I do use Badaboom to convert my final outputs to a more manageable size (Badaboom can do full HD for me at >60fps encoding) but that's still a huge time investment on my machine and as far as I know it's not available, nor will be, for linux.

So is there any way to get AVCHD into Cinelerra?

---

### Post by ceciliaFX on 2009-09-15
> I really only have two issues with OpenShot:

1) Export has a tendency to produce pixelated video output...even on high settings. I am not sure if this is my fault or the fault of the program, but it sounds like the video turned out fine on your end...so I would appreciate it if you could enlighten me to your settings for an OpenShot export.weird question: can OpenShot save frames in some format like PNG?

---

### Post by Stochastic on 2009-09-15
> **theZoid said:**
> I've installed Openshot without issue on my Ubuntu 9.04 x64 installation.  I installed the required dependencies as provided by the site which are shown in the attached screenshot.  Are those dependencies replacing existing files on my system?  I don't see any problems so far...how can I check this?  These dependencies were selected specifically for Ubuntu 9,.04 x64 by the dev team....hasn't the development team tested this?  thanks

Wonderful, now that there's .deb packages available from their site they have fixed a major portion of their install process.  Previously, their 'Build Wizard' had some very bad install script practices (it's unfortunately still available on their download page) where the latest development snapshot was being downloaded rather than a consistent version of the libraries.

The dependencies in that package are exact versions that the dev team has checked.  Some of these are official release versions, some are development snapshots of libraries, but all of them are higher than the version available in Jaunty.  They will replace the current version installed on your system, and I doubt the OpenShot team has checked that those versions work perfectly with all of the other Jaunty programs that will use the specified libraries.

These latest .deb files greatly reduce my concern over beginners installing this software, but does not eliminate it entirely.  I'm very glad to see that they've fixed the install process on specific versions of their dependencies - now reliable bug reports can be filed/tracked/fixed.

---

### Post by AlexanderDGreat on 2009-09-15
Hi, I don't have editing experience, but Cinelerra worked for me!

If you want a stable and crash-free (in my case) Ubuntu 9.04, Asus C2D 1g RAM, Desktop try Cinelerra,

I've tried kdenlive (crashes), OpenShot (crashes) and Kino (crashes), but Cinelerra is the one that FINISHED the project for me.

The catch, watch these tutorial videos: 

Basic Editing in Cinelerra Pt. 1 - [http://www.youtube.com/watch?v=-Q-NTYLiyKc](http://www.youtube.com/watch?v=-Q-NTYLiyKc)
Basic Editing in Cinelerra Pt. 2 - [http://www.youtube.com/watch?v=r4ollw6Cqjc&](http://www.youtube.com/watch?v=r4ollw6Cqjc&)
Basic Editing in Cinelerra Pt. 3 - [http://www.youtube.com/watch?v=cIjSBiWc9Qs&](http://www.youtube.com/watch?v=cIjSBiWc9Qs&)
Basic Editing in Cinelerra Pt. 4 - [http://www.youtube.com/watch?v=gxWbfhD6Tnw&](http://www.youtube.com/watch?v=gxWbfhD6Tnw&)
Basic Editing in Cinelerra Pt. 5 - [http://www.youtube.com/watch?v=PyxCf5qwYlE&](http://www.youtube.com/watch?v=PyxCf5qwYlE&)

They're 6-8 minutes long. If a newbie like me can do it, I'm sure you can do it too with patience, just like we have patience for Linux. =)

I hope it'll give you the confidence and take away your frustration to finally video-edit in Linux. Best of luck making it work for you. =)

---

### Post by theZoid on 2009-09-15
> **AlexanderDGreat said:**
> Hi, I don't have editing experience, but Cinelerra worked for me!

If you want a stable and crash-free (in my case) Ubuntu 9.04, Asus C2D 1g RAM, Desktop try Cinelerra,

I've tried kdenlive (crashes), OpenShot (crashes) and Kino (crashes), but Cinelerra is the one that FINISHED the project for me.

The catch, watch these tutorial videos: 

Basic Editing in Cinelerra Pt. 1 - [http://www.youtube.com/watch?v=-Q-NTYLiyKc](http://www.youtube.com/watch?v=-Q-NTYLiyKc)
Basic Editing in Cinelerra Pt. 2 - [http://www.youtube.com/watch?v=r4ollw6Cqjc&](http://www.youtube.com/watch?v=r4ollw6Cqjc&)
Basic Editing in Cinelerra Pt. 3 - [http://www.youtube.com/watch?v=cIjSBiWc9Qs&](http://www.youtube.com/watch?v=cIjSBiWc9Qs&)
Basic Editing in Cinelerra Pt. 4 - [http://www.youtube.com/watch?v=gxWbfhD6Tnw&](http://www.youtube.com/watch?v=gxWbfhD6Tnw&)
Basic Editing in Cinelerra Pt. 5 - [http://www.youtube.com/watch?v=PyxCf5qwYlE&](http://www.youtube.com/watch?v=PyxCf5qwYlE&)

They're 6-8 minutes long. If a newbie like me can do it, I'm sure you can do it too with patience, just like we have patience for Linux. =)

I hope it'll give you the confidence and take away your frustration to finally video-edit in Linux. Best of luck making it work for you. =)

You sure did put the bug in me, and probably a few others :P  Thanks for the links !

---

### Post by jukingeo on 2009-09-15
> **AlexanderDGreat said:**
> Hi, I don't have editing experience, but Cinelerra worked for me!

If you want a stable and crash-free (in my case) Ubuntu 9.04, Asus C2D 1g RAM, Desktop try Cinelerra,

I've tried kdenlive (crashes), OpenShot (crashes) and Kino (crashes), but Cinelerra is the one that FINISHED the project for me.

The catch, watch these tutorial videos: 

Basic Editing in Cinelerra Pt. 1 - [http://www.youtube.com/watch?v=-Q-NTYLiyKc](http://www.youtube.com/watch?v=-Q-NTYLiyKc)
Basic Editing in Cinelerra Pt. 2 - [http://www.youtube.com/watch?v=r4ollw6Cqjc&](http://www.youtube.com/watch?v=r4ollw6Cqjc&)
Basic Editing in Cinelerra Pt. 3 - [http://www.youtube.com/watch?v=cIjSBiWc9Qs&](http://www.youtube.com/watch?v=cIjSBiWc9Qs&)
Basic Editing in Cinelerra Pt. 4 - [http://www.youtube.com/watch?v=gxWbfhD6Tnw&](http://www.youtube.com/watch?v=gxWbfhD6Tnw&)
Basic Editing in Cinelerra Pt. 5 - [http://www.youtube.com/watch?v=PyxCf5qwYlE&](http://www.youtube.com/watch?v=PyxCf5qwYlE&)

They're 6-8 minutes long. If a newbie like me can do it, I'm sure you can do it too with patience, just like we have patience for Linux. =)

I hope it'll give you the confidence and take away your frustration to finally video-edit in Linux. Best of luck making it work for you. =)

You finished the project already? Hmmm, time to look at the documents and give Cinelerra another run.  At any rate though OpenShot DID work for me, but the program is still not finished yet.

At any rate, if you find more documents, just keep posting them here.  I always wanted to fully learn Cinelerra, but much of the documentation that I did come across was lacking.  Hopefully those videos are the 'holy grail' to Cinelerra.

Edit:

I looked at the first video just now and I wanted to double check my preference settings according to the video and sure enough, a couple of them were off.  So I made the changes, but it wouldn't change.  Looking closely at the video, my preferences box doesn't have the OK, APPLY, & CANCEL buttons on the bottom.  They are not there at all!  Naturally if I exit out of the Preferences screen and go back in, the changes I made are not saved.

That is weird.

Thanx for sharing
Geo

---

### Post by AlexanderDGreat on 2009-09-16
Hi, thankfully, I did finish my work in 1 day, but I'm not an advanced user so I just abided by the basics.

That OK, Apply, cancel also happened to me.

I had NVIDIA Xserver Settings, from what I know it controls the display and resolution of Ubuntu Gnome, if this works for you, System > Administration > Nvidia Xserver Settings > X server display configuration, then set your resolution to 1152x864 or higher than 1024x768. The thing will show up.

You can do something I like this. =)

PS Oh yeah, don't forget to save your settings so you can reboot with your new settings. Also, backup /etc/X11/xorg.conf.

---

### Post by cbstryker on 2009-09-16
No one has addressed my question about Cinelerra and AVCHD, does anyone know?

---

### Post by cotcot on 2009-09-16
> **cbstryker said:**
> No one has addressed my question about Cinelerra and AVCHD, does anyone know?

It is too early to have editor for direct editing AVCHD. It is not possible with cinelerra. Have a look at kdenlive. This editor can import AVCHD. The editing afterwards was not a success when I tried it. 

I convert my .MTS files to mpg and do the editing with .mpg.

I put the .MTS files in a folder, open terminal in this folder and convert with ```
find ~/ -name '*.MTS' -type f -exec mencoder '{}' -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o '{}'.mpg \;
```

Or a single file with  
```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 00126.MTS -vf lavcdeint -ofps 25 -fps 50 -o 00126.mpg
```

---

### Post by cotcot on 2009-09-16
> **jukingeo said:**
>  I have had a few problems with the program, but it is still a night and day difference compared to other editors out there that simply do not work at all or just often crash.


This is weird. I have at least 5 editors installed working fine. Amongst them Kino: well known to be easy, simple and rock stable. Maybe it is something with your installation rather than the editors themselves ?

---

### Post by cbstryker on 2009-09-16
> **cotcot said:**
> It is too early to have editor for direct editing AVCHD. It is not possible with cinelerra. Have a look at kdenlive. This editor can import AVCHD. The editing afterwards was not a success when I tried it. 

I convert my .MTS files to mpg and do the editing with .mpg.

I put the .MTS files in a folder, open terminal in this folder and convert with ```
find ~/ -name '*.MTS' -type f -exec mencoder '{}' -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o '{}'.mpg \;
```

Or a single file with  
```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 00126.MTS -vf lavcdeint -ofps 25 -fps 50 -o 00126.mpg
```

Look at my post on page 4, I have too many files to do that with, too much time plus it would be a waste of space for me. Even though I thoroughly don't like AVCHD, Windows 7 handles it quite nicely on it's own and Sharky's codec pack rounds out the mkv and other codecs support. So I'm not going to convert my entire 50 gb library of videos from the past year just for cinelerra. I need a solution that will handle AVCHD natively, it WILL come, we just have to wait I guess.

---

### Post by cooper77z on 2009-09-16
Openshot is great! It's the first nonlinear editor for hardy that I have tried that actually works. I am going to donate to the project as soon as can. I like the  program a lot. Don't know what the individual meant about open shot using dangerous libraries. My computer still works fine.:) Openshot is able to read the mp4 videos directly from my sdhc card, unlike Cinelerra. I can edit a program in Openshot and then use Devede to burn a DVD. I am so happy. I was about to abandon Ubuntu until I discovered Openshot.

---

### Post by jukingeo on 2009-09-16
> **AlexanderDGreat said:**
> Hi, thankfully, I did finish my work in 1 day, but I'm not an advanced user so I just abided by the basics.

That OK, Apply, cancel also happened to me.

I had NVIDIA Xserver Settings, from what I know it controls the display and resolution of Ubuntu Gnome, if this works for you, System > Administration > Nvidia Xserver Settings > X server display configuration, then set your resolution to 1152x864 or higher than 1024x768. The thing will show up.

You can do something I like this. =)

PS Oh yeah, don't forget to save your settings so you can reboot with your new settings. Also, backup /etc/X11/xorg.conf.

Hmmmm, I don't have an Nvidia card, my card is an ATI card.  If I set the resolution higher than 1024 x 768, it looks awful.   However, I DID find a work around.  If I click on the top left icon of the preferences window and select  "move", I can nudge the window high enough to show the missing OK, Apply & Cancel buttons.  I was like, "Oh THERE they are!"

I just now rechecked my settings after yesterday's "save" and everything is as I set it.  GOOD!

Now, next problem...I don't have an X11-OpenGL setting.  I know my card IS OpenGL.

Oh! I wanted to ask you, do you have a codec for .flv files?  I come across those often and Cinelerra doesn't recognize them.

Thanx,

Geo


> **cotcot said:**
> This is weird. I have at least 5 editors installed working fine. Amongst them Kino: well known to be easy, simple and rock stable. Maybe it is something with your installation rather than the editors themselves ?

Are you using KDE?  If so then that explains quite a bit.  Kdenlive doesn't like Gnome.  Could be my video card doesn't like Kino.  Open Movie Editor was the worst on my system...crashed with in 5 second on file load up and the community couldn't help me.  So I dropped that one like a hot potato.   Cinelerra was the first one that actually 'worked'.  I do have some issues with it, but I have been correcting them as I go along.   OpenShot seemed to offer the least headache of all, but it isn't finished yet and there are a couple bugs, but I do have high hopes for that program.  BUT I do still want to learn Cinelerra.  

> **cooper77z said:**
> Openshot is great! It's the first nonlinear editor for hardy that I have tried that actually works. I am going to donate to the project as soon as can. I like the  program a lot. Don't know what the individual meant about open shot using dangerous libraries. My computer still works fine.:) Openshot is able to read the mp4 videos directly from my sdhc card, unlike Cinelerra. I can edit a program in Openshot and then use Devede to burn a DVD. I am so happy. I was about to abandon Ubuntu until I discovered Openshot.

I like the program as well, but I don't know if you noticed, there are sync problems with the audio/video when editing.  They are working on it though.  I can put together a video much faster in OpenShot than Cinelerra, BUT Cinelerra is without a doubt much more powerful.  I like the idea of having the two editors though.  OpenShot will handle the 'quickie' projects and Cinelerra will handle the heavy duty stuff.

The Tutorials that Alex found seem to be pretty good.   I found out some new areas and new settings in Cinelerra that I could take advantage of.  I figured I will learn more about Cinelerra now until all the bugs are ironed out of OpenShot.

Anyway, this is a good discussion, so I will be sticking around.  I am off for now though. G'nite!

Geo

---

### Post by cooper77z on 2009-09-16
To solve the audio sync problem in Openshot one must simply add soundtracks and mute the video soundtrack. It's a simple fix and it works perfect. Just duplicate the video on another soundtrack and mute the video track, then align the two video segments visually. Next, make sure you didn't accidentally mute the wrong track. The whole process only takes 20 seconds. But yea, if you don't put the audio on its' own trak then you will have sync issues. Peace out.

---

### Post by Chronon on 2009-09-16
> **jukingeo said:**
> If I click on the top left icon of the preferences window and select  "move", I can nudge the window high enough to show the missing OK, Apply & Cancel buttons.  I was like, "Oh THERE they are!"


You can alt-click to grab a window anywhere and move it around.

---

### Post by jukingeo on 2009-09-17
> **Chronon said:**
> You can alt-click to grab a window anywhere and move it around.

Yup, I figured that one out last night too.  What I don't get is for some reason I can't just simply resize that window. It is a bit of a pain to remember to "manually" move the window.  I am wondering if other Cinelerra pop-up screens will be like that.  Thus far they are usually small enough to move around...but I haven't tried to resize them.  I know the resize works on the on screen displays as I have resized the video screens before. Oh, well, at least there is a solution and I don't have to get in that screen often.

Thanx,

gEo

---

### Post by jukingeo on 2009-09-17
> **cooper77z said:**
> To solve the audio sync problem in Openshot one must simply add soundtracks and mute the video soundtrack. It's a simple fix and it works perfect. Just duplicate the video on another soundtrack and mute the video track, then align the two video segments visually. Next, make sure you didn't accidentally mute the wrong track. The whole process only takes 20 seconds. But yea, if you don't put the audio on its' own trak then you will have sync issues. Peace out.

Nope!  I did that and the video still goes out of sync.

---

### Post by cooper77z on 2009-09-17
hmmm, jukingeo

Try this, enable both audio tracks and offset the second audio track to make an echo effect then see which track is actually synced up. That should show you how much you need to offset the second track to get a perfect sync.:guitar:

How long is the segement you are editing anyway? My segment is only 90 seconds long. And it stays in sync. If I make the above mentioned mod, but if I don't put the audio on another track then it goes out of sync within about 20 seconds.

---

### Post by AlexanderDGreat on 2009-09-17
@jukingeo, sorry, I don't know anything about codecs, hey, I've an idea, why don't  ask that guy who made those Cinelerra videos? He responses pretty quickly in the comments area. I think he's good, I saw in his profile that he's a programming engineer.

---

### Post by kiddo on 2009-09-17
> **cbstryker said:**
> No one has addressed my question about Cinelerra and AVCHD, does anyone know?

I have a camcorder that records AVCHD (H.264 in a mov container), PiTiVi 0.13.3 (currently in the [GStreamer PPA]("https://launchpad.net/~gstreamer-developers/+archive/ppa") for Jaunty) works 100% fine with it. Don't know about the .m2ts container, but I think it should be the same.

With its current feature set though (as of today), you are limited to basic editing. But it works fine with HD files from modern camcorders, as long as you have a powerful-enough machine to play them and the proper gstreamer plugins (namely, gstreamer0.10-ffmpeg).

---

### Post by jukingeo on 2009-09-17
> **cooper77z said:**
> hmmm, jukingeo

Try this, enable both audio tracks and offset the second audio track to make an echo effect then see which track is actually synced up. That should show you how much you need to offset the second track to get a perfect sync.:guitar:

No it isn't like that.  The video "shifts" when you play it.  So it will not go out of sync in the same place.  Sometimes it lags sometimes it shifts forward and sometimes it plays right on the money.  How I know this is because I have a transition in one spot and the fade point on the .flv video changes.

> How long is the segement you are editing anyway? My segment is only 90 seconds long. And it stays in sync. If I make the above mentioned mod, but if I don't put the audio on another track then it goes out of sync within about 20 seconds.

Mine is about 90 seconds long too.  Here is my scenario.  I have a clip from a movie intro that I am going to use however I am going to replace the movie intro with my own, BUT the original music will still play on.  What I initially did was make a cut in the point in the video where I would transition to my custom intro and I blacked out the video.  This is when I noticed that on playback the audio makes a 'pop' or 'crackle' at the edit point.  I didn't want this so then I decided to make a copy of the movie intro and one I would black the video on and use it as an audio track only.  The other I would mute the audio and cut off the end.  Then I would transition from the point I selected into my custom intro with the original music playing in the background.  Are you still following?  If so, Good!

Ok, the above scenario works with no popping in the audio...however when I exported the file I noticed it was out of sync.  It was then I played around with the program and discovered it is not necessarily the export that is causing the shift in sync.  I had a shift in sync just using the .osp file (saved OpenShot file setup).  The audio is unaffected. So the problem definitely is running deeper. 

My guess is that the video and audio are using separate buffers...video, being more intensive, can cause the buffer to fill up and overload first and thus cause the hiccups in the output.  Thus I would seem that the video should have way more buffer space than the audio AND the audio and video buffers should be synced, which they probably aren't. That is an educated guess of course, as I am NO computer programmer. But I been around computers long enough to know a few things about them :).

> **AlexanderDGreat said:**
> @jukingeo, sorry, I don't know anything about codecs, hey, I've an idea, why don't  ask that guy who made those Cinelerra videos? He responses pretty quickly in the comments area. I think he's good, I saw in his profile that he's a programming engineer.

That is probably a good idea. I think it could be possible that many people are converting the files first.  As I recall, Cinelerra is pretty limited on the type of files it handles...however, on the Cinelerra site they DO say it can play .flv files.  They don't seem to play on my machine though.  But a standard Mpeg file plays flawlessly.  I mostly use Mpeg with Cinelerra anyway.  But I figured with the installation of the correct codecs it should be able to accept other files.  OpenShot on the other hand has the ability to play just about all the popular file types, so the codecs are already there.  I have not had to install anything extra for OpenShot.

Geo

---

### Post by cooper77z on 2009-09-17
jukingeo, I don't know but there is definitely an audio sync issue

I learned how to solve audio sync problems in Final Cut Pro by shifting the audio track, and this technique is working so far for me with Openshot. But I haven't tried anything complex yet, I just made a 90 second monologue, duplicted the video track, muted the audio on track one, set the in points for both tracks about 5 seconds into the project, and aligned the 2 tracks visually. It solved the extremely pronounced sync problem without any kind of modification. I think Openshot has a lot of potential and I am looking forward to an official release. :) I didnt even disable the video on track 2 because track one was taking priority,

I suspect that creating keyframes might also solve the sync problems, but I haven't tried it yet.

---

### Post by jukingeo on 2009-09-17
> **cooper77z said:**
> jukingeo, I don't know but there is definitely an audio sync issue

I learned how to solve audio sync problems in Final Cut Pro by shifting the audio track, and this technique is working so far for me with Openshot. But I haven't tried anything complex yet, I just made a 90 second monologue, duplicted the video track, muted the audio on track one, set the in points for both tracks about 5 seconds into the project, and aligned the 2 tracks visually. It solved the extremely pronounced sync problem without any kind of modification. I think Openshot has a lot of potential and I am looking forward to an official release. :) I didnt even disable the video on track 2 because track one was taking priority,

I suspect that creating keyframes might also solve the sync problems, but I haven't tried it yet.

It could depend on what kind of system you have.  My machine is an older Pentium 4 2.8ghz.  If you have a dual core processor (or better) then perhaps your chance of success is greater.  I have found out that OpenShot does use a tremendous amount of CPU resources and sometimes instead of 'chilling out' when the CPU is full, it causes problems.  This sync problem could be one of the issues.  I think OpenShot needs to make use of system resources better.  Monitoring system usage, OpenShot really doesn't even budge the system memory (or swap file) resources, but it drives the CPU resources through the roof.  I think the developers of OpenShot are relying on the CPU to do too much.  Today's video cards have OpenGL and other features that remove much of the processing burden off of the CPU.  I don't think OpenShot is using the video card resources to it's fullest advantage.

It could be that the developers are relying more on the CPU because video card support in Linux really isn't that stellar.  You have so many different makes.  Even if they stuck with the two big ones (Nvidia and ATI), there are so many models and sub models to worry about, it would take quite a bit of computer code and trouble shooting going that route.

Naturally for those that have a multi-core processor the load is shared and probably the results are better.

In terms of overall video editing I wanted to pick out a semi complex situation that would rely on good syncing ability to test OpenShot's abilities...apparently it failed on my system. If it would have passed, then everything else I do would require less of my system.

Certain forms of editing such as playing family home video clips and just putting them to music in the background and using the transition tools that comes with OpenShot would yield very good results because in a situation like that, you are really not relying on perfect sync.  If the video 'slides' in relation to the audio track it isn't critical.

But if you come along and want to make a music video and you want certain visual cues to line up with the music...then you would be out of luck.  So unless OpenShot has a fairly quick solution to this problem, I am probably going to go back to figuring out Cinelerra.

Thanx,
Geo

---

### Post by cooper77z on 2009-09-17
I am using an old laptop with one 2.2 ghz processor and 256meg of ram. I am editing 640x480 NTSC MP4 Digital Video, and Openshot is fine. I did have an issue trying to convert to FLV, but Avidmux could probably convert the video just fine. But I can upload to vimeo just fine with an Mp4. I think your sync problems are more related to your editing technique than a flaw in Openshot. I put together another segment with a b roll and transitions using my technique and the audio sync was flawless. The export was back to DVD quality MP4. I am so happy to have an editor for Ubuntu that I can actually use to produce with :popcorn:

---

### Post by cbstryker on 2009-09-17
> **kiddo said:**
> I have a camcorder that records AVCHD (H.264 in a mov container), PiTiVi 0.13.3 (currently in the [GStreamer PPA]("https://launchpad.net/~gstreamer-developers/+archive/ppa") for Jaunty) works 100% fine with it. Don't know about the .m2ts container, but I think it should be the same.

With its current feature set though (as of today), you are limited to basic editing. But it works fine with HD files from modern camcorders, as long as you have a powerful-enough machine to play them and the proper gstreamer plugins (namely, gstreamer0.10-ffmpeg).

From what I understand .mts and .m2ts are pretty much the same. I think there are some additional playlist info files that go along with .mts for the camcorder, but they are the same when I comes to holding the video and audio. The Sony HD Motion Browser software that came with mine automatically converts the extension from .mts on the camcorder to .m2ts when I puts it on your hard drive. I don't use that program I simply manually copy the files and use Lupas Rename to mass convert the extensions to .m2ts.

---

### Post by cooper77z on 2009-09-17
Hi jukingeo and community! I published my openshot sync test of vimeo to show you that Open Shot doesn't have audio sync problems if the correct technique is followed. [http://www.vimeo.com/6634413](http://www.vimeo.com/6634413)

---

### Post by cooper77z on 2009-09-17
How do I download? "Lumiera is still in an early stage of development. It is not usable yet." [http://lumiera.org/](http://lumiera.org/)

---

### Post by cooper77z on 2009-09-17
P.s. The slight echo you will hear on the video is becuase I didn't get the two audio tracks close enough. I could have synced the tracks better if I wasn't in such a hurry. :guitar:

---

### Post by cooper77z on 2009-09-17
I hate to reply to myself, but somebody deleted their post. My test on vimeo with openshot worked perfectly. I'll post up a more complex vid soon :popcorn:

---

### Post by theZoid on 2009-09-17
> **cooper77z said:**
> I hate to reply to myself, but somebody deleted their post. My test on vimeo with openshot worked perfectly. I'll post up a more complex vid soon :popcorn:

Great....thanks for the demo's....

---

### Post by cooper77z on 2009-09-18
Here's my latest Openshot video, the software works great, but you can blame me for problems when you find them. [http://www.vimeo.com/6636800](http://www.vimeo.com/6636800)

---

### Post by Ubuntiac on 2009-09-18
Hmmm... seems to be a "Private Video" according to Vimeo. Any chance of making it public so we can see it?

---

### Post by cooper77z on 2009-09-18
It takes vimeo some time to transcode the video and approve the content. You should be able to access the content that I created with openshot under hardy now. the videos have been uploaded and transcoded. b :popcorn::popcorn:

---

### Post by jukingeo on 2009-09-19
> **cooper77z said:**
> Hi jukingeo and community! I published my openshot sync test of vimeo to show you that Open Shot doesn't have audio sync problems if the correct technique is followed. [http://www.vimeo.com/6634413](http://www.vimeo.com/6634413)

What would you call the "correct technique" ?

In my case I don't have an audio problem...it is the VIDEO that goes out of sync with the audio.  The audio stays put.  The video is what is jumping around and going out of sync.

I have NOT converted my .flv files and I am using them straight, so I am not sure if that could be an issue.

I know that Cinelerra doesn't like .flv files  either (even though they say it can handle them).  Trouble is that most of the files I grab off the web are .flv files.  It would take a few evenings to convert them all.  ....a job I REALLY don't want to do.

Thanx,

Geo

---

### Post by cooper77z on 2009-09-19
What version of Openshot are you using? Maybe there is a quasi patch for my version that works when I duplicate the audio/video track and then use the audio and the video visually on two seperate tracks. Personally I am really pleased with Openshot. It's great for low budget productions. It's extremely intuitive and powerful. I could do pretty much anything I put my mind to with it. I am using version, 0.9.22, what version are you using jukingeo? Does anyone know an easy way to upgrade to a higher version of Openshot because installation was kind of a pain in the ****.

---

### Post by cooper77z on 2009-09-20
Hey, you know that flash video can even tell where my zits/pimples are? Cause the flash program always spots/makes a " on my pimples. That is just wrong.:lolflag:

---

### Post by jukingeo on 2009-09-29
> **cooper77z said:**
> What version of Openshot are you using? Maybe there is a quasi patch for my version that works when I duplicate the audio/video track and then use the audio and the video visually on two seperate tracks. Personally I am really pleased with Openshot. It's great for low budget productions. It's extremely intuitive and powerful. I could do pretty much anything I put my mind to with it. I am using version, 0.9.22, what version are you using jukingeo? Does anyone know an easy way to upgrade to a higher version of Openshot because installation was kind of a pain in the ****.


I believe I have that version as well.  I have to double check as I am at work right now so I can't tell you for sure.

I think for the most part just making a nice home video with about 2 years of footage from my sons since they when they were born would be good enough to do in OpenShot.  I also would like to dabble with some music video editing as well.  But I do know if I am going to do some more precise work that is very sync dependent...I probably will need to use Cinelerra.

> **cooper77z said:**
> Hey, you know that flash video can even tell where my zits/pimples are? Cause the flash program always spots/makes a " on my pimples. That is just wrong.:lolflag:

I have noticed that too with You Tube lately.  Some videos just get that red " mark that comes up for a split second.  When I first saw it, I thought it was the 'pause' indication on someone's video camera going haywire...but then the " jumped around.  About a year ago I NEVER seen that happen.  And yeah it IS wrong that they would release a program with a 'blemish' (pun intended) like that.

Geo

---

