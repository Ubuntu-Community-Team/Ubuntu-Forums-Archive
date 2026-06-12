---
title: "Annoying YouTube issue"
date: 2008-05-31
forum: System76 Support
---

### Post by ctsdownloads on 2008-05-31
Definitely not something I am having much luck with. Latest recommended updates on 8.04 64 bit, tested with both Flash 9 and 10-beta - all other Flash video seems to be fine (Ustream.tv, etc) however youtube has a nice little habit of playing 3-5 seconds of video then stopping.

Not appearing to be network related, tested on both wifi and wired. Also stopped Pulse audio and even that did not seem to help.

Was thinking it might be related to this bug, however even taking steps to make sure pulse audio is out of the picture is not helping...grrrr.

[http://ubuntuforums.org/showthread.php?t=598034&page=2](http://ubuntuforums.org/showthread.php?t=598034&page=2)

:mad:

I have to get back to work, but at any rate, I doubt seriously that this is an isolated incident. I have been here before with this issue, last time I believe it was fixed with a system76 driver upgrade, but could be wrong.

Tom, seriously, I am pulling my hair out - you name it, I have removed, reinstalled or tried alternative versions of it. I need this to be resolved, hoping it can be. This includes everything relating to Flash and its wrapper, extra support modules and even a separate install of firefox RC 1 with Flash 10 - I believe this is something YouTube specific, but cannot figure it out.

---

### Post by ctsdownloads on 2008-05-31
Well, n/m that, it is ALL flash based video sites...

I am leaning with audio issue.. :confused:

---

### Post by ctsdownloads on 2008-05-31
Well that was interesting. Running on LiveCD, then installing Flash (I have a lot of RAM), things work fine.

final thoughts - it must be a hosed configuration (doubtful) or more likely, one of the updates that messed things up. Will backup my home folder and reinstall later.

---

### Post by buntunub on 2008-05-31
Really weird. I have 5 home systems of various flavors all running Hardy. Some are x64, some are i386, couple of them are laptops. Some were upgraded from Gutsy, some have fresh installs. Not one single one of them however, has ever had any problems whatever with flash or java.

---

### Post by ctsdownloads on 2008-05-31
> **buntunub said:**
> Really weird. I have 5 home systems of various flavors all running Hardy. Some are x64, some are i386, couple of them are laptops. Some were upgraded from Gutsy, some have fresh installs. Not one single one of them however, has ever had any problems whatever with flash or java.

Yeah, I must have hosed something with my existing config myself. My 32 bit 8.04 and 7.04 (never bothered with Gutsy much) never gave me this problem either. I guess I will just bu the home folder and track the updates closely, testing each time with YouTube for changes.

---

### Post by tk03759 on 2008-06-02
I've got a weird problem with youtube and myspace music players where flash plays, but its just a gray box with no visual (no video or no audio control). It fixes sometimes if I turn off Basic Page Styles in firefox and then turn them back on.
Really odd. This is a fresh install.

---

### Post by thomasaaron on 2008-06-02
Try turning off Desktop effects and see if you still get that problem.

---

### Post by ctsdownloads on 2008-06-09
> **thomasaaron said:**
> Try turning off Desktop effects and see if you still get that problem.

Thanks, will try this. To reiterate since doing a clean install, all Flash works fine (including YouTube now), now it's just the issue with Ustream.tv specifically and only [as described here]("http://ubuntuforums.org/showthread.php?t=776311").

---

### Post by noerrorsfound on 2008-06-09
Disabling Desktop Effects won't do anything because this is a Flash bug.

---

### Post by ctsdownloads on 2008-06-09
> **noerrorsfound said:**
> Disabling Desktop Effects won't do anything because this is a Flash bug.

Eh, not too sure about it being a Flash bug as I mentioned in the above linked post that everything is working outside of one streaming service. So it might be a Flash bug with one service perhaps, but it seems to me that the bulk of the issue is elsewhere.

---

### Post by gameryoshi600 on 2008-06-10
> **noerrorsfound said:**
> Disabling Desktop Effects won't do anything because this is a Flash bug.

its the truth. Linux has lots of flash bugs. T[here is a list of bugs and you can vote for them to be fixed]("http://ubuntuforums.org/showthread.php?t=769906")

---

### Post by ctsdownloads on 2008-06-10
> **gameryoshi600 said:**
> its the truth. Linux has lots of flash bugs. T[here is a list of bugs and you can vote for them to be fixed]("http://ubuntuforums.org/showthread.php?t=769906")

Sorry, should have been more specific. Yeah, Linux has plenty of Flash bugs, however based on my research, they apparently do not apply in this case as it affects one single website's service, not Flash in general. :)

YouTube works just fine as do every other Flash site I choose to use.

---

