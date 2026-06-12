---
title: "warcraft 3 LAN game connections"
date: 2009-06-06
forum: Wine
---

### Post by racerraul on 2009-06-06
Gang... I have Warcraft 3 working on 3 machines at home. But to my surprise when we tried to join in a game together, we can see the game hosted but get a connection error.

I had this same problem in XP, and creating new rules in the firewall to open up UDP\TCP 6112 on each system fixed the connection problem.

I tried to open up the ports via UFW command, but while the rules updated It didn't make a difference... Do you think the problem is WINE?

I found some instructions that required I install PvPGN, is that necessary in Ubuntu to get Warcraft 3 to work in a LAN environment?

I did search the forums, but I've come up empty, with the exception of using PvPGN.

---

### Post by racerraul on 2009-06-09
Is there no solution to this?

Is everyone playing Warcraft 3 able to play LAN games?

At least if this is working for anyone post your wine and W3 versions, so I can give that a try.
Connecting to Battle.net is not a problem, just want to be able to host and play LAN games.

---

### Post by BeniF on 2009-07-14
Hello Buddy,

I've been searching for a solution to this problem all day, but I didnt find anything. Me and my brother are both using ubuntu and Wine version ```
wine-1.1.23
``` from their official APT repository.

After these error messages appeared the first time, we upgraded our WC 3 to 1.23.0.6352 but it didn't work aswell.. :-(

I'll be on journey for a week now, so my next reply could take a bit longer. Of course I'll notify you when we solve this problem :-)

-beni

---

### Post by BeniF on 2009-07-14
I just had a look on the winhq page for Warcraft 3 at

[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

and there was this little sentence:

> 
**What works**
Campaign, Single player, Saving game, Lan game, Videos 

**What does not**
[COLOR=Red]Creating lan server. Lan game works only if server is started on OS Windows(wine is returning some ioctl error). Joining into game is OK. [/COLOR]


:-(

---

### Post by skidriprekah on 2009-08-12
Bump.

I have been searching for a resolution to this issue to no avail. This is a shared favorite by all my friends and coworkers, and not being able to host games is a major pain.

---

