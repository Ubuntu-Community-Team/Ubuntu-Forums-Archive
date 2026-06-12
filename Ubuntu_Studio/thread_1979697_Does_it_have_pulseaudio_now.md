---
title: "Does it have pulseaudio now?"
date: 2012-05-13
forum: Ubuntu Studio
---

### Post by JC Cheloven on 2012-05-13
Hi, I used ubuntustudio karmic and couldn't be happier by the time. RT kernel which was also good for any other stuff, and so. It hadn't pulse. 

For one reason or another, from lucid onwards I opted for building my audio studio pc on top of Lubuntu. It hasn't pulse either.

As 12.04 has switched to xfce, it caught my interest. I see it has pulse now. 

Could you please tell your experience? It used to be rather terrible ;) But maybe it succeeded at improving the behaviour of plain alsa in some way? I'm considering going back to UbSt, hence my question.

Thanks in advance
JC

---

### Post by lykwydchykyn on 2012-05-13
My DAW computer is a little on the old side, and it was doing well under Lubuntu, but I installed Ubuntu Studio 12.04 last week because the upgrade blew up.

I found that pulseaudio killed my performance, and I ended up removing it because I can't see what purpose it serves.  After dumping it, and several other loads of ballast (cups, NetworkManager, bluetooth, etc) over the side, I almost have decent and reliable performance again.

Maybe on better hardware pulseaudio is worth the extra resources, but not for me.

---

### Post by JC Cheloven on 2012-05-14
> **lykwydchykyn said:**
> (...) Maybe on better hardware pulseaudio is worth the extra resources, but not for me.

Thanks for sharing! 
My pc is not as old, I guess it could comfortably run pulse if needed (as well of, for example, compiz, or whatever), and yet being usable as a DAW. 

But I'm wondering about the benefit of doing so. I'm not clear about the "extra resources" mentioned. What can pulse be used for in audio-related work? Someone has found an advantage of using it for a particular task?

I mean, if a random guy likes pulse and decides to use it, it's nothing for me to think about. But if the DEVELOPERS OF UBUNTUSTUDIO decide to pack it, there must be something I'm missing 
:confused:

---

### Post by lykwydchykyn on 2012-05-14
This is just a guess, but I think it comes down to application compatibility.  When i was just running JACK on ALSA, if I wanted to (for example) just play back an audio file, I had to make sure I was using a JACK-compatible audio player, because JACK owned the audio hardware.

More applications are likely to be pulseaudio-compatible than JACK compatible, since pulse is used on the desktop.

---

### Post by sgx on 2012-05-14
To me, pulse has always been buggy, and  without a clear purpose,
lacking usability, and offering only an added layer of complexity that most people never benefit from. Like a third axle on the Mercedes.
It's inclusion surely diminished the potential userbase of computer savvy musicians who flailed around one too many hours trying to get a working linux daw, and frightened away many others away who read such disasters in the search engines. Blame the distro maintainers for dismal linux uptake. Not like pulse is the only blunder.

I tried a new distro, and you couldn't even get to the desktop
without choosing a default search engine for Chromium. I never
even use that bugly rash browser anyway, so one might imagine how long that session lasted. Freedom in linux is sadly diminishing,
especially for the new user, who doesn't know the potential
enjoyment and power hidden behind redundant and boring eye candy.

Somebody wants to play some mp3, watch a dvd, record a song? None of that requires pulse.

As long as pulse is not a dependency, or a default, I hope the
project advances, and creates a large and happy user base. Make
it an option, and nothing more.
Cheers

---

### Post by Guilden_NL on 2012-05-14
I am no fan of Pulse, but understand the Canonical folks wanting to have something they can maintain some control over.  I run Lubuntu on every single non-server system we have, using ALSA for audio.  However, I have a monster desktop that has an 8.1 channel sound system that I would like to use.  Three hours wasted last weekend trying to get ALSA set up and it never happened. I get sound out of the front left channel and that's it.

With Pulse, there is a glimmer of hope that Canonical will get the bugs out and perhaps Ubuntu of all variants will provide a better out of the box audio experience.

---

### Post by JC Cheloven on 2012-05-14
> **lykwydchykyn said:**
> This is just a guess, but I think it comes down to application compatibility.  When i was just running JACK on ALSA, if I wanted to (for example) just play back an audio file, I had to make sure I was using a JACK-compatible audio player, because JACK owned the audio hardware.
More applications are likely to be pulseaudio-compatible than JACK compatible, since pulse is used on the desktop.
That's true. Pulse makes sense for a non-specialized desktop, as many users will expect to hear sound for several concomitant applicatios if they run them, and alsa can't do that out of the box. But, UbuntuStudio?

@sgx: One thing is certain: you don't have a lukewarm opinion :D Thanks for sharing! I'm trying to not judge based on my outdated experiences (3 years ago), but what you said would have been in fact my first impression answer.

[quote=Guilden_NL](...)I have a monster desktop that has an 8.1 channel sound system that I would like to use. Three hours wasted last weekend trying to get ALSA set up and it never happened. I get sound out of the front left channel and that's it. (...)[/quote]
Hi, thanks for your answer. At least this use case could be, in theory, a point of pulse. But again, for a desktop. An audio dedicated pc... would need that? 
I'm thinking (applicable to your problem also): In the setup of Jack, you can specify how many outputs your device has. If it is 8.1, it should be 9, or whathever. A single audio clip in Ardour, and thus a track, can have as many channels (not limited to mono/stereo). Everything should show up in Jack's connections, and you should be able to route any channel to any output. Perhaps not nice for an average joe user, but, hey, we're talking about daw's! 
Anyway, I hope the above can be of help for your use case. I did similary for a firewire device I have.

---

### Post by lykwydchykyn on 2012-05-14
> **JC Cheloven said:**
> That's true. Pulse makes sense for a non-specialized desktop, as many users will expect to hear sound for several concomitant applicatios if they run them, and alsa can't do that out of the box. But, UbuntuStudio?


That was my feeling as well, but then UbuntuStudio ships with a lot of things that aren't DAW-oriented, like browsers and chat clients and whatnot.  To be fair, it's not *just* a DAW system; it has video and graphics tools as well, and one could argue that it's more of a desktop system for people who like to be creative than a turnkey DAW system.

Still, it's all pretty easy to uninstall if you want to tighten and lighten the load.

---

### Post by jejeman on 2012-05-15
I use Ubuntu Studio not just for audio creation, but also for video editing and graphics creation. So, usualy I install all apps.

What I'm missing is alternate instaler. Live dvd is good, but we need alternate instaler also. The good thing about it is selection of task meta packages. So on DAW pc one can install only audio packages.

As a long term user I don't need live dvd. Alternate instaler is fine for me.

JC Cheloven alternate instaler could be answer for you, there you could select just audio tasks, but 12.04 doesn't have one. As for pulseaudio I don't mind it, if it gives me trouble I simply turn it off.

What could be made is more tasksel options. Existing options, plus ones that not include pulseaudio, etc. I don't know how much work is needed to make meta packages, but more metapackages and alternate instaler can give more flexibility to the users.

As I see Ubunutu Studio is oriented to new users and maybe to new linux users (like Ubuntu), although makeing music in linux is not (still) for linux beginners.

I don't know, maybe from us, the old users, is expected to use mini.iso and build our systems. Which is not that simple, but with variety of specialised metapackages would be much easier.

---

### Post by lykwydchykyn on 2012-05-15
An alternate DVD would be nice, but if you install any minimal version and run tasksel, there are installable tasks for the various ubuntu-studio tasks.  I don't know if it gives you the lowlatency kernel, though.

---

### Post by JC Cheloven on 2012-05-15
> **lykwydchykyn said:**
> Still, it's all pretty easy to uninstall if you want to tighten and lighten the load.

[quote=jejeman]JC Cheloven alternate instaler could be answer for you, there you could select just audio tasks, but 12.04 doesn't have one. As for pulseaudio I don't mind it, if it gives me trouble I simply turn it off.[/quote]
Yep, building from a text-only system is a nice idea. I remember once I did, but after a month, I still was installing now and then things I didn't realize I needed. My conclusion was: much less work to take a pre-built setup.

OK, guys, as you suggest the way to go for me will be (more than likely) stopping or uninstalling pulse. To end my questions, could you please have a look to these methods I have in my old notes, to tell if they're still correct?

To stop pulse: create file ~/.pulse/client.conf, put a line "autospawn=no" in it. Then, "pulseaudio -k" at terminal stops pulse, "pulseaudio -D" restores it.

To remove pulse:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio 
sudo apt-get autoremove 
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui 
sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer 
reboot
```

Still applicable nowadays?

---

### Post by lykwydchykyn on 2012-05-15
I just purged the pulseaudio package, and let apt take its course.  I'm not sure the rest of that is necessary.

---

### Post by jejeman on 2012-05-15
Yes JC Cheloven, the method you described for stoping pulseaudio is the same that I use, and it is still valid.

I never uninstalled pulseaudio, so I can't tell you about that, but I never had the need for that, because stoping it is enough.

---

### Post by JC Cheloven on 2012-05-15
Ok, thanks, marking as solved then.

Best of luck to you all 
JC

---

