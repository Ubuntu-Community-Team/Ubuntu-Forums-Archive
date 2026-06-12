---
title: "Rosegarden 10.2 Thorn Released"
date: 2010-02-14
forum: Ubuntu Studio
---

### Post by barisurum on 2010-02-14
For now it can only be compiled from source. I will test and let you know how it works.

---

### Post by kayosiii on 2010-02-15
compiling now

---

### Post by prokoudine on 2010-02-15
A guy built a deb for i386: [http://solostudio.nnov.ru/sites/default/filesfile/soft/rosegarden_10_02-1_i386_deb.zip](http://solostudio.nnov.ru/sites/default/filesfile/soft/rosegarden_10_02-1_i386_deb.zip)

I hope he can start a PPA instead though :)

---

### Post by trulan on 2010-02-16
I'm using the .deb made by Gmaq from AVLinux (in AVLinux, don't know if his would work in Ubuntu or not) and it is sweet.  Maybe I just finally figured out what I was doing, but midi, qsynth, vst plugins, it all worked flawlessly which has never happened before with Rosegarden.  Maybe philip5 will package this for us in his ppa.  I'll link this thread to his here:
[http://ubuntuforums.org/showthread.php?t=1350304&page=18](http://ubuntuforums.org/showthread.php?t=1350304&page=18)

---

### Post by VertexPusher on 2010-02-16
Does this version of Rosegarden still install 80% of the KDE desktop as a dependency?

---

### Post by prokoudine on 2010-02-16
> **VertexPusher said:**
> Does this version of Rosegarden still install 80% of the KDE desktop as a dependency?
You wouldn't ask that if you read release notes :) There is no dependency on KDE now, it's a pure Qt4 application.

---

### Post by trulan on 2010-02-16
And here it is for Karmic, in philip5's ppa.  That's right, no KDE dependencies.
[https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75](https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75)

---

### Post by VertexPusher on 2010-02-17
> **prokoudine said:**
> There is no dependency on KDE now, it's a pure Qt4 application.
That's great. I remember they were planning this for Thorn. Currently I am using Qtractor, but competition is always a good thing. ;)

---

### Post by barisurum on 2010-02-17
I think the "final" product has many missing features that prevent me from using it. The pros and cons:

Pros:

* Pure qt4 application
* Much simpler to use midi device and external control management
* Looks stable enough not to crash :D

Cons:

Definitely not an end product because;

* Velocity ruler lines are missing (one of the most important features a composer uses to make music)
* Gui works slow, the wheels on the lower right and left are sluggish and useless
* Gui space is not planned well
* Possible memory leak signs (performance deteriorates over time)

---

### Post by prokoudine on 2010-02-17
> **barisurum said:**
> 
Cons:

Definitely not an end product because;

* Velocity ruler lines are missing (one of the most important features a composer uses to make music)
* Gui works slow, the wheels on the lower right and left are sluggish and useless
* Gui space is not planned well
* Possible memory leak signs (performance deteriorates over time)
If you want to see any of those fixed, then perhaps you realize that this forum is somewhat  a wrong place for that and that you could possibly wrap up the above in more descriptive text and send it to developers either way :)

---

### Post by barisurum on 2010-02-17
1. Do you know if I report bugs or not? no... so its not logical to say that.
2. The purpose of this thread is to give an impression to multimedia creators and to share experiences. And to encourage people to do just as you say, report bugs to make it better ;)

---

### Post by prokoudine on 2010-02-18
> **barisurum said:**
> 1. Do you know if I report bugs or not? no... so its not logical to say that.
I understand that English is not your native language, and neither it is mine, but could you please try to rephrase the quote above so that everyone understood what you tried to say? :)

> 2. The purpose of this thread is to give an impression to multimedia creators and to share experiences. And to encourage people to do just as you say, report bugs to make it better ;)
But you won't change anything that way. Reporting things directly to developers works, while complaining in some forum definitely doesn't. It's really that simple :)

---

### Post by trulan on 2010-02-18
Well, English is my native language, and I can understand both of you with no trouble at all.  Please, lighten up!  Go make some happy music or something...

For all we know, barisurum may have already filed several bugs on this issue.  You criticized him without knowing whether or not he reports bugs.  That's what he was saying.

---

### Post by prokoudine on 2010-02-19
> **trulan said:**
> Well, English is my native language, and I can understand both of you with no trouble at all.
Good for you :) However...

> **trulan said:**
> For all we know, barisurum may have already filed several bugs on this issue.  You criticized him without knowing whether or not he reports bugs.
No, you definitely don't understand me. I'm not criticizing, I'm suggesting. I can file bug reports myself for him if he cares to explain what exactly he was meaning — no problem. But if the whole point of commenting was to say that he doesn't like Rosegarden, well... :)

---

### Post by barisurum on 2010-02-19
Have a look at this thread and enlighten yourself a bit:

December 27th, 2009
[http://ubuntuforums.org/showthread.php?t=1365751](http://ubuntuforums.org/showthread.php?t=1365751)

---

### Post by prokoudine on 2010-02-19
> **barisurum said:**
> Have a look at this thread and enlighten yourself a bit:

December 27th, 2009
[http://ubuntuforums.org/showthread.php?t=1365751](http://ubuntuforums.org/showthread.php?t=1365751)
*sarcasm* Oh, so kind of you! Now, what is there to enlighten myself with? "Some parts like scrolling, multiple note selection, event rulers are still crap."? What kind of explanation is that? Come on, I know you a smart guy, you can do better than that.

---

### Post by barisurum on 2010-02-20
Without criticism and freedom of speech it will turn out to be an eastern bloc style development in which the users have no right to criticize anything and always have to be happy with the outcome.. But the outcome will always be the same: collapse.

---

### Post by prokoudine on 2010-02-21
> **barisurum said:**
> Without criticism and freedom of speech it will turn out to be an eastern bloc style development in which the users have no right to criticize anything and always have to be happy with the outcome.. But the outcome will always be the same: collapse.
Blimey, what the hell are you talking about? The question is NOT about freedom of speech. The question is: what are Rosegarden's bugs exactly? I don't bloody care if you like Rosegarden or not. I really don't. All I want is details to log them into tracker. What's the point of resisting to provide details and help developers to make the application better?

---

### Post by mango42 on 2010-02-21
Grief - this thread has turned from the delight at hearing there's a new version of Rosegarden available to some weird between-the-lines ideological tussle!

+1 for trulan's take - lighten up! Although I guess if this is a Turkey vs Zionism thing, count me out, on this forum at least! WhatReallyHappened or Les Visible's blogs would be better venues for any politically oriented bitterness...

Those who want to file bugs - just file them!

Those who want to make music but the software is getting in their way - try something else. Alternatively, there's no real harm in criticising ergonomics or failure to understand why a certain app doesn't do stuff the way you'd expect it to. In this Linux world awash with literally hundreds of ways of achieving the same end, developers should develop thick skins *before* releasing code - the very fact they are being criticised is **good**, IMO - it means someone actually cares about their offering! ;-)

Whatever - groove on ;-)

---

### Post by prokoudine on 2010-02-21
> **mango42 said:**
> Grief - this thread has turned from the delight at hearing there's a new version of Rosegarden available to some weird between-the-lines ideological tussle!
Ideological? Not from me :)

> there's no real harm in criticising ergonomics

Right, there is nor harm criticizing anything provided you actually explain what exactly it is that you criticize :) I think I've heard enough strange things today already, so it's end of discussion with barisurum for me.

In the mean time, a bugfix release of Rosegarden is out.

It basically completely disables partially disabled and unfinished new progress dialogs. So if you've seen some weird phantom dialogs in top left corner, they should be away now.

[Download source]("http://sourceforge.net/projects/rosegarden/files/rosegarden/10.02/rosegarden-10.02.1.tar.bz2/download")

---

### Post by philip5 on 2010-02-26
> **prokoudine said:**
> 
In the mean time, a bugfix release of Rosegarden is out.

It basically completely disables partially disabled and unfinished new progress dialogs. So if you've seen some weird phantom dialogs in top left corner, they should be away now.

For anyone who prefer deb-packages to hussle with dependencies to compile the latest Rosegarden 10.02.1 do I have it on my Launchpad repository ready for any Ubuntu Karmic user t enjoy.

The update make the gui look much cleaner and that's a nice step.

Have fun!

---

