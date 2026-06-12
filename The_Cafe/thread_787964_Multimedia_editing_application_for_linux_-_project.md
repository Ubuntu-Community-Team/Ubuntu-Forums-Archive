---
title: "Multimedia editing application for linux - project possibility"
date: 2008-05-09
forum: The Cafe
---

### Post by Delever on 2008-05-09
Forgive me if this post is going to be a little bit tecnical.

The reality is, linux world does not have really good multimedia editing applications. There are tools, and there are ways, and there is code somewhere, but not really much under professional, stable, easy-to-use interface.

I am going to post my agenda, and feel free to discourage/encourage, give advices, point to different direction, etc.

The project goal is to make framework, or library, for editing multimedia content. That does not sound hard, but actually it IS very hard. I am going to break down this project to piecies so you can count them for yourself.

**Realtime playback of modified content:**
The timeline obejct will be needed, with multiple tracks, and multiple media events attached. It should:
- not depend heavily on amount of media content added to it; that is, it should work fast with any amount of multimedia added
- handle preloading of content to give as smooth playback as possible
- define generic framework to handle different media sources and reuse existing libraries, using Events as abstraction
- multithreaded where necessary to use all CPU resources when necessary
- editing during playback
- support for multiple clients editing the same timeline
- nested timelines

**Audio/video event**
Audio/video event, or just Event, which define resource (file) handling rules, what is possible to do with resource, and how this resource can be modified. This Event lives in timeline and can be played or rendered.
Then, of course, what anyone using it would expect from such event:
- Copy/paste
- Transitions if they overlap (and their types matches), using Transition object as abstraction

**Transitions**
Automatically generated objects when events overlap. We need to define them when events are moved, because caltulating them during playback or rendering would not be fastest way; also, they have to be represented graphically, and that would help alot.
- Goes without saying, proper creation/cleanup of them

These are very basic and obvious objects of course, and this list written quickly. What is also needed:

**For audio and video**
Define quality levels for all processing tasks (audio/video):
- Draft - fastest possible way, but still close enough to final result
- Close to original - what it says
- Good - on the edge where it is hard to distinguish from Best
- Best

**Audio**
- Realtime resampling and efects (or at least possibility for them)
- Do not limit it to stereo

**Video**
- Automated deinterlacing, aspect ratio handling, resizing

**Rendering**
- Open source file formats should be promoted
- Handling of multi-pass rendering with different file formats

This library should be without any non-free content, but with possibility to use non-free plugins if they are installed.

Ok, writing this, I skipped many things, just to get it finished for now :).

Final goal would be full featured Video editor, but it is just too far away (i have not mentioned any interface related requirements too). So I decided first milestone to support simple audio editing application, which would be good for some audio or music mixing (no video).

Any comments are welcome. I have not started on it yet; I have time now, but I just need to investigate what is worth to do and what is already done.

:KS

---

### Post by hessiess on 2008-05-09
sounds interesting.

Blender can handel video editiong quite well. but there is a lack of audio editing tools on linux.

---

### Post by renzokuken on 2008-05-09
have you looked at cinelerra at all?

---

### Post by FuturePilot on 2008-05-09
> **renzokuken said:**
> have you looked at cinelerra at all?

I think the point here is *simple*. Cinelerra is *far* from simple.

Cinelerra is good, but it is confusing and overkill for most people's needs.

---

### Post by barbedsaber on 2008-05-09
there are lots of video editing apps for linux, there just not very good (yet) why don't we all work on of them, rather than start agian.

then again, they may have been borked from the start, maybe they are too broke to fix, still seems like somthing to think about.

---

### Post by Delever on 2008-05-09
> **renzokuken said:**
> have you looked at cinelerra at all?

Cinelerra seems to be ok: however, it seems very tied to it's interface. Thanks for pointing me to it.

---

### Post by mridkash on 2008-05-09
Hi, I also support this idea. Now even Kdenlive doesn't work on my pc, it crashes as soon as it starts.

Anyway, as you say,
> The project goal is to make framework, or library, for editing multimedia content. That does not sound hard, but actually it IS very hard. I am going to break down this project to piecies so you can count them for yourself.

Have you looked at MLT Framework?

If Kdenlive can do things (if it starts!) like non-linear editing, rendering, titling, color clips, slideshow clips, transition clips etc. then I think MLT Framework is good for this stuff.

Only thing is to make a good app (in GTK or QT) which takes advantage of that. 
Though, I know it is easy said than done but still it wont be as hard as making a library/framework and then making an app based on that. 
What do you say?

---

### Post by Delever on 2008-05-09
Making library only indeed is not a good idea; I imagine that very simple applications should be made which use this library, to have something working early, have something to test and to generate some interest.

I am going to investigate MLT Framework. Lot's of reading to do.

---

### Post by madjr on 2008-05-09
> **Delever said:**
> Cinelerra seems to be ok: however, it seems very tied to it's interface. Thanks for pointing me to it.

i think you could fork of the bigger applications creating an easy interface and hide or remove the "advanced" tools.

right now Linux needs something really uncomplicated as windows movie maker, nothing too professional for the average Joe.

all those projects focus on features, but none focus on simplicity.

i remember inkscape doing something similar with Inkscape lite (aka inklite)

[IMG]http://bryceharrington.org/files/inkscape-lite-small.png[/IMG]

[http://ubuntuforums.org/showthread.php?t=734222](http://ubuntuforums.org/showthread.php?t=734222)

even thou the normal inkscape interface is not "too hard", they wanted something even simpler that even a 10 year old kid could pick up right away. As i remember i seen 10 year olds using Windows movie maker too.

this one would get really popular. A "**linux movie creator**" or "**simple movie creator**"

[IMG]http://www.portalprogramas.com/sc/520_1_grande.jpg[/IMG]

[IMG]http://media.wiley.com/assets/3/30/fg0-7645-0897-0_0310.jpg[/IMG]


this may not be your final goal, but as a start it would make a great proyect.

and as you said above, linux is lacking something **stable** (less unstable features/code) and "**easy-to-use**" interface

---

### Post by tadcan on 2008-05-09
Can you tell us which Linux video editors you have tried. i.e kino [http://www.kinodv.org/](http://www.kinodv.org/) avidmux [http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/)

What windows/mac applications do imagine it being like.

---

### Post by Delever on 2008-05-09
I am focusing on non-linear multitrack playback. Sony Vegas would be my main inspiration, but no need for clone.

I tried Kino and avidemux (which reminds alot VirtualDub), but found them somewhat lacking.

The first side goal is to make non-linear, multitrack audio mixing application, with realtime playback. However, keeping the main goal - reusable API for multimedia editing, suitable both for simple and advanced applications.

I understand that linear editing may be easier to implement and easier to understand, however, with good planning, multiple tracks should not be confusing and far superior.

This is very new - so far I have not had time to prepare full specifications, but I wanted to share ideas with community right from the start - that's what makes open source great.

Now I am analysing MLT source code - lot's of great stuff there!

---

### Post by fatality_uk on 2008-05-09
Delever, don't forget what we said. The main point is, **simple**.

For the "simple" interface you just need an audio track, video track.
The video track has to be able to just drag a wide range of media into it, photos (jpg, bmp, xcf) & of course video.

And the main piece of the puzzle to make this a "killer Linux" app is a simple Burn to CD/DVD" button. That's it. No need for multitrack audio and video.

A few simple transitions that can be written in XML for instance **so a community can easily build a LOT of added features quickl**y. The ability to add titles and sub-titles and that's about it.

This as a release would be perfect.

I don't know your programming skill level but don't get too carried away. Have a rigid idea of a 0.1 release and stick to it. As it's FOSS, then all can then add to that.

---

### Post by Delever on 2008-05-09
> **fatality_uk said:**
> Delever, don't forget what we said. The main point is, **simple**.

For the "simple" interface you just need an audio track, video track.
The video track has to be able to just drag a wide range of media into it, photos (jpg, bmp, xcf) & of course video.


When you have possibility for multiple tracks, two tracks is piece of cake ;)

I don't know about the "killer", I haven't even started project yet. I need to group and organise stuff so that it would be easy to understand for others.

---

### Post by fatality_uk on 2008-05-09
> **Delever said:**
> When you have possibility for multiple tracks, two tracks is piece of cake ;)

I don't know about the "killer", I haven't even started project yet. I need to group and organise stuff so that it would be easy to understand for others.

As I advised, don't get too bogged down in the detail yet. Get a group together. There's no point thrashing ideas about with yourself for 12 months ;)

I'll offer to project manage it!!! I don't have time to code anymore. There's plenty of folks here and especially on the Fedora forums who I know would be up for being involved!!

---

### Post by magnus0 on 2008-05-09
I think the best program for editing video in windows is Sony Vegas Pro 8. There could be a Linux application similar to that too.

---

### Post by fatality_uk on 2008-05-09
> **magnus0 said:**
> I think the best program for editing video in windows is Sony Vegas Pro 8. There could be a Linux application similar to that too.

It's a great app, but, imho, far too complex!!

---

### Post by Delever on 2008-05-09
> **fatality_uk said:**
> As I advised, don't get too bogged down in the detail yet. Get a group together. There's no point thrashing ideas about with yourself for 12 months ;)

I'll offer to project manage it!!! I don't have time to code anymore. There's plenty of folks here and especially on the Fedora forums who I know would be up for being involved!!

Do you have good knowledge of organising and developing C/C++ code on linux? My experience is somewhat lacking here. BTW we can communicate using PMs or IMs.

---

### Post by madjr on 2008-05-09
> **fatality_uk said:**
> Delever, don't forget what we said. The main point is, **simple**.

For the "simple" interface you just need an audio track, video track.
The video track has to be able to just drag a wide range of media into it, photos (jpg, bmp, xcf) & of course video.

And the main piece of the puzzle to make this a "killer Linux" app is a simple Burn to CD/DVD" button. That's it. No need for multitrack audio and video.

A few simple transitions that can be written in XML for instance **so a community can easily build a LOT of added features quickl**y. The ability to add titles and sub-titles and that's about it.

This as a release would be perfect.

I don't know your programming skill level but don't get too carried away. Have a rigid idea of a 0.1 release and stick to it. As it's FOSS, then all can then add to that.

+1

as long as the interface is as simple as windows movie maker, then get it rolling :D

---

### Post by fatality_uk on 2008-05-09
> **Delever said:**
> Do you have good knowledge of organising and developing C/C++ code on linux? My experience is somewhat lacking here. BTW we can communicate using PMs or IMs.

yeah PM me and we can get something started!

---

### Post by SunnyRabbiera on 2008-05-09
> **madjr said:**
> +1

as long as the interface is as simple as windows movie maker, then get it rolling :D


have you tried kdenlive?
its very close.

---

### Post by zmjjmz on 2008-05-09
> **SunnyRabbiera said:**
> have you tried kdenlive?
its very close.

People.
iMovie (not the new one, the ones from before that) has(d) the _best_ video editing interface known to mankind!
Maybe you could make it switch between WMM like and iMovie like, but that'd seem a bit clonish.
Also, the option to have multiple Audio/Video tracks would be a good idea, start out with say one video track and two audio tracks.

---

### Post by Delever on 2008-05-09
> **zmjjmz said:**
> People.
iMovie (not the new one, the ones from before that) has(d) the _best_ video editing interface known to mankind!
Maybe you could make it switch between WMM like and iMovie like, but that'd seem a bit clonish.


I like idea of selecting part of clip and dragging it to the timeline.

---

### Post by fatality_uk on 2008-05-09
> **SunnyRabbiera said:**
> have you tried kdenlive?
its very close.

I have. It's good, but way too buggy. I have managed all of about 7 minutes in it with about 3 crashes

---

### Post by keykero on 2008-05-09
Have you guys heard of the Lumiera project? It's being done by the developers who maintain the CV of Cinelerra and will be needing coders/designers/documentators to get it off the ground.  It would be so nice if everyone could pull together to focus on one project such as this.  I believe that is why we have so many half-complete 0.6 apps in this area; people get fired up and start a new project only to realise how difficult this is to do without significant collaboration.

---

### Post by bobbybobington on 2008-05-09
Preventing "feature creep" should be an important goal. Using popular video codecs seamlessly should be a big focus. If the user can't simply drag any video clip and have it "just work" or has to convert the video first, then the program will be useless to them.

---

### Post by fatality_uk on 2008-05-09
> **keykero said:**
> Have you guys heard of the Lumiera project? It's being done by the developers who maintain the CV of Cinelerra and will be needing coders/designers/documentators to get it off the ground.  It would be so nice if everyone could pull together to focus on one project such as this.  I believe that is why we have so many half-complete 0.6 apps in this area; people get fired up and start a new project only to realise how difficult this is to do without significant collaboration.

Yeah I have heard of it, but the problem with it is this. It's aim is to be a fully fledged video NLE. It will have bells, whistles and lots buttons, I think.

What id like to see is what I referred to in my other thread. A simple video editor that can take on the role of Windows Movie maker.

There's quite a few editors out there, and in one way or another, the feature list current and future seems to be heading for adobe premier ground. What Linux needs, imho, is a what I said above. A good alternative to Windows Movie maker. I think so many people will be happy to try Linux if they can "easily" edit home movies onto DVD in a few clicks.

---

### Post by FuturePilot on 2008-05-09
Yes, the focus needs to be on simplicity ala Windows Movie Maker. All of the Linux video editors are slightly more complicated. I remember the first time I used WMM. It barely took any time to figure it out. The first time I used Cinelerra, I was totally lost. Took me about an hour to figure out how to add a title. :(

What most people want to do is put some video clips together, add some effects and transitions, add some music overlay, and possibly add some images. Then export it to some format like .avi or some other of the various formats. Possibly burn it to a DVD as well. Cinelerra or even some of the others are obvious overkill for this.

---

### Post by madjr on 2008-05-09
> **SunnyRabbiera said:**
> have you tried kdenlive?
its very close.

**jahshaka** looks good too:

[IMG]http://www.estrellateyarde.es/photos/jahshaka.jpg[/IMG]

[http://jahshaka.org/](http://jahshaka.org/)

---

### Post by fatality_uk on 2008-05-09
> **madjr said:**
> **jahshaka** looks good too:

[IMG]http://www.estrellateyarde.es/photos/jahshaka.jpg[/IMG]

[http://jahshaka.org/](http://jahshaka.org/)

It's great, but I am guessing you have never used it ;)
After you have spent about 4 weeks getting into the mind boggling interface in some sections, you are then left with a headache.

I have tried to use it for day to day editing and quite frankly it's impossible. It can create some amazing effects, especially the rotating cube with multiface video, but I dont need that right now. I don't work in the "New Hollywood" and would like something easier on the brain :D

---

### Post by madjr on 2008-05-09
> **fatality_uk said:**
> It's great, but I am guessing you have never used it ;)
After you have spent about 4 weeks getting into the mind boggling interface in some sections, you are then left with a headache.

I have tried to use it for day to day editing and quite frankly it's impossible. It can create some amazing effects, especially the rotating cube with multiface video, but I dont need that right now. I don't work in the "New Hollywood" and would like something easier on the brain :D

yea i haven't tried it.

but the interface does look "inviting" and not too cluttered making me wanting to try it :)

thats something imovie and wmm have :)

but like u said, it's still kinda lacking and difficult to use on a daily basis.

also they just started work on new version

[IMG]http://jahshaka.org/images/news/jahshaka_v3_large.jpg[/IMG]

[http://jahshaka.org/News/p2_articleid/76](http://jahshaka.org/News/p2_articleid/76)

and r using 

[IMG]http://jahshaka.org/images/logos/Powered_By_OpenLibraries.jpg[/IMG]

---

### Post by zmjjmz on 2008-05-09
I can't seem to find a Jahshaka package for Linux >.>

---

### Post by madjr on 2008-05-09
anyone tried "Lives"?

there seems to be a new version

[IMG]http://lives.rm.org/lives091.jpg[/IMG]

[http://lives.sourceforge.net/index.php?do=screenshots](http://lives.sourceforge.net/index.php?do=screenshots)

---

### Post by fatality_uk on 2008-05-09
Can you load stills into it?

---

### Post by FuturePilot on 2008-05-09
Yes, I've tried Lives. Again, overkill and confusion. Where's the time line? Also Jackd doesn't play nice with PulseAudio.

---

### Post by Delever on 2008-05-09
> **fatality_uk said:**
> Can you load stills into it?

Have you got my PM?

BTW, for anyone interested, you can PM me, but bear in mind that right now it is research phase, like, what is already done by others. I need to investigate different areas (interface, decoding/encoding, sound playback, gstreamer, etc). Just got out of GTK+ jungle, I hope I won't dream about it.

---

### Post by zmjjmz on 2008-05-09
Just a thought, but is it feasible to make it GTK+/Qt independent?
EDIT: I tried LiVES, I couldn't figure it out though.
It's really a professional system.

---

### Post by barbedsaber on 2008-05-10
do you think we could convince whoever we need to convince, to get jahshaka into the repos, it looks awesome, and i'm sure more people would use it if it was there.

---

### Post by magnus0 on 2008-05-10
> **fatality_uk said:**
> It's a great app, but, imho, far too complex!!

Everything is complex if you're not used to it. I just sat down and started learning Vegas and no I know everything about it.

---

### Post by mridkash on 2008-05-10
I want something which my mom can use easily for video editing. 
It should have simple interface like WMM. Even, Kdenlive's interface is good.
Cinerella, lives, pitvi, jahshaka, sony vegas all look professional and not simple like WMM, iMovie or Kdenlive.

---

### Post by MONODA on 2008-05-10
have you seen: jokosher, kdenlive audacity lmms?

---

### Post by dnbozss on 2008-10-14
I know this is a tad late (4 months....) But I'd like to ask if there's been any progress. I LOATHE WMM, and I've been searching for a replacement for quite some time. Don't get me wrong, I love the interface, some of the features and such, but it's just so buggy! For example, I tried making a video for youtube for mobilephone2003 (maybe you've heard of him). I spent hours collecting pieces, adding effects, syncing video to audio, and then, WMM froze up. I had it saved, so I wasn't worried. But I tried opening the file, and WMM crashed. Again and again. So I had to scrap the whole thing.

Then yesterday, for example, I tried making a simple video with scenery. I spent a few hours collecting pictures and syncing them to a song, and then I save the movie file, and the pictures are completely unsynced,

I'm just trying to make a point, something has got to be done. I say, if Microsoft releases a program for FREE, the open source community can make it better. The thing is that there's software out there that has the opportunity to be better than WMM (Jahshaka, for instance) but it seems like their aim is off.


I have a very basic understanding of programming, but nothing worth helping a cause. But I'd be willing to help in any other way possible, whether it be testing, or spreading the word, or whatever it may be.

---

### Post by remeeraz on 2008-10-14
> **he who eats pie said:**
> I know this is a tad late (4 months....) But I'd like to ask if there's been any progress. I LOATHE WMM, and I've been searching for a replacement for quite some time. Don't get me wrong, I love the interface, some of the features and such, but it's just so buggy! For example, I tried making a video for youtube for mobilephone2003 (maybe you've heard of him). I spent hours collecting pieces, adding effects, syncing video to audio, and then, WMM froze up. I had it saved, so I wasn't worried. But I tried opening the file, and WMM crashed. Again and again. So I had to scrap the whole thing.

Then yesterday, for example, I tried making a simple video with scenery. I spent a few hours collecting pictures and syncing them to a song, and then I save the movie file, and the pictures are completely unsynced,

I'm just trying to make a point, something has got to be done. I say, if Microsoft releases a program for FREE, the open source community can make it better. The thing is that there's software out there that has the opportunity to be better than WMM (Jahshaka, for instance) but it seems like their aim is off.


I have a very basic understanding of programming, but nothing worth helping a cause. But I'd be willing to help in any other way possible, whether it be testing, or spreading the word, or whatever it may be.

Progress? Yup, I've posted a thread on how to install Kino from Source and how to get your Firewire to work if it isn't already.

[http://ubuntuforums.org/showthread.php?t=946708](http://ubuntuforums.org/showthread.php?t=946708)

---

### Post by BlackS3th on 2008-11-03
Ok ... Noob here. Is there really something that i can use? Im Reading from the begining and i havent still realized what the heck i should do ... Can you send me a direct link so i can Download a "movie maker" style? I dont care if its complicated i just want to make movies and edit some of my music ... PlzzZzz i cant find a single little thing ...{ive tryied to download kino but its only downloaded in a file} cant be downloaded from update manager? ... I just want a direct link plz

---

### Post by renzokuken on 2008-11-04
open a terminal and run

```
sudo apt-get install kino
```

it will then be installed from the repos and available in your menu

---

### Post by CinemaScope on 2008-11-21
Anything new on the proposed project? Might be a good idea to find a name so everyone knows what they are referring to (and it tends to create a rallying point for interest).

I happen to come across a NLE project called **saya-VE** ([www.saya-videoeditor.blogspot.com](www.saya-videoeditor.blogspot.com)) which seems to have a sensible list of goals and progress charts.

I don't know if the **gneve** project has been mentioned before ([http://1010.co.uk/gneve.html](http://1010.co.uk/gneve.html)) which is an EDL-type editor using **MPlayer**, though latest news seems to be from last year. Wonder if that's still active?

---

### Post by Ubuntiac on 2008-11-22
Seriously, check out the new version of Kdenlive which has largely been rewritten for KDE4. Seems much better and developing rapidly. It even does HDV and video screen captures.

Unfortunately because it hasn't been packaged for Ubuntu yet, the only way at the moment is to use the repo's at Debian-Multimedia.org (with backports enabled if you're on Ubuntu 8.10 only. Kubuntu's fine).

We seriously need this natively packaged though so we can get rid of all this backport nonsense. If you agree, I'd also add your voice to the packaging request at:
[https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/269191](https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/269191)

---

### Post by Swagman on 2008-11-22
One click Print HDV to Blu-Ray would win you thousands of converts !

---

### Post by Ubuntiac on 2008-11-22
Feel free to wishlist it, right ->[here]("http://kdenlive.org/mantis")<-. :)

---

