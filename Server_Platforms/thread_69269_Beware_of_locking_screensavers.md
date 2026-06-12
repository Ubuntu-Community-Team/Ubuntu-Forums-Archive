---
title: "Beware of locking screensavers"
date: 2005-09-26
forum: Server Platforms
---

### Post by Fyrzen on 2005-09-26
Here's something that just happened to me, it appears to be a gnome problem.

Short version: I was prompted for my password after the screensaver had kicked in during a game(nexuiz), after typing it and pressing enter **once** i soon found out a friend had opened a gaim window in the background to talk and i saw i had typed him my password...

Full version:
I was playing nexuiz, gaim was running in the background but no im windows were open. I changed nexuiz effects settings during gameplay, nexuiz appeared to have shut itself down, then began reloading itself, only slowly, i just went to another rooma nd watched tv for a few minutes. I had the following screensaver settings: 
Blank screen only
Blank after 12 minutes
Cycle after 12 minutes
Lock screen after 0 minutes

And all power management settings set to 5 minutes. I came back from watching tv and saw the screensaver had kicked in, monitor was off, moved my mouse and got a blank screen with the username/password prompt, i entered my user password and found myself in soem other nexuiz map, must have been because of the map cycle time. I noticed it was a bit laggy so i exited, the menus were displaying oddly, but i managed to find my way out, when i got back to the gnome desktop i saw an im window. A friend had asked me if i was there then closed the window, after which **i had typed my password and entered it for him to see**. And after which he asked me about a game.  

I seriously didn't expect this kind of low-security cr*p to be present in gnome.

---

### Post by Mustard on 2005-10-04
I read the post a week ago and thought ..naaah...I'm not wading into this one.  Reading it a week later I think it's amusing.  My first thought concerning the low security cr*p was that users are present on most every ubuntu system, its the one security risk that is pretty hard to get rid of. :)

Can you reproduce it?

Sounds like a bug fix if you can.

---

### Post by nocturn on 2005-10-04
[QUOTE=Fyrzen]  
I seriously didn't expect this kind of low-security cr*p to be present in gnome.[/QUOTE]

If this is reproducable, it is a security bug with a high severity.  Have you filed it in Bugzilla?

---

### Post by Fyrzen on 2005-10-12
It's already on the bugzilla list. [https://bugzilla.ubuntu.com/show_bug.cgi?id=10865](https://bugzilla.ubuntu.com/show_bug.cgi?id=10865).

I admit that last sentence was a bit... un-tactful, it was my way of putting it mildly that this bug is somewhat simple, too simple to actualy exist, but it does. You have to understand it's not a very good feeling when you realise you've just typed your 3rd most important password to someone.

---

