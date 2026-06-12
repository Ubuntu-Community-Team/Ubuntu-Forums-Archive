---
title: "Pulseaudio - why is it default?"
date: 2009-05-23
forum: The Cafe
---

### Post by Cape on 2009-05-23
I'm not going to go into detail, but for me and a lot of other people it seems pulseaudio has caused a lot problems, which outweigh whatever tangible benefits pulseaudio might bring to the user. I've found the majority of sound related problems and some other problems on ubuntu can now be solved by "killall pulseaudio". Unfortunately improved integration in 9.04 means that "killall" has a very transient effect on pulseaudio. Therefore I've had to remove the package, when I would rather keep everything standard. Now the first thing I do in every fresh ubuntu install is "sudo apt-get purge pulseaudio".

Do I notice any differences as a result of this course of action? Am I missing some useful features? Yes, everything works. No, what features?

On that second question brings me to another problem, which is the poor integration of pulseaudio on ubuntu. Now I understand one of the neat and most advertised features that pulseaudio has to offer is individual volume controls for each sound related application. A great idea and I understand the long term benefits that can be derived from this. However, on ubuntu the package necessary to use this exciting new feature is not installed and configured by default. This just seems half-assed.

Granted, pulseaudio and its implementation on ubuntu certainly seems to have improved a lot over the past year, but it is clearly not worthy of release calibre. So what was the rational that made pulseaudio default last year in distros like ubuntu and fedora, and why is it still default today in light of these problems when ALSA is fine for most users in the short to medium term?

---

### Post by dragos240 on 2009-05-23
> **Cape said:**
> I'm not going to go into detail, but for me and a lot of other people it seems pulseaudio has caused a lot problems, which outweigh whatever tangible benefits pulseaudio might bring to the user. I've found the majority of sound related problems and some other problems on ubuntu can now be solved by "killall pulseaudio". Unfortunately improved integration in 9.04 means that "killall" has a very transient effect on pulseaudio. Therefore I've had to remove the package, when I would rather keep everything standard. Now the first thing I do in every fresh ubuntu install is "sudo apt-get purge pulseaudio".

Do I notice any differences as a result of this course of action? Am I missing some useful features? Yes, everything works. No, what features?

On that second question brings me to another problem, which is the poor integration of pulseaudio on ubuntu. Now I understand one of the neat and most advertised features that pulseaudio has to offer is individual volume controls for each sound related application. A great idea and I understand the long term benefits that can be derived from this. However, on ubuntu the package necessary to use this exciting new feature is not installed and configured by default. This just seems half-assed.

Granted, pulseaudio and its implementation on ubuntu certainly seems to have improved a lot over the past year, but it is clearly not worthy of release calibre. So what was the rational that made pulseaudio default last year in distros like ubuntu and fedora, and why is it still default today in light of these problems when ALSA is fine for most users in the short to medium term?
I'm not sure cape, but it's very annoying. I like to uninstall it. Either that or try arch :D

---

### Post by yoasif on 2009-05-23
> **dragos240 said:**
> Either that or try arch :DI see this a lot, and I'm not sure I get the point. Why not just install ubuntu minimal instead?

---

### Post by .Maleficus. on 2009-05-23
> **yoasif said:**
> I see this a lot, and I'm not sure I get the point. Why not just install ubuntu minimal instead?
Ubuntu Minimal != Arch.  Never was, never will be.  This topic has been beaten to death in the Cafe so I'm not going to explain but if you're really interested, download Arch and try it out.

---

### Post by Swarms on 2009-05-23
Works more than fine for the majority, the developers just took a leap of faith by including it early.

---

### Post by Bölvaður on 2009-05-23
If there would be a standard, it would be Pulse.

The more people using it the faster it becomes ready, as more people are thrust into testing it. If you have problems with it there is [launchpad]("https://launchpad.net/") to report your problems so it can be fixed.

I had more problems with Alsa than pulse.

---

### Post by SunnyRabbiera on 2009-05-23
Puse is experimental, but very promising, it could fully replace ALSA or OSS on most systems soon.

---

### Post by Simian Man on 2009-05-23
> **Bölvaður said:**
> I had more problems with Alsa than pulse.

I agree.  Also, most of the PulseAudio "bugs" are really just driver problems or obscure bugs in Alsa that are activated by PulseAudio.

---

### Post by Cape on 2009-05-23
> **SunnyRabbiera said:**
> Puse is experimental, but very promising, it could fully replace ALSA or OSS on most systems soon.


I agree completely, but that doesn't mean that it should be installed by default.

---

### Post by scotty32 on 2009-05-23
I had loads of problems with Pulseaudio on 8.10, Amorak would never work unless I killed Pulseaudio. Same goes for other KDE apps, Flash and even the login music. I think it was a case of one audio source at a time?

I eventually figured out I just needed to disable it in Session list to stop it loading and everything was fine.


But once I upgraded to 9.04 everything was fine (though I don't use Amarok now, V2 is horrid :( ).

I haven't had any more issues with it and dont need to kill it at all.

---

### Post by JohnSearle on 2009-05-23
> **scotty32 said:**
> But once I upgraded to 9.04 everything was fine (though I don't use Amarok now, V2 is horrid :( ).

Install V1 instead:

[http://ubuntu-blog.com/how-to-install-amarok-14-in-ubuntu-904](http://ubuntu-blog.com/how-to-install-amarok-14-in-ubuntu-904)

---

### Post by Polygon on 2009-05-23
because the old system was horrid. ESD would lock the soundcard and then make it so certain programs could not access it (audacious anyone?)

pulseaudio is in every sense of the word, better. I have tried everything under the sun and i have not been able to get pulseaudio to screw up, i'm at a loss on why everyone complains it doesn't work. Sound editing, music, video, youtube, all works....at the same time. My guess is that the drivers for your motherboard/soundcard are wonky and that is causing the problems, not pulseaudio.

---

### Post by michaeldt on 2009-05-23
The only problem I get with pulseaudio is stuttering in music playback. It's hard to replicate, seems to be quite random. But it happens in Rhythmbox, songbird and videos played in firefox. Killing pulseaudio fixes it as does a reboot. Hopefully it'll get sorted soon.

---

### Post by gnomeuser on 2009-05-23
[An interview to shed a little light on Pulseaudio](http://jaboutboul.blogspot.com/2009/05/sound-of-fedora-11.html)

---

### Post by Kareeser on 2009-05-23
> **Cape said:**
> I agree completely, but that doesn't mean that it should be installed by default.

I think Pulseaudio _should_ be installed as default. Its benefits-on-paper outweigh the potential conflicts and bugs, and it's important that we get new technologies bug-free as soon as possible, instead on relying on old standards that have blatant limitations that must be worked around. Yes, this means there will be problems, but I'd much rather have Pulseaudio now, than wait 10+ years while a very small group of volunteer testers slowly discover bugs.

You might say "why do we have to reinvent the wheel?", and the answer to that is simple: "because we're better off travelling with rubber tires instead of hand-carved bumpy wooden spindles".

If you don't want to participate in the testing of Pulseaudio, that's fine! You can revert back to ALSA until Pulseaudio "goes gold", so to say, we won't fault you for it!

Remember, Ubuntu was originally supposed to be "Debian with newer technology", and that tradition still holds, with each subsequent version taking new code straight out of the unstable branch of Debian repositories.

Pulseaudio is just another one of these new technologies that will be great once it's been properly tested and fixed.

For the record: In my experience, I have had zero problems with Pulseaudio. If I did, and the only workaround was to uninstall PulseAudio, I'd preceed that with a bug report to launchpad. Simple.

---

### Post by Mr. Picklesworth on 2009-05-23
Here is a nice example of PulseAudio's magic:
[http://weblog.savanne.be/170-pulseaudio-bluez-fantastic](http://weblog.savanne.be/170-pulseaudio-bluez-fantastic)
It's totally justified.

A recent story, as well! I was helping someone troubleshoot Windows audio problems. Granted, the final output it delivers tends to be clear for general purposes and low latency, but it's incredibly difficult to tell Windows which device an audio stream should go to.

So I was trying to get it talking with a USB headset. A stream started playing / recording via the internal speakers. I EXPECTED to open up Volume Mixer, find the stream, tell it "output to headset instead" and never think about it again. To my shock and amazement, such an option (which I am used to from PulseAudio's custom volume control tool) was not there! I had to instead set the headset as the default audio device and then restart the application so its stream would go to the appropriate device.


Unfortunately, Fedora continues to be the only distro which sensibly applies bleeding edge audio technology, with functioning Intel audio drivers and the fresh new bluetooth stack which does headsets out of the box without needing a terminal. (Just Connect and it appears as a device with PulseAudio).

I'll forgive Ubuntu for the latter and cross my fingers for a bluez-gnome repository :)


Finally, not all audio problems are PulseAudio related. Audio (with ALSA) is just a pain for some reason, and PulseAudio highlights the problem by stretching it to its limits. With 9.04, I have finally been witness to the problems people describe since I have a particular Intel sound card. (Coincidentally, with this release Intel seems to have completely broken the vast majority of their drivers which I use, getting to the point that the proprietary Nvidia driver is the only major one I don't hate).

When I played with Fedora recently, I noticed a package for OSS support with PulseAudio. Never looked into it, but it appeared at a glace we *may* be getting that magic touch to have a pragmatic audio solution bundled with a fantastically awesome mixer.

---

### Post by mikewhatever on 2009-05-23
I also keep removing pulseaudio and think it shouldn't be there by default. Ubuntu is supposed to be a solution for home and office users with sound working out of the box, and not the testing ground for new packages. Fedora can allow itself that luxury, because, contrary to Ubuntu, it is the testing ground. Having pulseaudio installed was a poor choice in 8.04, and it's still far from perfect in 9.04.
PS: and no, I am not going to try arch.

---

