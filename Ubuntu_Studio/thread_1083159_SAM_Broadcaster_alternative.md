---
title: "SAM Broadcaster alternative"
date: 2009-02-28
forum: Ubuntu Studio
---

### Post by TuxOtaku on 2009-02-28
Hey guys and gals,

Does anyone know of a good Linux-based alternative to SAM Broadcaster? I run a small shoutcast station and have been trying to get SAM to run under WINE for the past little while. I've just been hitting a brick wall with it, so I'm ready to seek out alternatives.

---

### Post by Naiki Muliaina on 2009-03-01
Well, to use the main Shoutcast program for broadcasting, [**Click Here**]("http://naiux.wordpress.com/2009/01/24/linux-shoutcast-guide-part-1/").

For alternatives you can try Amarok and VLC with the shoutcast plug ins. Or, and i hate to say this things name cause i hate it, IDJC. Internet DJ console. It uses JACK control, and i have never ever gotten JACK to work without epic fiddling. These three are in the Ubuntu repos so grab them throug add / remove.

---

### Post by TuxOtaku on 2009-03-01
I'm not a big fan of IDJC either. But shoutcast "plugins" are kind of what I want to avoid. What I do involves a lot of beat mixing and talkovers. A cheesy little shoutcast plugin just won't cut it there from everything I've seen. And the Linux version of the shoutcast broadcaster is worthless. I've tried it before, all you do is just throw a text file fulla songs at it. Thanks for the suggestion, though.

---

### Post by Naiki Muliaina on 2009-03-01
Theres another one that uses Jack (muse or something i think). If Jack was your problem in IDJC though, you will have them with Muse. Jack is the source of all my problems with IDJC though.

---

### Post by StephenF on 2009-03-01
> **Naiki Muliaina said:**
> Theres another one that uses Jack (muse or something i think). If Jack was your problem in IDJC though, you will have them with Muse. Jack is the source of all my problems with IDJC though.
You are a little confused and I don't blame you. There are two programs one is a streamer called MuSE note the use of capital letters, and the other is called MusE which is a midi/audio sequencer. Only the latter runs on Jack but MuSE has some serious show stopper bugs (literally).

As an aside I installed Mint 6 on my testing PC and found IDJC to work stably having made no system modifications.

---

### Post by Stochastic on 2009-03-01
I'm no shoutcaster, so my suggestions might be useless.

Rivendell is a very powerful radio application (but I don't know if it has beatmatching): [http://www.rivendellaudio.org/](http://www.rivendellaudio.org/)

Could you possibly use a program like Mixxx (DJ mixing software) and then pipe the output into a broadcasting stream setup by some other app?  This would be done easiest through Jack.

From this guide: [http://www.linux.org/docs/ldp/howto/MP3-HOWTO-11.html](http://www.linux.org/docs/ldp/howto/MP3-HOWTO-11.html)
It sounds like LiveIce might be the tool to do the job - taking a mixed signal from something like Mixxx.  But that guide is quite good from the looks of it, and details many other apps - take a read.

---

### Post by BigD77 on 2009-03-01
> **Stochastic said:**
> I'm no shoutcaster, so my suggestions might be useless.

Rivendell is a very powerful radio application (but I don't know if it has beatmatching): [http://www.rivendellaudio.org/](http://www.rivendellaudio.org/)


Hmm...On Rivendell's website it says that requirements are SuSe Linux.  Will it work on Ubuntu?  If so, how?

---

### Post by TuxOtaku on 2009-03-02
Linux is Linux dude. No matter how you slice it.

That being said, this is yet another JACK app. I'd like to avoid dealing with JACK and all of the headaches it brings, if possible.

> **BigD77 said:**
> [quote=Stochastic;6820197]I'm no shoutcaster, so my suggestions might be useless.

Rivendell is a very powerful radio application (but I don't know if it has beatmatching): [http://www.rivendellaudio.org/](http://www.rivendellaudio.org/)


Hmm...On Rivendell's website it says that requirements are SuSe Linux.  Will it work on Ubuntu?  If so, how?[/quote]

---

### Post by Stochastic on 2009-03-02
Really?  Avoiding Jack for your audio applications is like avoiding diesel for your towing needs.  There's just a touch of setup learning curve to Jack, then the rest is smooth sailing.

It's much less to learn than shoutcasting IMHO.

On another note, did you look at that last link I posted?  Any useful info there?

---

### Post by markbuntu on 2009-03-03
Jack. The problem with jack is that most people never take the time or know where to turn to to learn it.

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)


Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by Naiki Muliaina on 2009-03-06
> **markbuntu said:**
> Jack. The problem with jack is that most people never take the time or know where to turn to to learn it.

I think the problem with Jack is it takes to long to learn if you have a problem. I have had it work once and it knocked sound out of every other app. I spent days / weeks / months looking over documentation, asked on forums, followed simple steps people gave me and still it didnt work.

I know in Linux not everything is plug and play, and im quite willing to read about how my PC and the apps in it work. But there is a limit to how much you should have to learn to perform simple tasks that dont work as they should even after all that reading ^^

---

### Post by ram130 on 2010-09-18
I guess there will be never be a true sam alternative.

---

### Post by jerehart on 2010-10-04
So... After digging and spending many hours trying to Rivendell up on  an OpenSource Linux Distro (OpenSuse, Ubuntu) I came across this.


 [http://rrabuntu.sourceforge.net/](http://rrabuntu.sourceforge.net/)
[URL="http://rrabuntu.sourceforge.net/"]
[/URL]
 Some developers at Rivendell built a custom distro of Ubuntu with Rivendell included in the install scripts.
 I doesn't get easier than that! Ha... Free Radio Automation to the masses!
 

~Jeremiah

---

### Post by ram130 on 2010-10-05
> **jerehart said:**
> So... After digging and spending many hours trying to Rivendell up on  an OpenSource Linux Distro (OpenSuse, Ubuntu) I came across this.


 [http://rrabuntu.sourceforge.net/](http://rrabuntu.sourceforge.net/)
[URL="http://rrabuntu.sourceforge.net/"]
[/URL]
 Some developers at Rivendell built a custom distro of Ubuntu with Rivendell included in the install scripts.
 I doesn't get easier than that! Ha... Free Radio Automation to the masses!
 

~Jeremiah

Still missing alot of features..but happy at least someone as taken up the task. I wish it had AGC though!

---

### Post by Geek2theCore on 2010-11-14
I've actually had pretty good luck with SAM Broadcaster up until I tried to get OSS4 working with it.  Oh, and while I bought v.4.7.1, I could never get it to work as well, so I fell back to v.3.4.3  which has a deserved Gold rating in the WineDB.  I've had it running on every version of Ubuntu since Hardy, currently playing on my Dual-core 4GB Lucid machine.  On less than a multi-core CPU SAM stutters, but it's usable if you don't run anything else.

The other option--my favorite on a fast, multi-core machine with lots of RAM--is to run it in a VirtualBox virtual machine.  I remove EVERY single browser link inside the VM so the DJs aren't tempted to use them instead of the one on the Ubuntu host, then I snapshot it and if anyone ever manages to kill the VM completely, I revert to the snapshot and all is fixed.  Even with a gig of RAM, though, SAM can stutter if you access networked drives via Explorer that are currently in use in the VM.

Unfortunately, on the Quad-core machine I've been setting up as our new studio machine, I tried to shift to OSS4 and now I can't find any setting that doesn't throw an error in the sound.  Still working on that, but SAM, at least 3.4.3, has worked great otherwise.  (I even had 4.7.1 working in Jaunty, but it had glitches with some of the sub-functions.)  I just set it up to use the mySQL server on the host machine, which you have to connect to as if it were remote.  

RAM and CPU capabilities are, of course, paramount.

---

### Post by ram130 on 2010-11-14
If got to use a old version just to get things to work 50% then its not worth the effort and time to setup..

---

### Post by Geek2theCore on 2010-11-14
Actually, my 3.43 version running on wine works flawlessly.  It's only in the virtual machine that it has any issues, so that's our backup, on the desktop in case the other one fries for whatever reason.  From a saved state the VM, fully loaded with SAM, takes about 10 seconds to come up.

And yes, granted, you lose all the features and fixes that were implemented since 3.43, but I'm never averse to regressing a version or two to get one that works, as long as it does everything I need it to do, and the fact that it gets as close as it does on 4.7x with almost no fiddling leads me to believe that it's possible, even if it's not quite there yet. ;)

I'm still looking at Rivendell as an Open Source alternative, but it's been kind of back-burnered.

---

### Post by ram130 on 2010-11-14
> **Geek2theCore said:**
> Actually, my 3.43 version running on wine works flawlessly.  It's only in the virtual machine that it has any issues, so that's our backup, on the desktop in case the other one fries for whatever reason.  From a saved state the VM, fully loaded with SAM, takes about 10 seconds to come up.

And yes, granted, you lose all the features and fixes that were implemented since 3.43, but I'm never averse to regressing a version or two to get one that works, as long as it does everything I need it to do, and the fact that it gets as close as it does on 4.7x with almost no fiddling leads me to believe that it's possible, even if it's not quite there yet. ;)

I'm still looking at Rivendell as an Open Source alternative, but it's been kind of back-burnered.

Great point! I would try this if I haven't already gotten a dedicated windows machine ..I just wish someone would make a just as good sam alternative for linux already with agc :)

---

