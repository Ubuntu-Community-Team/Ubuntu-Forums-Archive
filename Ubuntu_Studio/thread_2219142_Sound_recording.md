---
title: "Sound recording"
date: 2014-04-23
forum: Ubuntu Studio
---

### Post by stevie5 on 2014-04-23
Hi there,

I would like to kill my XP-Installation on my desktop in order to install UBUNTU-Studio on it.
Hardware:
Intel-PC with 2GB RAM, 40GB HDD, and some kind of Dualcore Processor.Onboard Soundcard, Ethernet-Card 
and 4 USB. Also OnBoard Garphics-Adapter.

_What should the box do:_

In our Bandroom, we would like to record some session with this box and convert the recording to MP3. Until now we have used Cubase, but never got to the point of understanding it all,
cause it's way to mighty and for our purposes overloaded. Due to only 2GB RAM it crashed quite often.
No we do run a Behringer Xenyx 2442FX with a USB-Audiointerface called UCA222. 
What we are looking for is a Software similar to Apples "GarageBand" easy to use and easy to convert recordings to MP3.

Which Software should I use if would like use UBUNTU as my new OS.

cheers,
Stevie

---

### Post by jejeman on 2014-04-23
Since it is a stereo recording you can use Audacity, even on windows too.

---

### Post by stevie5 on 2014-04-23
well to be honest! I don't like M$ too much. I have always been a friend of the open source thoughts.
So is it a good idea of installing UBUNTU-Studio 14.04, or is there no need for this "Studio" and one could achieve
the same by installing the regular UBUNTU 14.04. TLS ?

Cheers,
Stevie

---

### Post by m-dw on 2014-04-23
> [COLOR=#000000]So is it a good idea of installing UBUNTU-Studio 14.04, or is there no need for this "Studio" and one could achieve[/COLOR]
[COLOR=#000000]the same by installing the regular UBUNTU 14.04. TLS ?[/COLOR]

Ubuntu Studio is the better option for audio production.  The kernel has been optimised for low latency so you'll get the most out of your audio hardware.   Your machine's specifications are similar to mine (slightly better - I have only a single core CPU).  It should work well - probably much better than Windows XP.  And the onboard graphics adapter will probably play nicer than a flashy 3D card that needs a proprietary driver (note to self).

You don't have a huge amount of disk space to play with, so if you can fit an internal SATA drive for /home (where user data is stored) you'd have more room for recording stuff.  The installer will give you all you need for audio production by default.  I've never used GarageBand.  It seems to combine music production and music recording into a single application.
 
Ardour 3 will give you a digital audio workstation for multi-track recording.  It can also act as a host for LADSPA plugins (sound processing), or you can use external effects processors.

Hydrogen is a usable drum sequencer with a variety of built sample kits - but you won't need it if you have a drummer!

There are a number of synthesizers available in the repositories.  I've only really used zynaddsubfx (superseded by yoshimi) but others will be more knowledgable.
You might also use JAMIN for post-production mastering.

For simpler recording needs there is Audacity which you may have used on Windows.  I've also used it to isolate and slow down guitar solos as a learning aid.  There's lots of other stuff too, from metronomes and tuners to DJ style samplers and loopers, which you'll discover as you start using it.

---

### Post by jejeman on 2014-04-23
> **stevie5 said:**
> well to be honest! I don't like M$ too much. I have always been a friend of the open source thoughts.
So is it a good idea of installing UBUNTU-Studio 14.04, or is there no need for this "Studio" and one could achieve
the same by installing the regular UBUNTU 14.04. TLS ?

Cheers,
StevieIf it is just stereo recording and you don't planing on doing music productiuon then you don't need studio variant, but it less resource hungry than Ubuntu. Maybe try the Xubuntu variant.
Using just Live CD you can record. So, you can experiment which variant suits you best.

---

### Post by CrocoDuck on 2014-04-23
Hi! The daw that is more close to Garage Band, from the GUI point of view, is Jokosher. I never tryed it. I'm used to record with Ardour. When I need an mp3 file I just import my master into Audacity and then I export it as an mp3 (you can use a huge ammount of converters and tool even from the command line though). I used ubuntu studio 10.04 on a computer with 80 Gb hardrive, 512 Mb ram and an amd64 that was running XP before. It has been amazing for years and UStudio boosted the audio performaces A LOT. Now I've updated my computer to one with specs close to your machine.

Ubuntu Studio uses Xfce, a graphical environment which is light enough (12.04 runs smoothly on mine). If you need more performances just install LXDE (as I did with the old computer I described, it has been very effective). Your soundcard should work out of the box (I own a very similar one I used in almost the same way).

My advice: make a bootable media with UStudio and try Ubuntu before to install. Check If everything is working. If so, you are ready to go. Expect to have to invest some time learning the new system. Expecially from the audio point of view, linux is more complex.

---

### Post by CrocoDuck on 2014-04-23
Ooops... I posted this by error... sorry.

---

### Post by stevie5 on 2014-04-29
thx CrocoDuck,

what does the DAW stand for?

cheers,
Steve

---

### Post by jejeman on 2014-04-29
The first thing when you google it - Digital audio workstation

In context here it is referred to a software with audio and MIDI sequence capabilities.

---

### Post by stevie5 on 2014-04-29
well, from what was written, I had the impression, that it was a dedicated software product ...

---

### Post by jejeman on 2014-04-29
> **stevie5 said:**
> dedicated software product ...
What do you mean?

---

### Post by stevie5 on 2014-04-29
I ment, that the abbreviation sounded like a software product. Are you a native english speaking person?

---

### Post by jejeman on 2014-04-29
No, I'm not a native speaking English person. And I don't see it how could you interpret "daw" as a name for the software product. If you are referring to this sentence
> Hi! The daw that is more close to Garage Band, from the GUI point of view, is Jokosher. "Jokosher" is the name of the software product.

I've looked again at your first post. I have a similar setup as you, but using xenyx 1202fx and ESI MAYA44 USB.

---

### Post by stevie5 on 2014-04-29
&#8230;then I must have overread that. Sorry for that!

---

### Post by cub on 2014-04-30
As you have already used Cubase I think there is no downside to using Ardour in Ubuntu Studio. Then if you choose to do more than "just" record you already have the files in there and are familiar to the application.

---

