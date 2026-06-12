---
title: "How to make money out of free software and games  ?"
date: 2007-10-28
forum: The Cafe
---

### Post by MaximB on 2007-10-28
I know several ways of making money of free software but they doesn't apply to many other programs.
RedHatd and other Linux distro's make money by tech support which is reasonable.
If you make programs you can charge for commercial use  live VMware or Xen.
But what about games ?
In Second life you can buy game money from real money, but if it was covered by the GPLv3 (not 2) it would be harder to "call if free software" as if you would change part of the code it must work on the server thus making cheating very much possible.
**But what about stand alone games (not mmorpg) ? how can you make money from them ? under GPLv3 ?**

---

### Post by mridkash on 2007-10-28
What if it leads to "everybody cheating against everybody else" 
That would make a kind of "most secure code ever"

What do ya think? :guitar:

---

### Post by original_jamingrit on 2007-10-28
For online  MMO games, I guess it depends on how much is on the client side and how much is on the server side.  You could make the game's client and server both open source, but make sure that the game client can only change input.  This goes for closed source games, as well, since any code you distribute is liable to get hacked.

Client Side:
-Includes the interface.
-Does all the graphics stuff itself.
-Can transmit player's actions and commands in the game world. (Run, Jump, Cast Spell, Do a dance)
-Does not control the money, health, etc, but is updated on it at regular intervals and/or when the client program expects a change.

Server side:
-Accepts command transmissions and changes the player's state in the game worlds accordingly(Run forward, Make him jump, calculate Spell's chance of happening and effect, begin the "dance" animation)
-Controls secure and private variables for health and money, but never allows client direct access to these variables.  public get method, and a private set method used internally.

You can still be open source if you release the code for the client and server.  Allowing the client to be crossplatform and open source will allow people to make technical and aesthetic changes to their client interface.  But it won't give them the ability to cheat.

---

### Post by original_jamingrit on 2007-10-28
Sorry for the double post.

Also, you could charge money for a private server, (It will likely need to be powerful enough to accept connections and commands from many people at once), but also release code for the server, so people can start their own server, with whatever tweaks they like.

Do not charge money for updates and patches, but you could make money by charging for a private server-subscription and for in-game expenses (To use real world money for game money, for example).  Or go the route where you allow free-demo accounts and premium accounts.

Of course, releasing code for the server also generates competition for you, you can assume that some people will host their own servers for free.  So you can't charge too much for your subscription.  Or you may not release the server code.  The client side is still technically open source.

---

### Post by Steveway on 2007-10-28
> But what about stand alone games (not mmorpg) ? how can you make money from them ? under GPLv3 ?
Easy. Do it like ID-software. The engine is open-source but the media-content, like player-models music etc must be bought to play the original game.

---

### Post by ericartman on 2007-10-28
Sort of off topic but one thing in mmorpg's that was being talked about when I left WoW was the idea  of real world taxes on virtual (game) objects. After paying 180  dollars a year to play WoW the idea of paying taxes on my stuff seemed ludicrous to me, wonder how much traction that idea is getting?

Cart

---

