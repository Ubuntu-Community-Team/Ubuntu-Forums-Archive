---
title: "Looking for DJ Software"
date: 2009-12-05
forum: Ubuntu Studio
---

### Post by bshosey on 2009-12-05
I am looking for a GTK dj software that will use pulseaudio. similar to Mixxx. two problems I have with Mixx is no auto-play feature and that it uses QT. Does any one have any ideas.

---

### Post by ayampanggang on 2009-12-06
sorry to say but you can be assured that mixxx is just the best we have for linux out there =(

i still have my windows installed for my music production and NI traktor needs

---

### Post by bshosey on 2009-12-06
> **ayampanggang said:**
> sorry to say but you can be assured that mixxx is just the best we have for linux out there =(

i still have my windows installed for my music production and NI traktor needs

OK. Then I will hope they will have the autoplay feature working soon. Mixxx is a good program I was not trying to take credit away from it. I just prefer GTK over QT

---

### Post by AutoStatic on 2009-12-06
You could try [UltraMixer]("http://www.ultramixer.com/").
Not free though but at least they offer a Linux version.

@ayampanggang, music production can be done perfectly with Ubuntu. DJ'ing is another thing. BPM detection and looping can't be done with Mixxx, it can be done with UltraMixer but UltraMixer doesn't have the ability to snap automatically. And both don't have direct JACK support.

---

### Post by bshosey on 2009-12-06
You know I tried that like 1 year ago. I will try it again. I thought it was a decent one as well.

---

### Post by DerickX on 2009-12-07
AFAIK bpm detection is possible with mixxx and it also has JACK support!

---

### Post by AutoStatic on 2009-12-07
PortAudio is not direct JACK support. And you're right, Mixxx does have BPM detection, but I didn't find it really reliable. Maybe I should give it a try again. And the upcoming version apparently has a loop function.

---

### Post by ayampanggang on 2009-12-07
> **AutoStatic said:**
> 

@ayampanggang, music production can be done perfectly with Ubuntu. DJ'ing is another thing. BPM detection and looping can't be done with Mixxx, it can be done with UltraMixer but UltraMixer doesn't have the ability to snap automatically. And both don't have direct JACK support.

What linux DAW software is as good as those available on windows and mac?

And then, do all the VSTs / plugins found on windows or mac works on linux? I use Native Instruments Massive, IL Gross Beat and Kontakt, do they work on linux?

Oh thanks for the ultramixer link. I was so sure that mixxx is the only available DJ software on linux.

---

### Post by DerickX on 2009-12-07
> **ayampanggang said:**
> What linux DAW software is as good as those available on windows and mac?

Ardour 2.8.4 is the best you can get on Linux. It's good.
Also Renoise and EnergyXT are available for Linux.

> 
And then, do all the VSTs / plugins found on windows or mac works on linux? 
No. There are a few VST plugins which runs natively on Linux. A lot are able to work on Linux with the help of FST, Dssi-vst or wineasio / VSThost. 

I suggest to try the Linux Jack apps and LADSPA, DSSI & LV2 plugins first, before you are going to struggle with vST on Linux..

> 
Oh thanks for the ultramixer link. I was so sure that mixxx is the only available DJ software on linux.
There is also terminatorX, with a nice old school scratching feature.

---

### Post by AutoStatic on 2009-12-07
> **ayampanggang said:**
> What linux DAW software is as good as those available on windows and mac?

And then, do all the VSTs / plugins found on windows or mac works on linux? I use Native Instruments Massive, IL Gross Beat and Kontakt, do they work on linux?To be honest, I really don't care. Wrong place and wrong person for this kind of discussion, sorry.

---

### Post by completeidiot on 2010-01-05
I'm just starting to play with mixxx and it has some strong potential. I hope. I have some djing experience with vinyl but until recently had sworn off djing in any electronic format....however my dream is to now be able to dj while traveling...using a simple set up of external hard drive (i have a pretty absurd music collection), Ubuntu Netbook remix, and maybe i will pick up some sort of basic mixer if i don't like mixxx.

What set ups are currently being used by experienced Ubuntu Djs?
Are we in agreement that mixxx is the only viable option?

---

### Post by mrufino1 on 2010-01-05
What about DJ Play? I am not a DJ, I play bass in a band, but I DJ'd our breaks with DJ Play last week, worked fine. I wasn't beat matching or anything, just crossfading between songs, but it was solid. I can't get mixx to work right.

---

### Post by FinalCoyote on 2010-01-06
I tried Mixx when i first got linux - definitely not reliable enough for live use.
Not professionally anyway, still gonna stick with Windows & Traktor's DVS System

---

### Post by jocampo on 2010-01-06
> **FinalCoyote said:**
> I tried Mixx when i first got linux - definitely not reliable enough for live use.
Not professionally anyway, still gonna stick with Windows & Traktor's DVS System

Respect your opinion but I'm not agree. 

Which Mixxx version are you referring to and which Ubuntu flavor and hardware are you using? I have a Compaq Laptop dual core with Jaunty on it, and mixxx 1.7 runs with no issues at all, really low latency; I'm using Stanton3d as interface. Planning to do the same with Ubuntu Studio to get even better performance but it is running ok on Jaunty.

Regarding professional or not, can't discuss that because I don't DJ for living (know about performance though 'cause I'm an IT guy and I'm using the software on my laptop) but the interface is one of the easiest to use.

---

### Post by Stochastic on 2010-01-06
> **FinalCoyote said:**
> I tried Mixx when i first got linux - definitely not reliable enough for live use.
Not professionally anyway, still gonna stick with Windows & Traktor's DVS System

The Ubuntu package of Mixxx tends to be a little buggy at times.  If you're serious about using the program you may want to get a copy from their website and compile it.  Though their use of port audio is a feature I wish they would remove.

I personally use XWax [http://www.xwax.co.uk](http://www.xwax.co.uk) for my live shows.  Rock solid and light.

---

### Post by jocampo on 2010-01-06
> **Stochastic said:**
> The Ubuntu package of Mixxx tends to be a little buggy at times.  If you're serious about using the program you may want to get a copy from their website and compile it.  Though their use of port audio is a feature I wish they would remove.

I personally use XWax [http://www.xwax.co.uk](http://www.xwax.co.uk) for my live shows.  Rock solid and light.

Interesting program Stochastic, does it work with a Stanton 3d ?

---

### Post by Stochastic on 2010-01-07
> **jocampo said:**
> Interesting program Stochastic, does it work with a Stanton 3d ?

I'd assume no, as it relies on the audio input of timecode vinyl or CDs.  

I personally can't stomach any 'DJ' technology that doesn't use a needle and a spinning platter - the control just isn't there otherwise - but that's just my personal opinion/taste.

On a sidenote, the timecode features in Mixxx use the libraries that xwax developed, so they should perform that feature fairly similarly - in theory.

---

### Post by jocampo on 2010-01-08
> **Stochastic said:**
> 
I personally can't stomach any 'DJ' technology that doesn't use a needle and a spinning platter 

I've heard similar comments years ago with the beta-max, then VHS, then CDs, and most recent, Amazon Kindle ;)

I´m not a pro DJ but I strongly believe that technology and midi players will kill classic spinning platters and you stop seeing those in a few years.

---

### Post by Stochastic on 2010-01-08
> **jocampo said:**
> I've heard similar comments years ago with the beta-max, then VHS, then CDs, and most recent, Amazon Kindle ;)

I´m not a pro DJ but I strongly believe that technology and midi players will kill classic spinning platters and you stop seeing those in a few years.

Those technologies you've mentioned are all playback devices whereas the turntable is a musical instrument.

The haptic response that vinyl gives the performer is invaluable.  That's why programs like xwax and serato exist and are so popular - to digitally leverage the excellent interface of a turntable.

But it looks like we'll just agree to disagree.

---

### Post by FinalCoyote on 2010-01-08
> **Stochastic said:**
> 
I personally can't stomach any 'DJ' technology that doesn't use a needle and a spinning platter - the control just isn't there otherwise - but that's just my personal opinion/taste.


I'm with you there - turntables are the definitive, controllable medium.
 
I don't know about you, but i've found a few clubs that exclusively use a Serato Scratch Live setup w/ some Technics - no CDJ's, which is fantastic.
Personally, i think the feel of digital vinyl systems (like my own) is good, but for some reason not the same as a 'real' record.

I've seen xwax used by some DJs, and i'm sure that with time it could be just as good as a professional, bought system like serato or traktor.

For me, my system works great and i'm not keen to change it.

> **jocampo said:**
> 
I´m not a pro DJ but I strongly believe that technology and midi players will kill classic spinning platters and you stop seeing those in a few years.

Sadly though, this probably will be the case eventually.
Modern CDJ systems (especially the high-end ones, like pioneer's) are becoming the native format for new DJs.
Of course, the days of pressing your own dubplate are long gone, and the conveniences of CDs do stand out - i suppose that's why DVS is becoming so popular.

---

### Post by Switch_Zero on 2010-01-13
Currently I'm working with Atomix Virtual DJ on Windows XP (on a laptop) and use the Behringer BCD3000 as a controller. I have to admit that using that controller doesn't give you the same control and feel as you would get using vinyl or pro-equipment (i.e. Pioneer CDJ controllers). But it's an easy-to-carry and quick-to-setup...setup :P
 
I'll be switching to the latest Ubuntu release sometime soon and want to see if I can get Atomix VDJ working in combination with Wine and use my controller and still be able to give a good performance (including Beatmatching/mixing).
If so, I'll be sure to report it here and give you details.
Otherwise it'll be a dual-boot for me. 
I've been looking at Mixxx and Ultramixer, the latter looks better, but I have no experience with either of them so can't give any opinion. I will try both anyway, just to see which will 'feel' more like VDJ.
 
[SIZE=1](Oh, and I've tried using NI Traktor...because it came with the controller...not my kind of program, but will look into it after I've got Ubuntu running)[/SIZE]

---

### Post by AutoStatic on 2010-01-13
The BCD3000 works fine with Ubuntu, got one too.
But I'm still not very fond of Mixxx and personally I think UltraMixer is not really a DJ tool, it's a good player with some extra effects.

---

### Post by FinalCoyote on 2010-01-13
Shame, i can see Linux being an excellent platform for DJ/Producers.

---

### Post by Switch_Zero on 2010-01-14
I think we need some DJ'ing/Mixing/Coding enthousiasts to get together and start working on an open source VDJ/Traktor-a-like project. ;)
 
I'll do the graphics for the GUI and beta-testing for BCD3000 controller compatibility :P
Anybody else who has skills that could be usefull?
 
[SIZE=1](This may sound like a joke, but I'm not kidding. If there are any people out there who know how to code for Ubuntu/Linux and know how to create scalable/skinnable GUI's...maybe we could start a project)[/SIZE]

---

### Post by AutoStatic on 2010-01-14
Then I would consider hooking up with the Mixxx team. The only things Mixxx lacks for me is looping, 1.8.x will have it though, and stuff like snapping to the beat grid, good BPM detection and last bot nut least, decent JACK support that doesn't rely on an extra layer like PortAudio.
As soon as that works in a decent manner I will scream and yell good riddance at the very last XP installation in our household.

---

### Post by Stochastic on 2010-01-14
> **AutoStatic said:**
> Then I would consider hooking up with the Mixxx team. The only things Mixxx lacks for me is looping, 1.8.x will have it though, and stuff like snapping to the beat grid, good BPM detection and last bot nut least, decent JACK support that doesn't rely on an extra layer like PortAudio.
As soon as that works in a decent manner I will scream and yell good riddance at the very last XP installation in our household.

I'm fairly sure that PortAudio is ingrained into the Mixxx code.  Mixxx is after all, a three-OS program (win, mac, and linux) and PortAudio is designed to be a compatibility layer for audio across operating systems.  This is unfortunate because I too feel that proper/direct jack support would turn Mixxx into a more reliable/stable/efficient piece of software.

if(PortAudio == partOfMixxx2) {
  linuxMixxer = fork(mixxx);
} else {
  rejoice();
}

---

### Post by Switch_Zero on 2010-01-14
> **AutoStatic said:**
> Then I would consider hooking up with the Mixxx team. The only things Mixxx lacks for me is looping, 1.8.x will have it though, and stuff like snapping to the beat grid, good BPM detection and last bot nut least, decent JACK support that doesn't rely on an extra layer like PortAudio.
As soon as that works in a decent manner I will scream and yell good riddance at the very last XP installation in our household.
 
Same here, I'll be glad when I can completely move over to Ubuntu. And yes joining the Mixxx team might be a good idea. So, I'll look into that. Besides the instability and bugs that come with the app, I'm not too happy about the GUI. I haven't tried the app yet, so can't really make a fair or solid statement. Yet looking at the screenshots it doesn't come close enough to the feel and look that VDJ gives me.
I'm not saying they should make a GUI that looks exactly like VDJ's. But something closer to it would be nice.
i.e. putting the faders and knops more to the center instead of the left and right side.
 
== Edit
 
Scratch all of the above. I just read the info on the site more thourougly. Looks like there are more skins available (don't know where to get them) and you can design them yourself.
I'll be looking closely to that last option :)

---

### Post by AutoStatic on 2010-01-14
Yup, Mixxx is highly skinnable. I kinda like the way Mixxx looks, compared to UltraMixer it looks really tidy and uncluttered.

---

### Post by Switch_Zero on 2010-01-14
> **AutoStatic said:**
> Yup, Mixxx is highly skinnable. I kinda like the way Mixxx looks, compared to UltraMixer it looks really tidy and uncluttered.
 
True, Mixxx looks solid with straight lines and hardly (if at all) any 3D-like graphics.
But I like gradients, light reflections, and a bit of a 3D effect for buttons, knobs and panels. So if I can create a nice skin which looks a little more 3D, I'll be happy :)
 
[SIZE=1][COLOR=gray]Besides that, I still don't like the way the faders are on the sides instead of the center of the GUI. I'm used to a DJ setup which has the mixer in the center and the turntables on either side. Not the other way around. But that's me :P[/COLOR][/SIZE]

[SIZE=1][COLOR=#808080].[/COLOR][/SIZE]

---

### Post by Miscible21 on 2010-01-14
> **ayampanggang said:**
> sorry to say but you can be assured that mixxx is just the best we have for linux out there =( No no no! This isn't true. If you have a sound card with multiple inputs and outputs and some analogue gear you could use [COLOR=Lime][Xwax]("http://www.xwax.co.uk/")[/COLOR]. It's a no nonsense, streamlined DVS that works well and requires little processing power. (Do yourself a favour and check out [COLOR=Lime][this article]("http://www.djforums.com/content/2009/04/26/xwax-an-open-source-dvs/")[/COLOR]). The draw back is that you do need the appropriate sound card (i.e multiple inputs and outputs for your turntables), preferably serato time coded vinyls, and analog turntables. So even though it's free there is some cost involved  if your don't have the gear. But it still beats paying the earth for Serato that will never be ported to linux. Plus the gear will always be an investment as long as you don't buy cheap CD players in the hope of using serato time coded cd's instead vinyls.

ps. you could use something as basic as a maya 44, but you would still need phono preamps.

---

### Post by psidrum on 2010-04-24
try Deckadance,

just installed it this week version 1.62 works flawlessly with wine 1.1.43 ALSA and wineasio using BCD3000 as controller, on a karmic system

only problem is how to send the audio out to headphone,

---

### Post by Switch_Zero on 2010-05-03
> **psidrum said:**
> try Deckadance,
 
just installed it this week version 1.62 works flawlessly with wine 1.1.43 ALSA and wineasio using BCD3000 as controller, on a karmic system
 
only problem is how to send the audio out to headphone,
 
I like your idea. (Looked up some info on the app).
Deckadance looks nice. Bit more towards the style of N-I Traktor.
But I notice 2 things about it.
**1.** (and I quote) works flawlessly with wine...
I'm looking for apps that don't require Wine.
**2.** It's not OSS. So I have to look for ways to crack it.
And I'm really working out a way to go OSS all the way.
Already replaced my Adobe Photoshop and MS Office with good alternatives.
Only need to replace Virtual DJ and Reason (which will probably be impossible).
And they all have to work with Ubuntu without using Wine (or alike)
 
Still, thanks for the tip.

---

