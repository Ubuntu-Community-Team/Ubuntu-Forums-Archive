---
title: "Well, happy new year to you too, XScreenSaver, but why whine now ?"
date: 2015-01-01
forum: The Cafe
---

### Post by HerixFromParis on 2015-01-01
First boot of the year, and I'm greeted by a transient XScreenSaver splash reading "This version is very old, please upgrade".

I'm a bit puzzled because
[LIST]
[*] I'm on autologin
[*] I usually don't see XScreenSaver unless I explicitely lock the screen
[*] I'm on Xubuntu 14.10, yes it's last year's version ;-)
[*] This is not the usuall Ubuntu way to prompt for updates
[/LIST]

For a couple of seconds I was even worried that it could be some sort of malware (coffee hadn't kicked in yet ;-) )

A quick googling points straight to [https://github.com/danfuzz/xscreensaver/blob/master/driver/splash.c](https://github.com/danfuzz/xscreensaver/blob/master/driver/splash.c) so OK that's the legit thing. Specifically on lines 225-226 :
```
if (whine)
{
[INDENT]sp->body3_label = strdup("WARNING: This version is very old!");
sp->body4_label = strdup("Please upgrade!");[/INDENT]
}
```

the ```
Bool whine
``` seems to be defined in another library but I'm not a fluent enough reader of C and it's too early in the morning to investigate further and it's not the point anyway.

The point is ... well I don't know exactly. Maybe the version in the Xubuntu repositories is very old indeed. I rekon I don't know anything on how a distro is put together. Then, what's the logic of XScreenSaver showing up at boot time ? And by showing up, it's just a flash, then it's gone. Anyway, it seems there is an itch about this whole screen saver thing in Xubuntu, like it doesn't know exactly which strategy to follow : in the Parameters menu, there is something for XScreenSaver indeed (which, by the way, displays the same "old version" message [IMG]http://i.imgur.com/LEiiXgZ.png?1[/IMG]) , then there is something for Light Locker ... And then the screen saver kicking in in the middle of a movie ... Or maybe the autologin thing is not completely mature yet ?

But finally, I really appreciate this : something puzzles me, and I am able to quickly zoom in to where it happens in the source code, even though I'm not a competent programmer.

Good year to you, friends !

---

### Post by Dennis N on 2015-01-01
You had to install xscreensaver, since it is not part of the default Xubuntu 14.10. It has to be in your startup applications as well. I have always installed it on my own computers, but never seen such a message. The splash should be disabled - maybe yours isn't. If not disabled, disabling the splash might prevent the message. You should use **xscreensaver -no-splash** as the startup command.

---

### Post by Dennis N on 2015-01-02
I see a similar warning when I started up Xubuntu 14.10 today, so the command is not at fault as suggested in post #2. Never appeared before now. My warning advised I had version 5.26 and that it is "very old". Yours doesn't mention a version. Looks like it is going to nag us on every login. Need to investigate further.

---

### Post by oldos2er on 2015-01-03
I just grabbed xscreensaver_5.30-1+b1_amd64.deb and installed it. Problem solved.

---

### Post by Dennis N on 2015-01-03
I solved mine by using the previous version, 5.15, so that is also possible. No files other than xscreensaver (such as xscreensaver-gl or the data files) needed to be changed.

---

