---
title: "Interactive help with audio in Ubuntu Studio?"
date: 2010-09-03
forum: Ubuntu Studio
---

### Post by Th3Professor on 2010-09-03
Hi!

I have home some decent recording gear... nice cardioid condenser mics, a Mackie mixer, a Delta 1010 rack, a few other things, recently bought a portable Zoom H4n, and I'm running Ubuntu Studio. (And I need to upgrade my system, I think I'm running 2009 Studio.)

Due to my real life responsibilities, I have not had a chance to actually get my li'l home recording studio fully set up. Sadly all of that great gear is collecting dust. 

A long, long time ago in a galaxy far, far away I studied recording... and I've basically forgotten just about all of what I learned. And so, I have to essentially start over.

Where can I get some very easy and very user-friendly interactive help with learning how to use the recording software in Ubustu and setting up the recording gear/hardware to work with it?

I'm figuring that this forum is one go-to-place for that interactive help, though are there any other sources too that anybody knows of?

In addition to the interactive variety, something like howto-blogs or similar would be a great help too.

I know that my gear is compatible. I just need help with learning how to use all of the software built into Ubuntu Studio. JACK, of course. And after that *definitely* Ardour. Lots of help with Ardour would be great. And then pretty much any other of the good apps that work well for recording music and/or composing music.




Thanks!

---

### Post by Darktrax on 2010-09-04
Hi Professor

This could get interesting for both of us.
I also have the mixer, mics, Korg N1, Electric Guitars, Sax etc.

This does NOT mean we are going to have it easy! Audio in Linux can get complicated. see [LINK http://tuxradar.com/content/how-it-works-linux-audio-explained]("http://tuxradar.com/content/how-it-works-linux-audio-explained")

There are incompatibilities between the necessary needs of professional tools like Ardour, Rosegarden+Lilypond, etc., and the way PulseAudio is used in Ubuntu to deliver audio streams from more everyday apps (media players, etc)  The jackd audio server is needed for the best tools, but is not well served by PulseAudio, currently in favour at Ubuntu.

I also need help in figuring how to escape these "one app ceases to work after  some other has been used" funnies. Not that we should end up discouraging ourselves. When one finally gets it to run, it is just very,very good!

PS. Have a look at this link to -->[Ubuntu Based KX Studio at http://kxstudio.sourceforge.net/]("http://kxstudio.sourceforge.net/")
I did not know of it until now, and the write-up seems to address what we face.

---

### Post by AutoStatic on 2010-09-04
> **Darktrax said:**
> This does NOT mean we are going to have it easy! Audio in Linux can get complicated. see [LINK http://tuxradar.com/content/how-it-works-linux-audio-explained]("http://tuxradar.com/content/how-it-works-linux-audio-explained")That article over-complicates stuff. As a 'normal' user you only have to know about PulseAudio (the default sound- DAEMON) and ALSA (the default sound DRIVERS). That's it. If you want to use Ubuntu for audio production add JACK (a 'pro' sound-DAEMON) to that list and FFADO (sound DRIVERS for FireWire audio devices) if you use a FireWire card.

> **Darktrax said:**
> There are incompatibilities between the necessary needs of professional tools like Ardour, Rosegarden+Lilypond, etc., and the way PulseAudio is used in Ubuntu to deliver audio streams from more everyday apps (media players, etc)  The jackd audio server is needed for the best tools, but is not well served by PulseAudio, currently in favour at Ubuntu.PulseAudio has no business whatsoever in an audio production environment. PulseAudio is a 'consumer' sound-DAEMON, as opposed to JACK which is a 'pro' sound-DAEMON. So if you want to make music you don't need PulseAudio. Create a separate music account, disable PulseAudio for that account and use JACK instead. For your day to day stuff use an account with PulseAudio. If you do want to record stuff realtime from Flash movies with your FireWire card, then you might run into problems. But you can't do that either with ASIO drivers in Windows. Hence I don't see these 'incompatibilities' at all, for me they're non-existent.
This is in no way a rant against PulseAudio, PulseAudio is a perfect day-to-day sound-daemon that does its job quite well afaic.

> **Darktrax said:**
> I also need help in figuring how to escape these "one app ceases to work after  some other has been used" funnies.It's really simple: PulseAudio can output/mix the sound of several apps at once, JACK too. That's because they're sound-DAEMONS. ALSA, as a sound DRIVER stack, cannot do this, unless you create custom .asoundrc files and stuff like that, but PulseAudio is designed for this, so use it for this purpose :) Then there's OSS, but once you installed that, well, since it's IMHO an in-between solution between deamon and drivers it will only over-complicate stuff. FYI, I've never used OSS, yeah, when I started using Linux in the 90's.

Best,

Jeremy

---

### Post by Th3Professor on 2010-09-04
Where can I get some very easy and very user-friendly interactive help with learning how to use the recording software in Ubustu and setting up the recording gear/hardware to work with it?

In addition to the interactive variety, something like howto-blogs, videos, or similar would be a great help too.

Thanks!

---

### Post by Pablo_F on 2010-09-04
You can try the chat

#ubuntustudio 
#ardour
#opensourcemusicians

at irc.frenode.net

See also

[www.linuxmusicians.com](www.linuxmusicians.com), wiki and forums
ardour FLOSS manual
ardour.org, forum
youtube, search ardour
google is your friend

Interactive help is hard to find. 

Cheers! Pablo

---

### Post by AutoStatic on 2010-09-05
> **Th3Professor said:**
> Where can I get some very easy and very user-friendly interactive help with learning how to use the recording software in Ubustu and setting up the recording gear/hardware to work with it?IRC, like Pablo_F already said. That's the best way, especially #opensourcemusicians is worth a try.

> **Th3Professor said:**
> In addition to the interactive variety, something like howto-blogs, videos, or similar would be a great help too.There are already some YouTube howto's around, unfortunately they practically all contain all kinds of mistakes and wrong assumptions.
But there are some nice blogs of which the authors know what they're doing:
[LIST][*][http://wootangent.net/](http://wootangent.net/) Has some nice tutorials on how to use softsynths and samplers. And [lsd] is a very knowledgeable person, he also hangs around a lot on #opensourcemusicians.
[*][http://www.linuxjournal.com/users/dave-phillips/track](http://www.linuxjournal.com/users/dave-phillips/track) Dave Phillips is _the_ Linux Audio guru if you ask me.
[*]Check the planet of LinuxMusicians.com too: [http://planet.linuxmusicians.com/](http://planet.linuxmusicians.com/) It might contain some interesting links to blogs.[/LIST]

Hopefully that helps a bit. And I too can recommend the LinuxMusicians.com forum, nice folks, nice community.

---

