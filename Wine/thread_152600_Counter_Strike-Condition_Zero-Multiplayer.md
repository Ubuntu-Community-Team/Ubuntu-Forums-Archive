---
title: "Counter Strike-Condition Zero:-Multiplayer"
date: 2006-03-30
forum: Wine
---

### Post by RajivNair on 2006-03-30
I am a part of a local lan in our housing complex.We play CS-CZ all da time.Everyone here uses Windows except me.Someone everyday hosts an server on which they play.I installed CS-CZ using wine(installing tahoma fonts n mozilla activex n all).The game runs perfectly but only for single player.Im neither able to find any servers nor able to host one.CAn someone guide me solve this problem.

---

### Post by Mikecore on 2006-03-31
I had the same problem with CS 1.5 and wine. 

How are you starting CS?

I had to change dirtectory into my CS folder and start the game from that folder.
once I did that I was able to host and play on LAN servers.

Try that.

---

### Post by shinygerbil on 2006-03-31
My Steam doesn't even work unless I change directory first :/

---

### Post by samad909 on 2008-01-21
I know that this thread is really old, but guess it might help the people who search google in the future,

To play CS-CZ or any other version in a LAN just rename the motd.txt files in the cstrike/czero directories to oldmotd.txt and start the game with wine and wola everything works perfectly ;)

Hope it helps ;)

---

### Post by vinayihegde on 2008-06-12
Thanks a lot... Renaming the motd.txt files to oldmotd.txt helps! I know this thread is really old, but can you explain why this works and how this works?

---

### Post by samad909 on 2008-10-28
This work as wine was not able to render the motd.txt file properly. I was using ubuntu a few months back. Need to move back to it soon.

---

### Post by TheShader on 2008-10-28
Hey this is my first message, I've been reading and observing this forum for a long time. So hello to everyone.

The MOTD issue happens because WINE can't render the html with Half-Life 1 engine. If you are trying to join another server, you can prevent your client from rendering the server's WINE-crashing motd.txt.

Create a file called motd_temp.html in cstrike or czero directory and make it read only. If that file already exists, just erase everything in it and make it read only... When you join a server, your client will not be able to download and replace, then show the motd.txt which crashes your WINE and show you an empty window ^^ You can play happily in other players servers now ;)

---

