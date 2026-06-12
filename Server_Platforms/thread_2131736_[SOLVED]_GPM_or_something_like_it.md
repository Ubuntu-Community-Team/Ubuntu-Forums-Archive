---
title: "[SOLVED] GPM or something like it"
date: 2013-04-02
forum: Server Platforms
---

### Post by conradin on 2013-04-02
Hi all,  
I am running an Ubuntu 10.04 server, and I am looking for a mouse / cursor for when i interact with the server directly. 
I tried gpm, but when I tried to start the service it just failed. I am not certian the gpm (general purpose mouse) is even the correct thing.
Does anyone know a program that will give me cursor and mouse functionality on a shell server?

---

### Post by spynappels on 2013-04-03
I'm not exactly sure what you are asking for. There is no point to using a mouse on Ubuntu Server Edition, as it is CLI only, there is no Desktop or Window manager to interpret the mouse movements. Perhaps you might be better off with a lightweight Desktop Environment like XFCE or LXDE?

---

### Post by conradin on 2013-04-03
There is a point: it makes things easier. 
Further more, this is something that exists, I just don't know what its called.

---

### Post by spynappels on 2013-04-04
I'm sorry, maybe I'm thick or something, but how does it make things easier? Are we talking about a normal console on a CLI only server?

I don't doubt it could be made to work, I just don't see why....

---

### Post by conradin on 2013-04-04
Upgraded my kernel to get support for liquidsoap, and retried installing gpm. Now it works!
This is a CLI only box. No xinit, X, gui or what ever. 
The premise of recommending a GUI is implication for understanding that functionality, and simplicity exist from using them. 
mods trollin my thread? no idea, but gpm works now.

---

### Post by spynappels on 2013-04-04
Ok, so I Googled it, and I can see that it works. 

I wasn't trolling, I genuinely cannot see why it would make life easier if you don't have a GUI, hence my suggestion of a light weight DM. I know you can use a mouse in Midnight Commander but never saw the point. But hey, if you got it working, great.

Thanks for coming back with the solution so if anyone else wants to do the same they might find your solution useful.

---

