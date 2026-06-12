---
title: "[Idea] General sound equalizer"
date: 2007-06-24
forum: Ubuntu Brainstorm
---

### Post by lemsto on 2007-06-24
Some apps have an equalizer integrated but i'm looking for a general one that can be set in Gstreamer itself (or ALSA ???)  I use an Hifi amp and a headphones that don't have same "frequency response". I'd like to be able to set/register some general equalization for ALL apps i use.
I couldn't find any actual project that integrate this kind of functionality.

[edit]: As Pulseaudio is going to be next Gnome sound server, does someone know if it integrates an equalizer?

---

### Post by lemsto on 2007-06-27
I was also thinking about some sound effects that could be added directly to the output??

---

### Post by CompactDestruction on 2007-06-27
I would love this idea too :)

---

### Post by TheVault on 2007-06-27
Oh sweet, I like this idea.
For windows, if your using Windows Media Player, Realone and I think some other plays can have this, you can download this plugin called "DFX Enhancement" and it really enhances the sound and quality of your music. You can turn it on and off at will, and you can see the changes right from the start. 

Having an enhancer or equalizer is a great idea. Good one :guitar:

---

### Post by lemsto on 2007-06-29
> **TheVault said:**
> Oh sweet, I like this idea.
For windows, if your using Windows Media Player, Realone and I think some other plays can have this, you can download this plugin called "DFX Enhancement" and it really enhances the sound and quality of your music. You can turn it on and off at will, and you can see the changes right from the start. 


Yeah but i was thinking of an equalizer that can work directly to the sound output, i mean working on any sound that comes out!!!! Media players, _games_, voip clients, etc. Because a plugin would work only with apps that are compatible with?!

---

### Post by jspangler on 2007-07-04
Awesome idea.

---

### Post by oomingmak on 2007-07-04
Definitely +1  for the equalizer

(but you can keep the 'sound effect' though).

 :)

---

### Post by amoore on 2007-07-09
+1

---

### Post by chipotlehero on 2007-07-10
Since many audio playback applications (including the included Rhythmbox) don't have graphic equalizers, or equalizers at all for that matter, I think it would be a cool idea to include one that you could use with via the sound controls, that had presets and other standard features.

---

### Post by tgoose on 2007-07-10
I don't see any real need for an EQ... it's certainly possible to do this through JACK, but I'd have thought that anyone that needs equalisation will be happy to use JACK anyway?

---

### Post by 23meg on 2007-07-10
I've merged the two threads where the same idea is discussed.

---

### Post by san_ignucio on 2007-07-10
there's actually one for windows called SRS Audio Sandbox, that makes system-wide equalization by creating a virtual sound card. It isn't only EQ but a complete audio enhancement, including virtual 3D, and other goodies.

It'd be fantastic to have an app like this one in Ubuntu.

---

### Post by lemsto on 2007-07-13
> **tgoose said:**
> I don't see any real need for an EQ... it's certainly possible to do this through JACK, but I'd have thought that anyone that needs equalisation will be happy to use JACK anyway?

Games i play, gstreamer apps (rhythmbox, soundjuicer, ...) and some other apps i use can't use JACK!!

---

### Post by tgoose on 2007-07-15
Gstreamer does work with JACK! It's not ideal but possible. I'd like to see JACK pushed as an **all-purpose**  sound server in conjunction with ALSA rather than purely concentrating on audio creation since I think it has a lot of potential. It would need a less involved GUI (the present one is perfect for someone working with audio, of course, but I really think it could achieve something for consumers, too.)

Mind you, if the current effects integrated into JACK could be modified to run without, that would be fine as well.

---

### Post by lemsto on 2007-07-19
> **tgoose said:**
> I'd like to see JACK pushed as an **all-purpose**  sound server in conjunction with ALSA rather than purely concentrating on audio creation since I think it has a lot of potential. 
As said on JACK website: "JACK was designed from the ground up for **professional audio** work, and its design focuses on two key areas: synchronous execution of all clients, and low latency operation." It doesn't include features that are necessary for a **desktop** sound server. I'm thinking about multi-user use of the soundcard or sound trough network... Features that, i think, would make increase JACK latency and/or responsiveness ??
PulseAudio IMO is best-suited to be integrated as the default **desktop** sound server. But it does not include any EQ hehe

---

### Post by kapula on 2007-07-19
Many soundcards, even integrated sound chips have an EQ and it is accessible through software. At least C-Media and Realtek include it in their driver bundles. It's in that little system tray icon most people simply turn off to save some miniscule amount of resources.

I've enjoyed it immensely while using Windows, because it works for everything the computer plays. Games, music, videos, no difference. I've noticed that the sound output of many integrated cards is biased towards some end of the spectrum, or the output  needs adjustment to get the best out of cheap computer speakers. I too use headphones occasionally and switch presets when listening with them, because the corrections for my cheap speakers makes it sound bad with the headphones and vice-versa.

That was one thing I immediately missed when I switched to Ubuntu.

---

### Post by easyease on 2007-08-12
+1 for the all encompassing eq idea, this would make ubuntu very media friendly indeed.

---

### Post by crjackson on 2007-08-20
Count me in too.  Default sound is crap.

---

### Post by Kosimo on 2007-08-21
+1 !!!!  Definitely !!!  This will solve lots of my problems. Getting the sound I want in Rhythmbox and all my games at once and for all.

---

### Post by Chymera on 2007-08-22
yep, definitely, a set of presets, and some reverberation effects (like the ones you get with the standard CMedia drivers under ms win) would be great.

---

### Post by lemsto on 2007-10-05
up :)

---

### Post by bb10 on 2007-10-06
+1 for EQ/sound enhancer :)

---

### Post by FuturePilot on 2007-10-07
I totally love this idea. If there's anything I miss from Windows (I can't believe I just said that:p) it's being able to set a global EQ.

---

### Post by skotadi on 2007-10-07
Yes definitely.  My Creative Live! soundcard Windows drivers included sound sweetening software (which I assume used some hardware EQ and stuff on the card).  My sound was really much better in windows, and it's something I've really missed since switching.  A general EQ would be *very* welcome

---

### Post by FuturePilot on 2007-10-07
> **skotadi said:**
> Yes definitely.  My Creative Live! soundcard Windows drivers included sound sweetening software (which I assume used some hardware EQ and stuff on the card).  My sound was really much better in windows, and it's something I've really missed since switching.  A general EQ would be *very* welcome

Yes. I also have a Sound Blaster Live! and I could do some pretty cool stuff with it in Windows, but I can't do too much with it in Linux. I'm pretty sure it was equalizing off the hardware too.

---

### Post by Nonno Bassotto on 2007-10-08
+1

---

### Post by rcorlett on 2007-10-13
+1 

my monitor speakers are VERY quiet and are only a decent volume with apps like gxine where i can boost the freqs

---

### Post by Nervo on 2007-10-14
+1 :guitar:

---

### Post by FuturePilot on 2007-10-14
From what it sounds like, PulseAudio is the answer to this. However it still needs to be fully implemented into the system. Hopefully this will happen in Hardy.

This is from the PulseAudio Wiki page
[https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")
> L. is using an average-quality speaker set. It needs some equalization to sound right, however his audio player of choice (Rhythmbox :P) does not yet feature an EQ. He simply modifies the overall equalizer and everything that his PC plays now sounds good on his setup.

:)

---

### Post by LeovonKlenze on 2007-10-16
+1
An equalizer would be very nice!

---

### Post by patambrosio on 2007-10-30
+1 and dugg too.

let's get some attention, [digg it]("http://digg.com/linux_unix/Idea_for_the_next_Ubuntu_release_General_sound_equalizer").

---

### Post by Centx on 2007-10-31
+1 and dugg, we could really use a global and global per-app EQ for that matter, and if it's possible to get optional effects without too much latency I'll have that too, even if it's just for trying out, maybe others than me could need it?

---

### Post by BlueSkyNIS on 2007-10-31
Definitely +1 for the equalizer :)

---

### Post by qix on 2007-10-31
I would love an equalizer. I'm not an audio technician, but I'm a musician. Sometimes I might wanna mix with the EQ to make it easier to listen to stuff in a song, or similar.

And by the way: Equalizer should be a general tool available. It's just so common, and it's one of those things where Windows is better - it serves the users needs.

---

### Post by mato2 on 2007-11-05
where can I find +1......please!!! I've never met with it and google says stupidity

---

### Post by teasum on 2007-11-10
+1 from me as well.

---

### Post by FruitieX on 2007-11-12
+1 and dugg. This is the only thing I could think of that I miss from Windows. :)

---

### Post by Shin_Gouki2501 on 2007-11-12
"sounds" like a good idea
+1

---

### Post by hyperair on 2007-11-13
I'm all for the equalizer idea. Gstreamer ugly already has a plugin that enables equalizer usage, but the only application I know which uses the equalizer is Exaile. I certainly wouldn't mind if a global equalizer could be done such that I can use it even with MPlayer and Totem =P

---

### Post by Awalton on 2007-11-14
Good News Everybody.

[Bug about GStreamer's Equalizer; currently in GStreamer-plugins-bad, soon to be in GStreamer-plugins-good].
[http://bugzilla.gnome.org/show_bug.cgi?id=415627](http://bugzilla.gnome.org/show_bug.cgi?id=415627)

[Equalizer Widget for Rhythmbox, updated to support GStreamer's equalizer].
[http://bugzilla.gnome.org/show_bug.cgi?id=76522](http://bugzilla.gnome.org/show_bug.cgi?id=76522)

Similar one should be out there for Totem... somewhere... but at least GStreamer's Eq is of "good enough" quality to be in -good now. If all goes well between now and GNOME 2.22, this should be a solved problem.

(PulseAudio, if it becomes the next sound server, would still need an Eq for global equalization, but most people aren't that pedantic).

---

### Post by hyperair on 2007-11-14
Awesome!!

---

### Post by k99goran on 2007-11-16
+1

This is one thing I've been missing in Ubuntu, a DSP.

---

### Post by Next.Step on 2007-11-17
+1

---

### Post by Octagonal on 2007-11-20
+1

---

### Post by light50 on 2007-11-21
+1:guitar:che' bro

---

### Post by geokker on 2007-11-29
I can't believe there's not an equalizer in the sound prefs. Come on Linux, stop dragging your feet and join the 21st century!

---

### Post by tjagoda on 2007-11-29
+1

---

### Post by lemsto on 2007-12-03
As i think i should part of Pulseaudio, i made a "enhancement" ticket in their bug tracker
see here:
[http://www.pulseaudio.org/ticket/174](http://www.pulseaudio.org/ticket/174)
So waiting for response from the pulseaudio team

---

### Post by info2 on 2007-12-06
I wonder if PulseAudio offers some kind of interface to set up the amplification of different ranges of frequencies.
PulseAutio itself is running file on my ubuntu box ("8.10").

If so it would be easy to create a GUI / TrayIcon to set values to it.

There are some command line interfaces to PA. I will dig into them, maybe there is something that can be used.
If somebody of you find a way let us know.

---

### Post by hyperair on 2007-12-06
"8.10"?! Awesome! Could you get me a copy please? I'm dying to know what Hardy + 1 looks like. xD

---

### Post by info2 on 2007-12-09
No GUI differences to see until now.
You can try to install Murrine Engine in Gutsy but there is no Ubuntu Murrine Theme by now as far as I know.

But I love it to see every single day what new packages are in the repos :)

---

### Post by hyperair on 2007-12-09
Eh well, just so you know Hardy = 8.04.

---

### Post by lemsto on 2007-12-17
up! :D

---

### Post by Kzin on 2007-12-27
Is it too late for another +1?:guitar:

---

### Post by crjackson on 2007-12-27
> **Kzin said:**
> Is it too late for another +1?:guitar:

It's never too late.

---

### Post by OliW on 2008-01-13
> It's never too late.Well in that case, +1

I'd love this to feature into PulseAudio before Hardy is finished. It has been [suggested and assigned in PA]("http://www.pulseaudio.org/ticket/174") but I can't see any development happening on it.

---

### Post by tuesday20102001 on 2008-02-29
This EQ idea would be great for linux. Found a need for it when purchasing high quality logitech system with subwoofer that puts out too much bass through ubuntu when listening to general audio. These EQ apps are already used in windows, but not available for linux. Would be great if there was a general app that did this like kmix add on or something.:)

---

### Post by teetee on 2008-03-03
+1(000)

---

### Post by keller999 on 2008-03-03
If you'd like to support the idea of a Graphical EQ for PulseAudio, please vote up this idea at Ubuntu Brainstorm:

_[COLOR="Blue"][idea #2984: Equalizer]("http://brainstorm.ubuntu.com/idea/2984/")[/COLOR]_

So, if you've +1'd here, make your vote count!  Let's get some of these great sound tools in Ubuntu.

-Keller

---

### Post by almalaci on 2008-03-05
+1

---

### Post by goanga on 2008-03-19
+1

---

### Post by MofT on 2008-04-01
+1

---

### Post by quasar277 on 2008-04-01
+1

You CAN live without it but it makes a great adition.

I have a creative audigy and in windows it comes with a nice software pack  (including equalizer) which replaced the native windows app called "volume" - eveytime I'd use someone else's PC and wanted to fiddle with the sound I always found it so strange microsoft never bothered to improve it - and they have that same ugly tray icon for... decades! :)

---

### Post by stenyak on 2008-04-10
+1!

---

### Post by FuturePilot on 2008-04-10
I thought PulseAudio was supposed to have an equalizer, but I don't see one anywhere. :confused:

---

### Post by hyperair on 2008-04-10
I agree. I've read in more than one place about PulseAudio geting a system-wide equalizer, but I don't see it anywhere either.

---

### Post by FuturePilot on 2008-04-11
I found this, but it hasn't been updated in a long time. No clue as to how far it's gotten
[http://pulseaudio.org/ticket/174]("http://pulseaudio.org/ticket/174")

---

### Post by stiansoftcore on 2008-04-12
any news on this one?

---

### Post by xelapond on 2008-04-12
This is half implemented in ALSA.  Go into the command line and type alsamixer.  I think if someone just wrote a GTK Gui for it it would be pretty good.

---

### Post by FuturePilot on 2008-04-13
> **xelapond said:**
> This is half implemented in ALSA.  Go into the command line and type alsamixer.  I think if someone just wrote a GTK Gui for it it would be pretty good.

That would be a volume control, not an equalizer. There are many front ends to Alsamixer. Most notably
```
gnome-volume-control
```

---

### Post by xelapond on 2008-04-13
> That would be a volume control, not an equalizer. There are many front ends to Alsamixer. Most notably

Oh, sorry.  It looked like it had a lot of dials, so I assumed it was an EQ:)

---

### Post by LexRoss on 2008-04-14
It would also help laptop users like myself to get decent quality sound from built-in speakers. Should be available from the same speaker icon on the launch bar. It pisses me off at times how GNOME is all fragmented while KDE has all bits and pieces nicely integrated just like UNIX tools. And I believe KDE comes with a general sound EQ as well. Still, I use Ubuntu as my office desktop for the sake of simplicity. Way too much settings in KDE, it's just too fancy. So there are trade offs as usual. Hope we'll see EQ in Ubuntu soon as it is coming to more laptops.

---

### Post by rockin_goliath on 2008-04-15
PulseAudio is the system wide sound server in Hardy. JACK is not designed for this, since its for professional audio, a resource hog, and has to be manually started.
In the most recent version of Gstreamer, the equalizer has been moved to plugins-good.
A system wide equalizer would be a start, but i think it would be better implemented by incorporating equalizers into individual audio applications. My equalizer settings for listening to music are different than what I use to watch movies which are different from flash in Firefox etc. 
What would be REALLY cool would be to incorporate an equalizer into the pavucontrol application (a volume control application for PulseAudio, check it out in the Hardy repos). That way we could control both the volume and equalizer settings for individual applications from one convenient location, which would also relieve developers from having to put equalizers in their own applications.

---

### Post by perseas on 2008-04-16
+1

---

### Post by Bd0g on 2008-04-21
Let me just add a +1 

"One EQ to rule them all, One EQ to find them, One EQ to bring them all and in the software bind them"

---

### Post by Erik. on 2008-04-23
+1

---

### Post by psyke83 on 2008-05-11
> **lemsto said:**
> Some apps have an equalizer integrated but i'm looking for a general one that can be set in Gstreamer itself (or ALSA ???)  I use an Hifi amp and a headphones that don't have same "frequency response". I'd like to be able to set/register some general equalization for ALL apps i use.
I couldn't find any actual project that integrate this kind of functionality.

[edit]: As Pulseaudio is going to be next Gnome sound server, does someone know if it integrates an equalizer?

Hi,

I have just finished writing up a tutorial to enable EQ (or rather, LADSPA audio processing) in PulseAudio. See my guide here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by BlueSkyNIS on 2008-05-12
Wow, thanks psyke83, will try that later... :KS

---

### Post by vprasaj on 2008-05-17
+1 This is a need... MS has it. Here, in ubuntu (well, mint) i miss it.

Only audacious has working one(build-in). (eq-audacius 31 band is not recognized in 1.5.0)

---

### Post by upa_bigtree on 2008-05-19
+1

---

### Post by charlesE on 2008-05-19
I just released a equalizer plugin for ALSA that may accomplish what you're looking for. You can adjust the frequency response in realtime using and ALSA compatible mixer control, e.g. alsamixergui.

You can find it here:
[http://www.thedigitalmachine.net/alsaequal.html](http://www.thedigitalmachine.net/alsaequal.html)

It works for me but please keep in mind that it's an early development release.

Cheers,
Charles

---

### Post by almightybunghole on 2008-05-20
:guitar:Yeah count me in too, got to this thread looking for exactly this, need an EQ alright!:guitar:

---

### Post by hesjnet on 2008-05-30
+1

My 2.1 speakers is way too heavy on the bass and i have no hardware ways to control it.

---

### Post by Gripp on 2008-05-30
> **charlesE said:**
> I just released a equalizer plugin for ALSA that may accomplish what you're looking for. You can adjust the frequency response in realtime using and ALSA compatible mixer control, e.g. alsamixergui.

You can find it here:
[http://www.thedigitalmachine.net/alsaequal.html](http://www.thedigitalmachine.net/alsaequal.html)

It works for me but please keep in mind that it's an early development release.

Cheers,
Charles

that was you eh?!  i'm fairly sure that is what i used (i'm on another machine now, so...)
but it if it is then you helped me solve a big problem with my card, across both linux and windows!

the surround sound on was turned all the way down. so rear speaker sounds were very faint.  this was in both OS's until i fixed it using that app.

so, again, THANKS!

---

### Post by groupmsl on 2008-10-18
+1

---

### Post by ShawnX on 2008-11-20
+1 for an all-encompassing equalizer!

---

### Post by caglarersoz on 2008-12-23
+1 we need it

---

### Post by obscur156 on 2009-04-13
+1 for the EQUALIZER,it would be great.

---

### Post by smartboyathome on 2009-04-13
For everyone for the equalizer, think of it this way:

Software equalizers usually require a fair bit of CPU power whenever audio is being played. This means that there are less resources for all the other apps, and because of that, Ubuntu becomes heavier, and slower. Would an equalizer be worth the performance hit you would get?

---

### Post by oomingmak on 2009-04-14
> **smartboyathome said:**
> Software equalizers usually require a fair bit of CPU power whenever audio is being played. This means that there are less resources for all the other apps, and because of that
That applies to *any *software that you run. Why would EQ software be any different?

> **smartboyathome said:**
> Ubuntu becomes heavier, and slower. Would an equalizer be worth the *performance hit* you would get?
On what basis are you saying that there would be a noticeable performance hit? Do you have any data to support your assertion? (e.g. % of PCs that would be detrimentally affected, and by how much). You are making a sweeping assumption and concluding that everyone should be denied the option to enable such functionality just because some people have very low powered computers. Surely those people would just not enable the EQ (just like they won't enable Compiz if they don't have the CPU power or inclination).

---

### Post by smartboyathome on 2009-04-14
> **oomingmak said:**
> That applies to *any *software that you run. Why would EQ software be any different?

I am just saying, is a software equalizer worth the high CPU usage.

> **oomingmak said:**
> On what basis are you saying that there would be a noticeable performance hit? Do you have any data to support your assertion? (e.g. % of PCs that would be detrimentally affected, and by how much). You are making a sweeping assumption and concluding that everyone should be denied the option to enable such functionality just because some people have very low powered computers. Surely those people would just not enable the EQ (just like they won't enable Compiz if they don't have the CPU power or inclination).

Personal experience, as well as the experience from others (see [here]("http://wiki.archlinux.org/index.php/ALSA#System-Wide_Equalizer")). I never said that people shouldn't have the option (heck, the link I posted already tells you how to enable it). The discussion here is on whether it should be default, and I am saying why I don't think it should be. And, to top it off, my computer isn't low powered. It is very modern (bought it in the last year).

Please, don't attack me when I did nothing wrong.

---

