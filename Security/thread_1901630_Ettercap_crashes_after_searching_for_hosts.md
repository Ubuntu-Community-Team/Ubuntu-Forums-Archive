---
title: "Ettercap crashes after searching for hosts"
date: 2011-12-29
forum: Security
---

### Post by Triblaze on 2011-12-29
I figure the security section will have the best opinion on this matter. Ettercap (gui) crashes after I scan the netmask for hosts. I've done some searches on it and it seems that there are others with this problem, but I haven't found a solution. On Ubuntu, at first it did this all the time, but eventually it started working more, to the point where it now only crashes 20% of the time. However, on Backtrack, I have the same problem, and there it never works, it always crashes. I figured I might have set it up wrong on Ubuntu, but for it to not work out of the box on a BackTrack install is very odd. Is it something wrong with my computer, or am I doing it wrong?

It gives this error when it happens, which doesn't really tell me much:

Ooops ! This shouldn't happen...
Segmentation Fault...

Sometimes it crashes out completely, with the window disappearing and the process terminating, while other times (mainly on BackTrack), the program just halts and becomes unresponsive. All other functionality in Ettercap seems to be working.

Oh, and in addition, this is a separate topic but it ties in just a little bit, on Backtrack nmap (and zenmap) says it can't find the interface wlan0. What causes this? Sorry to diverge off Ubuntu territory.

---

### Post by Triblaze on 2011-12-30
Bump to save this from going second page.

And I solved the part at the end, I believe the problem was that I had left monitor mode on by accident.

---

