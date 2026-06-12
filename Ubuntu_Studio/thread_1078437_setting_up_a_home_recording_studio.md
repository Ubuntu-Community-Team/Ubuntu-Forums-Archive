---
title: "setting up a home recording studio"
date: 2009-02-23
forum: Ubuntu Studio
---

### Post by jitup on 2009-02-23
hello, I am new to linux and I am looking for someone to give me some pointers as far as software goes
I am now running intrepid, my DAW is ardour 2.7.1, is there a newer version? Is there a vst wrapper avalible (I have a nice collection of free vsts I have been building for the last 3 years) If not, can anybody suggest the best of the best in
reverb, flanger, phaser, chourus, delay, tape delay, EQ, gater and any thing else that realy sticks out in what ever format it is that ardour recognizes? what about vsti's? can I run those?
LMMS supports vsti's right? if so is there any way I could use jack or something else to "connect" LMMS to ardour, like I would reasons using rewire into cubase? I was looking at ubuntu studio, but it appears to be out dated, so I thought I would make my own studio set up and then take a snap shot to post for any one who is interested. I was also interested in A/V linux, but that runs on ubuntu 7.10, which ends in april. please help me!

Thank you

---

### Post by Reeman on 2009-02-23
> **jitup said:**
> hello, I am new to linux and I am looking for someone to give me some pointers as far as software goes
I am now running intrepid, my DAW is ardour 2.7.1, is there a newer version? Is there a vst wrapper avalible (I have a nice collection of free vsts I have been building for the last 3 years) If not, can anybody suggest the best of the best in
reverb, flanger, phaser, chourus, delay, tape delay, EQ, gater and any thing else that realy sticks out in what ever format it is that ardour recognizes? what about vsti's? can I run those?
LMMS supports vsti's right? if so is there any way I could use jack or something else to "connect" LMMS to ardour, like I would reasons using rewire into cubase? I was looking at ubuntu studio, but it appears to be out dated, so I thought I would make my own studio set up and then take a snap shot to post for any one who is interested. I was also interested in A/V linux, but that runs on ubuntu 7.10, which ends in april. please help me!

Thank you
Wait a while on Ubuntu Studio no stable realtime kernel yet the one that they have in repo works but borks on proprietary video and acpi (bad shutdown and reboot) atleast on newer amd64x2. 

I have given up trying to compile a kernel with the 2.6.28 releases from the kernel archives. The debian/Ubuntu hacked kpkg compile is stopping because the patches do not put a realtime XEN directory under arch and I have no idea how to work around this pile of barf.   There are compile issues and lots of fudge. I am waiting. 

I will try to see if this problem happens to the nerds that run pure Debian when they try to compile with the rt patches or if this is an Ubuntu only situation. 

I think I will go back to Blue White and see if I can compile one there...the Slackware compile is so much easier and does not rely on kernel packaging software at all, though you can pack it up if it is any good! I have had really good results when I was using Zenwalk for audio, but that was with a realtime simple 32bit only system.


The other choice is to wait for the next release of 64Studio which is going to happen soon. They have a working realtime X86-64 2.6.28 that does not barf on proprietary drivers which will be the kernel for their next release...They still use a real xorg.conf file so you can always stop the defective modules and easily go back to vesa if necessary with the xorg.conf.bak

VSTs will be problematic (as ever) with linux....they can work but there are some mods of freeverb that are OK but they are only usefull for post and are almost impossible to use any other way. 

If I do any reverb or chorus I do it outside the pc and with good add on boxes. Suprising what you can do with some of the cheap $150-200 pedals!
Not as good as a German Plate but not bad hall sounds at all. For home recording I would not recomend any of the post effects available for Linux. Good mics and gear (especially cables) come first. Mackie or Yamaha mixers and reasonably good mics come first. It comes down to GIGO as always.

Ardour however has come one heck of a long way and can do much of what would cost atleast $500 in software for the PC and perhaps $1000 bucks for the "$MAC$".

---

### Post by thorgal on 2009-02-24
hey Reeman,

I guess I can identify as a pure "debian nerd" since my DAW is running debian sid :lol:

Anyway, I have been toying with 2.6.28 from the RT git tree. I have been describing some of my observations here: 
[http://linuxmusicians.com/viewtopic.php?f=27&t=821&st=0&sk=t&sd=a#p3829](http://linuxmusicians.com/viewtopic.php?f=27&t=821&st=0&sk=t&sd=a#p3829)

I am still using 2.6.24-RT for production though.

---

### Post by cb951303 on 2009-02-24
You can't use your windows or mac vst/vsti in linux (unfortunately :/)
But we have a plugin type of our own, [http://www.ladspa.org/](http://www.ladspa.org/) (it's superseded by LV2 but there are still more plugins for ladspa)

Ladspa website can redirect you to the plugins you want.

---

### Post by thorgal on 2009-02-24
@cb951303: wrong.

I use win32 VSTi's in my debian based DAW :)
You have a few VST hosts:

dssi-vst which is based on the DSSI plugin architecture

fst : it is now using the vestige header file (reverse engineering of the steinberg SDK). 

For example, ardour will now be packaged with the FST code so it can be distributed with VST capability without the legal issue with Steinberg.

The upcoming 2.x release will have VST support :)


Rosegarden is using DSSI and therefore can use dssi-vst for VSTi's. You can use dssi-vst as a standalone VST host as well. I use it every day with the VSTi Addictive Drums by XLN Audio (excellent piece of sofwtare in my opinion, beats them all for real sounding drumming).

Of course, you need wine to be installed.

---

### Post by cb951303 on 2009-02-24
dssi-vst uses wine to emulate windows vst plugins. All other winvst compatbility applications does.

saying that op can use windows vsts in linux is not right. For example you didn't mention anything about WINE in your post and it's misleading. you might cause someone to invest a lot of money into a studio that he won't be able to use unless dssi-vst decides to work with some particular plugin.

---

### Post by thorgal on 2009-02-24
re-read my post, I did mention wine. 
As a general remark, a binary that was produced on a win32 platform has no chance to run natively on a linux platform (ELF binary). Wine allows that to happen. 

Your statement :
> 
You can't use your windows or mac vst/vsti in linux (unfortunately :/)


is wrong. I DO use win32 VST / VSTi's on my linux DAW thanks to wine and dssi-vst or the latest fst. That contradicts what you are saying. 

What you probably meant is that these VSTi's / VST's do not usually come in the linux binary format. There is some work under development to that effect : see e.g. [http://www.linuxjournal.com/node/1000192](http://www.linuxjournal.com/node/1000192) or google Jost vst host to know more.


by the way, dssi-vst uses wine to interface with the VSTi or VST (win32 part) but dssi-vst has also the linux part which interfaces with DSSI capable apps and of course Jack. dssi-vst can be seen as a hybrid host. So can FST. There's a more win32 oriented host called vsthost.exe or savihost.exe (win32 app running well under wine) but they require wineasio to interface with jack.

---

### Post by cb951303 on 2009-02-24
> **thorgal said:**
> re-read my post, I did mention wine. 
As a general remark, a binary that was produced on a win32 platform has no chance to run natively on a linux platform (ELF binary). Wine allows that to happen. 

Don't get me wrong but saying "install wine" doesn't cut it. You need to explain what it is so that people can decide not according to your personal experiences with an experimental package but for them self.

> 
Your statement :


is wrong. I DO use win32 VST / VSTi's on my linux DAW thanks to wine and dssi-vst or the latest fst. That contradicts what you are saying. 

Let me say it this way. if someone asks you "does linux run windows applications?" what do you answer? VST and VSTis are nothing but desktop applications in a shared library form using the same backend for audio. 

> 
What you probably meant is that these VSTi's / VST's do not usually come in the linux binary format. There is some work under development to that effect : see e.g. [http://www.linuxjournal.com/node/1000192](http://www.linuxjournal.com/node/1000192) or google Jost vst host to know more.

No it isn't. I meant no one should invest money to Windows VSTs (lots of expensive stuff) trusting that they would work 100% with an experimental package like wine. 

@OP: If you want support for linux VSTs, ardour supports it. But you need to recompile to enable that.

---

### Post by thorgal on 2009-02-24
> **cb951303 said:**
> Don't get me wrong but saying "install wine" doesn't cut it. You need to explain what it is so that people can decide not according to your personal experiences with an experimental package but for them self.

don't get me wrong either: when you say "you can't", I say it's no true, you can. Or am I dreaming I do it in my studio ? You ask me to be careful with my wording but you are not accurate when you state things like "you can't run your win VSTi's on linux". 

> **cb951303 said:**
> 
Let me say it this way. if someone asks you "does linux run windows applications?" what do you answer? 

certainly not 'no'. I tell them that it is not impossible and that they should check wine and the wine app DB one can browse at winehq.org

> **cb951303 said:**
> 
VST and VSTis are nothing but desktop applications in a shared library form using the same backend for audio. 
and ? 

> **cb951303 said:**
> 
No one should invest money to Windows VSTs (lots of expensive stuff) trusting that they would work 100% with an experimental package like wine. 

wine is at version 1.1.x not 0.x. It's a sign of not being experimental any longer but useful for something. Moreover, I did invest in some expensive VSTi, they work nicely. Why should you say "no one should invest ..." ? let people experiment what they want! They are not all stupid, they can ask the vendors, consult forums, etc before making a choice. Man, you're being very conservative!

> **cb951303 said:**
> 
@OP: If you want support for linux VSTs, ardour supports it. But you need to recompile to enable that.

I am not aware of ardour supporting native linux VSTs (aka some_vst.so). Can you provide a pointer where this information is clearly stated ?

---

### Post by jitup on 2009-02-24
Ok...............
I am a bit confused now...

so vst's are maybe, but I have to use a wrapper or compile myself, and since I want to run FREE WARE vst's I have nothing to loose if they don't work.

can some one send me a link to 64studio were it is talking about the new release?

I read some where that ardour is updating inn the beginning of march, is this true? jack already installed on my PC if I just installed ardour this morning? does ardour update itself through the update manager, or do I have to do it manually?

How do I install LMMS and is there interconnectivity with ardour using jack?
thank you

---

### Post by thorgal on 2009-02-24
hey jitup, read this post about ardour, written by its author (Paul Davis) :

[http://ardour.org/node/2443](http://ardour.org/node/2443)

as to your confusion, no you're not, considering what you stated, you perfectly understood what it takes to run win32 VSTs in linux. And as you recalled here, VSTs can be freewares as well, there are a bunch out there and experimenting with them is perfectly fine. I simply don't understand cb's statement that it's not possible.

---

### Post by cb951303 on 2009-02-24
> **thorgal said:**
> 
certainly not 'no'. I tell them that it is not impossible and that they should check wine and the wine app DB one can browse at winehq.org

certainly! so why didn't you here?
 
> 
and ? 

wine is at version 1.1.x not 0.x. It's a sign of not being experimental any longer but useful for something. Moreover, I did invest in some expensive VSTi, they work nicely. Why should you say "no one should invest ..." ? let people experiment what they want! They are not all stupid, they can ask the vendors, consult forums, etc before making a choice. Man, you're being very conservative!

and since VSTs are like desktop applications, there is no reason for us to believe that they will work better than any other application with wine. That means, very poor compatibility. Check the platinium and gold list in appdb. How many applications are there? And gold means you may have some quirks to work out. I surely don't want that in my studio.
wine being 1.x means nothing. It's nowhere near complete and there is absolutely no way you can tell if an application will work before buying it. (even appdb users don't agree sometimes, so it may be misleading too)

> 
I am not aware of ardour supporting native linux VSTs (aka some_vst.so). Can you provide a pointer where this information is clearly stated ?
[http://ardour.org/node/280](http://ardour.org/node/280)

---

### Post by thorgal on 2009-02-24
dude, I don't understand you.

You say "you can't use use win32 VSTs in linux", I say you can, and I have proof of it everyday since I use 2 VSTi's compiled for win32 in my linux DAW. Do you understand basic logic rules ? "you can't" is an extremely strong statement, while "you can" does not mean "all is perfect" but that it is possible. And again, I do it every day. I am not saying that All VSTs will work OOB. As to wine, I mentioned wine from the very beginning. Either you're blind or you like ignoring what ppl are saying to you. 

About ardour, I did not ask whether it would support win32 VSTs, which it's been doing for a long time now thanks to the FST wrapper (which requires wine), but native linux VSTs (as in Jost). There's a nuance here, we're not talking DLL's but .so's, i.e. linux binaries. As far as I know, ardour does not support NATIVE linux VSTs but I may be wrong. That's why I asked if you had a pointer to such info.

May I suggest you READ _carefully_ what ppl say before posting ? 

I would also suggest you leave ppl a choice for what they want in their studio. The OP is free to try out the wine dependent VST wrappers that linux has to offer, who are you to say he/she cannot ?

---

### Post by cb951303 on 2009-02-24
> **thorgal said:**
> dude, I don't understand you.

You say "you can't use use win32 VSTs in linux", I say you can, and I have proof of it everyday since I use 2 VSTi's compiled for win32 in my linux DAW. Do you understand basic logic rules ? "you can't" is an extremely strong statement, while "you can" does not mean "all is perfect" but that it is possible. 
You don't want to understand the fact that you running some VST plugins through dssi-vst means NOTHING. That doesn't give you the right to tell people linux runs windows VSTs (that's exactly what you did).

> 
And again, I do it every day. I am not saying that All VSTs will work OOB. As to wine, I mentioned wine from the very beginning. Either you're blind or you like ignoring what ppl are saying to you. 

Well you didn't say it at first. And you only mentioned wine's name. That's only as good as not mentioning at all. 
Save the personal attacks, and learn to explain yourself better before causing someone to pay money to something they won't be able to use.

> 
About ardour, I did not ask whether it would support win32 VSTs, which it's been doing for a long time now thanks to the FST wrapper (which requires wine), but native linux VSTs (as in Jost). There's a nuance here, we're not talking DLL's but .so's, i.e. linux binaries. As far as I know, ardour does not support NATIVE linux VSTs but I may be wrong. That's why I asked if you had a pointer to such info.
and link I provided is for native linux vsts. 

> 
I would also suggest you leave ppl a choice for what they want in their studio. The OP is free to try out the wine dependent VST wrappers that linux has to offer, who are you to say he/she cannot ?
when did I say that?that's you. not me. I'm just being realist. Wine is not good enough to run pro audio software. period. "It may or may not work" is not acceptable in pro work.

---

### Post by angelsguitar on 2009-02-24
> **jitup said:**
> 
can some one send me a link to 64studio were it is talking about the new release?

64 Studio's homepage is [http://www.64studio.com](http://www.64studio.com) . They recently (just a few hour ago) released 64 Studio 3.0 Beta 2. They are using kernel 2.6.29, which provides support for recent hardware, and now they are using Ubuntu Hardy's repos for their base packages.  The kernel and most multimedia packages are compiled  and configured by 64 Studio.  I believe 64 Studio 3.0 will be out soon.

The stable official version, as of today, is 64 Studio 2.1.  It is based on Debian etch, but with their own kernel and multimedia packages.  In my experience and opinion, it's the best distro for audio & MIDI work out there.  I use it for both live and recording work.  Very stable, and lots of audio and MIDI packages.  Highly recommend it.  But if you have newer hardware, you may run into some problems, due to compatibility and the age of the packages (Debian etch is a little dated now; Lenny has just been released)

> jack already installed on my PC if I just installed ardour this morning? does ardour update itself through the update manager, or do I have to do it manually?

The fact that Ardour itself is updated does not mean that you'll get that update automatically.  It depends on the people that package it for your current distro.  If they make an updated package, then it should show on the update manager (or any other software used for managing updates)

Generally, you can just wait until it gets updated in the repos of your current distro (which may or may not happen), or go ahead and compile the latest version yourself.

> How do I install LMMS and is there interconnectivity with ardour using jack?
thank you

LMMS should be in the repos of most distributions.  You can install it by synaptic or using apt-get.

I believe lmms is compatible with jack, so it should be able to connect with Ardour.  However, I don't use lmms myself, so I'm not sure.

---

### Post by thorgal on 2009-02-24
> **cb951303 said:**
> You don't want to understand the fact that you running some VST plugins through dssi-vst means NOTHING.

sure, I sort of figured it meant nothing _to you_, while it means something to me because I use them in my work. Just being curious: what is it supposed to mean _according to you_ ?

> **cb951303 said:**
> 
 That doesn't give you the right to tell people linux runs windows VSTs (that's exactly what you did).

haha, are you saying you're denying me the right to tell people that I run VSTi's on my linux DAW ? :lol: jeeze man! What are you allowing me to say then ?

> **cb951303 said:**
> 
Well you didn't say it at first. And you only mentioned wine's name. That's only as good as not mentioning at all. 

that's even better. What kind of statement is that ?? So, let me understand: I am mentioning something, and that something is like it's not mentioned at all ... we don't live in the same world I think ... 

> **cb951303 said:**
> 
Save the personal attacks, and learn to explain yourself better before causing someone to pay money to something they won't be able to use.

personal attack ? I won't comment too much on that. However, you're the one who came up with the money thing in the first place. If I remember the OP's statement correctly, he mentioned something about freeware. You know, or maybe you don't, that some VSTs are available for free ;) 


> **cb951303 said:**
> 
and link I provided is for native linux vsts. 

nope, you still don't get it. The VST host called FST is still a wrapper around win32 VSTs (DLLs). But it will be compiled against a header file (vestige) that was the result of some reverse engineering, and that vestige header file can now replace the non freely redistributable steinberg SDK. Got it ?

> **cb951303 said:**
> 
when did I say that?that's you. not me. I'm just being realist. Wine is not good enough to run pro audio software. period. "It may or may not work" is not acceptable in pro work.

you have to know what you're thinking:

- first you say "you can't run VSTs in linux"
- then you deny that my running VSTi's on my linux DAW means anything at all (that's a good one, makes me smile each time I think about it).
- then you say "no one should invest money in VSTs" if their studio is linux based
- after that, you continue by defining what's not pro.

... what's next ? why don't you let the whole assembly here enjoy your wisdom in this matter ? I would be glad if you could tell us what we should invest in and what a pro work / studio sounds or looks like. And most of all, if the FST wrapper will be able to run linux native VSTs ... ;)

You can speak up if you want, I think I had my share with you. 

@jitup: if you want to try using VSTs in linux, go ahead, experiment. No one has the right to tell you what's pro and what's not. Do your own things, learn from them, and if you're happy about them, I guess that's good enough (pro or not).

---

### Post by cb951303 on 2009-02-24
I lost interest in trying to make you understand that giving misleading information is bad. Suit yourself.

EDIT: And for what its worth the money thing is not an attack. it's a legit argument. the support you give here isn't just for OP. it's important for future ref too, meaning, you may mislead others too.

I read over and over again your first post. The conclusion is the same. If I didn't know what wine is, you could have easily convinced me that I could run my guitar effect VSTs (which cost me > 1000$ in total) in linux. Which would be absolutely WRONG. But instead, if you had explain that dssi-vst uses wine **which is a an emulator(!) and it's not guaranteed that all VST will work**, people reading your statement might reconsider things before buying.

> **thorgal said:**
> 
nope, you still don't get it. The VST host called FST is still a wrapper around win32 VSTs (DLLs). But it will be compiled against a header file (vestige) that was the result of some reverse engineering, and that vestige header file can now replace the non freely redistributable steinberg SDK. Got it ?


Use your own advice. Read carefully. But this time read your statemnets carefully. You asked me to show a source for Ardour's native linux vst support and I did. Where do you see FST in that link? Ardour supports native linux VSTs.

@OP: Try any VST you want by any means. I don't know how he managed to think that but I never said you what to use or not. That's your choice. But know that, still, if someone comes to me and asks if he/she can use win32 VSTs in linux, I'll say no :) I think it's ethically the better approach comparing to saying that you can run them with dssi-vst without explaining the details.

---

### Post by thorgal on 2009-02-24
argh! I have to reply to that:

> **cb951303 said:**
> I lost interest in trying to make you understand that giving misleading information is bad. Suit yourself.

thanks, I will (suit myself). I don't think we use the same semantic.
 
> **cb951303 said:**
> 
EDIT: And for what its worth the money thing is not an attack. it's a legit argument. the support you give here isn't just for OP. it's important for future ref too, meaning, you may mislead others too.

I don't mislead anyone, if there's some misleading here, it is from you. I CAN run VSTs on my linux DAW, period. I do it every day. When you say you CAN'T, this is contrary to physical evidence that I observe every day. So who is misleading here ? And this is a forum, not a tech support that I am paid to provide in the most accurate way, so I say whatever. Capice ?

> **cb951303 said:**
> 
I read over and over again your first post. The conclusion is the same. If I didn't know what wine is, you could have easily convinced me that I could run my guitar effect VSTs (which cost me > 1000$ in total) in linux.

if you don't know what wine is, you go and look for what it is, or ask someone. 

> **cb951303 said:**
> 
 Which would be absolutely WRONG. But instead, if you had explain that dssi-vst uses wine **which is a an emulator(!) and it's not guaranteed that all VST will work**, people reading your statement might reconsider things before buying.

But instead, you could just mention it  like this:
Dear jitup, thorgal may be lucky enough to successfully run his VSTi's but know that blabla ... instead of all this BS. 
If you thought I was too light in my original post, you could have added this fine statement about wine being an emulator, etc. The rest is useless.

> **cb951303 said:**
> 
Use your own advice. Read carefully. But this time read your statemnets carefully. You asked me to show a source for Ardour's native linux vst support and I did. Where do you see FST in that link? Ardour supports native linux VSTs.


OK, here you should really understand what we are talking about:
first of, this is from the same post about the upcoming ardour 2.x :
> **"Paul Davis"]
[blabla ...] Improvements in VST support come from the work done by Torben Hohn on **FST**. [blabla ...]
[/quote]

second, here is the source code of ardour, regarding VST :
[http://viewcvs.ardour.org/index.cgi/ardour2/ardour2/branches/2.0-ongoing/libs/fst/](http://viewcvs.ardour.org/index.cgi/ardour2/ardour2/branches/2.0-ongoing/libs/fst/)

oh! but what an amazing coincidence, this ardour _fst_ subdirectory is exactly a subset of the original FST git tree:
[quote=FST.git.tree]
thorgal@dlap:~/src/fst$ ls -1
audiomaster.c
COPYING
fpsparser.c
fst.c
fstconfig.c
fst.h
fstinfofile.c
gtk.c
jackvst.h
jfst.c
Makefile
README
vestige/
vsti.c
vstinfo.c
vstwin.c
[/quote]


[QUOTE=cb951303 said:**
> 
@OP: Try any VST you want by any means. I don't know how he managed to think that but I never said you what to use or not.

simply your very first statement, reread yourself carefully ;)

> **cb951303 said:**
> 
 That's your choice. But know that, still, if someone comes to me and asks if he/she can use win32 VSTs in linux, I'll say no :) I think it's ethically the better approach comparing to saying that you can run them with dssi-vst without explaining the details.

ah, it's a question of ethic now ... amazing, we do live in a different world ...

---

### Post by Reeman on 2009-02-24
The user forum at [[COLOR="Blue"]64studio[/COLOR]]("http://www.64studio.com/forum") is where to get the goods on what is happening. 

To answer the vst and vsti thing...the plugins require a windows api so if you try to recompile them they will bork with the gnu gcc unless you wrote a plugin wrapper that had the headers for audio in linux...in short a can of alphaghetti code that would take years to debug. Some vst plugins will work with the wine wrapper but they are crash prone and unreliable at the best of times. Like I said the only decent effects available for linux are post process ones.

I have the feeling that Fedora will beat us all to the punch with a really good working low latency desktop as RedHat is developing some commercial military and monetary processing systems that are designed from the ground up with low latency. 

Don't forget it is RedHat that has led the charge to lowlatency, and the kernel varients tuned for low latency will be available to the Fedora community as RedHat releases them. The difference is RedHat may seem behind the kernel releases but they are more focused on absolute stability.

---

### Post by Sandsound on 2009-02-24
> **jitup said:**
> Ok...............
I am a bit confused now...


This is how I use Win VSTi's :[Win VSTi's on Linux]("http://www.sandgreen.dk/index.php?side=linux_vst")

If you can't find the DSSI-VST in the repros, try the .deb I have on this side :[Misc. files and other stuff]("http://www.sandgreen.dk/index.php?side=diverse_filer")
or you might be able to find a better one if you google dssi-vst.

I have also made a small Python program "ubuntu-audio-tools" that (among other things) allow you to install wineasio, 8.04-realtime-kernel and setting your system up for realtime :[My python programs]("http://www.sandgreen.dk/index.php?side=prog_python")
It's still in a early stage of development, but so far I have tested it on 8.04 and 8.10 without problems.

---

### Post by jitup on 2009-02-25
thank you for your help, but can you please take your personal battle somewhere else? I don't mean sound like an ***, but I thought the ubuntu community was supposed to be the most respectful and curtious linux community? I do appreciate the help, don't get me wrong I do, but I am a little disappointed at the fact that this thread was hijacked for a personal war. also, I was a little surprised, all the other forums on this site where quite different and polite.

also, why would you spend $1000+ for guitar vst's? for that price you could buy some nice hardware (I would go for a real amp over a soft amp any day) . what do you have?

---

### Post by Sandsound on 2009-02-25
The discussion often gets a bit overheated with issues like wine, but I'm glad to see that you're sticking around anyway :-)

As for 1000$ guitar VST's, it might sound crazy, but there are situations where it's justified. Personally I would never use that much money on a guitar VST, specially when there's so many great Linux alternatives like [ELE]("http://www-personal.umich.edu/~mslutsky/elepage/index.html") and [Tapiir]("http://www.iua.upf.es/~mdeboer/projects/tapiir/") (to name a few), but all thou I have a rather decent drum kit, it's not always so smart to be banging along in the middle of the night ;) so I use a VST'i called XLN-Addictive drums (about 300$). An alternative could be to use Hydrogen, but the feel of XLN is a bit more realistic.

---

### Post by Reeman on 2009-02-25
> **jitup said:**
>  
also, why would you spend $1000+ for guitar vst's? for that price you could buy some nice hardware (I would go for a real amp over a soft amp any day) . what do you have?

Personally I record from mics. I am a classical guitarist. Though sometimes I like to play a good nylon electric through my old fender twin, especially live for more modern stuff. 

When I do some recordings of tracks I put down and then add stuff in Rosegarden. I have used some dlls through wineasio to mod the sound before I import it into Rosegarden to add created bumps and thumps. 

I have had no luck with recording directly into Rosegarden with effects on and if I want to do some high def audio I use Ardour cause Rosegarden will only record up to 44,100 cd quality through jack. 

Being a bit of lazy sob though I have not tried recording directly into Rosegarden since the 1.6 releases, and have no idea how much better or whether or not record functions through jack have improved. You still must remember to correctly connect the track through jack and arm it or you will do dead air for sure. 

Just remember that Rosegarden will do a really good job putting midi over an audio file but has some trouble doing things the other way around.

Seems everybody is waiting on Ardour midi...but if you really want music notation to and from midi Rosegarden is the ticket and is getting really good at easily translating a midi file into good quality readable notation. Single line melody and chords to create a usable chart for a tune is as good as any of the commercial stuff like Cakewalk. And the Rosegarden printout is more flexable and of much better quality than even Steinbergs stuff!

---

### Post by jonathonblake on 2009-02-25
> **jitup said:**
> thank you for your help, but can you please take your personal battle somewhere else?


It is not a personal battle.  It is a conflict about libre, and the quality of non-libre applications in a libre environment.

---

### Post by jitup on 2009-02-25
I am sorry about my previous post, but at least the air has cleared now. any ways , I was just curious about what he was running for JUST GUITAR VST'S for $1000. I use amplitude or sometimes the guitar rig 3 demo to get a track down or an idea out, I just wan't sure of any vst for guitar that cost that much. I don't even think m-audio's eleven is that much, and that is the closest to real valve amps I've personally heard in software. I use free vsts and vsti's. If you are always looking, there is some pretty good stuff out there, or I like the beta's of comercial stuff like .99 beta. I have gotten my hads on stuff like that before. I do use some commercial stuff, but it was given to and it is a bit outdated and my free ware collection sounds better.

---

### Post by cb951303 on 2009-02-25
just to be clear (as everyone is curious about my vsts :)) I have guitar rig 3 (with midi pedal), several amplitubes and revalver mkIII, I also have various reverb vsts that I use for post processing.
in my country this setup is much more cheap comparing to a decent tube amp + analog setup. A decent tube amp by it self is approx 1000$ here so...

---

