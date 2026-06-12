---
title: "My head's been in the sand"
date: 2010-03-30
forum: Ubuntu Studio
---

### Post by BobLand on 2010-03-30
I feel like I've woken from a 20 year sleep.  I just found out about all of the open source sequencers, mixers, workstations and the like.  Years ago, I recall that Gigasampler was a very expensive product...something in the thousands of dollars.  Now, there are FOSS programs that read the samples and there are thousands of samplers everywhere.

When I installed Studio, I just selected the video segments.  Is there a way to get all of the audio pieces in one fell swoop, so to speak?

And...if you want to bring me back to the 21st century with you highly jaded opinions about digital music I'd really love to hear from you.

My last experience with synthesizers was an ARP 2600 and one of the first Emu consoles.  Like I said, that was a long, long time ago.

Thanks,
bobland

---

### Post by DerickX on 2010-03-30
Yes there is an metapackage for the audio packages

sudo aptitude search ubuntustudio

---

### Post by sgx on 2010-03-31
Some highlights,

Rackarrack for multifx

zynaddsubfx and phasex for synthesizers

hydrogen for drum machine/sample playback/pattern sequencer

linuxampler/qsampler  play giga format samples

fluidsynth/qsynth play soundfonts

audacity sound editing/recording

ardour HQ audio daw

jackd realtime sound server

qjackctl gui to connect soft/hardware to jackd

patchage and qtractor sequencing and midi connection

qtracktor, patchage, 

Most folks start setting up jackd/qjackctl, then pick the instrument
that beckons loudest. The studio preconfigures a lot to make life easy.

Cheers :)

---

### Post by BobLand on 2010-03-31
sgx,
Great recommendations.  Can you give a link for samples?  Most of the ones I found ask for a lot of money.  I'm sure they are great samples but I am not a great "composer."  Just a hack looking for some fun.

Thanks,
bobland

---

### Post by Krang the Brain on 2010-03-31
Linux Multimedia Studio reminds me of Acid Pro 4.0

Here's a list of samples you can download from there site.

[http://lsp.lmms.info/?action=browse&category=Samples](http://lsp.lmms.info/?action=browse&category=Samples)

---

### Post by DerickX on 2010-04-01
Here you can find a nice list of samples
[http://www.openstudioproductions.org/free-downloads](http://www.openstudioproductions.org/free-downloads)

---

### Post by sgx on 2010-04-01
> **sgx said:**
> Some highlights,

snip

Most folks start setting up jackd/qjackctl, then pick the instrument
that beckons loudest. The studio preconfigures a lot to make life easy.

Cheers :)
Just to be clear, the things I mentioned are software applications, not sound samples, and most are preinstalled by Ubuntu Studio. All are free, with donations welcome. Synaptic can be used by root, to update or install them as needed, its the gui package mananager, in case you have yet to use it, start the program when online, select repositories, press 'reload' to download the latest worldwide collection, and choose what you want to update, install, or remove.

PPAs usually have a how-to section on their webpage, explaining the
download procedure recommended by its maintainer.

For sound samples, a list of many many samples websites is here

[http://www.kvraudio.com/forum/viewtopic.php?t=37272](http://www.kvraudio.com/forum/viewtopic.php?t=37272)

Hydrogen is good for playing patterns and sequences of .wav files, commonly used as a drum machine.

linuxsampler specializes in giga format files, the high-quality Tascam standard that Tascam inexplicably abandoned.

Fluidsynth/qsynth loads soundfonts.

zynaddsubfx is a world class softsynth, with a few hundred patches to get
you going. 

I recently compared Rakarrack multi-fx version 0.4.2, to a high-end hardware fx processor, and the new Amplitube 3, and those who 'know' fx, will not find significant sonic limitations, although A3 works well in a linux wine setup, and is a great value for working musicians in cover bands, and people looking for sonic models of specific gear

qjackctl is the control center to connect all those to your computer hardware.
Cheers

---

### Post by mango42 on 2010-04-01
May I make a request for **sgx**'s latest gems to be made into a sticky?

I am certain they would help many people coming new to **UbuntuStudio** to wade through the minefield of setting up, with the minimum amount of head scratching.

Personally, I have found that it's been a very instructive 10 months. I have been constantly amazed and delighted at how much time, effort and persistence has been put into what is fundamentally free software.

I have seen on other fora how much notice is now being taken of Realtime Linux, Jack & ffado - most heartening and says a lot for dedication and co-operation.

---

### Post by sgx on 2010-04-02
> **mango42 said:**
> May I make a request for **sgx**'s latest gems to be made into a sticky?

I am certain they would help many people coming new to **UbuntuStudio** to wade through the minefield of setting up, with the minimum amount of head scratching.

Personally, I have found that it's been a very instructive 10 months. I have been constantly amazed and delighted at how much time, effort and persistence has been put into what is fundamentally free software.

I have seen on other fora how much notice is now being taken of Realtime Linux, Jack & ffado - most heartening and says a lot for dedication and co-operation. Its a bit incomplete to be sticky, for example,
someone mentioned phasex, so I thought I would try it, but the install conflicted with an earlier version, meaning I didn't know I had already installed it, or it came preinstalled in the shadows instead of in the menus! The new version is packed for power users, I am scratching at the surface, but you can use whatever is on your line-in as a sound source,
a rare feature in any OS/synth.

A more complete and frequently updated list would be handy.

Cheers

---

### Post by AutoStatic on 2010-04-02
There's a pretty complete and up to date list here: [http://wiki.linuxmusicians.com/doku.php?id=linux_audio_applications](http://wiki.linuxmusicians.com/doku.php?id=linux_audio_applications)

And for samples and downloads: [http://wiki.linuxmusicians.com/doku.php?id=free_audio_data](http://wiki.linuxmusicians.com/doku.php?id=free_audio_data)

---

### Post by mango42 on 2010-04-03
> There's a pretty complete and up to date list here: [http://wiki.linuxmusicians.com/doku....o_applications](http://wiki.linuxmusicians.com/doku....o_applications)

Okay - so make *that* a sticky here! 

There are just so many web pages one can keep tabs on, some redundant, some hopelessly out of date (though one doesn't sometimes realise this until reaching the end of the page!), others that never seem to show up on even the best search engines (eg: [www.startpage.com](www.startpage.com)).

Centralisation of data is impossible and probably not a good idea anyway but anything that can help newcomers get up to speed on the UbuntuStudio approach to music making would be best kept sticky'd here on this forum, IMO.

---

### Post by cchhrriiss121212 on 2010-04-03
> Centralisation of data is impossible and probably not a good idea anyway but anything that can help newcomers get up to speed on the UbuntuStudio approach to music making would be best kept sticky'd here on this forum, IMO.

I agree with this, particularly when it involves somewhat uncooperative programs like jack. There are probably up to 10 new users a week posting on here with the realtime priority issue in jack, and a simple sticky would no doubt reach most of them. 

I'm aware of the community documentation for things like this but I think a lot of users will sooner post a thread than search through documents (some of which are outdated).

---

