---
title: "Newbie Ubuntu Music Production"
date: 2009-05-19
forum: Ubuntu Studio
---

### Post by bravemenrun333 on 2009-05-19
Hello

Ive been using Cubase SX in WinXP a long time now. I want to switch over to Ubuntu for making music. Now, it is important to me to be able to use VST plugins... so far Ive read that this isnt possible?! Is this true?

Which would be the nearest equivalent to Cubase SX?

Thanks

---

### Post by subdee on 2009-05-20
Yes, you can use Ardour with JACK, but you must compile Ardour with vst=yes in order to use VST on it. It's not included in the Ardour binaries because it would infringe licenses.

Also, there's a new ArdourVST app that you can try although the devs say it's not ready for normal use.

Give it a shot.
[http://ardour.org/building_vst_support](http://ardour.org/building_vst_support)

---

### Post by wentzr on 2009-08-05
Let's get this out of the way... If you want to make your music with VSTs, you're better off doing that stuff in windows xp. period.  Reaper in wine works, and you can do vsts, but you wont spend most of your time creating music, you'll likely spend most of your time pulling your hair out and pissing vinegar.  The short of it (others chime in if you like here) is that VST architecture is written and maintained by Stienberg.. Stienberg will have nothing NOTHING to do with the linux community so I'd suggest you just do yourself a favor and give up on the VST on linux endeavour.  

I would recommend you look at renoise as a music production app. it's available for windows, linux and OS X... I don't hear it mentioned here often, but it handles both Midi and Audio beautifully.  I've been using apps like this (called trackers) since the early 90s, so i'm a bit biased... Producers have been using trackers for decades and I myself (among many others) still prefer them over piano rolls or step sequencers like fruity loops.. The interface of a tracker like Renoise might be a shock to you at first if you're a newbie producer... but I'd do yourself a favor and try it out for a spin. Challenge yourself to write a song using midi and audio samples in a tracker. If you're like many others it will be as much of an exhilarating ride as a first acid-trip... so I've heard. The analogy is undeniable: You'll never look at music production the same again and it will most likely be well worth the world tipping experience if you're used to the daw flavor-of the week, like live, or cubase, or even the (in my mind) fools who actually WRITE music in pro-tools. 

Renoise works with audio samples and outboard gear, and it might make you see trails... you can get a demo for free on windows, os x or linux: [www.renoise.com]("http://www.renoise.com")

---

### Post by paulmerchant on 2009-08-05
I'm going to second wentzr's invitation to try Renoise. It's brilliant, has a strong community, and the free version let's you do almost everything. Now that Renoise has Jack and plays nicely with Ardour, it's definitely worthy of the current buzz you might hear about it.

You'll probably want to learn Ardour for all your multi track audio needs. There are other options, but Ardour stands above the rest. If you hate Renoise for midi/tracking/sampling, I've also enjoyed using seq24 along with Ardour. ZynAddSubFx is a great synth. Energy-XT 2 for Linux isn't too bad. (I used to use Energy-XT for Windows, but I always had problems with version 2 on Windows or Linux.)

And, yes, if you're going to have a Linux studio, you might want to drop your VST addiction. Some people keep up the habit by compiling their own software, using Wine, playing around with things like LMMS, but it's probably better just to go cold turkey.

(By the way, great things can be done with LADSPA effects in Ardour and Renoise. Also, Renoise supports a handful of free VSTs that have been compiled for Linux.)

Edit: To answer your question more directly, Energy-XT or Rosegarden are probably the most equivalent to Cubase SX. Ardour is more like Pro Tools.

---

### Post by Grishka on 2009-08-05
LMMS supports VST plugins as well, it's like FL Studio, formerly Fruity Loops. there's a DSSI VST wrapper as well, many VSTs will work with it.

---

### Post by sgx on 2009-08-05
> **bravemenrun333 said:**
> Hello

Ive been using Cubase SX in WinXP a long time now. I want to switch over to Ubuntu for making music. Now, it is important to me to be able to use VST plugins... so far Ive read that this isnt possible?! Is this true?

Which would be the nearest equivalent to Cubase SX?

Thanks
For vsts, you need a soundcard/chip that is fully supported, older 
m-audio 24/96 pci cards are excellent for using Reaper or Cantabile as hosts. A properly configured alsa, qjackctl, wine, and wineasio are needed.
Realtime kernels are not needed for small projects, and indeed, of the Ubuntu Studio versions, only
Ubuntu Studio 8.04 has an acceptable one. Other audio-centric linux versions such as Studio64, JAD, avlinux2, and musix are worth testing.There are threads at the reaper and kvraudio forums, and here, that give the details needed, most apply to any linux version, but be prepared for several hours reading and googling, and note-taking, and try live dvd/cd versions before you commit to an installation, unless you have a spare system, or extra hard-disks dedicated to learning on. 

vsts with dongles or extravagant copy protection won't work, almost all
of the other 95% will. Reaper 3.06 is fast and stable using wine and wineasio, assuming the basics are set up correctly on supported hardware.

cubase, ableton, sonar etc are not workable now. The Ardour vst support is not intended by the author to be a full-featured vst host like reaper or cubase, so don't get sidetracked. It has other purposes that it does very well.
Cheers

---

### Post by sgx on 2009-08-05
Grishka reminded me of dssi-vsthost, and fst, both are commands that utilize wine/wineasio to run a single vst, install them, and wine and wineasio and qjackctl using a gui package manager, synaptic, in the case of Ubuntu.
Then start the jackd sound server like this:

jackd -d alsa -r 44100

then issue the command with the path to the .dll file

fst /home/your-username/IK_Multimedia/SonikSynth2.dll or
vsthost /home/your-username/IK_Multimedia/SonikSynth2.dll

This path would vary according to its installer.

Then open qjackctl, its a gui patchbay for the jackd soundserver, and connect the plugins to the sound system, you'll see it and figure it out.

 Windows installers work simply like

wine reaper30-install.exe

Easy to test and use individual plugins that way

Cheers

There are links to the needed tutorials for most things when you search this forum and google a bit

---

