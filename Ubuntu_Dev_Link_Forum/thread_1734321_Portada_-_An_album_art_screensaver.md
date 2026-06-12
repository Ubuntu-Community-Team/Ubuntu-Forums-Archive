---
title: "Portada - An album art screensaver"
date: 2011-04-20
forum: Ubuntu Dev Link Forum
---

### Post by Tahakki on 2011-04-20
Something I always wanted, having seen it on a friend's Macbook, was an album art screensaver. I couldn't find a single one for Ubuntu, so I decided to create one.

Portada is Spanish for 'front cover', and this screensaver pulls album art from your Banshee cache and displays it as animated tiles - so you will need to use Banshee as your default music player (hey, it's the best one!).

A couple of gotchas:
[LIST]
[*]You will need a working graphics driver as it's built with Clutter.
[*]Does not run well on very old machines.
[*]Best suited to higher resolution,  16:9 displays. It should work on nearly any resolution and most normal aspect ratios - tested on 16:9, 16:10 and 4:3.
[*]Not actually set up as a screensaver yet - the program is available as a .py executable. Turning it into a proper screensaver is in progress.
[*]You will need python-clutter installed. Look in Synaptic.
[/LIST]

Please, all you lovely people, test this for me! 

[http://launchpad.net/portada]("http://launchpad.net/portada")

---

### Post by skajoeska on 2011-04-21
Wow what timing. I haven't looked for an album art screensaver for linux in about 3 years. I randomly check today and find your script the day you put it online. Made me very happy.

I have no problems with running it. I installed python-clutter and everything acted as expected. I haven't looked into it much, but do you know a way to make this a screensaver? Someway to tell ubuntu to run python porada.py after X minutes idle time?

Thanks again.

joe

Edit: Just saw on your launchpad page your plan to implement this as a screen saver.

---

### Post by Tahakki on 2011-04-21
I'm actually having trouble implementing this into Gnome-Screensaver - can't see a way to do it. I'll look into Xscreensaver, and if that doesn't work it'll just have to be a standalone.

---

### Post by skajoeska on 2011-04-21
Yeah I couldn't see anyway of using gnome-screensaver. In the man pages of xscreensaver there is a section that describes how to run an external script or command when the screensaver is activated after a certain idle time by using the "watch" argument. You can specify the idle time in the xscreensaver preferences. It seems like the best option, but I don't know much.

---

### Post by Tahakki on 2011-04-21
I think I'll just work externally for now - it gives me the option to continue working on a rather sexy settings menu. Attached is what I have so far.

---

### Post by ChipOManiac on 2011-04-21
It's Cool, I Like It :D Nice Work!

---

### Post by Tahakki on 2011-04-21
Could you guys post some screenshots of how it looks for you? Just wondering how it looks at different resolutions and things. :)

---

### Post by hypergeek14 on 2012-02-11
Hey looks pretty good on my netbook!  I'd like to see this in xscreensaver... stretching effects would be nice.    [IMG]http://i.imgur.com/D30UM.jpg[/IMG]

---

