---
title: "Help a Music Producer switch to Ubuntu - I'm ready!"
date: 2009-04-08
forum: Ubuntu Studio
---

### Post by aXXo on 2009-04-08
Hello Ubuntu Forums,


This is a first post from someone with no prior knowledge of Linux or Ubuntu operating systems so brace yourselves ;)

I am a music producer currently in the process of backing up my data to re-install an OS on a fresh PC setup.
My specs are pretty old, but I have a little M-audio Delta Audiophile soundcard which makes the system workable.
Having used XP for years I have become aware of its failings and limitations. I have also read up on Vista and Windows 7, and the majority of feedback I'm getting is that they're a big step backwards for Microsoft.

I have heard good things about Ubuntu:
-That it's solid and less prone to malware and viruses.
-That it's streamlined and performs better that windows in many instances eg. simple copy-paste functions.
-That it's settings are more ergonomic and easily accessed.

Once I discovered that a multimedia specific distro called "Ubuntu Studio" existed I became more interested.


Before switching I have a few questions:

1.Software and VSTi compatibility:
I would hope to be able to run: 
Cubase SX 3, 
Ableton Live 7, 
Sony Soundforge 9 
and Reason 4. 
Any chance with these programs or are they only Windows compatible?
I also have quite a few VST instruments, effects and processors. Are some, all or none of these likely to work?
[Would I need to use Wine? or something]

2.mp3 compatibility:
I have heard that Linux doesn't support mp3 files. Is this true and if so is there any way around it?
Are there any other filetypes that it doesn't support?

3.Dual booting:
My main concerns about switching are compatibility issues. Could I avoid these by dual-booting, and how easy is it to set up your machine in this way?
If so which OS out of XP or Ubuntu should I install first, and which second?

4.Ubuntu Studio:
Any other music producers out there?
Is Ubuntu Studio actually the best choice for music producers wanting to use Linux, or are there other distros I should be considering?

5.Have I missed anything?:
Are there any other things I should know before going ahead and stepping into the world of Linux.


A lot of questions I know, but any help with all or any of them would be greatly appreciated. :cool:

Thanks in advance,
Julian

---

### Post by markbuntu on 2009-04-08
Dual boot would be a good way for you to start. you could still be productive while learningat your own pace. It is best to install any windows os first.

mp3 is no problem. Restriced format support is now in the ubuntu-resrticted-extras package.


Ubuntustudio is used by lots of professionals but for a pure production environment 64studio might be better. If you do any live recording or performance then you need the rt kernel which works very well in Hardy 8.04 but is broken in Intrepid 8.10 and will hopefully be working in Jaunty 9.04

vst support is still somewhat of a work in progress but many vst's work with lmms and in ardour with dsst. progress continues.

At the bottom of this post there are a bunch of links to info on setting up ubuntu studio and jack and ardour, rosegarden, hydrogen etc. You should look into them so you have an idea of what you are getting into and what ubuntustudio can do for you.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by sgx on 2009-04-09
Hi, your maudio soundcard will work with linux, and Reaper running under
wine/wineasio is the best 'mostly working' vst host at the present, followed by energyXT (windows version), and Cantabile 1.2. The hosts you
mention won't be reliable, so as mentioned, you can dualboot, or set up an extra computer for testing, while keeping  xp intact. Expect 20-30 hours of reading, and a dozen or so forum posts, and a notebook is essential, as there are a few dozen crucial settings and situations to consider. When you up and running, you'll soon find it is worth the trip. Reaper forum has discussions with linux details too, as does the energyXT forum. Using zynaddsubfx synth (16 part multi-timbral) with Rakarrack (10 fx in one app) in itself, makes  all the learning worthwile, the duo is
an awesome sound-design setup.
Cheers

---

### Post by simtaalo on 2009-04-09
you won't be able to run cubase or ableton or reason. no versions of this for linux.

what type of producer are you? traditional multitrack recording+arranging or electronic music?

if your the first i recommend ardour, if your the second i recommend lmms. ardour supports vst effects but not vsti, lmms can use both. although some won't work, but most will.

mp3 will work, you just have to install the codecs, goto the multimedia+video section for guides to this.

ubuntu studio is just ubuntu with some extra packages and the realtime kernel, if you use intrepid don't use the RT kernel as there are problems, but its fine with hardy. the best distro to use for production is the one you know the best, if your new i'd pick ubuntu just because there's so much info out there to help.

many people talk about the best distro for production, but its pointless really, cos its more about knowing your system well enough to keep it running smoothly rather than having the "best" distro.

if you wanna dual-boot i'd recommend using the linux mint which is ubuntu plus codecs n some other stuff, but the cd has the function that if you load it in windows it gives you the option to setup a dual-boot automatically.

---

### Post by kayosiii on 2009-04-09
1) the programs you mention do not run natively on Linux... If you have money invested in these programs and want to continue using them you are probably going to want to keep windows around but you can try looking up those programs in the wine app database.... If you can see value in using open source software then Ubuntu might make an interesting Addition. 

The closest thing to SoundForge that runs natively is Audacity - this may or may not meet your requirements but you can check that one out on windows.

There isn't really a replacement for Ableton Live... Ardour is probably what most people use instead of Cubase (though it probably thinks more like protools)... It is actually one of the biggest reasons for doing Audio on Linux in my books - It currently doesn't do midi... but support for that is coming soon.

Most Native Linux Audio Applications Connect together in the manner that Reason does so you will be looking for replacements of individual components rather than the package as a whole. [http://apps.linuxaudio.org](http://apps.linuxaudio.org) is probably the most comprehensive list of Audio software on Linux.

2) Most Linux Distributions don't ship with MP3 support by default for legal reasons (the owners of the mp3 patent require either a large one off fee (something in the ballpark of 40,000 dollars) or a small fee (in the ballpark of 80 cents) per copy of the software shipped which means that Canonical would have to pay for every copy of ubuntu they gave away... With Ubuntu Mp3 support can be added easily but it just doesn't ship that way.

3) Dual Booting is quite easy you will loose some hard-drive space... (Linux has it's own file-system which it needs for doing it's thing) It can read and write both NTFS and FAT drives.

4) UbuntuStudio is probably a little less specialised than most specifically for Audio distros. It's tends to be more bleeding edge/up to date than those too. It's not a bad place to start but there are other options as well. 64studio is one that comes off the top of my head.

5) Getting Audio set up in the first place on Ubuntu can be a bit of a choir(especially jack) the Studio tools do make this a bit easier.

---

### Post by aXXo on 2009-04-09
Firstly thanks people for your responses.


The general feel from your messages is that I should keep my XP running and dual boot to get a feel for Linux.
Also a couple of you mentioned 64studio as a worthy rival to Ubuntu Studio. I think something that has put me off Linux in the past is the sheer range of choice when it comes to distros, but until I try a few I'm not going to get anywhere with it.
 
-Once you have two [or more] OSs on your hard drive though, how do you choose the OS you're booting from? 
Or do you always have to boot in XP, and then switch to Ubuntu/Linux Mint/64Studio or whatever distro I choose afterwards?


@markbuntu:
Thanks for being first out the block to answer a noob post. No-one likes a never-ending list of questions do they.
The link you provided is real helpful in showing some of the troubleshooting i may come up against.
I'd be happy using the Hardy 8.04 version so long as it's solid.
What is dsst?

[edit: Now coming back to your post having read through the rest, I realise you were also talking about Imms and Ardour.-I guess seeing as most of you mentioned them they must be some of the better Apps out there] 


@sgx:
I've had a little look at the VST hosts you mentioned. I think I've heard of energyXT before, but it was the screens of Reaper that impressed me. 
[http://www.reaper.fm/feat-ss.php]("http://www.reaper.fm/feat-ss.php")
It looks quite nice actually, and kind of reminds me of a few different sequencers I've used. As we all know though, the interface is only half the battle. The audio engine itself is what I look for most in a sequencer. 
[eg. Apple Logic I don't get on with using, but their audio engine is second to none.
Propellerhead Reason has some nice "hardware feel" features, and some of the instruments are quite well constructed. The output however sounds like a cat slowly sliding down a wet blackboard]

That's good that my soundcard is supported. Will it use the same drivers? 

That zynaddsubfx synth and Rakarrack also sound interesting. 


@simtaalo:
I am for the most part an electronic music producer. 
I do occasionally record audio as well, generally vocals or solo instruments. 
You won't find me micing up a full drum kit to record, but my arrangements do tend to end up with mutiple tracks of bounced audio once I've settled on my MIDI parts. 
Of course when using applications like Live, you can throw audio at it so quickly, you end up with multiple tracks of audio in a matter of minutes.

On that note, if there are any Ableton Live users out there, have you found any similar sequencers that Linux supports?

Imms looks good!

If Linux Mint does some of the work of the dual-boot for you, then maybe I should start there.


@kayosiii:
Having written this, I kind of realise I was asking a bit much for all my Apps to work on Ubuntu. I do definitely see the value of exploring something new, and open-source software can often be functional and non-bloaty.
Audacity is actually a sound piece of kit, and i know some people who favour it over Soundforge, so that's good news it works natively

So Ardour is like your Protools eh -that's kind of what simtaalo was saying too No MIDI or VSTi function, but kickass sound quality.
Maybe Ardour would be worth exploring if only for "mastering " my finished work, or once all audio had been bounced to WAVs.
-incidentally you guys are using WAV right?

Thanks for the [http://apps.linuxaudio.org]("http://apps.linuxaudio.org") link. Looks like a useful resource.

---

### Post by simtaalo on 2009-04-09
unfortunately there is nothing like ableton on linux. its just too special, lets be honest theres nothing else in the windows/mac/proprietary world that comes close to ableton. there's an extraordinary amount of work/thought/imagination that has gone into making such an powerful yet intuituve DAW, hats off to them. its the only thing that i'd slightly consider going back to a proprietary o/s for, but i'm trying to find ways not to do that!!!

i would recommend you using lmms, and using audacity/ardour for recording in then importing that into lmms. 

reaper is good, but again its proprietary as is energy XT. although energy XT doesn't have anything that would make me choose it over lmms, reaper though is a very good DAW with some very good functionality, they are a bit of a cop out though by saying they officially support wine as a platform, seems like a get out clause to not support linux properly.

wav is supported yes, don't worry bout that :) and yes ardour is like pro-tools. also zynSubAddFx is part of the lmms-extras package and works inside lmms, and has been routed into the main package for next release.

linux mint will do all the work for you in setting up the dual-boot, i'd recommend it for your first foray into the world of linux.

---

### Post by thorgal on 2009-04-09
> **aXXo said:**
> Hello Ubuntu Forums,
1.Software and VSTi compatibility:
I would hope to be able to run: 
Cubase SX 3, 
Ableton Live 7, 
Sony Soundforge 9 
and Reason 4. 
Any chance with these programs or are they only Windows compatible?


Hey aXXo (nothing to do with the BT guy by the way ? ;) )

mmmm, I will be a bit more straight: if you need these programs, then I'm afraid you're not "ready" for linux. However, you can learn to do _without_ these programs and be not only ready but simply a linux user. What are your production needs exactly (not in terms of software brand but functionality) ?

---

### Post by simtaalo on 2009-04-09
> **thorgal said:**
> Hey aXXo (nothing to do with the BT guy by the way ? ;) )

lol i was thinking that too

---

### Post by Obradowic on 2009-04-09
Im music producer, Windows user too, looking for a better OS, to do music production...I have a few questions, 
-do I have to formate my hard disk or make partitions to install Ubuntustudio??
-is there an emulation software that could run Cubase, Nuendo or some other programs made for Windows??

Im new to Linux,Ubuntu,Fedora...I dont make much difference...If I install Ubuntustudio, it would be my first time to operate on Ubuntu based system...

Best Regards!

---

### Post by Stochastic on 2009-04-09
For those who are BRAND NEW to linux it might be an easier install process (that is if you want to dual boot XP or OSX) to install Ubuntu (the regular version) then install the extra Ubuntu Studio packages ontop.
Further instructions can be found here: [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)
and here: [https://help.ubuntu.com/community#Switching%20From%20Another%20Operating%20System](https://help.ubuntu.com/community#Switching%20From%20Another%20Operating%20System)

This process allows you to use the graphical installer, or even wubi (though I've never tested that) which is very easy to use from within XP.


As for your audio production software you're used to, you'll find some of it able to run in WINE (take a read through [http://appdb.winehq.org/](http://appdb.winehq.org/) for your specific application version), but in general I find it much easier and more flexible to just use the native software that comes with Ubuntu Studio.

It will take you some time to learn all the software here (and learn which ones to avoid - after all it's free software, it's not ALL perfect).

To the OP, if you're interested in producing electronic music on Ubuntu, I'd highly recommend purchasing (or at least trying) a copy of Renoise.  It's the best tracker I've ever tried - there are free trackers available, but renoise is quite nice.  You'll probably also quite enjoy Hydrogen the drum machine (you can even try it out on windows first).

---

### Post by sgx on 2009-04-09
> **Stochastic said:**
> For those who are BRAND NEW to linux it might be an easier install process (that is if you want to dual boot XP or OSX) to install Ubuntu (the regular version) then install the extra Ubuntu Studio packages ontop.
Further instructions can be found here: [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)
and here: [https://help.ubuntu.com/community#Switching%20From%20Another%20Operating%20System](https://help.ubuntu.com/community#Switching%20From%20Another%20Operating%20System)

This process allows you to use the graphical installer, or even wubi (though I've never tested that) which is very easy to use from within XP.


As for your audio production software you're used to, you'll find some of it able to run in WINE (take a read through [http://appdb.winehq.org/](http://appdb.winehq.org/) for your specific application version), but in general I find it much easier and more flexible to just use the native software that comes with Ubuntu Studio.

It will take you some time to learn all the software here (and learn which ones to avoid - after all it's free software, it's not ALL perfect).

To the OP, if you're interested in producing electronic music on Ubuntu, I'd highly recommend purchasing (or at least trying) a copy of Renoise.  It's the best tracker I've ever tried - there are free trackers available, but renoise is quite nice.  You'll probably also quite enjoy Hydrogen the drum machine (you can even try it out on windows first).

Hi, I installed a Ubuntu using wubi, I was skeptical, but happily, it worked exactly like a windows installer, and also uninstalled, leaving xp
in working order, all with just a few mouseclicks, no formatting, no partitiions, just a nice new choice of OS when I rebooted.

@ aXXo once a linux is installed, the lsmod command lists kernel modules that are present, snd_ice1712 is the module supporting maudio cards, and a mixer called envy24control is available to set your various i/o options. You won't need to faff about with a driver, like in some ancient old operating systems. The bulk of what you learn about linux will apply to all versions, and the 'wubi' installer is a great way to enjoy a testdrive, without a large investment of time up front. It works. 

Cheers

---

### Post by kayosiii on 2009-04-10
Some other small things to note...
It is easier to get support for windows based VSTs using the 32bit version of Ubuntu rather than the 64bit version.

For mastering there is a plugin/Application called Jamin.

---

### Post by bolex100 on 2009-04-10
> mmmm, I will be a bit more straight: if you need these programs, then I'm afraid you're not "ready" for linux. However, you can learn to do _without_ these programs and be not only ready but simply a linux user.

Actually I will be *more *straight.  Ardour and Audacity just about work but Cubase and Soundforge are way better.  You will no doubt have read threads about "software should be free" on other forums.  Well, this is as good as it gets when you don't pay.

I know I will get flamed for saying that but there is a difference between a Linux user who wants to use a music toy, and a producer who wants to use a different platform.  Windows apts were written full-time by teams of people.  Windows, for all its faults is an enveloping environment which connects things automatically. You don't even think about it.  Linux has enthusiasm.  With linux I get the feeling that you need to configure everything - which means that you do need to understand it.

I think it will be worth installing Ubuntu and learning to use it. Its a lot more stable so it won't go crazy or just quit like windows.  Just don't expect it to *replace* what you have.

BTW:- I don't think that anyone mentioned Jack (its in my program list as "jack control").  Jack is a software connection program which links the audio engine of some audio software to your sound card.  Ardour *needs* it. I tried Audacity with it this week and it didn't work (it probably will when I figure it out).

BTW2:- Don't install Ardour from Ubuntustudio.  They broke it.  Install it from [www.Ardour.org](www.Ardour.org)

---

### Post by simtaalo on 2009-04-10
> **Stochastic said:**
> 
To the OP, if you're interested in producing electronic music on Ubuntu, I'd highly recommend purchasing (or at least trying) a copy of Renoise.  It's the best tracker I've ever tried -

pity its proprietary

[quote=kayosiii]It is easier to get support for windows based VSTs using the 32bit version of Ubuntu rather than the 64bit version.[/quote]

doesn't make a difference if you run lmms, but for some reason even though ardour now use the vestige header from lmms they can't deal with using vst on 64-bit. seems to be a whole load of fuss over nothing.

---

### Post by Stochastic on 2009-04-10
> **bolex100 said:**
> Actually I will be *more *straight.  Ardour and Audacity just about work but Cubase and Soundforge are way better.  You will no doubt have read threads about "software should be free" on other forums.  Well, this is as good as it gets when you don't pay.

I'll try not to flame too much because you're entitled to your opinion, however I greatly disagree with your statements.  Ardour's sound quality is through the roof when compared to Cubase, it's flexibility is amazing, and it gives me the ability to do surround mixing.  Its integration with Jack alone is more flexibility than Cubase could ever dream to offer.

I won't stand up for Audacity - if you still think that's the best audio editor for linux you need to do some more research.

> **bolex100 said:**
> BTW2:- Don't install Ardour from Ubuntustudio.  They broke it.  Install it from [www.Ardour.org](www.Ardour.org)
Um, can you clarify this? Are you running Ardour in 8.10? That's the only Ubuntu Studio version I know of with major bugs, and since there's no RT kernel in 8.10 it's understandable that you think linux audio is as poor as you make it out to be.

---

### Post by bolex100 on 2009-04-10
Carry on disagreeing if you wish.  Please note that I am still here and still trying to make it work.  

The Audacity comment would be more useful is you would share the answer with the rest of the class.

---

### Post by simtaalo on 2009-04-10
people did mention jack and jack offers options that i'm sure alot of producers on windows/mac will have wished for at one time or another.

theres no doubt cubase is a very good DAW, i don't think anyone is disputing that but saying audio apps on linux are just toys and that you can't create quality music from them is rubbish.

---

### Post by rony0303 on 2009-04-10
2) Most Linux Distributions don't ship with MP3 support by default for legal reasons (the owners of the mp3 patent require either a large one off fee (something in the ballpark of 40,000 dollars) or a small fee (in the ballpark of 80 cents) per copy of the software shipped which means that Canonical would have to pay for every copy of ubuntu they gave away... With Ubuntu Mp3 support can be added easily but it just doesn't ship that way.

---

### Post by jimbosheep on 2009-04-10
you can run "cubase sx2" in "wine" (a program that lets ypu run some windows programs in linux) but not cubase sx 3 or 4 

"audiomulch" runs perfect in wine, as well

there are music production programs like "rosegarden" that are made for linux and have a very silar GUI to cubase, i think that it has support for VST but i am not sure, as i am also a music producer, and i find the best thing is to run "windows xp" in a virtual machine (like "virtual box") and just use it for cubase

---

### Post by thorgal on 2009-04-10
now come on guys, why does this have to drift again toward this nonsensical BS, i.e. winXp vs linux, open-source vs proprietary ? 

just use the tools you like to use and are good at using for your own production. Share tips if you have some. That's all. Personally, I don't use windows, never had, never will. I don't give a crap. So I use the linux "toys" and I derive the music I want thanks to them. So I personally don't call them toys but tools. If someone has a different view, fine with me, make yourself happy by using other tools.

but this is off-topic. The OP wished he used apps that are windows compatible in linux as well, and he said he was "linux ready". I think he's not by this very statement. But if he's curious, he could try out what linux has to offer. Then, he can decide whether the experiment is worth continuing or not. But being used to windows, one can only come with certain expectations. It takes time to learn a "new language".

---

### Post by Stochastic on 2009-04-10
Well said thorgal.

---

### Post by simtaalo on 2009-04-10
> **rony0303 said:**
> 2) Most Linux Distributions don't ship with MP3 support by default for legal reasons (the owners of the mp3 patent require either a large one off fee (something in the ballpark of 40,000 dollars) or a small fee (in the ballpark of 80 cents) per copy of the software shipped which means that Canonical would have to pay for every copy of ubuntu they gave away... With Ubuntu Mp3 support can be added easily but it just doesn't ship that way.

with every distro that doesn't ship mp3 support it can be added easily. i don't see what your point is other than mp3 isn't preloaded.

is it really that much effort to install it?

---

### Post by bolex100 on 2009-04-11
simtaalo,
Some people just love to find a argument.
> there is a difference between a Linux user who wants to use a music toy, and a producer who wants to use a different platform. Windows apps were written full-time by teams of people. Windows, for all its faults is an enveloping environment which connects things automatically
Read this again until you get it.  I am not saying that Linux music apps are toys or that it is not possible to use a linux app to make music.  What Is wrote is that that is a difference between the different types of user.  **USER** get it?

Producers want to USE things.  Connections are an inconvenience.  only a means to an end.
Linux users want to involve themselves in linux, and take their joy in that.  While it may be possible for an experienced linux user to start a music project, a producer has as much interest in apt-get install *stuff_you_never_even_considered*, as the average brilliant guitarist needs/wants to know the difference between a JFET and a bipolar.  Its just not their focus.  

I have no doubt that it can be made to work eventually.  However, my first installation of Cubs**is** was producing usable music in a couple of hours on WIN98.  I've had Ubuntu on a machine since Oct 08 and made nothing.

I understand that the approach might be confusing - even insulting to you.  I'm sorry for that pain. You and other experienced users could help by writing manuals and guiding new music users. 

Lets get back to helping the poster to make the right choices and install stuff that works.  If you have a "shopping list" of a disto and versions of applications that work together, that would be a great start.

---

### Post by kayosiii on 2009-04-12
> **simtaalo said:**
>  doesn't make a difference if you run lmms, but for some reason even though ardour now use the vestige header from lmms they can't deal with using vst on 64-bit. seems to be a whole load of fuss over nothing.

I will take another look at lmms when I can get it to stop hard locking my computer when attempting to start up with jack.... *sigh*

---

### Post by simtaalo on 2009-04-13
> **bolex100 said:**
> 
I have no doubt that it can be made to work eventually.  However, my first installation of Cubs**is** was producing usable music in a couple of hours on WIN98.  I've had Ubuntu on a machine since Oct 08 and made nothing.

i installed cubase when i used to run windows and never managed to make anything on it, read the same for logic, reason etc... i never managed to make any music with programs on windows, yes that was probably cos i didn't have a clue, but making out cubase is easy to pick up and play isn't true.

with lmms i did the little "first song with lmms" tutorial and within an hour i was making music.

i am not an expert, i am not an experienced music producer i do however have a massive interest in this area.

for me i did have difficulty with all the jack stuff, and only recently got it to work, BUT with lmms i don't use jack. 

when i first installed the latest ver at the time (0.4.2) it recognised my on-board soundcard straightaway through alsa without any configuring and i was away just making music, no setting up, no configuring or anything like that.

there are alot of guides to making jack work, if people took the time to go through the guides that people post links to then probably wouldn't have as much difficulty getting them to work.

---

### Post by B4RR13N705 on 2009-04-13
Hi, im a music producer too, i have a studio running with ubuntu and it works really nice! I used ubuntustudio for a while but i preferu ubuntu!
The softwares that you like to use have free alternatives!  
Good luck!

---

### Post by bolex100 on 2009-04-13
> I used ubuntustudio for a while but i prefer ubuntu! I thought that ubuntostudio was the same as Ubuntu except that it has all of the applications bundled with it.
Should I rebuild my system?  Is there a gain?

---

### Post by Stochastic on 2009-04-13
> **bolex100 said:**
> I thought that ubuntostudio was the same as Ubuntu except that it has all of the applications bundled with it.
Should I rebuild my system?  Is there a gain?

Your thoughts are correct - almost.  Ubuntu Studio doesn't come with all the regular Ubuntu software pre-installed, it comes with a much smaller number of items initially.  There really is no benefit/loss to either method, just less junk initially installed from Ubuntu Studio.

---

### Post by ken78724 on 2011-03-14
Thanks aXXo for your questions. Studying your Qs & their As, I benefited as I revisit dual booting XP after 6 years starting w/Hardy ubustu & staying thru kxstudio 10.04.02. Why? Can't find well built linux graphics for producing video & photo combos studded w/text. 

Again, thanks for the lively discussion! Will continue looking for the graphic' counterpart.
Kenneth :popcorn:

---

