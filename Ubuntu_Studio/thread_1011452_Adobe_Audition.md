---
title: "Adobe Audition?"
date: 2008-12-14
forum: Ubuntu Studio
---

### Post by Dumbestcrayon on 2008-12-14
I used Adobe Audition since it was Cool Edit Pro. Now that I am free of, that skid-mark, windows I would like to know if anybody knows of a similar program or something that is available for ubuntu that I could use.

---

### Post by Ng Oon-Ee on 2008-12-15
> **Dumbestcrayon said:**
> I used Adobe Audition since it was Cool Edit Pro. Now that I am free of, that skid-mark, windows I would like to know if anybody knows of a similar program or something that is available for ubuntu that I could use.
Audacity is the closest. Another one is Ardour, but that is just complicated. However, Audacity will NOT work from the repos, due to conflicts with Pulse.

If you're up for a bit of a challenge and learning experience in all things Linux, I've got a guide on compiling Audacity from source to use JACK. Within it is a link to setting up JACK to work with Pulseaudio. You can post questions on how to do those within those threads, respectively. Should do everything Audition can do. Just to note, though, in Audacity there is no Edit mode, editing individual tracks is done from the multi-track view.

[Check out this link if you're interested.]("http://ubuntuforums.org/showthread.php?t=982577")

If you don't want to compile from source, then just install Audacity from the repos and disable Pulse when you want to use it. You won't get to use any other sound apps (Flash in Firefox for example) while you're using Audacity then, and maybe it'll defeat the purpose if you wanna use Audacity to record sound playing from another app. I'd personally recommend you follow the guide I posted.

---

### Post by Stochastic on 2008-12-15
Welcome to the free and open software world.  In design, you won't find many products in Linux that replicate Audition.  Audition/CoolEdit was designed to be everything you needed in one package - a multitrack editor, a wave editor, an effects processor, and a CD burner all rolled into one - this is necessary in commercial software.

In Linux, audio software usually is designed to complete one task really well and interact with other pieces of software so that you can complete any chain of events you think is needed.  The software glue that holds everything together is the JACK audio server (it can be tough to setup at first, but it's pretty straightforward with the qjackctl controller).

For multitrack editing, you NEED Ardour - it's unbeatable and could easily stand head-to-head with pro tools.  I have no idea what Ng Oon-Ee is talking about when he says it's really complicated - for anyone who's used Audition, Ardour is a natural transition.

For effects plugins, install the ubuntustudio-audio-plugins package.

For a wave editor, I like Rezound, others think audacity is good, there are MANY to choose from in the repositories.  As for Ng Oon-Ee's claim that audacity doesn't work from the repos - I haven't experienced this nor have I heard about this before now.  He also doesn't explain which version of Ubuntu or Audacity he's talking about, but I don't want to hijack your thread to troubleshoot his problems.

If you really want to start producing audio on your linux machine, you may want to install the UbuntuStudio packages [http://www.ubutustudio.org](http://www.ubutustudio.org) as it has the realtime kernel tweaked for audio performance, as well as a host of audio applications.

Hopefully this helps.  You may also want to read through the [UbuntuStudio community wiki](https://help.ubuntu.com/community/UbuntuStudio") as there are some interesting and helpful tidbits gathering there.

---

### Post by nlz on 2008-12-15
i was also used to cool edit pro and use both Ardour and Audacity now. Ardour for advanced mixing and recording, but for fast work (and also to 'see' more directly what I do) I use audacity.

---

### Post by Dumbestcrayon on 2008-12-15
Thanks I think I like Ardour because its complicated =P . Adobe Audition is very complicated and once I got used to it I loved the things I could do. 

Thanks a bunch.

---

### Post by Ng Oon-Ee on 2008-12-15
> **Stochastic said:**
> For multitrack editing, you NEED Ardour - it's unbeatable and could easily stand head-to-head with pro tools.  I have no idea what Ng Oon-Ee is talking about when he says it's really complicated - for anyone who's used Audition, Ardour is a natural transition.

Perhaps to better explain what I meant, Ardour has many more capabilities, therefore it is much more complicated.

> **Stochastic said:**
> For a wave editor, I like Rezound, others think audacity is good, there are MANY to choose from in the repositories.  As for Ng Oon-Ee's claim that audacity doesn't work from the repos - I haven't experienced this nor have I heard about this before now.  He also doesn't explain which version of Ubuntu or Audacity he's talking about, but I don't want to hijack your thread to troubleshoot his problems.

Also for explanation, this is the case both for Hardy and Intrepid, Audacity as is does not play well with Pulse nor does it communicate with JACK. Of course, most capable audio workstations would have had Pulse removed and rely on ALSA-mix, but this isn't the same as fully functional from repos in a default install.

My apologies for not being detailed, my problems as they were have already been resolved or at least worked around. I just wanted to inform the OP of the troubles that seem to afflict many first-time Audacity users (this is my subjective judgement from my own experience and browsing these forums for Audacity-related topics).

> **Stochastic said:**
> If you really want to start producing audio on your linux machine, you may want to install the UbuntuStudio packages [http://www.ubutustudio.org](http://www.ubutustudio.org) as it has the realtime kernel tweaked for audio performance, as well as a host of audio applications.

QFT. Ubuntu Studio rocks, saves a lot of work. You may want to stick to Hardy for this, though, as the real-time kernel which many consider to be the most important bit of Studio is not fully functional (read - many weird bugs) in Intrepid. Specifically, dual-cores are not useable/detected and shutdown/restart is really bugged.


Another issue which may or may not be important to you, Ardour does not work with non-proprietary formats, whereas Audacity does. This was a clincher for me, as I have many mp3 resources. However, for professional applications where you're fully loss-less at all stages anyway, then this is not an issue.

---

### Post by ussndmac on 2009-01-29
> **Dumbestcrayon said:**
> Thanks I think I like Ardour because its complicated =P . Adobe Audition is very complicated and once I got used to it I loved the things I could do. 

Thanks a bunch.

As others have pointed out the choices are pretty much Ardour and Audacity.

I say A&A because Audition allows both mutitrack work and destructive editing in one place.

Ardour is a multi track mix/master tool and Audacity is a destructive editor.

I suppose Ardour is complicated, but once you get it through your head that it sort of mimics an old analog studio, at least for me, it helps.

Mac

---

### Post by simtaalo on 2009-01-29
goto getdeb and get audacity from there, installs+runs with no problems at all.

---

### Post by Ng Oon-Ee on 2009-01-31
> **julian5 said:**
> You can even install Adobe Audition.

You need to install a Windows emulator like Wine and run it on a copy of Windows within the emulator.

Or, you can try downloading Audacity, which is open source, free, and runs natively under ubuntu.

--Julina
While the idea does sound good, Adobe Audition does not work well in Wine (read, does not work at all). Please [check the Wine appdb here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2538") to see what apps will or will not currently work with Wine.

The problem with Wine for audio usage is that its stuck on 16-bit sound due to its architecture. Great for games, not so much for professional audio. Add on to that that its practically impossible for low-latency access using Wine (perhaps the JACK out/input helps with that though).

P.S. This thread is actually from one and a half months ago =).

---

