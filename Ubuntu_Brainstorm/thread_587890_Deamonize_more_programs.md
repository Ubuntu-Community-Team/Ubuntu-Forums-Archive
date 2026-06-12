---
title: "Deamonize more programs"
date: 2007-10-23
forum: Ubuntu Brainstorm
---

### Post by Xbehave on 2007-10-23
i suppose this is more a long term goal but generally moving backends away from X (even desktop programs) would increase stability less information would be lost during an X crash allowing you to get back to work faster.
some programs that could have a separate back end include
torrent programs 
IM programs (even if a frontend is needed to chat, the network connections could be preserved and then when x restarts then the GUI would reconnect to the daemon)
Email
music players (in fact this would be a useful option for fast switching as if i don't switch off my media player, whoever logs in has no control over whats playing, as then root could lock down the music on a systems)
session managers (not sure if this affects GNOME but in kde if i crash x then the session goes back to the one i logged in to, it would make sense to have a Firefox style restore prompt on a crash, tho) * i dont think this would even need a daemon maybe just a cleaver way of running the session manager, FF manages it?


sorry if this is not possible, im no expert on linux i just find that the ability to restart X is getting pointless as everything else depends on it. If this edge could be brought back then ubuntu would be much more stable than windows as even if you crash it you don't really crash it

---

### Post by booljayj on 2007-10-31
This is an interesting idea, and I think it deserves serious consideration. However, be aware that too many programs spawning too many daemons wouldn't exactly be a good thing.

This could also go much further into integrating the GNOME desktop into itself. further separation of the frontends and backends would allow programs more ways to interface with each other, ie nautilus using the torrent daemon to keep track of file progress and increase the stability of dynamic space allocation. I agree that e-mail would also be something that might benefit from this setup.

---

