---
title: "Lyricue"
date: 2009-08-26
forum: Ubuntu Christian Edition
---

### Post by 480silverton on 2009-08-26
Has anyone tried using the other similar program to OpenSong called Lyricue?

If so could anyone help? I've tried using Lyricue but I cannot get the second monitor working.

---

### Post by debenham on 2009-08-26
What problem are you having?
Is it a problem getting two screens working in ubuntu - or is it a problem with loading the lyricue interface and server on seperate screens?

---

### Post by 480silverton on 2009-08-26
It seems to be Lyricue
I already have two monitors hooked up working in Twinview move (nvidia)

Lyricue loads but the presenters view does not.

---

### Post by debenham on 2009-08-27
What happens when you try to load the server?
Can you run it manually (ie from the gnome menu rather than from within lyricue)
Also, have you tried toggling the 'xinerama' option in the lyricue preferences dialog?

---

### Post by 480silverton on 2009-08-31
Well when I load it, it starts then everything loads. The control panel completely comes up and everything seems to work but the second monitor. The second monitor isn't even hidden behind the control panel or anything.
I tried toggling the 'x' on and off but no change what so ever.

---

### Post by debenham on 2009-09-01
What do you mean 'everything loads'?
Does the lyricue interface run?
Does the lyricue_server run?
Which is displayed on screen?
If both run, can you run lyricue_server on the second screen manually?

---

### Post by 480silverton on 2009-09-03
Well Everything but the display screen comes up.
And when i try messing with the settings. Its the same thing. Everything but the display screen.

---

### Post by mikehenson on 2009-09-11
did you try...
[http://www.lyricue.org/node/60](http://www.lyricue.org/node/60)

Starting the server manually

By default there is a menu item under Applications labeled Lyric Server
Click this to load the server.
If such a menu item is not available open a terminal, drag it to your second monitor and type lyricue_server. Keep the mouse on that monitor until the server is up and running so that the window manager will place the lyricue server window on the screen where your mouse pointer is. A more long-term solution is creating a shortcut to lyricue server on your second monitor, pointing to /usr/bin/lyricue_server

MSH

---

### Post by 480silverton on 2009-10-15
I have been slightly busy in recent days
but i have been using an older version
of lyricue.

I shall try the newer 2.0 version to see
if I can get it working. And hopefully
move away from the nasty high paying
windows and song show plus.

---

### Post by longtom on 2009-11-04
> **480silverton said:**
> I have been slightly busy in recent days
but i have been using an older version
of lyricue.

I shall try the newer 2.0 version to see
if I can get it working. And hopefully
move away from the nasty high paying
windows and song show plus.

You mentioned OpenSong in your first post.  Why don't you use that in Windows.

I use OpenSong in Ubuntu (where it can't print) and in Windows and have it access the same database from both OS'.  Works like a charm.

I surely hope the devs of OpenSong get that print issue in Linux sorted out.

---

