---
title: "emacs24 doesn't do anything in X"
date: 2013-03-18
forum: Ubuntu Development Version
---

### Post by gunksta on 2013-03-18
I upgraded from 12.10 to 13.04 this weekend. Over-all, everything works great. The only exception has been emacs, but I'm not sure what I can do to file a better error report. I have tried this using emacs32 and emacs24. I can start emacs if I use the -nw flags and run emacs in a terminal. But, if I run "emacs", "emacs24", or "emacs23" which should start emacs with a X window (frame in emacs speak), I get nothing. And I mean, literally, nothing. No error, nothing. I don't even get my cursor back and when I look in htop, emacs is using 0% CP and using just a shade over 0% RAM. 

I have run emacs with my current init.el. I moved my .emacs.d directory and tried it again, to make sure it wasn't because of a config error. I tried to run emacs as root and I tried to run it as my current user. Thus far, I haven't accomplished anything, other than waste some time.

Any thoughts? I don't understand how I can start emacs (emacs24) in a terminal but be completely unable to start it with a normal X GUI which is how I normally interact with emacs.

---

### Post by cariboo on 2013-03-18
Do you get any error messages, when starting emacs from a terminal?

---

### Post by gunksta on 2013-03-19
Nope. Nothing. If I drop to a terminal and just enter "emacs" or "emacs24", the hdd spins for a second and then . . . . nothing. No error, no emacs frame, no nothing. If I enter "emacs -nw" I get the non-X version of emacs and I don't have any errors in the *Messages* buffer. That's what has me stumped. I've borked more than one init.el, but I haven't tweaked anything in weeks (months?) and it starts up in text-mode like a champ.

Yes, I have the full emacs24 package installed.

I'm stumped.

---

### Post by gunksta on 2013-03-19
This morning I did some poking around in Launchpad and found a bug that sounds exactly like my problem.
[https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213) 

I just ran some updates. I'm going to reset and then try switching my theme to Raleigh to see if I can use the work around.

---

### Post by gunksta on 2013-03-19
This morning I did some poking around in Launchpad and found a bug that sounds exactly like my problem.
[https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213) 

I just ran the updates. I'm going to reset and then try switching my theme to Raleigh to see if I can use the work around.

Edit: After restarting my computer, I tried to start emacs with the same results. I looked at the packaging for emacs24 in 13.04 and saw it is compiled with gtk3, not gtk2. So, I opened up System Settings and went to the gtk settings and changed my gtk3 theme to "emacs". The bug report I saw recommended changing it to Raleigh, but I don't seem to have the gtk3 Raleigh theme installed. I didn't even know there was a gtk3 Emacs theme. I thought that was pretty funny. After applying this change I am able to start emacs, but it looks like an outcast from 1990. This Emacs theme is apparently the Raleigh theme with a new label or something because that is what it looks like. PLAIN and simple. But, it works which is super great.

I'm not going to mark this as Solved since there is clearly an outstanding bug. I'll follow the bug and when it gets straightened out, I'll make a note of it here and mark the thread as Solved.

---

### Post by PaulW2U on 2013-03-19
> **gunksta said:**
> This morning I did some poking around in Launchpad and found a bug that sounds exactly like my problem.
[https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213)

Hey, that's my bug report. :D

> **gunksta said:**
> 
I'll follow the bug and when it gets straightened out, I'll make a note of it here and mark the thread as Solved.


Please add something to it, even if it's just that it affects you too.

  I have a number of outstanding bug reports relating to Kubuntu 13.04 that I fear will never be fixed as no-one wants to provide any useful (additional) information. Bug reports need to be enhanced and improved not followed. :(

---

### Post by gunksta on 2013-03-21
Agreed. I commented that this bug affects me too and offered to test any updates or ideas.

---

