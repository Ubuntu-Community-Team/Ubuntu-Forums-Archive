---
title: "The state of sound in Linux?"
date: 2007-09-21
forum: The Cafe
---

### Post by FuturePilot on 2007-09-21
What do you think the state of sound in Linux is? And how can it be improved? I think something really really needs to be done about the sound in Linux. I have a pretty high end sound card but I can't do anything advanced with it. No rendering stuff off the hardware, no advanced options etc. And it's really bad if you have an integrated card in a laptop of something, you always get that cannot open /dev/dsp error. 

I'm not sure if this is related but why do all the equalizers reduce sound volume by like half when activated? There's no use in using an equalizer if it muffles my volume.

Edit: Poll title should read: The state **of** sound in Linux

---

### Post by hessiess on 2007-09-21
works perfectily, exept blender, but thats a bug with blender and not ubuntu;)

---

### Post by glupee on 2007-09-21
yup works fine for me. Better than windows at least in windows i have to update the drivers else i get a crackling sound. Mind you i'm using the sound integrated into my mb, so nothing fancy shmansy.

---

### Post by bruce89 on 2007-09-21
PulseAudio would probably solve everything.

---

### Post by FuturePilot on 2007-09-21
> **bruce89 said:**
> PulseAudio would probably solve everything.

What is PulseAudio?

For the most part everything works ok for me, the thing is I've only got basic options. I can't do anything advanced with my sound card.

---

### Post by rustybronco on 2007-09-21
Had a sound issue with vlc player once.

---

### Post by RageOfOrder on 2007-09-21
> **FuturePilot said:**
> 
I'm not sure if this is related but why do all the equalizers reduce sound volume by like half when activated? There's no use in using an equalizer if it muffles my volume.

Edit: Poll title should read: The state **of** sound in Linux

The thing about using an equalizer is that now you can control the gain of your signal. If you've ever worked with amplifiers, you'll know that the signal is a sine wave, and by increasing the gain, you increase the size of said wave. Increase too much and the wave takes  on a square shape. This is known as signal clipping, and is extremely bad for your hardware.

So equalizers automatically drop the signal levels so you can't create clipping if you bump the gain up too high.

Go try it on windows. Increase your gain. Sound goes to **** pretty fast.
That's also why alsamixer defaults your channels at 71/100 instead of maxing them like you would do on windows.

---

### Post by Lord Illidan on 2007-09-21
Personally I find it ok, but then I am using an snd-hda-intel soundcard, and I am not an audiophile.

However, for people with X-FI soundcards, they're in the sh**, until Creative releases a driver.

Even with my card, I have to write a line in /etc/modules/alsa-base to make it work, which imho is very unuser friendly.

So sound support in linux can range from the good to the mediocre to doesn't work at all.

---

### Post by bruce89 on 2007-09-21
> **FuturePilot said:**
> What is PulseAudio?
[URL="http://www.pulseaudio.org/"]
PulseAudio is a sound server for POSIX and Win32 systems. A sound server is basically a proxy for your sound applications. It allows you to do advanced operations on your sound data as it passes between your application and your hardware. Things like transferring the audio to a different machine, changing the sample format or channel count and mixing several sounds into one are easily achieved using a sound server.[/URL]

It's a replacement for ESD, which is dead since 2000.

---

### Post by FuturePilot on 2007-09-21
> **RageOfOrder said:**
> The thing about using an equalizer is that now you can control the gain of your signal. If you've ever worked with amplifiers, you'll know that the signal is a sine wave, and by increasing the gain, you increase the size of said wave. Increase too much and the wave takes  on a square shape. This is known as signal clipping, and is extremely bad for your hardware.

So equalizers automatically drop the signal levels so you can't create clipping if you bump the gain up too high.

Go try it on windows. Increase your gain. Sound goes to **** pretty fast.
That's also why alsamixer defaults your channels at 71/100 instead of maxing them like you would do on windows.

Yeah, I've noticed that too on Windows. But how does this relate to the equalizer cutting the volume in half?

And PulseAudio does sound promising. I hope they get this implemented soon.
[https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")  
[https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble]("https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble")

---

### Post by Paul820 on 2007-09-21
I have never had trouble with sound on my Acer laptop or self built desktop. If it was windows i would of had to use drivers so i think the developers have done a good job with the sound.

---

### Post by Crashmaxx on 2007-09-21
The only issue I've ever had is that if one thing is playing, often another won't be able to. But really, that is almost a feature as it rarely does any good to play two things at once.

---

### Post by SupaSonic on 2007-09-21
I actually get 'cannot open /dev/dsp' on a regular basis, which is annoying, but is usually solved by closing Firefox. It is an issue in games especially - the sound never works with Firefox running. 

So for me, the sound doesn't 'just work'. No issues on Windows.

Oh yeah, and I tried to configure Surround sound in Ubuntu, which is not a problem at all in Windows, but I failed miserably in Linux. So I'd say the sound still needs a lot of work.

---

### Post by DJ_Peng on 2007-09-21
It seems to work pretty well for me with my SB Live card, although I lost the right channel sound as soon as I run it into my 2.1 system. Headphones and 2 channel speakers are fine, so maybe it's my Creative speaker system that's screwing the pooch.

Otherwise it could be a little easier to get sound working for non-geeks. I have had some instances where I had to tell an app (like Amarok) how to use the sound system which could really throw someone less technically inclined.

---

### Post by kostkon on 2007-09-21
I never had any sound problems; I have many applications using the sound at the same time and everything works fine.

I have a *Soundblaster Live 5.1*

And +1 for* PulseAudio*, it would be the absolute solution, although is not ready for pro audio, not yet at least.

---

### Post by treis on 2007-09-21
I had to compile ALSA and some other things on my computer to get the headphone jack working properly.  I don't know if that's a problem with a lack of drivers for my hardware or what, but it's by far the worst thing I had to deal with in Ubuntu.  

Separate volume levels for each application is an absolute must have.  

I've only briefly read about the OSS vs. ALSA situation, but that sounds like something that needs to be resolved.

---

### Post by joecool362 on 2007-09-21
At least your sound works. On Ubuntu Feisty Fawn I can't get it to work!!!

---

### Post by FuturePilot on 2007-09-21
From what I can see, is that sound works for the most part in Linux. But what I'm getting at is the functionality of sound in Linux. There's really no advanced options to adjust sound and stuff. And I can't play MIDI off the card.

---

### Post by Matakoo on 2007-09-21
Well, I voted okay. It still needs some work, but generally speaking it works satisfactory personally speaking. Not a high-end soundcard in my machine by any means - just an integrated intel-hda controller. This is subjective, but I think the sound is clearer than it is in XP or Vista.

Still, that is not to say it is perfect. In my opinion, there are a few problems that need to be solved.

1. The Alsa/OSS situation. For the most part, ALSA is sufficient. Some programs insist on having OSS or the OSS-compatible alsa-lib installed, which is annoying to begin with but it seems the sound-quality is degraded a little when the OSS/ALSA lib is utilized. Secondly, even when there is an option in the program of whether to use ALSA or OSS, some programs work better with ALSA while others work better with OSS. It's really a trial-and-error affair there.
2. Secondly, if I see that "cannot open /dev/dsp" again I'm gonna scream!
3. Finally, the entire sound infrastructure is too complex. Driver support in the kernel, plus the choice/combination of ALSA/OSS is just the beginning. Then we have PulseAudio (need to look more into that), eds, arts, timidity, jackd, and God knows what else. Honestly, this is too complex and needs to be simplified/unified a lot. There are too many factors and too many things that can go wrong. It usually doesn't, but the potential for it is there. Now, I don't know how to accomplish such a simplification or even if it is possible but I do think it is needed in the long run.

I'm all for the freedom of choice, but is this really a choice or an unnecessary complication? My vote is for the latter, and I'm only a consumer of audio (albeit one that likes to play around with Audacity and Rosegarden - and if it wasn't for the latter I wouldn't even have jackd installed).

Feel free to disagree, and I would love to be proven wrong about how this is too complex and too error-prone.

---

### Post by insane_alien on 2007-09-21
the only sound issues i've had are hardware issues(loose connections in the headphones jack, fixed with a bit of solder, a screwdriver and a 5 pound sledgehammer, it was the only thing i had at hand that would work, you would never have seen a sledge hammer weilded so precisely.)

---

### Post by bruce89 on 2007-09-21
Gutsy has PulseAudio but it doesn't work 100%

I have a USB turntable, it's fine in Linux, but when it is plugged in when Windows is on, there is no sound output.

---

### Post by Bungo Pony on 2007-09-21
My onboard sound card is made by Realtek. It works fine for just everyday sound use, but the minute I fire up Jack audio control, everything goes to hell. That's why I have an extra sound card installed in my PC and a switchbox to control which sound card my main input and output use. It's a bit of a pain in the butt, but it's a nice temporary solution for now since Jack loves the soundblaster card I put in. I also have a SB X-Fi card that I haven't put in yet since the Linux support apparently isn't very good yte.

I really like the fact that my Realtek card has multiple inputs and outputs, but the fact that Jack doesn't like it and that Ubuntu is a little bit goofy in handling it is a bit disappointing. That's why I still do a lot of audio and video work in Windows.

I hope it improves in the future.    

On the plus side, I used the Hydrogen drum machine, and it's an absolute dream to work with!

---

### Post by FuturePilot on 2007-09-21
> **Matakoo said:**
> 
2. Secondly, if I see that "cannot open /dev/dsp" again I'm gonna scream!
:lolflag: Lol, that's a nasty one isn't it?

> **Matakoo said:**
> 3. Finally, the entire sound infrastructure is too complex. Driver support in the kernel, plus the choice/combination of ALSA/OSS is just the beginning. Then we have PulseAudio (need to look more into that), eds, arts, timidity, jackd, and God knows what else. Honestly, this is too complex and needs to be simplified/unified a lot. There are too many factors and too many things that can go wrong. It usually doesn't, but the potential for it is there. Now, I don't know how to accomplish such a simplification or even if it is possible but I do think it is needed in the long run.

I'm all for the freedom of choice, but is this really a choice or an unnecessary complication? My vote is for the latter, and I'm only a consumer of audio (albeit one that likes to play around with Audacity and Rosegarden - and if it wasn't for the latter I wouldn't even have jackd installed).

Feel free to disagree, and I would love to be proven wrong about how this is too complex and too error-prone.
I totally agree with you on this. Look at this and it goes along exactly with what you said.
[https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble]("https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble")

---

### Post by Polygon on 2007-09-21
sound works for me, but different programs have different volume levels, like when i play movies i have to turn my main volume down, but then i start up exaile and its really soft and i have to jack up my volume

my microphone does not work

there are still some programs that dont work with alsa and you gotta OSS it which is annoying....


hopefully that pulseaudio thing or w/e will solve this

---

### Post by RAV TUX on 2007-09-21
Sound for me is great, everything works outstanding!

In Elive Gem 1.0

---

### Post by jrusso2 on 2007-09-21
Ever since they went to Alsa sound has been poor.  Lots of common sound cards don't seem to work anymore or have to be manually configured. Duplex seems to not work.  Microphone's don't work.

I wish they would go back to OSS sound now thats its  GPL

---

### Post by thisllub on 2007-09-21
I am using 64Studio with a Lexicon Omega.  Everything works beautifully. 64 bit Ardour worked first go with all 4 inputs and 2 outputs. Using Jack I can sync Ardour to Rosegarden to Hydrogen to other synths.  Brilliant.

The only Issue I have is with Flash. Once a Flash page loads in Iceweasel sound won't  work with anything else until I close it and vice versa.

Jacklab looks like an interesting distro too. They claim to have VST support under Wine. I might try and get that working with 64Studio. I would much prefer a 64 bit Debian based system to a 32 bit SUSE based one.

---

### Post by PatrickMay16 on 2007-09-21
Sound on linux is dire compared to Mac and windows. There are several different audio servers and so on... OSS, ALSA, JACK, etc... and on cards without hardware mixing, you'll get "cannot open sound device" errors fairly often.

---

### Post by RAV TUX on 2007-09-21
> **PatrickMay16 said:**
> Sound on linux is dire compared to Mac and windows. There are several different audio servers and so on... OSS, ALSA, JACK, etc... and on cards without hardware mixing, you'll get "cannot open sound device" errors fairly often.

I would honestly say for me sound is better in Elive Gem 1.0, better then both Windows and Macs.

---

### Post by SunnyRabbiera on 2007-09-21
hardly any issues here, yeh sure at first because I had no idea what I was doing but once I learned I was doing fine.
ALSA seems to work best on my current distro PCLinux but OSS worked the best on Ubuntu, but both have worked pretty well for me.

---

### Post by Mr. T on 2007-09-21
Mixed. It's definately better than it used to be, but there's still way too many audio servers around. I also often have issues that I wouldn't be seeing in Windows. For example, I'd get "clicky" audio in all OpenAL games unless I had a special .openalrc file to force the sound to run through OSS I think. That fixed the issues with Freespace 2 and OpenArena, but UT2004 would have stuffed audio unless I REMOVED the file. I'd prefer not to have to deal with this crap.

---

### Post by Skorzen on 2007-09-21
Everything's going well with my Realtek ALC880 HD 5.1 Audio On-Board system.

---

### Post by LowSky on 2007-09-21
i think it could be better, but then so could alot of things...

---

### Post by Polygon on 2007-09-22
> **RAV TUX said:**
> I would honestly say for me sound is better in Elive Gem 1.0, better then both Windows and Macs.

hes talking about the way sound is handled. In both windows and macs there is a single sound server/api/whatever that handles sound, and all programs use it. In linux there are many different sound servers and sometimes they conflic and cuase problems which is the reason why you get cant open /dev/dsp errors and stuff

---

### Post by Matakoo on 2007-09-22
> **FuturePilot said:**
> :lolflag: Lol, that's a nasty one isn't it?

So it is...I wouldn't mind as much if:
1. The error said WHY it wasn't able to open it. I.e. "Cannot open /dev/dsp because PID 3782 [amarok] is already using it." or something along those lines.
2. You get the error message when in a GUI only. At least I have never seen a window pop up with that kind of message but something went wrong with the sound anyway (i.e. getting just silence). When starting the app in the CLI, you get the error.


> **FuturePilot said:**
>  I totally agree with you on this. Look at this and it goes along exactly with what you said.
[https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble](https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble)

Definitely a big step in the right direction, and sounds just like what the doctor ordered, at least for those of us who are dabblers and/or consumers only! I'm not sure I understand how it is supposed to work, but as long as it works and doesn't break too many things (some breakage is probably unavoidable initially) I won't complain.

It isn't meant to replace ALSA and/or OSS is it? It sounds more like some sort of abstraction layer sitting between the user/the applications on one side and ALSA/OSS/Kernel-driver on the other, and making sure there are no conflicts between whatever wants to make use of the sound hardware.

---

### Post by Spr0k3t on 2007-09-22
Sound needs quite a bit of work to be on par imho.  I've got integrated RealTech on the desktop along with Audigy card.  There is a difference with the Audigy card but not by much.  I'm using Altec Lansing ACS 56 speakers and the rear channels work fine.  My problem though, I have to crank the speakers to no end to get a decent volume out of them.  Other systems do not require the same levels to achieve decent output.

PulseAudio looks interesting... I'd like to see what they end up with.

---

### Post by RAV TUX on 2007-09-22
> **Polygon said:**
> hes talking about the way sound is handled. In both windows and macs there is a single sound server/api/whatever that handles sound, and all programs use it. In linux there are many different sound servers and sometimes they conflic and cuase problems which is the reason why you get cant open /dev/dsp errors and stuff

ahhh thanks for the clarification Polygon. ;)

---

### Post by happy-and-lost on 2007-09-22
Works great on my machines (except for Audacity). I can imagine that people with exotic or expensive sound cards go through hell to get them working.

---

### Post by tpg on 2007-09-22
With onboard sound, I've never had any problems. Obviously you wouldn't expect it to do much more than just play sound though...

Things such as midi playback have been a pain in the past - I seem to remember trying to download and install soundfonts to get it to work. (That was on a SoundBlaster Live! - a pretty old card). I now use an MAudio Revolution 5.1 in our desktop, which is working well in Feisty, although I haven't tried to use all the features (only using it as 2.1 at the moment).

---

### Post by drivel on 2007-09-22
just soso,except gstreamer perfomance good

---

### Post by raycosm on 2007-09-22
Worked flawlessly with my old Dell E1505, but it does weird stuff with my Acer 5570Z. Example, when I plug in headphones, sound comes out of the headphones, AND the laptop speakers. I have to open volume control and use the PCM slider to change the volume of my headphones, but I just click the icon and use that slider if I want to change the volume of my laptop speakers.

Not really a big deal for me, I find it more amusing than annoying, but if I were to take my laptop into, say a library, then that would be a problem.

---

### Post by FuturePilot on 2007-09-29
I guess I really just want to be able to do something like this. (See attachment) Why isn't there a way to do this with ALSA or something? Will PulseAudio provide something like this?

---

### Post by Polygon on 2007-09-29
i really hope its easier to understand then that example future, i mean, what kind of enviroment is a bathtub? a sewer? stone box? wtf?

---

### Post by FuturePilot on 2007-09-29
> **Polygon said:**
> i really hope its easier to understand then that example future, i mean, what kind of enviroment is a bathtub? a sewer? stone box? wtf?

Now I'm confused:?

---

### Post by Frak on 2007-09-29
Ahh, the crackling :(

---

### Post by FuturePilot on 2007-09-29
> **Polygon said:**
> i really hope its easier to understand then that example future, i mean, what kind of enviroment is a bathtub? a sewer? stone box? wtf?

Wait. Now I get it. ROFL!:lolflag:
I'm slow....

---

### Post by cogadh on 2007-09-29
I think the sound situation in Ubuntu is OK, but I wish they would change it so that the sound volume is not turned all the way down by default on a clean install and it would be nice to see some good configuration tools for ALSA (if they are going to continue to use that for the sound system). I can't stand trying to get a custom .asoundrc configured manually, the documentation on it is cryptic at best.

---

### Post by rzrgenesys187 on 2007-09-29
I had a lot of problems getting it working right in ubuntu, had to edit dsdt.aml file

---

### Post by Frak on 2007-10-01
I don't know if this has been discussed yet, but if you goto System->Preferences->Sound->Device->OSS, at least I have gotten rid of the crackling :)

---

### Post by multifaceted on 2007-10-01
Once I installed all of the codecs...(which took less than 5 minutes)... everything worked perfectly. I doubted my machines soundcard because it's inferior for recording, when I used Windows that is....

Nonetheless, audio playback is hands down great. Still trying to figure out audio capture in Linux... I'll see how it reacts then. Maybe I'll get my new soundcard afterall.

---

### Post by herbster on 2007-10-02
I fiddled with my .asoundrc (with the help of #alsa) and now my sound is fantastic. I have it set to upmix stereo to all 5 speakers, 5.1 works perfectly, microphone/recording gets the thumbs up, etc.

---

### Post by Caffeine_Junky on 2007-10-02
Feisty:
Sound all works for me in feisty.  \\:D/
I find out of all the players that XMMS plays my mp3's at the best volume with default settings, ..and I can always up the db's on the EQ if Iwant..
___
(I run my PC audio through my home stereo so there is plenty of room for config' between the software/hardware)
----
Debian:
I have a partition with debian etch KDE (stock etch 4.0 kernel) ..and I am only able to have either "System Sounds"(ie: login/out etc) OR "Audio-playback"(xmms/ mp3's), ..not both!  ...If I have "System Sounds" enabled, I get an error when trying to start xmms or Audacity about the soundcard not being configured, ..so I have to run alsaconf as root every time I login!  ..grr ..annoying! So I have Sys' Sounds turned off now and that solves the problem in a "workaround"  kind of way, ..but I would like to have both working!

I have tried Gnome on "debian etch 4.0" as well and ALL sound is muted at startup! lol Boooo :p.  I have done a fair bit of Googling on the  "alsa issues" in debian etch 4.0, but didn't find anything decisive concerning a Fix .  Maybe the situation has improved in Lenny but I am not sure.
:guitar:  All sound is working in "Elive Gem 1.0" Sweeeet :)

---

### Post by jrlii on 2007-10-07
Consumer level sound is OK, but getting stuff to work with multi-channel audio boards is a pain.

---

### Post by aschaetter on 2007-10-11
Support for HDA-Intel is horrible!!! Hopefully after 1.0.15 is released things will work a little better. :)

---

### Post by Frak on 2007-10-11
Some recent upgrades on Gutsy were released that fixed the sound some.

Also, Amarok doesn't crackle like Rythmbox does. Plus, Amarok rocks!

---

### Post by Kalisandra on 2007-10-12
> **Frak said:**
> 
Some recent upgrades on Gutsy were released that fixed the sound some.

Also, Amarok doesn't crackle like Rythmbox does. Plus, Amarok rocks!


So far as I can tell either the updates or setting up Compiz to give me the cube broke my sound. Now it only works if I tell everything to use OSS even though OSS then sends everything through ALSA (I think - the ALSA mixers still control volume). It took hours to get even this, and I'm not at all sure what I did that worked. :(

So, I say sounds needs work, especially as I'd like to use the Creative X-Fi I've got one day.

---

### Post by julian67 on 2007-10-12
I voted OK

Mostly I'm satisfied. There are two aspects to this for me. First is the hardware detection and configuration and secondly Linux's sound architecture.

The hardware issue is a non-issue for some because everything works perfectly for most cards. For others it's the main issue because there are problems. I have several PCs, some with full soundcard support and some with partial/restricted. My ich7 sound on my laptop has been made to work very nicely but only on one particular kernel version so I am a little stuck with upgrading. My desktop has an old Audigy and I have no complaints, everything works and its myriad of options are just as confusing in Ubuntu as they ever were in XP :) but I have the benefit in Ubuntu of not having any of Creative's awful applications bundled in with the driver. In Windows I remember I even had started using the free alternative kx drivers as Creative's original ones were so bad. 

The Linux sound architecture itself is mostly good. I can use multiple applications using sound simultaneously *as long as none of them are streaming audio* at which point it all stops. 

These are not massive issues for me but neither are they trivial, though overall I'm still satisfied. As a comparison my "designed for XP"  Lenovo laptop with ich7 has trouble with the ich7 sound in XP and the Windows driver install was not issue free (using Lenovo's own supplied driver CD). In this respect both XP and Linux were a little problematic but the final result, in terms of consistently good trouble free playback, is that I get a better quality sound in Ubuntu.

---

### Post by Tom Mann on 2007-10-12
I voted OK as well - I noticed that people have had trouble with Flash but I think that's flash's problem to a point. I'm waiting for FFADO then I'll be happy cause Freebob on Jack into ALSA just doesn't work for me :(

---

### Post by Punio4 on 2007-10-21
State of sound... Bad. Exceptionally bad.
Every program uses its own... Thingies. Too much... thingies.. to choose from...
Alsa, Oss, Esd, Pulseaudio, this, that... What the hell...
Also, using ALSA which provides best results with minimum hassle.
But the sound still pops and stutters when starting to play... Like putting down a needle on a gramophone record.

High cpu usage means sounds stutter, plus, the sound is flat compared to XP.

---

