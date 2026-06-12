---
title: "Why do my Wine windows keep vanishing?"
date: 2010-07-26
forum: Wine
---

### Post by movieman on 2010-07-26
Does anyone know why, when I leave a Wine window running on a desktop and switch away for a while, the window will often have vanished by the time I switch back? I can see the program still running in 'ps', but the Wine window simply isn't there, on the screen, in the taskbar or in the alt+tab list. I've even seen a program pop up other windows when something happens (e.g. asking what to do when I insert a CD), even though the main window is nowhere to be found.

Having to exit the program any time I want to switch away to another desktop is a real pain.

---

### Post by sikander3786 on 2010-07-26
Hi.

Having another Virtual Desktop is a real pain (specially when you are already running 2, 3 or even 4 desktops) but I had the same problem in Jaunty and was solved by Wine Virtual Desktop. Nothing else I could figure out then.

---

### Post by asdfoo on 2010-07-26
what's the output on the terminal for the program that has disappeared?

make sure you're using wine 1.2

---

### Post by movieman on 2010-07-26
> **asdfoo said:**
> what's the output on the terminal for the program that has disappeared?

There's nothing new there, just the messages that came out at startup. I'm running whatever the latest version is in the Ubuntu repositories, which appears to be 1.1.42.

I'll take a look at Wine Virtual Desktop and see if that helps!

---

### Post by asdfoo on 2010-07-26
> **movieman said:**
> There's nothing new there, just the messages that came out at startup. I'm running whatever the latest version is in the Ubuntu repositories, which appears to be 1.1.42.

I'll take a look at Wine Virtual Desktop and see if that helps!

1.1.42 is a few months old now and is missing many of the latest fixes

visit winehq.org and follow the instructions for ubuntu

---

### Post by mjuhasz on 2010-07-28
This bug was fixed in 1.2-rc4. See: [http://bugs.winehq.org/show_bug.cgi?id=10142](http://bugs.winehq.org/show_bug.cgi?id=10142)

---

