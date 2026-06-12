---
title: "Ubuntu for music production?"
date: 2009-04-02
forum: Ubuntu Studio
---

### Post by Gp. on 2009-04-02
I use Cubase, Adobe Audition and Guitar Pro under windows.

These won't work on ubuntu even under wine.

Does anyone know of programs on Ubuntu that can match these?
(NOT TUX GUITAR BTW, I dislike it.)

I wish to use Ubuntu for my audio, but I'm not sure if it's really Ubuntu's area.

---

### Post by Cybie257 on 2009-04-02
check out this link:

[https://help.ubuntu.com/community/WindowsApplicationsEquivalents](https://help.ubuntu.com/community/WindowsApplicationsEquivalents)

A quick peek at the link labeled :

    Linux software equivalent to Windows software

has at least 2 of the three you mentioned..

-Cybie

---

### Post by Cybie257 on 2009-04-02
to add:

Guitar Pro  	
TuxGuitar ( [http://www.tuxguitar.com.ar/home.html](http://www.tuxguitar.com.ar/home.html) )
DGuitar ( [http://sourceforge.net/projects/dguitar/](http://sourceforge.net/projects/dguitar/) )
kguitar ( [http://sourceforge.net/projects/kguitar/](http://sourceforge.net/projects/kguitar/) )

Adobe Audition  	
Audacity ( [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/) )

Found these on :

     [http://www.linuxalt.com/](http://www.linuxalt.com/)

-Cybie

---

### Post by simtaalo on 2009-04-02
sounds like the type of production you do is recording live instruments then arranging etc...

for this stuff ardour is awesome, its fully featured and stable. its a very good program.

if your into electronic music production then ardour isn't as good for that IMO but lmms is very good.

both programs now support vst(i)

---

### Post by B4RR13N705 on 2009-04-04
I have a music sudio, and it runs under Ubuntu Hardy and it works amazing! I use Ardour, Gtick, Audacity, TuxGuitar, JackControls, Soundagarden, LMMS and others!

---

### Post by babarosa on 2009-04-04
Gp.,

I am earning money with my recordings using an audio workstation built on xubuntu 8.04.1 (I am on gnu/linux since 1 1/2 years), I am into the business since 1995, amongst working with international working artists reaching top 40 - sadly no number one hit until now ;), radio- and tv-stations (advertisements).

Customers whistle the melody, not the name of the operating system or software.

The progs are different and you have to change your workflow, the results are/can be professional. The learning curve can be steep and you have to do a lot of tinkering compared to Windows.

Examples for replacements, though not that mighty as the Windows ones, are:

Cubase --> Rosegarden, Muse, QTractor
Adobe Audition --> Audacity, Ardour
VST --> In development state, anyway plugins are fully automatable
plus various tools like arpeggiators, loopers, note editors, ...
Jump into the ocean at [http://linux-sound.org/](http://linux-sound.org/)

Video editing applications lag behind the ones of the other operating systems.

Regards,
Michael

---

### Post by Stochastic on 2009-04-05
When I moved from Audition/Cool Edit to Linux I couldn't stand Audacity, but found myself quite fond of Rezound for wave editing.

Ardour is the king of multi-track editing (the latest release includes VST support) and soon will also have MIDI editing.  It's like ProTools for Linux.

Oh, and I just realized nobody in this thread has mentioned UbuntuStudio.  [www.ubuntustudio.org](www.ubuntustudio.org) is a customized distribution of Ubuntu that is geared toward multimedia production.  Audio people will tell you that the biggest step to getting your Ubuntu box working with pro audio is to install the RealTime kernel (the one in Intrepid is borked, so be warned).  You can install all the ubuntustudio meta packages on top of a normal Ubuntu install too.  Here's a little more info: [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

### Post by markbuntu on 2009-04-05
Just so you can have an idea what you are getting into. 

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)


There are tons more how tos and if you need help just ask. Most of the apps also have forums.

---

### Post by fedexnman on 2009-04-05
which version for audio though   64 bit or 32 bit im guessing stay with 32bit ?

---

### Post by markbuntu on 2009-04-05
64 is faster, better all around. All the ubuntustudio audio apps have native 64 bit as far as I know. I tried 32 and 64 and 64 is way better.

---

### Post by Stochastic on 2009-04-06
> **markbuntu said:**
> 64 is faster, better all around. All the ubuntustudio audio apps have native 64 bit as far as I know. I tried 32 and 64 and 64 is way better.

Really?  I recall someone mentioning that only once you reach 4gig of memory will you get any improvements from 64bit.  I stick with 32 mostly because ChucK has not been ported to 64 (but most people won't need chuck), but also because many things like flash, skype, java, wine, etc... used to only work perfectly in 32bit (they're pretty much all compatible now, I think).

In general I think they're equivalent, but occasionally you'll stumble across an app that only runs on 32bit.  Please correct me if I'm wrong about any of this.  

Hmm, I just googled for benchmarks on 32vs64 Ubuntu and it looks like some programs/algorithms improve greatly while others will slightly decrease.  But the most thorough of the reports used LiveCDs for the tests - seems silly to me (wouldn't memory & harddrive read/write timing issues be totally out of whack?).

---

### Post by thorgal on 2009-04-06
for more than 4G of RAM on 32bit systems, enable PAE in the kernel, and make sure your h/w allows it (recent intel CPUs do).

If you want to use VSTs, you need a 32bit runtime environment. That's also something to keep in mind.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
[http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux](http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux)

---

### Post by simtaalo on 2009-04-06
> **thorgal said:**
> 
If you want to use VSTs, you need a 32bit runtime environment. That's also something to keep in mind.


not true, i use vsti's on my system through lmms on 64-bit ubuntu without any problem or special steps in install. although doesn't seem any other music program that uses vst's makes it as easy.

---

### Post by thorgal on 2009-04-06
simtaalo, when I say "runtime" I didn't mean the architecture itself but the program host for the VSTs, so maybe your lmms binary has been compiled in 32bit. 32bit programs can be used in 64bit machines. I remember Paul Davis being very strongly against ardour-64bit supporting VSTs.   

This is a post from him in his news post called "Coming up soon":

[quote="PaulDavis"]
 Submitted by paul on Sat, 2009-02-21 06:36.

We have no plans to support VST on x86_64 ... this needs a lot of kludgy work to make it work - all win32/x86 VST plugins are written for a 32 bit environment and the VST API contains pointers in structures, which makes it fundamentally broken for mixed 32/64 bit environments. I know that Cakewalk have hacked up a wrapper for win32/x86 VST plugins so that they can be used in their win64 version of Sonar, but frankly, the amount of work involved in doing this compared to the benefit to our user community doesn't justify starting on this effort (certainly not for me).

Vestige currently "models" the 2.4 SDK.
[/quote]

If you truly are saying that your lmms-64bit runs VSTs without problems, maybe you should tell Paul Davis.

---

### Post by alanj on 2009-04-06
Have you had a look at AV Linux?

[http://www.bandshed.net/AVLinux.html]("http://www.bandshed.net/AVLinux.html")

---

### Post by saunders on 2009-04-06
> **Stochastic said:**
>   Audio people will tell you that the biggest step to getting your Ubuntu box working with pro audio is to install the RealTime kernel (the one in Intrepid is borked, so be warned).

When I try to use the -rt kernel with Intrepid, I get dropped into a shell ~20 sec into the boot, at a initramfs prompt.

Is this a result of the borked kernel, or do I have an entirely different problem giving me the same result?

---

### Post by babarosa on 2009-04-06
@ alanj
> Have you had a look at AV Linux?

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

Thank you for this interesting project: Some time ago I (and stochastic) tried to guide an user through compiling of ffado, jackd, ... without success. I think this user withdrew from using gnu/linux for the moment :oops:

This project would have helped him very much, I guess [-o<

Greetings,
Michael

---

### Post by markbuntu on 2009-04-06
I could never get the Intrepid Kernel to boot on my machine. I use ubuntustudio hardy64. With the 64bit rt kernel I have lower latency/fewer xruns than the 32 bit and the hydrogen/rosegarden/ardour/jack combo runs better. It would always hang/crash disconnect etc on 32 bit. It was painful.

I haven't had the need for vst's so I don't use them.

---

### Post by simtaalo on 2009-04-06
> **thorgal said:**
> If you truly are saying that your lmms-64bit runs VSTs without problems, maybe you should tell Paul Davis.

i understand what you are saying, and there is a work around which means i can use 32-bit vst's on my 64bit lmms. i haven't had any problems with it, which is due to the work put in by the dev's.

i don't know how much paul davis knows about lmms, but he might have looked into the project as lmms has been using vestige for a while.

all i really know is that lmms is a small project compared to ardour and has nowhere near the same support, developer and money-wise. so it does confuse me a little when he says he would be too much trouble to do.

EDIT : i compile it rather than use the binary.

---

### Post by PayPaul on 2011-10-12
I took a look at the sites linked to on the first page of this thread. What I found was most of the programs listed on the equivalents pages for audio processing were either dead links or for older projects that saw no additional work done since about 3 years ago. The ones that had documentation links those links too were either missing or lacked substance. I'm looking for a program with the functionalities of Cool Edit Pro/Audition. It has to be able to multi-track and provide enough effects to make it worthwhile.

---

### Post by sgx on 2011-10-12
Hi, I think it is a year or two away. In the meantime, qtractor,
ardour, Muse2, Rosegarden, and oomidi-2011 offer various parts.

Reaper works very well
in wine, using wineasio to host vst plugins. FLStudio also has
several people using it, there is a long thread here:

[http://ubuntuforums.org/showthread.php?t=1260057](http://ubuntuforums.org/showthread.php?t=1260057) :popcorn:

There is now a linux renoise port that looks very well supported.

Your sound and videocards will largely determine your ultimate success.
maudio, focusrite, and edirol souncards, with nvidia video cards,
is a good combo. Also, devices that are mac-compatible without extra software, are likely to work.

maudio 24/96, and delta 1010 pci models are excellent, and quite a few
people now use firewire cards. Google your current gear with ubuntu
Cheers

---

