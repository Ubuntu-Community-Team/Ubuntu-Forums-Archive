---
title: "Second Life in 64-bit Ubuntu?"
date: 2011-01-02
forum: System76 Support
---

### Post by azion1995 on 2011-01-02
OK, so Linden Labs has a linux client for Second Life. Great. But it doesn't *quite* work in 64 bit linux: no music. Ambient sounds are audible, so I know it's not an audio problem, but no music- and I *know* there should be music (I'm at virtual concerts).

A Google search has revealed that this is a common problem- that the 64 bit SL viewer doesn't play the music. But has anyone here had any success with this? Heck, has anyone just geeked out and compiled a full 64 bit version from source code?

Any thoughts would be appreciated.

Thx,
-Z

---

### Post by azion1995 on 2011-01-02
Never mind- I solved my own problem. Turns out that the Open Metaverse Viewer project has a native 64 bit Ubuntu viewer, and it plays streaming music perfectly. The repositories are for Lucid, but it still works. Here's the link, in case anyone else is interested:

[http://omvviewer.byteme.org.uk/index.php/downloads/ubuntu/](http://omvviewer.byteme.org.uk/index.php/downloads/ubuntu/)

FWIW, the real-world acquaintance who plays gigs online goes by the alias of Twinghost Rhonas, and his group is the Twin Ghost Gang. Check him out- seriously good guitar work.

-Z

---

### Post by velvetsanity on 2011-03-29
unfortunately, OMV isn't fully functional on my system, with quite a few problems.  plus it's based on an outdated SL viewer (2.0.1).  I'm working on trying to get the latest release viewer to compile, but having trouble with configuring it to compile for 64-bit

---

### Post by isantop on 2011-03-29
Can you try the latest Viewer from Linden?

[http://wiki.secondlife.com/wiki/Linux_Viewer#64-bit](http://wiki.secondlife.com/wiki/Linux_Viewer#64-bit)

---

### Post by velvetsanity on 2011-03-29
the 32-bit viewer works on my system, but I'm also having the problem with the streaming audio.  I can edit the launch script for a partial fix:  it'll play, but it spurts and stutters.  I've gotten to the point in the instructions Linden Labs provides to where I'm repeatedly trying to compile and finding libraries missing that they don't mention.  Right now I'm stuck on getting google-breakpad installed so that the compile scripts can find it :\

---

### Post by isantop on 2011-03-30
Have you tried the Open Metaverse Viewer? What are the features in the new one it's missing? You may be fine there.

---

### Post by gigabz666 on 2011-05-16
> **velvetsanity said:**
> the 32-bit viewer works on my system, but I'm also having the problem with the streaming audio.  I can edit the launch script for a partial fix:  it'll play, but it spurts and stutters.  I've gotten to the point in the instructions Linden Labs provides to where I'm repeatedly trying to compile and finding libraries missing that they don't mention.  Right now I'm stuck on getting google-breakpad installed so that the compile scripts can find it :\

I've personally had a nightmare trying to sort this out. The only way I know how to fix the issue is to tell the compiler to ignore google-breakpad completely. You have to edit three files and comment out anything referring to google-breakpad. I've then since been able to successfully compile a 64 bit version of SL.

Now they've introduced autobuild though, I've not been able to compile again. The instructions for those with 64 bit systems is just awful and I've had very little help in IRC channels and such since the change.

---

