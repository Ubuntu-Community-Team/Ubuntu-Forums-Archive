---
title: "Which is best distro for multimedia?"
date: 2007-06-25
forum: The Cafe
---

### Post by Killtown on 2007-06-25
Which is the best Linux distro for audio and video editing/playing/etc?

Which would be better between Ubuntu vs Ubuntu Studio vs Kubuntu?

If Ubuntu/Kubuntu is your favorite distro for multimedia, which distro would be your 2nd and 3rd choice?

---

### Post by ricrac on 2007-06-25
LFS.

Seriously, you'll find fanboy's for OSx, Windows and many distros based on user experience or the "killer app".  
Your question is also vague, or rather, at this time those features editing vs. viewing are typically better in different "platforms". 
Better is extremely subjective.
Most choices will be "killer app" dependent.
What are you looking for?  
Viewing/playing
...Graphics -  automatic rotation, scaling slideshow?  Graphical pattern search, extended exif, HDR or RAW support?
...Video - an offline catalogue? codecs? dolby output, multi monitor, post processing, tv tuning
...Audio - an offline catalogue? codecs? dolby, spdif, multichannel, midi
Editing
online, offline, linear, programmatic, cluster, and on and on
  
Suggestions strictly linux.
Gentoo or LFS will usually give you better performance, it may not be worth the time invested if you only have one machine.  I prefer 5+ machines before bothering with it unless required.
More machines means faster compiles and one master compiles for all others regardless of platform(s).

64Studio and Fedora Core 7 + CCRMA have currently the "best" 64bit audio iso's.
64studio, jacklab, fedora+ccrma, ubuntustudio, dynebolic all have good 32bit iso's.

64studio 64bit
dynebolic has streaming apps, poorer english on some apps, great for webcasts, bars, parties.
jacklab has winasio and jost,  that's VST support, can be built on others with effort
fedora+ccrma is quite current and has more csound and other programmatic apps

ubuntustudio is adequate, impressive for a first releases, is a first release. Doesn't compile all apps with jack and pulse support even tho those are the preferred sound platforms. Hasn't yet optimized the environment. Gnome sucks for production, you'll want XFCE or E17.  You'll want to do a lot of tuning, remove avahi and other useless apps, tune irq's, asound.rc, etc.  
I'm not saying you won't also have to tune other distros.

And just to confuse you some more...
Mandriva 2007.1 and Mandriva based distros are the only distros that have mplayer with jack and pulse compiled in by default.

 
If you want to use already owned versions of VST intruments use Jacklab. (evil suse)
If you want the most current versions of apps use Fedora7+CCRMA.
If you want a cd distro for live performance use Dynebolic.
If you want an easy, all binary 64bit system use 64studio.
If you like Ubuntu, mainly want current audio and don't need VST use Ubuntustudio.

I will be recommending Ubuntustudio when:
It gets pulled into the main channel.
Mplayer and other apps are supplied compiled for jack and pulse.
asound.rc configuration support
midi configuration support
ships default with a low impact display manager, xfce or e17 currently
would love it it included winasio and jost for VST plugins.

I multiboot and use virtualization because no current distro can solve all my needs.
I am writing from Ubuntu Feisty in vmware on Mandriva 2007.1 Host.  I also have Ubuntustudio and Gutsy along with various windows, osx, freebsd, openbsd and other linux distros on vmware.
I usually boot to Fedora7+CCRMA or Jacklab Host for audio, still able to run optional vm's.
I was testing Ubustudio but trashed it trying to install current versions of gimp and blender from gutsy. 
I also boot into XP host, with vm's available to use Cubase.  I have VST's so I like jacklab even tho it's suse based.
Mandriva has the best mplayer binary, plays cd, dvd,wav,quicktime,tv tuning,streaming video, streaming audio and codecs for all media types so I use it for a Mythtv style party dj host.
All "Host" distros are volatile, so all "work" goes into a vm which I can access using a livecd if needed tha I can get to from any of the multiboots.  Many of the vms are Host based, this means I can boot to them or run them in a vm from another distro.
I use Ubuntu dapper host for EMC cnc work.
I use winXP in a vm running on any linux host for Roland CNC work, runs better than on winXP as
 host.

It's seems confusing to the novice, but I can build a box from parts, boot to a livecd with vmplayer, start my vms, start copying to multiboot host partitions, be surfing within boot time, be working within vm in wake from suspend time, and have the whole box completed with my main 6 distros in copy time.  When I'm finished I can call up my friend and see if he's located the dependencies for app X yet and finally gotten it to compile.  When I need to compile, I use the same system as the author and often everything just works.

If I had to use only one distro for audio I'd probably use Fedora+CCRMA, but in actuality I use the evil Jacklab because of the "killer app" issue, VST. 
 
Kudos on the great work done so far on Ubuntustudio and here's to hoping it takes the lead next year.

Xubuntu, converted to Ubuntustudio would be the best/least effort.  I don't know if menus and all work yet.
Gnome and KDE are too heavy for production use. If you like them better or want compiz,beryl, etc. fluff, you're probably not doing production work.
Fluxbuntu will probably be the best when finished, with gutsy next fall.
[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by Killtown on 2007-06-25
I should have added what's best for a Linux NOOB.

---

### Post by oxalá on 2007-06-26
that was the funniest post exchange i've seen in days :)

(but thanks for the info, ricrac -- i myself am beating my head against walls trying to accomplish simple narration recording via my mic...)

---

### Post by jrusso2 on 2007-06-26
Its been a while since I looked at it but I seem to remember Dreamlinux was pretty good for multimedia

[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

---

### Post by BobCFC on 2007-06-26
Great post ricrac good effort =D>

I like the style of ubuntu studio but I was put of by the lack of 64bit code.  I guess it will come in time but with my ram that rules 32bit out. 

Thanks for the headsup about CCRMA and a certain fruit-based vmware I will investigate both.  Although I am wary of RPM distros.

FLUX is lightning I agree!!!  Might shave a few ms off response time.



I think these studios should branch into music and graphics myself.  If I run Maya I probably won't want Jak and vice-versa

---

### Post by tseliot on 2007-06-26
I'm moving this thread to the Community Cafe since it's not a request for support.

---

### Post by mips on 2007-06-27
Something that comes with all the codecs and stuff installed by default and Ubuntu it is not.

---

### Post by PriceChild on 2007-06-27
Ubotu says:
> <Pricechild> !best
<ubotu> Usually, there is no single "best" application to perform a given task. It's up to you to choose among a number of different applications, depending on your preferences, the features you require, and other factors.Noone knows what is best for you... just experiment.

---

### Post by jacob01 on 2007-07-16
the best distro for multimedia for some one new to linux would probably be ubuntu because it is easier to use and has better support though the community than other distros

also some people complain that ubuntu is bad for multimeda because it does not include any included but it is so  easy to install the required codec packages through the add remove programs and play all of the formats that windows can play

if you are looking to edit videos there are not many good video editors currently that are either worth using or are stable enough to use for example kino and avidemux are ok for cutting and splicing video they are not to high end.

what i think is the best for video editor for ubuntu is main actor wich is a comercial video editor that costs 200 dollars but is realy stable and works great

---

### Post by jacob01 on 2007-07-16
stop complaining about ubuntu not having any codecs preinstalled they require little to no effort to install and the only reason why the codecs are not preinstalled was most likely for legal reasons

ubuntu being open source they can not include closed source codec

---

### Post by ThinkBuntu on 2007-07-16
Dyne:bolic is the best for media creation. No other OS comes close (in terms of every aspect of the system being customized with multimedia creation in mind) and I've enjoyed using it.

---

