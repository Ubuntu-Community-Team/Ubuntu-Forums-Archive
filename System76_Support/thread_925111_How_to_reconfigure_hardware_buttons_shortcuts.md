---
title: "How to reconfigure hardware buttons shortcuts?"
date: 2008-09-20
forum: System76 Support
---

### Post by Tart on 2008-09-20
Hi All,

I have Gazelle Ver5. I would like to reconfigure shortcuts keys for my hardware buttons. There are 5 of them and I don't really know that two of them do. One has S with outlet on the end, the other does something with USB. I would like to reassign them to something I use often. How do I do this?

Then I go to System->Preferences->Keyboard Shortcuts, and try to change preferences (for example I would like one of these button to run terminal) it would not react to me pressing these buttons. 

Thanks

---

### Post by thomasaaron on 2008-09-22
Yeah, I get the same thing on my GazV5.

I was able to configure the terminal to launch with, say, ctrl-alt-z.
It appears to configure with the hardware key but doesn't actually work.

I also tried calling gnome-terminal from /etc/acpi/mutebtn.sh and that didn't work, so it is not calling the main muting script.

I also tried configuring it via gconf-editor.

It seems to be hard-wired. I'll try to dig deeper into it.

---

### Post by tssgery on 2008-09-22
I've got a similar question about my Pangolin Performance. There are three buttons on the top left (Mail, Web, and one with an "M")...

What does the "M" button do by default (I don't see anything happen), and how do I set it up to launch a terminal?

---

### Post by thomasaaron on 2008-09-22
M is for Mute

Try setting it via System > Preferences > Keyboard Shortcuts.
If that doesn't do it, it is probably a similar issue to what is being discussed regarding the gazv5.

---

### Post by tssgery on 2008-09-22
> **thomasaaron said:**
> M is for Mute

Try setting it via System > Preferences > Keyboard Shortcuts.
If that doesn't do it, it is probably a similar issue to what is being discussed regarding the gazv5.

Well, it actually seems to be controlling the fan! when I press it, the fan toggles from high to low speed. very interesting. Going in to reset it via Keyboard shortcuts doesn't seem to work either. It seems to not realize a key has been depressed. 

I'll watch this thread and see where it goes.

---

### Post by thomasaaron on 2008-09-22
Ah, I see. On the documentation, it said "Silent Mode." So that probably means it slows the fan speed down. I assumed it meant mute. My bad.

---

### Post by Tart on 2008-09-23
Hey Thomas,

It is a really minor issue, I though there maybe quick and easy way to do it. If it too much trouble to figure it out, don't bother.

---

