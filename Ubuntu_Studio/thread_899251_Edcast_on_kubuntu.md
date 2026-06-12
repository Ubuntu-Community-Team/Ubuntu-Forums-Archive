---
title: "Edcast on kubuntu?"
date: 2008-08-24
forum: Ubuntu Studio
---

### Post by moody_mark on 2008-08-24
Hi, I currently use a Windoze PC to stream to a shoutcast server. Edcast (on windows) seems to be a viable alternative to the shoutcast DSP plugin, so I was wondering if Edcast will run on linux, as I would very much like to swap my streaming PC over to Kubuntu

If anyone has any pointers or links that will be greatly appreciated

---

### Post by Stochastic on 2008-08-24
I've never used Edcast, but according to the wikipedia article: > Edcast is one of the few (if only) free and open source encoders that is supported (in various forms) on both Windows and Linux platforms.

Although it's not in the ubuntu repositories, or readily found through google....  hmmm... I'll keep looking into this one.

---

### Post by moody_mark on 2008-08-25
Exactly, apparently its supposed to be supported on Linux but the only download I could get was a ".exe" file which was the same as the one I downloaded for using on the windows PC I use to stream on.

Im really suprised that I couldnt also google up some more on this. Surely not ALL internet radio station DJs use windoze? ;-)

---

### Post by Stochastic on 2008-08-28
Have you tried running the .exe with wine?

There are other linux apps that will work.  One that immediately comes to mind is called IDJC (url: [http://www.onlymeok.nildram.co.uk/](http://www.onlymeok.nildram.co.uk/) )

Edit: AHA! here's edgecast's SVN repository: [http://svn.oddsock.org/public/trunk/](http://svn.oddsock.org/public/trunk/)
This is a means of accessing the sourcecode of edgecast, so unless a pre-made package also exists, you'll need to build it from scratch.  Do you know how to use SVN?

---

### Post by moody_mark on 2008-08-29
> **Stochastic said:**
> This is a means of accessing the sourcecode of edgecast, so unless a pre-made package also exists, you'll need to build it from scratch.  Do you know how to use SVN?

Havent tried with Wine, but im trying to stay away from windows emulators. I havent used SVN or even done much building from scratch. Is there any good reading you could recommend (im pretty much a Linux beginner, thanks

---

### Post by Stochastic on 2008-08-30
Well I'd recommend the ubuntu community docs as a good starting place.  Here's a nice walkthrough of how to compile software from source (what you'll need to do after getting the software from subversion): [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

In general when building anything from source, there will be a few different methods you may encounter and the first place to look is the README file or INSTALL file inside the software source (it'll give instructions on how to compile).

Getting the software from the SVN is a simple process of doing ```
svn checkout http://svn.oddsock.org/public/trunk/edcast/
```  This will download the files located in the public SVN to your harddrive, then you go about building it.

---

