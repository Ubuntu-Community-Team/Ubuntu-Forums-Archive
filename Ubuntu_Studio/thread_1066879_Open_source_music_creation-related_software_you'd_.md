---
title: "Open source music creation-related software you'd like to see in Linux"
date: 2009-02-11
forum: Ubuntu Studio
---

### Post by spadewarrior on 2009-02-11
Hello everyone.

I am a computer science student who is about to choose an end-of-year project. My tutor suggested creating an open-source application on Linux that does not already exist and that perhaps exists in some form on another platform (i.e. Windows). Being a musician, I naturally thought of something in the field of music creation, but as a relative newcomer to the Linux platform, I am not very knowledgeable about what already exists and what needs doing. 

So, after that overlong introduction, I'm asking you all for some suggestions!  I am aware of the existence of the more well-known sound-related aspects of linux already (such as argour, rosegarden, jokosher, pulseaudio, jack and so forth) so please suggest smaller, overlooked things that Windows/Mac users take for granted and that no-one has yet implemented on Linux.

Also, I must just stress that 

a) I only have a limited amount of time to complete the project 

and

b) Only I will be working on it.

Naturally the code would be released into the wild after I have finished with it, should I go ahead with creating such a project.

Thank you very much for reading!

:)

---

### Post by Stochastic on 2009-02-11
Here are a couple of links that should help get you familiar with the code base already existing for linux musicians:
[http://linux-sound.org/](http://linux-sound.org/)
[http://apps.linuxaudio.org/](http://apps.linuxaudio.org/)

I think that for the scope of your project a nice softsynth or effects plugin would be good.  Look into the LV2 specification, or DSSI or LADSPA (LV2 is the shiny new spec in town).

---

### Post by spadewarrior on 2009-02-11
Great, thanks, I'll take a look at these. :)

---

### Post by lykwydchykyn on 2009-02-11
I haven't tried to do much audio production since switching to Linux, but from the times I tried most of what I missed were in the form of plugins.  For example:

1. I couldn't find an echo/delay plugin that would sync to tempo
2. I couldn't find a good reverb plugin.  Period.
3. No auto-tune, though that's an ambitious task.
4. Not a plugin, but I never found a satisfying alternative to Jeskola Buzz; but that's another extremely ambitious task.
5. We are really generally short on good DSSI instruments, from what I've seen.  Compare to the wealth of VSTi's on Windows/Mac.

Anyway, that's what I've seen, though my experience is not as thorough as others' might be.  I've basically just loaded up every ladspa/dssi in the repository and messed around trying to write something once or twice.

---

### Post by thorgal on 2009-02-11
hello,

maybe you could implement a graphical parametric EQ as an LV2 plugin ?
The mastering software Jamin has something very interesting but it may be too heavy to implement the whole jamin app into a plugin. Maybe a graphical 3 band parametric EQ would do. There's a huge amount of those things in VST format or integrated in VSTi's (like the very easy to use parametric EQ on the VSTi drums called Addictive Drums). But they remain VSTs, which requires wine, etc. A native linux plugin would be great. For the EQ "engine", there are already parametric EQ plugins in the LADSPA or LV2 world. I just miss the graphical interface where you can modify the parameters on the fly with mouse actions on the EQ curve.
Here is an example : you can drag the frequency points (low, mid, high) and also change the numbers (freq, width, level) by using the scroll-wheel above the numbers (this is a snapshot from Addictive Drums VSTi).

[IMG]http://img9.imageshack.us/img9/1919/grapheqac5.jpg[/IMG]

---

### Post by markbuntu on 2009-02-11
How about a LADSPA wrapper for VSTs?????

---

### Post by thorgal on 2009-02-11
markbuntu, the dssi-vst wrapper provides a LADSPA descriptor so you can in fact use VSTs as you would use with LADSPA plugins. I may be wrong but I read that somewhere ...

---

### Post by markbuntu on 2009-02-11
Hmmm...I will have to check into that and find my old windows hard drive...and figure out where to plug it in...it has about a hundred VSTs on it.

---

### Post by thorgal on 2009-02-11
yeah, it was introduced in version 0.7 :
[http://osdir.com/ml/linux.audio.announce/2008-05/msg00012.html](http://osdir.com/ml/linux.audio.announce/2008-05/msg00012.html)
I never tried it though since I only use a VSTi through dssi-vst.

---

### Post by simtaalo on 2009-02-12
do you have to start a completely new project? you could look at existing programs and maybe add a new feature?

---

### Post by cb951303 on 2009-02-12
I would like to see a LV2 plugin based guitar effects processor **simulating vintage circuits**. Of course it would require a pretty good electronics knowledge, but I thought I might give it a try :)

---

### Post by spadewarrior on 2009-02-12
> **simtaalo said:**
> do you have to start a completely new project? you could look at existing programs and maybe add a new feature?

This is actually what I am currently thinking about...

---

### Post by simtaalo on 2009-02-12
> **spadewarrior said:**
> This is actually what I am currently thinking about...

lmms project is currently looking for someone to do a wave editor for it.

---

### Post by spadewarrior on 2009-02-12
This one?

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/) 

Looks interesting.

---

### Post by insilico on 2009-02-12
An open source music creation project would be fantastic. Another field Linux hasn't hugely explored yet is video editing, but I've seen a bit of progress there recently.

---

### Post by sgx on 2009-02-13
> **spadewarrior said:**
> Hello everyone.

snip

Also, I must just stress that 

a) I only have a limited amount of time to complete the project 

and

b) Only I will be working on it.

Naturally the code would be released into the wild after I have finished with it, should I go ahead with creating such a project.

Thank you very much for reading!

:)
zynaddsubfx is a native linux  world-class softsynth, with an incomplete windows vst port. Adding things like standard fxb/fxp loading/saving
ability, and a gui makeover using a common windows gui toolkit are always
mentioned by people who attempt to use the windows version, loving the sound, but not the interface. See KVR for a forum, with a couple folks
adding some code enhancements recently.

---

### Post by spadewarrior on 2009-02-13
Hi sxg,

I'm afraid I won't be able to do that; it has to be Linux only. I don't have an installation of Windows and I'm more interested in making more things for Linux.

---

### Post by skullmunky on 2009-02-13
If you can work on a component of an existing project, that'd be great.  LMMS is pretty terrific, but more plugins and additions to it would I'm sure be welcome.  One specific thing that I've gotten feedback on from musicians: the VST support is good, lots of VST plugins work flawlessly (maybe they just all do - I haven't run into any problems yet, actually) but they seem to be missing the ability to load Presets.  Those are a real timesaver, particularly for plugins with many, many parameters.

Someone mentioned working on a video editor, which is also not a bad idea.  All the video editors out there could use contributions.

If you DID want to make an app from scratch, a video editor still might be worth it.  My money's on kdenlive to become a 'good' linux video editor, but having more people tackling the problem from all angles is certainly a good thing.  It might be really hard, though.  (See my post elsewhere on this forum entitled "Why is it so hard to code a video editor", which nobody seems to have an answer for ... :)  

Perhaps THAT could be a research project.  Not even necessarily WRITING a solid video editing application, but figuring out why that it seems to be so hard to do.  (My benchmark for "solid" is really low, like where Premiere was in 1998).  There's obviously something that makes it inherently thorny; the kdenlive team had to spend years coding an underlying media-handling framework, which itself relies on years of work on ffmpeg; cinelerra is some kind of mysterious promethean entity; etc.  

To me the reason why this is actually really relevant has to do with a kind of parallel between democratized access to media production and distribution and Free Software.  

Here's another way you could think about this, if you want to make a standalone app from scratch that's not too immense:

Music composition software like LMMS or FruityLoops are a certain "way" of creating music.  Traditional score-writing software is another way.  There are other approaches too, ranging from CSound to Pure Data.  What about other ways, or paradigms, for making music?  For example, the ReactAble project, or the game ElektroPlankton on the Nintendo DS.  Much simpler and less featureful than something like LMMS, but a whole new way of approaching music making.

---

### Post by sgx on 2009-02-13
> **spadewarrior said:**
> Hi sxg,

I'm afraid I won't be able to do that; it has to be Linux only. I don't have an installation of Windows and I'm more interested in making more things for Linux.
Just work on the linux version, then. It still needs a modern gui kit to fit in with future distros. It still needs revamped load-save abilities. It still needs to send/receive midi cc control info properly.

But  class project requirements aside, to isolate linux, and its open-source code, is a dagger in the heart of any future linux support from the companies that actually make useful products. This  will also guarantee a revolving door of unsatisfied noobies, who tried linux, but failed to find usability that was not either months or years behind the mainstream, or solidly bound to arcane kernel modules and svs compilations
with only sad-cousin drivers from nvidia to 'boast' about. The future is what we make it.
Cheers:)

---

### Post by XVampireX on 2009-02-13
How about getting support for some sample based vsti on linux? I am talking about supporting, for example, something like the huge kontakt library format, it would add QUITE a bit to musicians using Linux and not wanting to run something like dssi-vst/fst

---

### Post by simtaalo on 2009-02-14
> **spadewarrior said:**
> This one?

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/) 

Looks interesting.

yup that one. its a great project, only thing i really use for making music on linux. there's many different things that need to be done on the program although the wave editor thing came up as a major section. you could either join the developers mailing list or come hang out in the irc room at freenode ##lmms

would be really good to have you on board.

---

### Post by spadewarrior on 2009-02-14
Cool, I'm very interested in lmms. If I do not eventually choose to do my project on it, I will almost certainly contribute to it in the future.

First, I've got to work out how to use it... :)

---

### Post by neu2buntu on 2009-02-14
this is a big project you are taking on... i take it code is your second language(god i have trouble installing from source most of the time...lol)
   well ardour is under development as we speak ,and i think the developers are working on midi(ye...haaa)   but as posts above have mentioned about "LMMS" it does need a bit of work , and as an "lmms" user i think with a bit of work it ncan be brought up to date with its windows counterparts (flstudio   etc) the latest lmms has been a bit of a memory cruncher for me on my advent k4000 with 2gb mem compared to the 3. something version... hopefully you can help "lmms|"    another project that i think has ben neglected is "rezound"  it is amazing for editing a finished song/tune in linux,but as far as i know the developers have abanded it so maybe this is a project you could take on.it is along the same type of software as audacity,well i would be happy if you could improve both projects,,,,,well any way luck o the irish....:guitar:

---

### Post by neu2buntu on 2009-02-15
heres on for you.... its maybe a tricky 1 ,have you heard of rebirth rb338 for windows, well i have found the linux verion (clone) of it. there was a legal issue at the time around 2002 or so and the developer had to pull it down. but now the windows version is freeware from here [http://www.rebirthmuseum.com/](http://www.rebirthmuseum.com/) (works 100% through wine) 
        so hopefully the linux version does'nt have any more legal issues. it is called "reborn" .it took me ages to find it,but i used a combination of 2 archived search engines to get it.
    here you can get the source (tar.gz) [http://web.archive.org/web/19960101-re_/http://www.ossh.com/reborn/ ]("http://web.archive.org/web/19960101-re_/http://www.ossh.com/reborn/")
of "reborn".      the developer can still be contacted by his email in the README file, so maybe you can take the project off again and get it into the repos. it works great for me on 8.04 and 8.10 and i can get it to play through qjackctl with the "jacklaunch" app. (works 100% on its own)            maybe you could bring it up to date and get it fully functional, i believe that most users would enjoy this program... :guitar: reborn is 2 tb303 synths and 2 drum machines tr808 and tr909

---

### Post by roaldz on 2009-02-15
Maybe its worth to have a look at the Ardour project. The financial support of SAE has been stopped (for now), so the main Ardour developer (Paul) can use some help.
They are working on the 3.0-release which will have (almost) full MIDI support, but they announced  that another 2.x release (probably 2.8 or something) will come in about two weeks, which will have track-based preset options and open source VST support trough the VeSTige header. Nice project, see their website: [www.ardour.org](www.ardour.org).

Roald

---

### Post by Stochastic on 2009-02-15
> **neu2buntu said:**
> so hopefully the linux version does'nt have any more legal issues. it is called "reborn" .it took me ages to find it,but i used a combination of 2 archived search engines to get it.
    here you can get the source (tar.gz) [http://web.archive.org/web/19960101-re_/http://www.ossh.com/reborn/ ]("http://web.archive.org/web/19960101-re_/http://www.ossh.com/reborn/")
of "reborn".      the developer can still be contacted by his email in the README file, so maybe you can take the project off again and get it into the repos.

Well that program isn't open source, so modifying/redistributing the source code would be illegal unless the original author gave written consent.  Furthermore, just because a program is freeware, doesn't mean any knockoffs are legally acceptable - the problems that plagued that program before would still plague it today.  A fresh rewrite would probably be simpler - and allow for LV2 support ;)

---

### Post by Reeman on 2009-02-16
How about a really scookum ncurses front end for [ecasound]("http://ecasound.seul.org/ecasound/") with multitrack recording capabilities. That way one could do really effective audio recording without worrying about x11 compatability. I use alsamixer without the Xgui all the time and find it to be the best way to fine control my sound. I really miss the old simple days without having to eyecandy gui the heck out of every interface! I would like be able to use more system resources for sound exclusively and do high definition audio recording without having to put up with all sorts of rediculous desktop deamons messing with timing in the back end!

---

### Post by simtaalo on 2009-02-17
> **spadewarrior said:**
> Cool, I'm very interested in lmms. If I do not eventually choose to do my project on it, I will almost certainly contribute to it in the future.

First, I've got to work out how to use it... :)

if you need help gimme a shout, also come to our irc room on freenode ##lmms

---

### Post by kayosiii on 2009-02-19
Two suggestions -- first a manager for sound loops and samples along the lines of what digikam is for photos... Should do some sort of visual processing of file for easy reconising (maybe a combination of the wheel look from freewheeling and moodbar from the old amarok)... Should allow you to tag your samples and search through them.... As well as insert them into different other programs.

Second suggestion is this [http://boodler.org/doc/](http://boodler.org/doc/) is a really cool but would be cooler with some sort of graphical interface...

---

### Post by simtaalo on 2009-02-22
suggestions at things you could do on lmms
[http://lmms.sourceforge.net/wiki/index.php?title=Roadmap](http://lmms.sourceforge.net/wiki/index.php?title=Roadmap)

although its just become apparent that the vst host in lmms only accepts .dll and .exe, it doesn't actually accept native .so linux vsti yet, personally i think that would be a great project to undertake.

---

