---
title: "Free Software, Take Note: An Overview of Gnote 0.5.1"
date: 2009-06-27
forum: The Cafe
---

### Post by DeadSuperHero on 2009-06-27
Just finished my [write up]("http://www.fsdaily.com/EndUser/Free_Software_Take_Note_An_overview_of_Gnote_0_5_1") of an overview of Gnote, I thought current Tomboy users who are aware of the Mono issue would at least be interested in seeing what Gnote has to offer, complete with screenshots.

> Gnote was started on April 2009 by Gnome developer [Hubert Figuiere]("http://www.figuiere.net/hub/blog/"), known also for his work on Abiword. The goal of Gnote is to provide a Free Software implementation of Tomboy that doesn't rely on Mono. The ultimate goal is to replace Tomboy in an effort to make Gnome and GNU/Linux distributions non-dependant on Novell's implementation of Microsoft's .NET platform. For our testing purposes, I installed Gnote 0.5.1 on Ubuntu Jaunty through a personal PPA. I would love to see it packaged in Ubuntu officially in the near future.

---

### Post by directhex on 2009-06-27
Does it work on a clean install? 0.5.0 had a buggered default note

---

### Post by DeadSuperHero on 2009-06-27
You have to add the PPA for Jaunty, but it works like a charm.

[https://launchpad.net/~gnote/+archive/ppa](https://launchpad.net/~gnote/+archive/ppa)

---

### Post by pt123 on 2009-06-27
Is it possible to set the font used for fixed width in tomboy or gnote this is frustrating when you wish to do code snippets

---

### Post by gnomeuser on 2009-06-27
> **pt123 said:**
> Is it possible to set the font used for fixed width in tomboy or gnote this is frustrating when you wish to do code snippets

Tomboy has a plugin to do fixed width formatting would that suffice?

(right click the applet, select preferences then the plugins tab and it's under formatting).

---

### Post by DeadSuperHero on 2009-06-27
Yeah, currently I don't see an add-in for formatting in Gnote just yet, but it supports basic formatting natively with font sizes, bold, italicized, bullet points, etc.

I'll suggest this to the developer for a future version.

---

### Post by days_of_ruin on 2009-06-27
I see that you got it linked to on slashdot :D

---

### Post by pt123 on 2009-06-29
> **gnomeuser said:**
> Tomboy has a plugin to do fixed width formatting would that suffice?

(right click the applet, select preferences then the plugins tab and it's under formatting).

I know about that it comes enabled by default. But there is no way to set the font used for fixed width. This sucks esp. on Windows using its ugly default fixed width font.

---

### Post by k2t0f12d on 2009-06-29
You can select a fixed width default in Gnote prefs.

---

### Post by pt123 on 2009-06-30
> **k2t0f12d said:**
> You can select a fixed width default in Gnote prefs.

sweet more reasons to try it.

---

### Post by directhex on 2009-06-30
[Bug 534969](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=534969) is coming to eat your notes. FYI. Be sure to keep a backup.

---

### Post by nlp on 2009-07-10
> **directhex said:**
> [Bug 534969](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=534969) is coming to eat your notes. FYI. Be sure to keep a backup.
It's odd that you would link to a bugreport that was already closed-fixed before you even posted, but then I guess it's not the first time:

[http://mono-nono.com/2009/07/06/counting-on-you/](http://mono-nono.com/2009/07/06/counting-on-you/)

FUD-much?

---

### Post by directhex on 2009-07-10
> **nlp said:**
> It's odd that you would link to a bugreport that was already closed-fixed before you even posted, but then I guess it's not the first time:

[http://mono-nono.com/2009/07/06/counting-on-you/](http://mono-nono.com/2009/07/06/counting-on-you/)

FUD-much?

Um, right, because this post ISN'T about version 0.5.1, which specifically causes the bug, right?

---

### Post by BuffaloX on 2009-07-10
In a way Gnote being a total copy of Tomboy is sad.
Doesn't the Gnote developers have any ideas themselves?

I use Zim with a hotkey binding to take instant notes, and organizing them.
Zim is quite cool, but very different, you may want to try it out.

---

### Post by Warpnow on 2009-07-10
I've never understood why note taking is better that way than notecase. I much prefer notecase. I just wish the pro version wasn't so expensive.

---

### Post by hanzomon4 on 2009-07-10
The Mono issue in a nutshell... *AWWWW Microshaft!!* #-o

Come on people!!!

---

### Post by nlp on 2009-07-10
> **directhex said:**
> Um, right, because this post ISN'T about version 0.5.1, which specifically causes the bug, right?

Just who do you imagine would still be using version 0.5.1?  The review author clearly stated that he installed gnote using the Ubuntu PPA (as would anyone who uses gnote on Ubuntu), and the bug you are claiming will "eat your notes" (though this was *never* true) was fixed in 0.5.2. Since the new version was distributed to Ubuntu's gnote users over a week ago, this is a non-problem.

Why are you posting dire (and highly exaggerated!) warnings about bugs in a software version no one is using any longer?  How is this helpful?

You seem determined to try to discourage people from trying gnote, even if it means lying about the software and its capabilities.  gnote certainly has some limitations both in its design and implementation, and will sometimes have bugs (as does Tomboy, or any software), but it would be more honest to point to *actual* problems, rather than past ones.

---

### Post by tgalati4 on 2009-07-10
I like zim, but I will give gnote a spin.

Tomboy was simply a mockup until the usability was sorted out. Now it can be coded correctly.

Not sure what all the fuss is about.  Mono is good for mockups.

Any takers to recode banshee?

---

### Post by zekopeko on 2009-07-10
> **tgalati4 said:**
> I like zim, but I will give gnote a spin.

Tomboy was simply a mockup until the usability was sorted out. Now it can be coded correctly.

Not sure what all the fuss is about.  Mono is good for mockups.

Any takers to recode banshee?

you are confusing it with python...

---

### Post by hanzomon4 on 2009-07-11
> **nlp said:**
> Just who do you imagine would still be using version 0.5.1?  The review author clearly stated that he installed gnote using the Ubuntu PPA (as would anyone who uses gnote on Ubuntu), and the bug you are claiming will "eat your notes" (though this was *never* true) was fixed in 0.5.2. Since the new version was distributed to Ubuntu's gnote users over a week ago, this is a non-problem.

Why are you posting dire (and highly exaggerated!) warnings about bugs in a software version no one is using any longer?  How is this helpful?

You seem determined to try to discourage people from trying gnote, even if it means lying about the software and its capabilities.  gnote certainly has some limitations both in its design and implementation, and will sometimes have bugs (as does Tomboy, or any software), but it would be more honest to point to *actual* problems, rather than past ones.

Or non-existing problems \\:D/

Mono for the world... that could actually come across as gross

---

### Post by Viva on 2009-07-12
Is there a gnome-panel applet for gnote?

---

### Post by DeadSuperHero on 2009-07-12
> **Viva said:**
> Is there a gnome-panel applet for gnote?

Yeah. If you look at the screenshots in the review, you'll notice that Gnote is functionally the same to Tomboy.

---

