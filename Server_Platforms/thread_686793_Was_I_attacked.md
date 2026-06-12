---
title: "Was I attacked"
date: 2008-02-03
forum: Server Platforms
---

### Post by rockrocket on 2008-02-03
I think i just got attacked, my ubuntu desktop icons changed. I was configuring port 80 for outbound and inbound connections. 

Was this a attack, but then I locked the firewall and restarted ubuntu and everything returned to normal.
I also noticed alot of events happening in firestarter. 

What should i do now?

---

### Post by FaBi3ttO on 2008-02-03
Well, first try to understand which events firestarter has logged.
Maybe post it here if you need help.
But it seems strange to me an attack on port 80 changing desktop icons.
Bye

---

### Post by rockrocket on 2008-02-03
-Well, first try to understand which events firestarter has logged.
Maybe post it here if you need help.

Sorry I'm new to firestarter where would i see this? 

Thanks

---

### Post by lespaul_rentals on 2008-02-03
I would not worry about it.  The fact that a simple restart changed everything back to normal is huge evidence that it was not a "hack attack" of some sort.  Also, if someone were to find an Apache exploit (only service I could think would be running on port 80, as you said) and use it against you, I seriously doubt they would change your desktop icons.  Think about it...how does that benefit the hacker?  It doesn't log your keystrokes.  It doesn't hijack your connection.  If a hacker were to attack your computer he would try to be secretive about it, and changing the most obvious thing -- your desktop icons -- would be suicide.

---

### Post by tad1073 on 2008-02-03
The same thing happened to me earlier today. i was surfing around when all of a sudden my browser goes into full screen mode then minimizes to a small square in the upper left corner. When I shut down and restarted my window borders had been changed. i think my connection has been compromised also. for some time now there have been about four or five AP's showing full strength but no one or no router is that close to me. the ones I am reffering to are 4eveler, bowling, kirknet, MITTEN, ThompsonNet, WEST7221 and WORKGROUP.

---

### Post by tad1073 on 2008-02-03
bump

---

### Post by rockrocket on 2008-02-03
-I would not worry about it. The fact that a simple restart changed everything back to normal is huge evidence that it was not a "hack attack" of some sort. Also, if someone were to find an Apache exploit (only service I could think would be running on port 80, as you said) and use it against you, I seriously doubt they would change your desktop icons. Think about it...how does that benefit the hacker? It doesn't log your keystrokes. It doesn't hijack your connection. If a hacker were to attack your computer he would try to be secretive about it, and changing the most obvious thing -- your desktop icons -- would be suicide.


**I found it weird to, why would they change my icons, firestarter also gave me a weird error and i saw a bunch of computers connecting to me in the events page also ports like 1027 were connecting and a bunch of others, it was just weird i have never seen something like that, i ran chkrootkit and found nothing also checked the firewall afterwards and i see no events happening anymore. **

---

### Post by rockrocket on 2008-02-03
-The same thing happened to me earlier today. i was surfing around when all of a sudden my browser goes into full screen mode then minimizes to a small square in the upper left corner. When I shut down and restarted my window borders had been changed. i think my connection has been compromised also. for some time now there have been about four or five AP's showing full strength but no one or no router is that close to me. the ones I am reffering to are 4eveler, bowling, kirknet, MITTEN, ThompsonNet, WEST7221 and WORKGROUP.

** my broswer did'nt do that, i just got alot errors with firestarter, i hope my iptables weren't changed the only server i'm running is lamp, which includes apache and all the other things**

**Another thing that i noticed before this happened was firestarter when it was on wouldn't allow me to have any internet access through my mozilla broswer and when i did sudo apt-get update in the terminal it would read but it didn't download so i had to turn off firestarter to get internet access to my broswer and terminal. **

---

### Post by rockrocket on 2008-02-03
I think i found my problem in the firestarter in the run wizard the enable internet connection sharing was checked and was set to my ethernet. Now I understand why a bunch of computers and ports were connected to me and why got those errors, but it still doesn't explain the desktop icons changing unless they were set back to probably a older version of ubuntu desktop due to fact that there wasn't much ram because all the computers and ports were sucking it dry.

---

