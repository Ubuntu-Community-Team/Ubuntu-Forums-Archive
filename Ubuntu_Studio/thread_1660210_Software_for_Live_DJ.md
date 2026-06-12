---
title: "Software for Live DJ"
date: 2011-01-05
forum: Ubuntu Studio
---

### Post by no1daag on 2011-01-05
Searching for a software for use at a club / Live DJ
Right now I'm using [Mix Meister ]("http://www.mixmeister.com/products_mmexp7.html") which I'm satisfied with but it´s only works in Windows which I want to but in the trash ;) 
All my computers will run with Ubuntu so I'm looking for a software similarly to Mix Meister. 
Must work with 2 soundcard , one for preview listen and one for the audio output.
The software in the Ubuntu repositories doesn´t fit my needs. It´s not similarly to Mix Meister.

---

### Post by WarrenSH on 2011-01-05
I would love to find a program that will run on any Linux distro without having to use wine or VM. I been using Windows XP for this feature & sad to say it works & is stable now lets get Ubuntu & the rest of the Linux word on this. 

Hell I might go buy a older Apple Laptop just to use the terminal when mixing ;)

---

### Post by AutoStatic on 2011-01-05
@no1daag, try Mixxx from their PPA: [https://launchpad.net/~mixxx/+archive/mixxx](https://launchpad.net/~mixxx/+archive/mixxx)

Best,

Jeremy

---

### Post by no1daag on 2011-01-05
Thanks. I think I 've try this but I'll try beta version 1,9 
It has not function similary to Mix Meister but maybe it should work.

---

### Post by cchhrriiss121212 on 2011-01-05
> **no1daag said:**
> 
It has not function similary to Mix Meister but maybe it should work.
If it doesn't have a feature you would like to use, try submitting a request to the developers. They may consider putting it in if enough people show interest.

---

### Post by AutoStatic on 2011-01-05
What functionality is lacking for you? Probably reliable BPM detection?

---

### Post by mango42 on 2011-01-08
I'd love to get Mixxx working - if only to show the Native Instruments Traktor crowd what is possible on Linux - but I've hit snags trying to install the 1.8.2-1 files you linked to, AutoStatic - Gdebi won't let me install the mixxx-data_1.8.2-1~ppa1~lucid1_all.deb file, despite upgrading portaudio19 - 19+svn20100802-0ubuntu2, as it 'breaks the installed version dependencies' of Mixxx.

Okay, so I go to Synaptic to remove Mixxx 1.7.x but I'm back to removal also involving removal of '**ubuntustudio-audio**' and I can't remember whether this is 'just' a meta-data file or something totally & fundamentally destructive to my (now) very smooth running 32bit Lucid Studio.

Any hints gratefully received.

:popcorn:

---

### Post by cchhrriiss121212 on 2011-01-08
> I'd love to get Mixxx working - if only to show the Native Instruments  Traktor crowd what is possible on Linux - but I've hit snags trying to  install the 1.8.2-1 files you linked to, AutoStatic - Gdebi won't let me  install the mixxx-data_1.8.2-1~ppa1~lucid1_all.deb file, despite  upgrading portaudio19 - 19+svn20100802-0ubuntu2, as it 'breaks the  installed version dependencies' of Mixxx.
Try adding the PPA to your system rather than downloading the individual deb files. If you install via the package manager, dependencies should not be an issue.
> Okay, so I go to Synaptic to remove Mixxx 1.7.x but I'm back to removal also involving removal of '**ubuntustudio-audio**'  and I can't remember whether this is 'just' a meta-data file or  something totally & fundamentally destructive to my (now) very  smooth running 32bit Lucid Studio.
That package contains all the audio programs that come with studio (jack, ardour etc.) so I would not remove it unless you'd like to install all the newer software versions from PPAs.

---

### Post by mango42 on 2011-01-08
LOL :D - that's the exact *opposite* of another regular poster's advice but thanks anyway, **cchhrriiss** for saving me from yet another session with Clonezilla, as I'm at the stage of not wanting to install *anything* that messes any more with the audio system (but catch22 with Mixxx and that mos' excellent player, Aqualung ;-)

---

### Post by AutoStatic on 2011-01-08
> **cchhrriiss121212 said:**
> That package contains all the audio programs that come with studio (jack, ardour etc.) so I would not remove it unless you'd like to install all the newer software versions from PPAs.It's a metapackage and contains nothing.

```
music@gnuppie:~$ aptitude show ubuntustudio-audio
Package: ubuntustudio-audio
State: not installed
Version: 0.70
Priority: optional
Section: universe/metapackages
```

Best,

Jeremy

---

### Post by cchhrriiss121212 on 2011-01-08
> **AutoStatic said:**
> It's a metapackage and contains nothing.

So it is, I had just gone by the description in synaptic:
> A collection of packages aimed at audio creation and editing
If this package contains nothing and does not remove anything, then what does it do?

---

### Post by AutoStatic on 2011-01-08
It's a metapackage that doesn't contain anything itself, just dependencies:

```
Depends: a2jmidid, aconnectgui, alsa-tools, alsa-tools-gui, ardour, audacious,
         audacity, beast, bitscope, bristol, csound, denemo, ffado-dbus-server,
         ffado-mixer-qt4, ffado-tools, fluid-soundfont-gm, fluidsynth,
         freebirth, freqtweak, gcdmaster, genpo, gtick, hydrogen, jack-rack,
         jack-tools, jackbeat, jackd, jackeq, jamin, jdelay, lilypond,
         lilypond-data, lmms, meterbridge, mixxx, mscore, muse, patchage,
         puredata, qamix, qjackctl, qsynth, rakarrack, seq24, sooperlooper,
         terminatorx, timemachine, timidity, tk707, ubuntustudio-controls,
         vkeybd, xwax, zynaddsubfx, python-changesettings
```

So if you install the ubuntustudio-audio metapackage it will install all of its dependencies. As soon as you uninstall one of its dependencies Synaptic/apt wants to remove the metapackage also since not all of its dependencies are met anymore. But uninstalling this metapackage shouldn't cause any harm.

---

### Post by cchhrriiss121212 on 2011-01-08
Thanks, that makes sense.

---

### Post by mango42 on 2011-01-09
I think most of the confusion I cause around here is of my own making. Synaptic is barred to me at present due to me using a USB install of Ubuntu Studio, so every time I try to upgrade anything, at some point Synaptic asks me to 'Insert CD/DVD' rather than 'Insert USB drive'. So far, I just take note of the error messages showing what it wanted to get off the non-existent DVD, find it on the USB stick and try to install it manually.

No doubt this is the shortest route to 'dependency hell'. What I don't understand is why Synaptic cannot just get the files off the net if they're 'not found' locally...

Okay, micro-moan over! :D The guys at Synaptic are very kind and helpful and apparently they are working to get USB stick installs recognized 'real soon now'...

---

### Post by AutoStatic on 2011-01-09
> **mango42 said:**
> No doubt this is the shortest route to 'dependency hell'. What I don't understand is why Synaptic cannot just get the files off the net if they're 'not found' locally...Depends what is in your* /etc/apt/sources.list*. Could you post the contents of that file?

---

### Post by Pablo_F on 2011-01-09
> What I don't understand is why Synaptic cannot just get the files off the net if they're 'not found' locally...

Neither do I, but if you have a decent internet connection you certainly don't need the installer anymore. Upgrade packages from the official repos and/or trusted PPA's. 

To solve the problem, you might need to untick the CD:ROM entry in:

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories -> Other software tab.

Or, if available:

System -> Administration -> Software Origins -> Other Software tab

And then reload, (which is equivalent to "sudo apt-get update" if you prefer the CLI).

Cheers! Pablo

---

### Post by Pablo_F on 2011-01-09
For clarification, the Software Origins Window reflects the content of the file "/etc/apt/sources.list" and other files inside the "etc/apt/sources.list.d" directory. 

I like this command to show as text all the active repos:

cat /etc/apt/sources.list /etc/apt/sources.list.d/* | grep -v "#"


Cheers! Pablo

---

