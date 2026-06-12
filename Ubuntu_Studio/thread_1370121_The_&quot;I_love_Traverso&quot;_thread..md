---
title: "The &quot;I love Traverso&quot; thread."
date: 2010-01-01
forum: Ubuntu Studio
---

### Post by JC Cheloven on 2010-01-01
Hi, I'd like to draw your attention over a program called Traverso (see my signature). It is a multitrack audio recording and editing program. Its more obvious strong point is ergonomics.

Have you ever suffered from elbow or wrist problems? (mouse-related)

Do you find annoying to point and drag a tiny handle to change a volume, pan, etc? (specially with a touchpad!). 

Traverso implements a technique called "soft selection", which solves these ergonomics problems in an awesone way. Also it deals nicely with my audio, and I'm in love with it :-)  It's under active development though, but it is doing very well. As I think it deserves a bit of extra exposure and general awareness, I'd like to hear from other people their experiences/thoughts regarding this program.

Personally, I prefer using it over anything else.

The version in the repos (as for Lucid) is quite outdated. It's worth installing the current version.

EDIT: 
(obsolete-deleted)

EDIT 14jun2010: 
Traverso 0.49.1 stable has some problem in Lucid due to QT versions. The devel team has sent a patch in launchpad, which is applied (as for this writing, and up to my knowledge) in this PPA [https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra) So, It's recommended to use this one for traverso in lucid. Anyway, the next stable version will be available very soon. It has been under very active development and it's much improved.

EDIT 31aug2010:
Version 0.49.2 of traverso is out. It fixes the aforementioned problem with Qt, among others. It's not the 'true' new version of Traverso (which is taking a bit longer than expected), but a transitional release to cover the Qt problem until the new release is ready. You can find[ here]("http://traverso-daw.org/forum/index.php/topic,212.0.html") tips on how to install it from PPAs, or compile the program in your machine. (Note- this is not an endorsement of PPAs; use them at your own responsibility)

---

### Post by bobince on 2010-01-04
Yeah, I've been looking for a decent audio sequencer for Linux. The best I'd found so far was QTractor, but it had a habit of creating unloadable corrupted projects and didn't support envelopes. So I've just given this a try.

I loaded it. It wanted me to create a centralised project storage folder and import audio into it. Seriously, DAWs still do this in 2010? Let me organise my project files how *I* want please. Just save a .project file where I tell you and leave organising the audio to me, cheers.

Dropped a few audio files in. Try to select a time period. No. Playhead is set with the middle mouse button? OK, weird. Try to drag the edges of the audio. No. Try to change the gain, or split? None of these context menu functions work, the keyboard interface is the only one that goes. Zoom in with the mouse wheel? No. (Come ON!) Zoom in at all? Er? What? Hold the Z key and move the mouse in chunks? What insanity is this?

Press play. No sound. Traverso has chosen the Null audio driver. Try to pick ALSA instead. It doesn't list the Pulse output. Try &#8216;default&#8217;. Refuses to connect. Try direct ALSA sound card access with Pulse stopped. Connects, but no audio output. Start JACK, choose JACK output. Traverso crashes. Synaptic. Remove Traverso.

Needs more work. Linux DAW authors: *please* look at REAPER.

---

### Post by thorgal on 2010-01-04
what's wrong with ardour ?? :lol:

---

### Post by JC Cheloven on 2010-01-04
> **bobince said:**
> Yeah, I've been looking for a decent audio sequencer for Linux. The best I'd found so far was QTractor, but it had a habit of creating unloadable corrupted projects and didn't support envelopes. So I've just given this a try.

I loaded it. It wanted me to create a centralised project storage folder and import audio into it. Seriously, DAWs still do this in 2010? Let me organise my project files how *I* want please. Just save a .project file where I tell you and leave organising the audio to me, cheers.

Dropped a few audio files in. Try to select a time period. No. Playhead is set with the middle mouse button? OK, weird. Try to drag the edges of the audio. No. Try to change the gain, or split? None of these context menu functions work, the keyboard interface is the only one that goes. Zoom in with the mouse wheel? No. (Come ON!) Zoom in at all? Er? What? Hold the Z key and move the mouse in chunks? What insanity is this? 
Well, I'd say that for something to be better, it needs to be different. It's normal trying to do things the way one is used to, but Traverso has a radically different approach. You don't need to "select" anything. The middle button "is there" but isn't the prefered way to set things. In fact, the idea is that you don't have to push any mouse buttons at all!
Perhaps the benefits of this approach need a bit more time than "first sight" to be appreciated. PLease tell us if you give it a second try. 
NOTES: 1) You can have each of your traverso projects wherever you like, and access it hitting "select project dir" in the "open project" dialog. 2) Playhead is set to the mouse position hitting shift 3) Drag edges of audio is done pressing "e" and moving the mouse (no button to be pressed) 4) Zoom is awesome... and so on. Just a different way to do things. It's very easy to master, and it's worth imo.

> Press play. No sound. Traverso has chosen the Null audio driver. Try to pick ALSA instead. It doesn't list the Pulse output. Try &#8216;default&#8217;. Refuses to connect. Try direct ALSA sound card access with Pulse stopped. Connects, but no audio output. Start JACK, choose JACK output. Traverso crashes. Synaptic. Remove Traverso.

Needs more work. Linux DAW authors: *please* look at REAPER.

No pulse support by now, but I didn't experience any of your problems. Perhaps I had to choose one of my soundcards (not "default"), and click "restart driver" but that's all. And I like the way I can switch from one soundcard to another from whithin the program...

Wait... I forgot to mention that the repos version is a bit outdated. Current version is 0.49.1. There is an updated ppa [here]("https://launchpad.net/~bojo42/+ppa-packages")
I'll edit the OP for this.

---

### Post by JC Cheloven on 2010-01-05
> **thorgal said:**
> what's wrong with ardour ?? :lol:

Nothing wrong indeed. Ardour is probaby the most mature free audio software out there, and all in all, it's arguably the best one. Furthermore, the guy behind it is a gifted programmer who deserves my deepest respect and thankfullness. I donated myself several times to the Ardour project !

But everybody is aware of that. On the other hand, Traverso has its own strong points, which people seem not to be aware of. 

For example, in traverso you never have to aim with the mouse to a little handle, press left button, and drag. You simply hover the mouse to a big surface (be it a track, an audio clip...), and press a key on the keyboard.

Aim&drag is cumbersome and wrist-stress prone (let alone if you use a laptop's touchpad). The Traverso way is much more comfortable. This is said by someone (myself) who often has to pilgrimate to musician's places to overdub-recording their parts.

BTW: mi portable studio for this task fits in a small hand bag: a Dell Mini9, an usb FastTrack (not pro), and a Behringer b5 condenser mic :guitar:

---

### Post by thorgal on 2010-01-05
sounds good. But ardour has customizable key bindings as well, for most of its operations.

The only cons about ardour is that it depends on jack. No jack -> no ardour. However, if jack is running beautifully on your system, ardour is truly an amazing app ;)

---

### Post by Stochastic on 2010-01-05
It should be noted that these forums are for technical assistance threads.  Subjects like this should be kept to the Community Cafe area.

---

### Post by JC Cheloven on 2010-01-05
> **thorgal said:**
> sounds good. But ardour has customizable key bindings as well, for most of its operations.

The only cons about ardour is that it depends on jack. No jack -> no ardour. However, if jack is running beautifully on your system, ardour is truly an amazing app ;)
+1 , really.

I wouldn't like to head the discussion to a "traverso.vs.ardour" one. A fair comparison would be difficult... or better: they simply don't compare. By purpose, Traverso is lighweight, while Ardour aims to be full-featured. Traverso is at 0.49 while Ardour is at 2.84 (usually version 1.0 indicates the devels feeling of the app being stable and usable for production). 

And I never thought in Ardour's dependency of Jack as a weakness. Pro audio in a studio environment (where Ardour shines) will use jack anyway, so that's fine. But when the full power is not required, as in my on-the-go recordings, a lighter setup may be preferred. That's where I think Traverso fits better. And may also be considered advantageous for the kind of work involved in editing natural recordings, imo.

> **Stochastic said:**
> It should be noted that these forums are for technical assistance threads.  Subjects like this should be kept to the Community Cafe area.
I'm sorry for that. I was about posting it at the Cafe, but finally thought that people potentially interested in this subject would be a small percentage of the community, most likely people visiting this forum.
Of course feel free to move the thread if you find it appropriate. I wouldn't feel too bad about this, specially if you let us know your own opinion on the main subject ;-)

---

### Post by jsilas on 2010-01-08
I began having alot of problems with audacity when I upgraded to jaunty. I saw the suggestion to use traverso and so far I love it. It's alot of trial and error for me currently. I am having issues hearing the tracks in stereo/both speakers. any suggestions?

---

### Post by sgx on 2010-01-09
> **Stochastic said:**
> It should be noted that these forums are for technical assistance threads.  Subjects like this should be kept to the Community Cafe area.
What could be more foundational to technical discussions, than
revelations that xyz fails in this or works in that, needs help in this area?  Discussion of cars and food can be in the cafe, but the audio world deserves to hear the truth about features and failures, or this forum degrades into a few linux fanboys herding a couple sacred cows back and forth.

Reaper is the best linux software if you -->need<--
1.audio
2.midi
3.vsts

Using Hydrogen, and zynaddsubfx and rakarrack at the same time as Reaper, and recording the whole affair in timemachine, is great fun!:D

---

### Post by JC Cheloven on 2010-01-10
> **jsilas said:**
> I began having alot of problems with audacity when I upgraded to jaunty. I saw the suggestion to use traverso and so far I love it. It's alot of trial and error for me currently. I am having issues hearing the tracks in stereo/both speakers. any suggestions?

Yeah, when I landed in linux audio I pre-assumed that I'd be using audacity, but never got it working fine in my machines (irresponsive sliders among other things). In fact I'd probably never look around for something else if audacity had worked. Other people reports absolute success with it, and it seems to be a great program, but for some reason it didn't work for me.

As for your problem, it's strange. I always heared both speakers/stereo with Traverso or any other program for that matter. In fact, one of the great surprises I had with traverso is how easyly it handles soundcards. Do you have something special in your setup that could give us a clue? The driver loads ok when you press "restart driver" in settings-preferences-sound system? You can quickly see the driver status at the left bottom corner. Also try choosing your card from the dropdwun menu, not "default".

BTW, the trial and error approach isn't well suited for traverso (as the interface doesn't follow the typical guidelines). The interface is very easy to master and damn comfortable, but you have to read the manual [http://traverso-daw.org/UserManual](http://traverso-daw.org/UserManual) and the "getting started" section in the help menu.

---

### Post by jsilas on 2010-01-10
I'm using a two channel lexicon omega audio digital interface. The program reads the device, records and plays back without a hitch. the vu meeter also just reads the left channel, only on playback, however. 

I clicked on "restart driver" in the sound system setting and this is the message I was confronted with...

---

### Post by jsilas on 2010-01-10
I'll start on that manual asap.

---

### Post by JC Cheloven on 2010-01-11
> **jsilas said:**
> I'm using a two channel lexicon omega audio digital interface. The program reads the device, records and plays back without a hitch. the vu meeter also just reads the left channel, only on playback, however. 

I clicked on "restart driver" in the sound system setting and this is the message I was confronted with...

The message is not critical. It "only" means that you are not using a real-time linux kernel. The program will probably run ok, except for -perhaps- occasional xruns. You'll be noticed when an xrun occurs in the notification area at the bottom of the screen. In fact I see that you had 100 xruns in your session. If they occur when you start the program/driver, it's not serious, but if they do occur while recording, pay attention to the following.
(note: if not using jack, I didn't experience any xrun in my hardware, never, despite of the kernel version).

A rt kernel is generally adviced for audio tasks. You may want to install it. Use synaptic, or the terminal:
```
sudo aptitude install linux-rt
```
You should also set real time priority acces for your apps... well, better bookmark and have a look [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation") (real time section). If you need further advice in what a rt kernel is and does, feel free to ask back.

It isn't still clear to me what your left channel problem is. Is it while recording? Then hover the mouse on the armed track, press "b" (for buses), and see if only "left" is selected.

---

### Post by JC Cheloven on 2010-01-11
> **sgx said:**
> (...)
Reaper is the best linux software if you -->need<--
1.audio
2.midi
3.vsts
Using Hydrogen, and zynaddsubfx and rakarrack at the same time as Reaper, and recording the whole affair in timemachine, is great fun!:D

Thanks for sharing. Sounds as an awesome setup.

I may be wrong, but Reaper is proprietary software, isn't it? I always prefer -if I can- using free software, even if it is not yet as fancy or polished as proprietary counterparts. I always think: "it will improve if we use it".

I look forward to try out the new Muse 1.0 for my (very basic) midi needs. I didn't have much luck with rosegarden so far.

---

### Post by jsilas on 2010-01-11
Thanks for the kernel info. I took care of that. I'm really ignorant to ubuntu so I do appreciate all the help I can get. It's looking more and more like the issue with the channel select is coming form my omega. When I pug the mic into channel two it reads in the other speaker. So far though, this program is alot of fun and I can't wait to have some kind of finished product thorough it.

---

### Post by mango42 on 2010-01-11
Hola JC,

You've piqued my interest in a DAW that apparently doesn't insist on controlling a mouse at almost pixel level, if I understand you correctly.

However, do you happen to know if/when the devs will tackle timestretch/pitchshifting on the lines of Ardour's Rhythm Ferret?

---

### Post by JC Cheloven on 2010-01-11
> **mango42 said:**
> Hola JC,

You've piqued my interest in a DAW that apparently doesn't insist on controlling a mouse at almost pixel level, if I understand you correctly.

However, do you happen to know if/when the devs will tackle timestretch/pitchshifting on the lines of Ardour's Rhythm Ferret?

Yes, you understood ok. No "pixel level mousing" in traverso :-D

As a plain user, I dared to ask the devels (nice people btw) for some features: a metronome clip, and time & pitch stretching. See my posts (currently #1 & #3) in the traverso "feature request" forum [http://traverso-daw.org/forum/index.php/board,6.0.html](http://traverso-daw.org/forum/index.php/board,6.0.html) All I can say is that they apparently have shown interest on them, specially in my metronome idea.
Nevertheless, you can do time/pitch stretching via the "external processing" feature, using the sox program within traverso. But it's not the way to go, imo. A more friendly approach is needed. As you can see, I suggested to incorporate the functionality of the rubberband backend in the program's GUI.

---

### Post by kkdai on 2010-01-20
maybe a touch screen will solve this problem
 
 
[[COLOR=white]Office Furniture[/COLOR]]("http://www.officefurniture-supplier.com/eng/")
[[COLOR=white]Skin Cancer[/COLOR]]("http://www.health818.org/Skin-cancer-treatment.php")

---

### Post by JC Cheloven on 2010-01-23
Hi again, coming back with an update. I got a bit involved in the project last week, and now I'm now commited to make the spanish translation. It will available very soon :-)
As a result of this, I'm having quite an extensive e-mail activity with the devels. Related to your question:
> **mango42 said:**
>  (...) However, do you happen to know if/when the devs will tackle timestretch/pitchshifting on the lines of Ardour's Rhythm Ferret?
I can tell that I've appreciated a [real interest and plans]("http://traverso-daw.org/plans-for-2010.html") to implement the features I proposed: metronome, time stretching, and pitch adjustement. I've been told that they would be glad to hear about how (in which particular way) users would expect/like to see these features implemented. So if anyone is using Traverso out there, and is interested in such features, please go to traverso forums to let the devels know.

This will be more than likely my last post in this thread, as it already served its purpose (enabling anybody searching for a DAW over here, to find what traverso is about). Thank you everybody.

---

### Post by JC Cheloven on 2010-06-14
> **JC Cheloven said:**
> This will be more than likely my last post in this thread, as it already served its purpose (enabling anybody searching for a DAW over here, to find what traverso is about). Thank you everybody.

Well, after 5 months I somehow changed my mind, and thought that an update wouldn't hurt.

- Traverso stable 0.49.1 crashes in Lucid due to a problem with QT versions. The devel team sent a patch which is applied in some PPAs.  PLease see the end of the Original Post in this thread for updated info.

- Traverso has been under very active development these months. The new version will be available soon (some 2 months). It is much improved!

Greetings
JC
_________________

---

### Post by zettberlin on 2010-06-14
> **JC Cheloven said:**
> 
- Traverso has been under very active development these months. The new version will be available soon (some 2 months). It is much improved!


This is very good news indeed!

I would certainly NOT advocate Traverso if it would try to be a second Ardour for the poor. It's 
 completely different approach makes it interesting. Especially that the GUI can be customized and thus stripped to not much more then the bare Tracks is very cool if you need to work on a small screen like on a netbook. Plus its combined mouse+keys interface is quite smart :-)

What could be improved?

1.) Jacksupport should be complete and as stable and lean as the app is in general. (No, I take that back: it should be even more stable ;-) )

2.) Up-to date LV2-support incl. GUI
Traverso was one of the very first apps to support LV2 so it would be nice to see it being an avantgardist in LV2 again ;-)

And please: do not waste time and effort in native support for Pulse Audio or much worse: Port Audio. Jack and Alsa are perfectly enough and somehow jack alone would be enough for most of the advanced Linux Audio people...

---

### Post by JC Cheloven on 2010-06-14
Hi zett, thanks for your comments.
> **zettberlin said:**
> This is very good news indeed!Jacksupport should be complete and as stable and lean as the app is in general. (No, I take that back: it should be even more stable ;-) )
You'll love the new version then. Jack support is much improved. When you create a track, it promotes to jack as an independent i/o. Traverso is becoming "everything can be routed to everything", and a single track, a submix track, or a sheet or project main out, can be routed (well those what makes sense) to a submix, a main out, a jack main, or even directly to a hardware port!

> 2.) Up-to date LV2-support incl. GUI
Traverso was one of the very first apps to support LV2 so it would be nice to see it being an avantgardist in LV2 again ;-) 
I'm affraid this is a bit more difficult, due to the lack of a stable LV2 standard. Not much improvement is to be expected on this in the new version. Calf plugins and about a half (?) of other LV2 plugins out there I've tried, work correctly though.

> And please: do not waste time and effort in native support for Pulse Audio or much worse: Port Audio. Jack and Alsa are perfectly enough and somehow jack alone would be enough for most of the advanced Linux Audio people...
Well, you'd get my vote for Jack+Alsa, both as important ;-)

JC
___________

---

### Post by philip5 on 2010-06-15
FYI
On my PPA Traverso 0.49.1 have the QT 4.6 patch applied for Lucid so it should work as it should regarding to this problem.

---

### Post by thorgal on 2010-06-15
portaudio is for multiplatform support. 
I never really understand why a dev does not endorse one audio backend (... jack for example ... ) and be done. Jack runs on OSX, Windows, Linux, freeBSD, Solaris, maybe more! Isn't that enough ?

all other audio layers introduce more effort. The Jack API is in general nice and developer friendly. Why bother with other APIs ? I mean, if the app is to be a multitracking tool with complex mixing, routing, etc, Jack is the only thing needed.

---

### Post by JC Cheloven on 2010-06-15
@philip5:
Sure! I updated the OP yesterday, as soon as I was aware (see last "edit"). Your PPA is becoming indispensable. Thank you very much!

@thorgal:
Yes, I see your point. It plenty applies to studio recordings, among possibly other use cases. 
But, for example, I often have to record (overdubbing) a single musician at his place, using a very minimal equipment (netbook + usb card + condenser mic). And there are many situations in which an user wants to do a simple straightforward recording. IMO, for these 'quick' use cases, having to start by setting up jack is somehow cumbersome.

Greetings
JC

---

### Post by rsijrier on 2010-06-15
@thorgal:

I would love to only have to maintain one audio backend, and if JACK runs stable on all platforms (linux, mac os x and windows) that's fine.

So of course I do endorse to only use one audio backend. But you and I know that 5 years ago, there wasn't such a thing as JACK on Windows, was it?
Also, how stable and solid does it run on Windows? Another btw, afaik JACK on Windows relies on PortAudio as it's driver backend... 

A real nice solution would be that JACK becomes the default sound server on linux, and everything runs on top of it. For that we need a JACK that allows clients to use different buffer sizes. As far as I understand anyway.

Enfin, it's a bit weird imho to think that devs endorse multiple backends, it's rather that I'm forced to do so :(

Remon

---

### Post by rsijrier on 2010-06-15
@zettberlin:

Our intend is to keep Traverso as clean as possible. Traverso continues to be build around the input from it's user base, and as such it's a unique program that doesn't compare or compete with any other program.

JACK support has been improved to the state it always should have been in, but oh well, it's mostly there now.
The nice thing is that you can use either JACK or a hardware driver in the same project, it doesn't change your routing. So creating a project using the ALSA driver to do the recording (e.g. keep everything as simple as possible, using a netbook to do on stage recording) and on the main DAW box use JACK for all your plugins, etc.

@ philip5:

Thanks for the quick update, it helps a great deal to have a working Traverso on ubuntu 10.04 !

If you guys have any questions, you're all invited to join irc #traverso or [http://traverso-daw.org/forum/index.php](http://traverso-daw.org/forum/index.php) so we can together work on a better Traverso :)

Thanks,

Remon

---

### Post by thorgal on 2010-06-16
> **rsijrier said:**
> @thorgal:

I would love to only have to maintain one audio backend, and if JACK runs stable on all platforms (linux, mac os x and windows) that's fine.

So of course I do endorse to only use one audio backend. But you and I know that 5 years ago, there wasn't such a thing as JACK on Windows, was it?
Also, how stable and solid does it run on Windows? Another btw, afaik JACK on Windows relies on PortAudio as it's driver backend... 

A real nice solution would be that JACK becomes the default sound server on linux, and everything runs on top of it. For that we need a JACK that allows clients to use different buffer sizes. As far as I understand anyway.

Enfin, it's a bit weird imho to think that devs endorse multiple backends, it's rather that I'm forced to do so :(

Remon

true enough. Hopefully, things will converge nicely with time ...

---

### Post by Amorbis on 2010-06-18
I downloaded the installer package from the Traverso site, and installed Traverso. But Traverso closes as soon as i try to load it up. So now i want to remove it, but i can't do it... whenever i try to delete the files for it, it tells me that i don't have the permissions to do so... How can i remove the program?

Ubuntu version that i am using: 9.04

---

### Post by JC Cheloven on 2010-06-20
@amorbis:
So you downladed the traverso-0.49.1.tar.gz file, CAREFULLY installed all the dependencies, and compiled traverso yourself, right?

If the above is true, I don't know exactly why this happens to you. I think nothing is missing in Jaunty to make Traverso work (qt version included?). If you want to track your problem, please post the output of your console after running Traverso.

Anyway, the files should be in the ~/traverso directory, which you should be also able to delete without any special privileges at all. If it's not the case, please try ```
sudo rm -R ~/traverso
```

---

### Post by rsijrier on 2010-06-20
> **JC Cheloven said:**
> @amorbis:
please try ```
sudo rm -R ~/traverso
```

Phew, that's a dangerous rm command you do there. You're now removing recursively a directory as root, one typo and your whole system could be shredded... :D

@Amorbis:
If you installed via autopackage, you can uninstall it via autopackage, it should be a menu entry in your system or settings menu.

Remon

---

### Post by JC Cheloven on 2010-08-22
Quick news:

A new stable release of Traverso (0.49.2) is out.
 
First thing to say is that it is NOT the result of all the hard work put in the development version of Traverso since 0.49.1. It's more like a transitional release, intended to fix a particular problem induced by a change in the latest Qt libraries. That change made Traverso look like it freezed at startup in Lucid, and other distros packaging latest Qt. To sum up, this release offers:

- A working Traverso for Lucid (and previous!), until the "true" new release comes out, which is taking a bit longer than expected (note: the ppa from philip5 has a patched 0.49.1 which works in lucid, see OP).
- A fix for a bug in the fades, which wasn't completely applied under certain circumstances
- An spanish translation of the user interface. A spanish version of the manual is also available (I'm in charge of these translations)

You cand find everything in the Traverso download page: [http://traverso-daw.org/download.html](http://traverso-daw.org/download.html)

JC

---

### Post by Hylas de Niall on 2011-10-19
Repos only has 49.1 over a year after the release of a later version?
:confused:

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-22
Yeah I tried Traveso, and enjoyed it, but it is so vastly different from all the others, that to do something little I would have to learn how to do it...  I couldn't figure out how to split a track to edit it.... and I only had a few minutes to do it, so I just defaulted back to audacity (which is  very fast & lightweight).  I was intrigued with traverso, because it seemed like you could burn a whole cd and modify the gaps between tracks.

---

### Post by jejeman on 2011-10-22
> **Hylas de Niall said:**
> Repos only has 49.1 over a year after the release of a later version?
:confused:
Traverso is a esay one to compile. You should try it. And on the end, you get just one binary file which you just run.

I love traverso, too. I'm using it often to sketch up ideas. Because it is very easy and fast to work with.

---

### Post by Hylas de Niall on 2011-10-24
> **jejeman said:**
> Traverso is a esay one to compile. You should try it. And on the end, you get just one binary file which you just run.

I love traverso, too. I'm using it often to sketch up ideas. Because it is very easy and fast to work with.

LOL! I wouldn't know where to start with compiling anything myself, though i dare say it's something i'll try sooner rather than later.

I'm pretty happy with the repo version anyway, it's a lot of fun and *outstanding* for a free DAW.

Thanks to Traverso, I no longer have any reason* to go back to Windows! (*no pun intended)

---

### Post by Hylas de Niall on 2011-11-10
> **TREESofRIGHTEOUSNESS said:**
> Yeah I tried Traveso, and enjoyed it, but it is so vastly different from all the others, that to do something little I would have to learn how to do it...  I couldn't figure out how to split a track to edit it.... and I only had a few minutes to do it, so I just defaulted back to audacity (which is  very fast & lightweight).  I was intrigued with traverso, because it seemed like you could burn a whole cd and modify the gaps between tracks.

I think you hover the cursor where you want the split, and then hit 'X'.
I've been playing around with it a little, and i'm liking it now i have a basic grasp of the key controls. I miss being able to add effects on the fly (I'm used to Acid & Ableton), but i dare say i'll learn the ins and outs of Sox in due course.
Yeah, i like it. It's a keeper!
:D

---

