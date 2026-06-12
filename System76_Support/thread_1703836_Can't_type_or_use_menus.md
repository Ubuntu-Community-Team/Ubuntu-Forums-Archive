---
title: "Can't type or use menus"
date: 2011-03-09
forum: System76 Support
---

### Post by Carleas on 2011-03-09
I'm on a new Starling, and I've been having an experience from time to time where I'm unable to type or use menus, and the only thing I've found that fixes it is hard rebooting by holding down the power button.

The keyboard hardware still works, because I can still turn the use fn to trackpad on and off etc., but I can't input text in any application (tried Chrome, gedit, terminal).  Furthermore, I can't use any menus, so right clicking doesn't do anything, and I can't use the power menu to restart.

The past time, I had been watching a show no Hulu full screen, and when I ended I noticed the problem.  While clicking around, I tried the update manager thinking some update might restart things.  When I hit "check" I got an error that said something like "could not grab keyboard", and mentioned malicious software or another application that had 'focus'.

That latter suggestion seems right, considering I was exiting full screen; could my keyboard be stuck giving its input to Hulu?  Is there a way to prevent that from happening?  and more importantly, if it does happen, is there a way to get back from it without holding down the power button?

---

### Post by isantop on 2011-03-10
You might try pressing Alt+PrtSc+R if your keyboard dosen't seem to work. That should put the keyboard back into "Raw Mode" which may allow you to use it. As for rebooting, it should bring up a dialog box if you press the power button and release it. You can use that to shut down, restart, etc.

Does this only happen after viewing full-screen flash content? Or is it triggered by other things too? Or, is it completely random?

---

### Post by Carleas on 2011-03-13
It's only happened when exiting full screen video, but I don't think I have a large enough sample size to say that's the only time it happens (I've only had the computer for a couple weeks).

I'll try the solutions you've suggested.  Is there something I can do to diagnose things further once I've switch to raw keyboard mode?  Perhaps a terminal command to test the "focus"?

Thanks for your help.

---

### Post by kbon on 2011-03-21
I have a friend who had the same issue on his laptop pc. His keyboard wouldn't respond every five minutes or so however, which is more frequent than yours...he's on Ubuntu netbook 10.10

---

### Post by isantop on 2011-03-21
Can he test it with Ubuntu Netbook Edition 10.04, since we don't officially support 10.10 on the Starling?

---

### Post by zimbico on 2012-12-19
I know this thread is old, but..
I just had this problem on 12.10. Turns out it was caused by attempting to drag an icon around on the unity sidebar, which then didn't go back in place properly. I got back the use of menus and my keyboard by simply dragging another icon which seemed to fix the original icon's position as well..
Anyway, I thought I'd post in case this was helpful for anyone else =)

---

