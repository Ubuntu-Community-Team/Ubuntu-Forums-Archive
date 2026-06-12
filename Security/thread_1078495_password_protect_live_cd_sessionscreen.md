---
title: "password protect live cd session/screen?"
date: 2009-02-23
forum: Security
---

### Post by linuxexplorer on 2009-02-23
I've been using Ubuntu 8.04 installed but computer keeps crashing it (which I have other reasons to believe the issue is a hardware problem FWIW), but it seems stable running the live cd for now.  (How) can I password protect the live cd session, and closely related (how) can I get it to recognize the keyboard shortcut to lock the screen?  I hope someone has an answer, since it may be a while before I can afford to fix or replace my computer.  Thank you all in advance.  This is my first posting, if you couldn't tell.

---

### Post by komputes on 2009-02-25
> (How) can I password protect the live cd session

To add a password to the live session open a terminal and put in the following commands:

$ sudo -s
# passwd ubuntu

Then you enter the password and verify for the user ubuntu.


> keyboard shortcut to lock the screen?

Ctrl-Alt- L to lock the screen

---

### Post by Philo1 on 2009-02-25
To add a password to the live session open a terminal and put in the following commands:

$ sudo -s
# passwd ubuntu

Then you enter the password and verify for the user ubuntu.

------------------------------------------------------------

Neat, that is interesting...

---

### Post by linuxexplorer on 2009-02-27
Thank you very much.  I'm afaid I don't know my way around the terminal commands at this point, but I guess it's time to learn!  While I'm at it, I feel honored to actually "meet" someone who is using the version of Ubuntu that is not even publicly available!  I'm looking forward to switching over to 9.04 as soon as I can.  Also, kudos to someone else in TN using Ubuntu, as I'm here too.

---

### Post by komputes on 2009-03-02
> version of Ubuntu that is not even publicly available

linuxexplorer, Jaunty is publicly available, just not officially released, it's just at the alpha stage, which means don't go crying when your machine blows up*. If you have a computer you would like to see on Jaunty or blown to bits, go right ahead and try it.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

:P

*P.S. I am exaggerating of course, but some hardware may be damaged by software. If I recall correctly, this was the case for a few days with Intrepid and a specific Intel Ethernet Adapter.

---

### Post by RealG187 on 2009-09-16
I tried this on Ubuntu 9.04 in a Live CD session and when I lock the screen it goes back to the session without asking for a password...

---

### Post by ground21 on 2011-12-09
> **RealG187 said:**
> I tried this on Ubuntu 9.04 in a Live CD session and when I lock the screen it goes back to the session without asking for a password...

Same problem for me on Ubuntu 10.04 LiveCD :/

---

