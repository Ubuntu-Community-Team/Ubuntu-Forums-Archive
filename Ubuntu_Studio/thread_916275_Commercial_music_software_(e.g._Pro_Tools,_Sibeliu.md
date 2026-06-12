---
title: "Commercial music software (e.g. Pro Tools, Sibelius, etc.) on Ubuntu?"
date: 2008-09-10
forum: Ubuntu Studio
---

### Post by Qjimbo on 2008-09-10
Hi,
I'm considering permanently switching from my current Windows XP setup over to Ubuntu Studio for music production. I used Ubuntu Studio earlier this year and was really impressed with the low latency and how it worked pretty much with all my hardware including the midi interface.

Since then I've gone back to XP but I pine for the slick environment Studio provided but I was wondering first what my options are in regards to *commercial* software? I normally use Sibelius and Pro Tools on my PC and was wondering, is it possible to get these working well under Wine? Or perhaps using the Mac version somehow (as that is also *nix?) My main worry is Pro Tools as that requires an M-Audio interface and I don't know if the detection would work.

I use a lot of VST plugins and so on so it'd be really handy for me to have all this stuff in Studio. Is this possible or will I be stuck with free software only?

Many thanks

---

### Post by SunnyRabbiera on 2008-09-10
Eh wine is touch and go, you could try to install your apps under wine but it might not work.
Your options are limited I am afraid, but blame that on the developers of those softwares and not on linux.

---

### Post by Stochastic on 2008-09-10
> **Qjimbo said:**
> ...what my options are in regards to *commercial* software? I normally use Sibelius and Pro Tools on my PC and was wondering, is it possible to get these working well under Wine?

Well there has recently been some inroads into commercial audio development for Linux.  However they're very small inroads.  Both EnergyXT and Renoise have released native versions of their software for Linux.

Wine is the free windows emulator but the only audio application that works well under it is Reaper.  Linux VST support also utilizes wine.  Unfortunately this is all there is for wine (I've heard some versions of Sibelius do work, but maybe not all features, and maybe not the version you own).

There are other windows emulators that are released commercially - I have no idea if audio apps work any better under them.

> **Qjimbo said:**
> Or perhaps using the Mac version somehow (as that is also *nix?)

You'd think this, but unfortunately the graphics systems on Mac are entirely proprietary and therefore these programs are harder to get running than the windows ones.  :(

> **Qjimbo said:**
> My main worry is Pro Tools as that requires an M-Audio interface and I don't know if the detection would work.

I think you mean M-Box (or other equivalent digi soundcard) not M-Audio (that's a different company).  M-Audio products actually work quite well (other than their firewire line) in Linux.  I don't know about Digi soundcards though - the M-Boxes sound bad anyways.

> **Qjimbo said:**
> I use a lot of VST plugins and so on so it'd be really handy for me to have all this stuff in Studio. Is this possible or will I be stuck with free software only?

Many thanks

Luckily, many VST plugins (but not all) will run fine on Linux.  It does take a bit of work to set the support up, but it's not the hardest thing in the world to do.

In the end, for Pro Tools, I'd highly recommend looking into Ardour (it's better than Pro Tools in my opinion - can Pro Tools do 8-channel mixes?).  For a replacement for Sibelius, you'll end up taking a step down in user interface; good notation programs include MuseScore, Denemo, Rosegarden, or my personal favorite (for its flexibility, which also makes it the hardest to learn) is Lilypond (it can do many things that Sibelius simply can't).

In the end, Linux isn't Windows and vice versa.  Switching systems unfortunately still means switching workflows and programs of choice.  This may change in the future as more people become fed up with Windows and learn about the stability and flexibility of Linux - it may not.

You may want to dual-boot for a while to make the transition easier.  As for the first little while in Linux most people don't grasp everything (workflow, programs, etc...) right away so your productivity might slow down if you switch cold turkey.

Welcome to the community!

---

### Post by Qjimbo on 2008-09-11
> **Stochastic said:**
> Well there has recently been some inroads into commercial audio development for Linux.  However they're very small inroads.  Both EnergyXT and Renoise have released native versions of their software for Linux.
Thats interesting, I guess it's a start!

> You'd think this, but unfortunately the graphics systems on Mac are entirely proprietary and therefore these programs are harder to get running than the windows ones.  :(
That is quite surprising, and frustrating considering Mac is now x86 as well. Oh well, nothing we can do I guess.

> I think you mean M-Box (or other equivalent digi soundcard) not M-Audio (that's a different company).  M-Audio products actually work quite well (other than their firewire line) in Linux.  I don't know about Digi soundcards though - the M-Boxes sound bad anyways.
Nah, the latest versions of Pro Tools are "m-powered" and support any M-Audio interface as they are now owned by the same company that owns pro tools.


> Luckily, many VST plugins (but not all) will run fine on Linux.  It does take a bit of work to set the support up, but it's not the hardest thing in the world to do.
That's good to hear, can you point me to any guides on how to set them up?

> In the end, for Pro Tools, I'd highly recommend looking into Ardour (it's better than Pro Tools in my opinion - can Pro Tools do 8-channel mixes?).
Yeah I will have to give it a go.

> For a replacement for Sibelius, you'll end up taking a step down in user interface; good notation programs include MuseScore, Denemo, Rosegarden, or my personal favorite (for its flexibility, which also makes it the hardest to learn) is Lilypond (it can do many things that Sibelius simply can't).
Yeah I gave lilypond a go but it had that kind of free-software feel to it, focussing on functionality rather than usability, so I couldn't get used to it at all! I guess wine will be my only option here.

> In the end, Linux isn't Windows and vice versa.  Switching systems unfortunately still means switching workflows and programs of choice.  This may change in the future as more people become fed up with Windows and learn about the stability and flexibility of Linux - it may not.
The organization and overall robustness of the operating system is definitely what is drawing me. Windows seems to do so much stuff behind the scenes that causes strange lags when using audio after being powered on for a long period of time (presumably due to memory leaks) and I'm fed up with it.

> You may want to dual-boot for a while to make the transition easier.  As for the first little while in Linux most people don't grasp everything (workflow, programs, etc...) right away so your productivity might slow down if you switch cold turkey.
Well I've used linux a fair bit already, just I could never get audio software sorted on it, so I was forced back to Windows. I'm hoping with enough preparation before switching I'll be able to take the plunge.

> Welcome to the community!
Thanks! :D

---

### Post by renesisspeed on 2008-09-11
It may not be exactly whay you are looking for, but i'm suprised no one mentioned LMMS (Linux Multimedia Studio).
It supports VST plugins & "LADSPA". It uses Wine en-route to use these plugins, but the program its' self does not depend on it.

[http://lmms.sourceforge.net/home.php](http://lmms.sourceforge.net/home.php)

I've been using it for about 6 months now & love it, I would highly recommend it!!! 
-------------------------------------------------------
Just as a fair warning I have had some problems with it not running so well on certain systems. 
For example no way in he11 it would run on my laptop (presario 6030us AMD Turion 64 w/ PCLos) (which is really a shame). It would crash immediately, before even addressing the typical linux/laptop audio problems.
 
I also had problems with one desktop (AMD Athlon 64 [don't remember the mobo or chipset] w/ UbuntuStudio x64). Despite far superior processing power, the CPU would spike very easily, causing a freeze, extereme lag or crash. & the program would sometimes crash for no apparent reason anyway.

The only reason I mention any of the specs on these, is that there seems to maybe be a trend of incompatibility.

Computers that I have had few to no problems on are: 

intel core 2 duo w/ intel board w/ Ubuntu Studio x86 (actually built using a Shuttle xpc barebone) <-- This actually is the best system i've had for running LMMS.

intel P4 w/ MSI mobo w/ Ubuntu Studio x86 Ubuntu Studio x86 (plauged by the ocassional freeze, but livable)

AMD Duron 1.3 w/ MSI mobo (actually ran suprisingly well, although not much flexability on the cpu)
----------------------------------------

So, basically I have come to the conclusion (quite possibly unfounded & way off) that LMMS doesn't do so well with certain dual x64 amd processors & amd chipsets & or even the x64 version of UbuntuStudio (I have no doubt the developers would have a quarrel with me on that)

---

### Post by Stochastic on 2008-09-11
LMMS is a very different type of music production environment than Pro Tools and Sibelius are - it's more equivalent to Fruity Loops.  But renesisspeed does raise a good point about LADSPA plugins (they're the open source plugin format).  I had forgotten/neglected to mention that many people don't bother with setting up VST support in Linux because of the vast selection of free LADSPA plugins available.

As for setting up VST support, one thing you'll need to do is download the VST SDK (2.3 is the best working version for Linux) from Steinberg's website (because of the license it can't be distributed in FOSS apps).  Then you've got a selection of hosts for Linux:
-FST is one hosting option: [http://joebutton.co.uk/fst/](http://joebutton.co.uk/fst/)
-DSSI-VST is another: [http://dssi.sourceforge.net/](http://dssi.sourceforge.net/)
-Jost is yet another: [http://www.anticore.org/jucetice/?page_id=4](http://www.anticore.org/jucetice/?page_id=4)
there's even a host that you can put right into audacity: [http://audacityteam.org/vst/](http://audacityteam.org/vst/)

I should warn you that not all VSTs will work in the Linux environment, so you might want to consult the VST/VSTi plugins database for linux: [http://ladspavst.linuxaudio.org/](http://ladspavst.linuxaudio.org/)

Lastly, even if you have them up and running through the hosts you won't be able to add them directly to an ardour session unless you rebuild ardour from scratch with VST support (instructions here: [http://ardour.org/building_vst_support](http://ardour.org/building_vst_support) ).  I've never bothered as the LADSPA set is more than I need for my personal work.

So now you can see why the LADSPA plugins are more popular for serious Linux audio work (no extra setup required).  And quite a few of them have been authored by some very smart computer audio people at Stanford etc...

---

### Post by JC Cheloven on 2008-11-14
> **Qjimbo said:**
>  ... I normally use Sibelius and Pro Tools on my PC and was wondering, is it possible to get these working well under Wine? ... 

A sibelius fan here.

I succeded at running sibelius4 under wine. First I had to copy gdiplus.dll from a windows installation, to a wine directory (windows/system32 relaying on my memory). Then I was able to install sib4, with kontakt silver included.

It worked, but with some issues. The sound was a little crappy, and some symbols (as time signatures...) piled up in the score or the menus.

Didn't find any way to put sib5 to work at all.

There's no drop-in substitute for sibelius right now. The nearest promising thing is musescore, but still has to evolve. It was a bit unstable for me.
Also NtEd is a nice program, quite usable by now, although it's goals aren't so ambitious I think. Both are in heavy development.

Greetings

---

### Post by djdolber on 2008-11-24
Just to get an understanding of how bad it is, i saw a previous archived post talking about running Reason with ubuntu+wine.. What kind of latency settings was acheived when trying it out, and on what hardware?

---

### Post by lindarthebard on 2009-12-19
> **Stochastic said:**
> 

I think you mean M-Box (or other equivalent digi soundcard) not M-Audio (that's a different company).  M-Audio products actually work quite well (other than their firewire line) in Linux.  I don't know about Digi soundcards though - the M-Boxes sound bad anyways.


I think you're confused. M-Audio makes the M-Box, and M-Audio is owned (they were purchased) by Digidesign, which is subsequently owned by Avid. They were (originally called MidiMan) bought out in August 2004 by Digidesign.

So no, they're not a different company, and M-Audio equipment is the exact same stuff as M-Box equipment, it's just that M-Box is the model name of the equipment made by M-Audio.

I'm going to try over the holiday to get ProTools LE 8 with an M-Box Mini to run on Ubuntu. I'll let you cats know how it goes. <3

Also, I've seen Ardour, it looks kinda cool, but what the heck do you mean by "8 channel mixes"? ProTools can play back and mix up to 48 channels, so I'm not really sure what you mean by that. Either way, the issue is not what the best software is, it's what is commonly used in the workplace (in my particular situation), so I have to know ProTools/Cubase/Nuendo.

---

### Post by Stochastic on 2009-12-20
lindarthebard, you might find this driver useful: [http://www.zamaudio.com/?p=97](http://www.zamaudio.com/?p=97) for an m-box

As for clarification on 8-channel mixes, I mean the audio tracks each have eight channels (i.e. octophonic audio rather than just stereo) and they are mixed together into an 8-channel final master mix.  As for number of tracks, Ardour doesn't have a limit.

I totally understand that a particular project may require certain software (or at least be able to open & save in their formats reliably).  I luckily am able to choose the gigs I want to work on, thus allowing me flexibility in software choice (hence my choice of Ardour).

---

### Post by mrufino1 on 2010-01-03
> **lindarthebard said:**
> I think you're confused. M-Audio makes the M-Box, and M-Audio is owned (they were purchased) by Digidesign, which is subsequently owned by Avid. They were (originally called MidiMan) bought out in August 2004 by Digidesign.

So no, they're not a different company, and M-Audio equipment is the exact same stuff as M-Box equipment, it's just that M-Box is the model name of the equipment made by M-Audio.



Just to clarify this, M-audio and M-box are just similarly named. Avid owns Digidesign and M-Audio, purchasing them both. The M-Box was the 2 channel interface made by digidesign (with focusrite) for Protools LE (after the digi001 pci interface). 

When M-audio was acquired, a version of protools LE called "M-Powered" was released, which used an ilok for copy protection and would run on m-audio interfaces. M-powered does not work with an M-Box, LE works with an M-box. So different products all owned by the same parent company. The Mbox 2 came out when focusrite and digi ended their relationship (they were not the same company) and digi no longer used the focusrite preamps in the m-box 2.

In any event, digi is about as closed source as it gets, getting protools to work under linux would be surprising (and kind of pointless really, just use it on windows or a mac- and I'm not doing either...). And m-powered definitely would not work in linux because you need an ilok, which is not going to ever work on linux. It barely works on windows! :-)

Hope that helped in some way...

---

### Post by redhuxley on 2010-02-05
> **JC Cheloven said:**
> A sibelius fan here.

I succeded at running sibelius4 under wine. First I had to copy gdiplus.dll from a windows installation, to a wine directory (windows/system32 relaying on my memory). Then I was able to install sib4, with kontakt silver included.

It worked, but with some issues. The sound was a little crappy, and some symbols (as time signatures...) piled up in the score or the menus.

Didn't find any way to put sib5 to work at all.

There's no drop-in substitute for sibelius right now. The nearest promising thing is musescore, but still has to evolve. It was a bit unstable for me.
Also NtEd is a nice program, quite usable by now, although it's goals aren't so ambitious I think. Both are in heavy development.

Greetings

Bump to see if there are some fresh opinions on music notation software.  I'm new to Ubuntu and wondering what to use in place of Sibelius, if there is anything...

---

### Post by prokoudine on 2010-02-05
> **redhuxley said:**
> I'm new to Ubuntu and wondering what to use in place of Sibelius, if there is anything...

MuseScore is what you will find easiest to use with Sibelius background. Denemo has its pros too.

---

### Post by niffcreature on 2010-02-06
ableton live works fairly well as far as im concerned.

---

### Post by naught101 on 2010-02-07
Ardour3 has MIDI support, I haven't tested it yet. It doesn't have any release candidates, but you can get it from SVN and compile it. Takes a while...

---

### Post by redhuxley on 2010-02-08
Thanks for the info.  I'm going to install MuseScore to try it out.  I mentioned Sibelius earlier, but in fact the last program I was using was a Finale product.  

I'll find out soon enough, but does anyone know about file compatibility with these.  Long story short, had some in-progress arrangements going that I managed to save after a Vista meltdown.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2010-02-08
I ran REAPER under wine and it was ok. However since I moved, I no longer have my midi controller..I miss it.

---

### Post by niffcreature on 2010-02-09
there is a lot of information in this thread... 
i cant tell if anyone has mentioned wineasio?
i was thinking of compiling it. maybe its not legal to talk about lol
looks like it uses a developers version of cubase asio to help it. i never found any official documentation, but there seems to be a lot of really good feedback.

---

### Post by prokoudine on 2010-02-09
> **redhuxley said:**
> I'll find out soon enough, but does anyone know about file compatibility with these.

Use MusicXML as exchange file format. Native file formats from Sibelius and Finale are not supported.

---

### Post by sgx on 2010-02-09
> **niffcreature said:**
> there is a lot of information in this thread... 
i cant tell if anyone has mentioned wineasio?
i was thinking of compiling it. maybe its not legal to talk about lol
looks like it uses a developers version of cubase asio to help it. i never found any official documentation, but there seems to be a lot of really good feedback.
Hi, you should be able to find a .deb file,
or just google and download an .rpm version, and use the alien command to make a .deb

alien wineasio-0.7.3-1pclos2007.i586.rpm

That should place the new .deb file in the same folder next to the .rpm version. Then run

dpkg -i name-and-path-to-new.deb

Then 

regsvr32 wineasio.dll

Assuming wine is first installed, of course. Now Reaper, Cantabile, or other windows apps that work in wine will list wineaasio in their respective preferences/configuration gui.

There may be advantages to compiling a version, but us Country Western
types are a pretty simple lot ;)

---

### Post by raboofje on 2010-02-09
I've had reasonable success using the notation part of Rosegarden as a Sibelius/Finale replacement. It has its limitations/quirks though...

---

### Post by niffcreature on 2010-02-10
> **sgx said:**
> Hi, you should be able to find a .deb file,
or just google and download an .rpm version, and use the alien command to make a .deb

alien wineasio-0.7.3-1pclos2007.i586.rpm

That should place the new .deb file in the same folder next to the .rpm version. Then run

dpkg -i name-and-path-to-new.deb

Then 

regsvr32 wineasio.dll

Assuming wine is first installed, of course. Now Reaper, Cantabile, or other windows apps that work in wine will list wineaasio in their respective preferences/configuration gui.

There may be advantages to compiling a version, but us Country Western
types are a pretty simple lot ;)

thanks a lot, seems to have installed correctly but not working whatsoever with live 8.0.1 or 7.0.3. i just dont get any audio.
i was reading this thread [http://ubuntuforums.org/showthread.php?t=923957](http://ubuntuforums.org/showthread.php?t=923957) but no one has that problem, not much there to help me.
guess i should test it with something else to see if i installed it correctly.

i found a deb of version .7.4 or something, which is for jaunty and im running intrepid. think that would screw things up?
ableton has worked perfectly for me before, with jack, just never low latency

---

