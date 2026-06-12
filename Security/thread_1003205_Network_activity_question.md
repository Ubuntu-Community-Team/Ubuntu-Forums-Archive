---
title: "Network activity question"
date: 2008-12-05
forum: Security
---

### Post by sheridon on 2008-12-05
I have the network monitor graph on my taskbar and sometimes watch what activity is going on.  

I sometimes see the network activity show a blip about every 5 seconds even when I'm not doing anything on the computer.  Does anyone have a clue as to what that could be?  Or how I can find out what program is accessing the internet?

Also other times I see the network activity bar accessing the net alot more than every 5 seconds, and when I notice this i disable my network connections and ofcourse it goes away, when I re-enable the connection the activity doesn't start again.

Guess I'm really looking for a way to find out what exactly is using the network.  Is there a program that will tell me what is using it? 


Thanks

---

### Post by lovinglinux on 2008-12-06
The 5 seconds network activity usually occurs here when the DSL modem connection is down and the machine is probing the router to reconnect. Other activity are related to e-mail checkers, the clock trying to sync with a server or simply the package manager doing it's update check.

I use iptstate for monitoring connections. It is really nice and you can also delete a connection state.

---

### Post by t.h.w. on 2010-11-22
Hi!
I had the same question, thanks for answering. I've found a suggestion of another user to give Wireshark (is in repositories) a try, to see what it is exactly. 
Greetz!

---

