---
title: "Totem not ready to be default media player..."
date: 2005-06-28
forum: The Cafe
---

### Post by ZephyrXero on 2005-06-28
Ok, here's a rant coming up...so first a little background. I've been using Linux for around a year now, I tried Warty briefly, but went back to Gentoo after a week or two because I missed portage ;) I'm giving Ubuntu another go with the new version and have been pretty damn impressed with it :) It's nice having everything pretty much ready to go out of the box now. There's just one small problem...media players. This is  one of the main reasons I got frustrated with Ubuntu before (didn't know as much back then though). I'm very pleased to have all my sound and stuff working right after install, but the actual media players are still very lacking in Hoary. I know the Gnome guys think's that Totem's ready to be used by everyone...but it's still got a long way to go as far as I'm concerned. Rhythmbox looks neat, but it's not quite up to snuff yet either. I tried about 20 different radio stations and video tests and hardly any of them worked. Totem kept telling me it didn't know what an mpeg was! And forget about playing anything that's embedded in a webpage... This unfortunately leaves a very ugly tarnish on what otherwise seems to be an excellent desktop. After uninstalling both of them and installing VideoLan things are going a little better, but it's still not nearly as well integrated into the desktop as Totem/Rhythmbox were :( This is probably one of MS's main strengths over Linux still, with the WMP built in supporting most formats right out of the box. Watching video and listening to audio are some of the main things people use their computers for, so this needs to be a top priority for an easy to use OS. Anyway, my main point here is that for the next release (Breezy?), if Totem has not progressed much more you should include a more robust and functional media player as the default install next time (I'd suggest either VLC or Mplayer). Otherwise...great work guys! :)

*note: Wasn't sure which forum this should go in, so I just went with general...*

---

### Post by kvidell on 2005-06-28
Ahhh... Totem...

I went to a BayLISA meeting last month and Brian Cantrill of Sun was the featured speaker that day...
He was showing off his DTrace project to us...
He used Gnome-Terminal and Totem as his examples to pull things that are broken out of other people's software for indepth, real time debugging...

Gnome-Terminal wasn't terrible... I think the group of us decided it was only minorly broken...
Totem on the other hand... well.... It's dtrace output was... expansive to say the least.
Stupid things were showing up broken... and something that really pissed off Cantrill about Totem was how it was putting temporary files in the users home directory in .totem/temp.
He went on some diatribe about how files that aren't necessary after a reboot should always be put in /tmp.

I thought it was interesting. Totem needs a _lot_ of work.
- Kev

---

### Post by sapo on 2005-06-28
man.. learn what a paragraph is.. then i will read it

> 
"The Collaborative International Dictionary of English v.0.48"
Paragraph Par"a*graph, n. F. paragraphe, LL. paragraphus, fr.
   Gr. para`grafos (sc. grammh`) a line or stroke drawn in the
   margin, fr. paragra`fein to write beside; para` beside +
   gra`fein to write. See Para-, and Graphic, and cf.
   Paraph.
   1. Originally, a marginal mark or note, set in the margin to
      call attention to something in the text, e. g., a change
      of subject; now, the character para, commonly used in
      the text as a reference mark to a footnote, or to indicate
      the place of a division into sections.
      1913 Webster

   Note: This character is merely a modification of a capital P
         (the initial of the word paragraph), the letter being
         reversed, and the black part made white and the white
         part black for the sake of distinctiveness.
         1913 Webster

   2. A distinct part of a discourse or writing; any section or
      subdivision of a writing or chapter which relates to a
      particular point, whether consisting of one or many
      sentences. The division is sometimes noted by the mark
      para, but usually, by beginning the first sentence of
      the paragraph on a new line and at more than the usual
      distance from the margin, also called indenting the line.
      See indentation4.

   3. A brief composition complete in one typographical section
      or paragraph; an item, remark, or quotation comprised in a
      few lines forming one paragraph; as, a column of news
      paragraphs; an editorial paragraph.
      1913 Webster


anyway.. i love totem.. is simple and play ALL my movies.. even mkv with dual audio and subtitles.. 

i just miss a equalizer...

---

### Post by GazaM on 2005-06-28
I agree that TOTEM as a program needs a lot of work, but the main problem in my view is the lack of support for codecs. This not TOTEM's fault, it is ubuntu's. TOTEM works on the Gstreamer framework by default, but ubuntu devs refuse to support proprietry codecs out-of-the-box, so it is up to the user to install the necessary Gstreamer plugins to allow TOTEM to play proprietry files. For me I just installed the Gstreamer plugins and Gstreamer-ffmpeg packages and now TOTEM plays most of my files without a hitch. The TOTEM devs need to work on UI and more features, but quality of playback and support for many codecs is up to the gstreamer and ubuntu teams respectively. That's my $0.02.

---

### Post by kvidell on 2005-06-28
[QUOTE=GazaM]I agree that TOTEM as a program needs a lot of work, but the main problem in my view is the lack of support for codecs. This not TOTEM's fault, it is ubuntu's. TOTEM works on the Gstreamer framework by default, but ubuntu devs refuse to support proprietry codecs out-of-the-box, so it is up to the user to install the necessary Gstreamer plugins to allow TOTEM to play proprietry files. For me I just installed the Gstreamer plugins and Gstreamer-ffmpeg packages and now TOTEM plays most of my files without a hitch. The TOTEM devs need to work on UI and more features, but quality of playback and support for many codecs is up to the gstreamer and ubuntu teams respectively. That's my $0.02.[/QUOTE]
 is it really so hard to install w32codecs?

---

### Post by sapo on 2005-06-28
[QUOTE=kvidell]is it really so hard to install w32codecs?[/QUOTE]

i think it is.. as we all know windows comes with divx, xvid, and everything by default.. we just need to install the wmv codec  :roll:

---

### Post by granite230 on 2005-06-28
lol, the first thing I removed from my Sound & Video menu is Totem. This player didn't play a thing! Errors errors errors... today it actually does play a thing! Only the sound can be heard, but just some weird replacement pictures are shown. So that means no movie pictures.

It's just that I don't know how to make Xine my default player.... Xine plays everything I want to play. I always right click > Play with Xine.

I also have MPlayer, but sometimes that won't work perfectly either...

I guess I'm doing something wrong, or maybe I'm forgetting something.

---

### Post by sapo on 2005-06-28
[QUOTE=granite230]lol, the first thing I removed from my Sound & Video menu is Totem. This player didn't play a thing! Errors errors errors... today it actually does play a thing! Only the sound can be heard, but just some weird replacement pictures are shown. So that means no movie pictures.

It's just that I don't know how to make Xine my default player.... Xine plays everything I want to play. I always right click > Play with Xine.

I also have MPlayer, but sometimes that won't work perfectly either...

I guess I'm doing something wrong, or maybe I'm forgetting something.[/QUOTE]

have you ever heard of totem-xine? thats what i use.. i dont like xine nor mplayer.. too many buttons just to show a movie  :roll:

---

### Post by manicka on 2005-06-28
I find Kaffeine pretty reliable but xine is nice to. I'd have to agree about Totem.. hopeless

---

### Post by manicka on 2005-06-28
[QUOTE=manicka]I find Kaffeine pretty reliable but xine is nice to. I'd have to agree about Totem.. hopeless[/QUOTE]
 Just tried totem-xine which seems to fix the issues that I was having with totem

---

### Post by man.life on 2005-06-28
Use backports, upgrade totem and install totem-xine (if you hadn't done it before): lots of improvements and **web plugin** included. Works great for me.

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=GazaM]This not TOTEM's fault, it is ubuntu's.[/QUOTE]

Its not Ubuntu's fault. Ubuntu wasn't the one that patented all of those formats (such as MP3 and WMV) and said "you must pay ____$thousands____ to use our codecs" (in some cases there is no legal way for Ubuntu to use the codecs). 

If its not legal...Ubuntu can't risk doing it (I'd rather money be spent of fixing bugs then hiring expensive IP lawyers).

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=ZephyrXero]This is probably one of MS's main strengths over Linux still, with the WMP built in supporting most formats right out of the box.[/QUOTE]

Actaually...MS "out of the box" media support is weak. I think out of the box it supports only MP3, WMV and old MPEG files. Once you install the w32codecs in Ubuntu you can play quicktime files, divx files, wmv files, etc. 

> Anyway, my main point here is that for the next release (Breezy?), if Totem has not progressed much more you should include a more robust and functional media player as the default install next time (I'd suggest either VLC or Mplayer). Otherwise...great work guys! :)

My favorite is Gxine. But the real problem isn't with totem....its with the heavy use of closed codecs....even though you are right, totem is definately not used much by me.

---

### Post by RaymondQE on 2005-06-28
Someone suggested this before on the forums, but a good idea is to install gxine or xine-ui but use totem-gstreamer initially for video files.  If the file doesn't play right, file a bug report, then set that file type to open with gxine instead.  That way, you can help with the gstreamer development process and still be able to watch the video files.

---

### Post by Kvark on 2005-06-28
Totem is ok. The two things that gives a feel of horrible multimedia support is...

1. Many video clips embedded in webpages won't work as they should with firefox on linux, and there is no way to fix it. The best one can do is get the MediaPlayerConnectivity extension that provides a very poor workaround for most clips.

2. Before you realize which package to install to get the codecs you are hammered with messages about not being able to play anything.


Btw, the worst media player I've ever encountered is windows media player, it has loads of features that are completely unrelated to the task of playing music and video, yet it lacks some basic functions that would be useful in a media player.

The best ever is old versions of winamp, exactly the features that are useful for playing music, add the basic DVD player functions and all codecs to an old school winamp clone and there you got perfection.

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=Kvark]
1. Many video clips embedded in webpages won't work as they should with firefox on linux, and there is no way to fix it. The best one can do is get the MediaPlayerConnectivity extension that provides a very poor workaround for most clips.[/QUOTE]

Did you do this?:

[http://www.ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger](http://www.ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger)

---

### Post by Kvark on 2005-06-28
[QUOTE=poofyhairguy]Did you do this?:

[http://www.ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger](http://www.ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger)[/QUOTE]

Yeah, did that, but it didn't work.

edit: oh, wait I didn't use his version of it...

---

### Post by kvidell on 2005-06-28
My favourite is still mplayer... The one that came with Debian awhile back was nice.
I don't like gui stuff often, so mplayer was pretty cool for me.

Wanted to watch a fullscreen movie?
```
mplayer -fstype fullscreen -fs movie.ext
``` Works great :)
- Kev

---

### Post by gil-galad on 2005-06-28
Totem-xine works great for me.  The interface is nice and (with xine) it supports everything.  It was horribly buggy in the pre1.0 days (warty, et al) but it works much better now that it is officially part of gnome.  I also have a no gui version of mplayer for the mozilla-mplayer plugin, but that just works in the background when I need it.

---

### Post by psychicdragon on 2005-06-28
I've never been able to play anything with totem-gstreamer but totem-xine works flawlessly for me. It'd be nice to see xine backend become the default in breezy as totem-gstreamer definately doesn't seem like it's ready yet.

---

### Post by Quest-Master on 2005-06-28
VLC rocks hard. It's fast, lightweight, and is just an all-purpose media player. I love it. <3

---

### Post by kvidell on 2005-06-28
[QUOTE=Quest-Master]VLC rocks hard. It's fast, lightweight, and is just an all-purpose media player. I love it. <3[/QUOTE]
 My media player of choice on OS-X-10.4 :)

---

### Post by Optimal Aurora on 2005-06-28
I don't understand why you dislike it so, because totem is just that one of the many media players available through synaptic. You should just go out and download your favorite, for me however, I don't have any problems with totem because I prefer totem-xine... go figure...

---

### Post by ZephyrXero on 2005-06-29
Well my main point wasn't to just straight up diss on Totem. I just think it makes no sense to try and create a very easy, user friendly linux distro and then make one of the primary things people do with their computers not work right out of the box. For all I know, totem may become a great player a few versions down the road or with Xine even, but it's not the default player when you install Ubuntu, and that's the problem.

And as many pointed out, proprietary codecs are definitely a problem, but I had trouble getting an Ogg Vorbis radio station to even run using the default software of Hoary. There's no excuse for not having full support of Vorbis, Theora, Xvid and any other major open codecs. As far as mpeg, why couldn't they just include ffmpeg and/or lame? If some sort of legal issues arose between those guys and the people who's codecs they reverse engineered, then the next release could just simply remove support. The other option is to include a script or something that will tell the user exactly why the file would not play and explain to the situation and how to download the codecs manually. To the average person, seeing error, and no explination is a very confusing and somewhat scary thing.

My vote goes towards VideoLan ;)

---

### Post by Big Venus on 2005-06-29
I am sorry you have had problems with Totem, I am newbie and starting to like synaptic and apt-get, to download linux you had to have a dsl connection or know some one who has or better yet call canonical (however it is spelled) and as them for the dvd disc with all the main repo on it, then install the one you want. 

I have used fedora since fedora 1 and I have used totem almost as long since fc2, and I haven't ever heard anyone complain about errors or anything like that coming from trying to run totem or xine, heck even mplayer. Like I said in the above paragraph, you have over 15 thousand packages to choose from, go out their in synaptic and just get the right one for you. 

I haven't seen any other people say that they have had problems with totem on other forums before...

I agree with Aurora my favorite has been totem-xine, but I do use mplayer.

---

### Post by jiyuu0 on 2005-06-29
i've updated this howto:
[http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)

it will associate xine-ui to be the default player for multimedia files and auto-run dvd movie

---

### Post by desdinova on 2005-06-29
[QUOTE=sapo]i think it is.. as we all know windows comes with divx, xvid, and everything by default.. we just need to install the wmv codec :roll:[/QUOTE]

No it doesn't - they're third party addons

---

### Post by Knome_fan on 2005-06-29
Why don't people at least try to educate themselves before they start to bash other peoples work?

I just don't get it, finding out how to solve all your problems with totem would have taken you 5 minutes at most, yet you chose to start a thread with the sole purpose of bashing totem. Impressive.

And the problems with propietary codecs and tools like lame and ffmpeg have been discussed over and over again here and on about every website dealing with free software. Why people chose to bring up all these things that have been discussed and discussed and discussed and discussed and discussed again and again and again and again and again is simply beyond me.

---

### Post by ZephyrXero on 2005-06-29
Maybe they keep getting discussed because it's not a cut and dry issue like you think ;) ...there's nothing wrong with discussion. But since some have seemed to miss the point, I'm not worried about getting it to work for myself. I want it to work for people who aren't familiar with Linux. If I hand a live CD to a buddy and tell him how awesome Linux is and then he tries it out and has these kinds of problems, he's gonna take the disc out and boot Windows right back up :( I would think an Ubuntu person would understand the importance of this...geez it's like I'm back on the Gentoo forums again :/

---

### Post by Knome_fan on 2005-06-29
[QUOTE=ZephyrXero]I would think an Ubuntu person would understand the importance of this...geez it's like I'm back on the Gentoo forums again :/[/QUOTE]

That's exactly how I felt after reading your, ehem, complaint.

Would I agree, that GNU/Linux in general and Ubuntu specifically should improve when it comes to multimedia? Absolutely.

However I also know that many of the problems are caused by legal issues, not by technical issues.

Finally, I frankly don't like your discursive strategy of arguing against something I never said. I never claimed everything is fine, I just commented on your uninformed (to put it mildly) and totally uncalled for bashing of totem.

---

### Post by ZephyrXero on 2005-06-29
Totem does not work very well out of the box. I tested numerous types of files and streams... this also went for Rhythmbox as well. What's there to be uninformed about? There's nothing to argue about, it's not an opinion it's an observation.

---

### Post by daveisadork on 2005-06-29
Eh, I've been really happy with Totem and RhythmBox. Granted, the gstreamer version is almost useless, I haven't run across anything that totem-xine wouldn't play. All you need are a couple of packages and RhythmBox will play most formats (including M4A/AAC). As far as a plugin for Firefox, I use gxine and it works well enough for me.

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=ZephyrXero] If I hand a live CD to a buddy and tell him how awesome Linux is and then he tries it out and has these kinds of problems, he's gonna take the disc out and boot Windows right back up :( I would think an Ubuntu person would understand the importance of this...[/QUOTE]

We do. There is nothing we can do about 90%+ of the file formats being closed formats though. Nothing we can do besides pointing people to the howto.

This comes up every time...it would be nice to support all those things...and I agree with you, the fact that Oggs don't play is a disgrace. But if someone is going to dump Ubuntu simply because their media doesn't work out of the box, I have to think that they would have found some other reason to dump Ubuntu if this wasn't the case.

> geez it's like I'm back on the Gentoo forums again :/

If we ever have 1/5th the info that the Gentoo forums has in it....I would be happy.

The Gentoop people (and Fedora and all free Linuxs) are in the same boat as us. Complaining doesn't make all those nasty media patents go away.

I believe that Linux can work well IF A NERD SETS IT UP. If you just hand your friend a Live CD and expect that you have done your part then all you hoped for was failure.

---

### Post by Tsukasa on 2005-06-30
I agree that Totem doesn't do so well out of the box. I just want to mention that Windows doesn't do any better: The Windows Media Player is the worst thing you could possibly play your videos with. It's slow, it has about zero features and it can't play 3rd party codecs out of the box (as mentioned in reply to "Windows comes with all the shiny codecs...").

Personally I think it's much more work to grab a decent media player, check the web for all the latest versions of the codecs (because codecpacks never do any good!) etc. on Windows... On Ubuntu it's pretty easy, after my drivers are set up and loaded I just get gxine and the codecs for use with all the other players around and I'm set. Keeping all the stuff up to date is easier too ;) .

And yeah, my favorite player is (g)xine because - just like vlc - it has a very neat way of  keeping the video playback smooth and synchronized to the audio (one of the things Totem lacks too ;)).

---

### Post by Optimal Aurora on 2005-06-30
[QUOTE=Knome_fan]That's exactly how I felt after reading your, ehem, complaint.

Would I agree, that GNU/Linux in general and Ubuntu specifically should improve when it comes to multimedia? Absolutely.

However I also know that many of the problems are caused by legal issues, not by technical issues.

Finally, I frankly don't like your discursive strategy of arguing against something I never said. I never claimed everything is fine, I just commented on your uninformed (to put it mildly) and totally uncalled for bashing of totem.[/QUOTE]
Exactly, way to go Knome_fan... Its not about technical problems but legal ones...

And agreed, I don't like the strategy of arguing against something, people should since Ubuntu, Gentoo, Fedora, Turbo Linux, etc  are free and most programs out there are free, use what they feel is right, not starting up flame wars or arguing that this should not be included with Ubuntu and that something else should...

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=Tsukasa]
And yeah, my favorite player is (g)xine because - just like vlc - it has a very neat way of  keeping the video playback smooth and synchronized to the audio (one of the things Totem lacks too ;)).[/QUOTE]


Gxine is good enough it converted a friend of mine to Linux.

---

### Post by aaarg on 2005-07-01
[QUOTE=Quest-Master]VLC rocks hard. It's fast, lightweight, and is just an all-purpose media player. I love it. <3[/QUOTE]


good call, VLC is my favorite on every OS

---

### Post by doclivingston on 2005-07-02
My 2c for the various topics:

* Ubuntu isn't the only distro that doesn't support various codecs out-of-the-box dut to legal reasons; quite a few others (such as Fedora) don't either. If you don't like it then, convince various governments that these kinds of patents are bad.

* Windows can't play quite a few codecs out of the box either; such as DivX, XviD, Ogg Vorbis, FLAC, Quicktime, Real Audio, AAC and a few others 

* If you install the appropriate plugins for gstreamer, totem gstreamer does okay. The only problems I've really had with it are
a) DVDs, but I've heard in #gstreamer that the CVS version of totem has menu and subtitle support
b) it goes aout of a/v sync for some really badly encoded video files; most other movie players include lots of kludges to play badly encoded files.

* If you install the mp3/aac codecs Rhythmbox is reasonably good (assuming that you like that type of music player). RB has quite a few features in CVS/arch branches which will be good whenever a 0.9 development release finally comes out

---

### Post by cowlip on 2005-07-02
Totem-gstreamer is completely broken, thank god for the xine version.  But you don't know how long it took me to figure that out :(

---

### Post by polo_step on 2005-07-02
[QUOTE=poofyhairguy]We do. There is nothing we can do about 90%+ of the file formats being closed formats though. Nothing we can do besides pointing people to the howto.

This comes up every time...it would be nice to support all those things...and I agree with you, the fact that Oggs don't play is a disgrace. But if someone is going to dump Ubuntu simply because their media doesn't work out of the box, I have to think that they would have found some other reason to dump Ubuntu if this wasn't the case.[/QUOTE]
The problem is that all this important stuff is not where a new user can find it.  I'm STILL looking.

All the "essential" explanations -- like adding repositories, adding codecs, adding software -- should be covered in a totally transparent, quick-start, no-BS, no-puffery file linked to a big poke-in-the-eye NEW USER READ THIS! icon square on the first-boot desktop.  The basic explanations should not have a single extra word, but contain links for more detailed explanations if the user is interested.

"A/V Media Players:  For legal reasons, the default player is not distributed with codecs for playing all types of mutimedia files.  If you wish to play [list of unsupported file extensions here] files, you must install these codecs on your computer. [howto link]"

That's all you have to say.  Then move on to the next "problem," like adding/removing software and repositories.

Still, the A/V players are a mess.  Totem doesn't work right at all, and gXine won't work right if started from an icon, but works fine if invoked from command line...until I click fullscreen mode, and then it crashes the system with a lockup, etc., blah...

---

### Post by doclivingston on 2005-07-02
[QUOTE=polo_step]"A/V Media Players:  For legal reasons, the default player is not distributed with codecs for playing all types of mutimedia files.  If you wish to play [list of unsupported file extensions here] files, you must install these codecs on your computer. [howto link]"[/QUOTE]
Personally I can't see how distributing it on the CD, and having a "click this button to install" thing are really that different from each other. Which is probably why I'm not a lawyer.


One thing that gets tricky is the list of file extensions: particularly with multimedia, the file extenstion don't mean much.

Take AVI files: Ubuntu can play AVI files perfectly fine, it's just the DivX/Xvid and MP3 content (which is what you find inside AVI files 99% of the time) that it can't play. RM, ASF, AVI, Ogg, Matroska, et cetera are only containers - you can't tell if you can play them or not, just by looking at the file extension.

What do you tell users - ".avi files are not supported, except when they are"?

---

### Post by polo_step on 2005-07-02
[QUOTE=doclivingston]
What do you tell users - ".avi files are not supported, except when they are"?[/QUOTE]
If it's a shorter list, put down what extensions it WILL run without problems.  Same ultimate outcome.

The point is that an extremely succinct "distro weirdnesses" list of necessary user tweaks to achieve customary functionality should be linked to an icon right square in front of their noses.

It doesn't have to provide the fix, merely a very brief explanation with a link to more info.

And keep it **short**!

This is a no-brainer.

---

### Post by poofyhairguy on 2005-07-02
[QUOTE=polo_step]
All the "essential" explanations -- like adding repositories, adding codecs, adding software -- should be covered in a totally transparent, quick-start, no-BS, no-puffery file linked to a big poke-in-the-eye NEW USER READ THIS! icon square on the first-boot desktop.  The basic explanations should not have a single extra word, but contain links for more detailed explanations if the user is interested.[/QUOTE]

Sounds great. When will you be done with this great new howto guide? I'll use my weight to help get it included. I'll proofread too.

---

### Post by polo_step on 2005-07-02
[QUOTE=poofyhairguy]Sounds great. When will you be done with this great new howto guide? [/QUOTE]
About three weeks after I cut my contract with Shuttlesworth for it.

---

### Post by gil-galad on 2005-07-02
I don't think telling people how to break the law is much better than breaking it yourself from a legal point of view.  

And I don't think the average user needs to watch pirated movies as soon as they install ubuntu. :\

---

### Post by ZephyrXero on 2005-07-03
I think DocLivingston made an excellent point....how is distributing these patented codecs via the install CD any different than distributing them from the repository? It's not...both are equally legal/illegal. If legallity was an issue, then they wouldn't be in the repositories either...

Polo Step had a very good idea, similar to mine... if you're not going to (or can't) include these codecs then make it blatently obvious to the user how to rectify the situation. I'll be glad to help write it up, but I don't have the most free time in the world...

To Gil-Galad, not all videos on the internet are illegal...even though a large portion are, there's a very worthwhile portion that are not.

Last I'd like to add to my ideas (not complaints!) that whatever player goes into the future version of Ubuntu, there should be a Firefox plugin for embedded movies included by default as well.

---

### Post by Knome_fan on 2005-07-03
[QUOTE=ZephyrXero]I think DocLivingston made an excellent point....how is distributing these patented codecs via the install CD any different than distributing them from the repository?[/QUOTE]

Because in one instance you are actively distributing them, while in the other instance you merely give people the opportunity to download them if they deem it proper to do so.

---

### Post by Cynical on 2007-02-06
I love totem's gui, its perfect for how I watch videos. My only problem with it is that when I try to play large mkv files it just can't handle it. VLC and mplayer on the other hand have no problems at all.

---

### Post by tbroderick on 2007-02-07
nice bump on a thread from 2005 ;)

---

### Post by Polygon on 2007-02-07
> **sapo said:**
> i think it is.. as we all know windows comes with divx, xvid, and everything by default.. we just need to install the wmv codec  :roll:

no it doesnt! no it doesnt! every time i reinstall windows i have to reinstall ALL of my codecs, including divx, xvid and some other random ones

and i do agree that totem and most movie players need a lot of work....

---

### Post by Kindred on 2007-02-07
Yeah I think he was being sarcastic there... Anyway this thread is old.. :)

---

