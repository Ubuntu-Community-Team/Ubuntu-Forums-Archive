---
title: "Proxy Server?"
date: 2009-05-14
forum: Server Platforms
---

### Post by Ghoztrider on 2009-05-14
I'm looking to log the traffic or Websites visited or web usage that come from my home network, I believe that is a proxy server? Can anyone recommend anything. I have limited experience with Wingate but am looking for a linux solution to logging traffic and stuff. Thanks for any help you can provide me.

---

### Post by a9k3d on 2009-05-14
If you have an old 800mHz box and a couple of ethernet cards to put in it, you could try IPCop. It is a router/firewall. It graphs traffic and has squid (caching proxy) which can give reports. You may have to SSH into the box to get the complete data on web accesses. squid can be made to use common log format which means you could use aswtat to analyze your family's browsing habits. IPCop also shows current connections - very handy when your internet seems slow and you find your brother has 30 connections - all bittorrents.

If you're checking on your kids, web port access is not the only thing you have to worry about. Anything with a chat channel can be trouble. There's IRC for romantic chats. There are MUD and MOO clients for more chatting hidden from Dad. And there are all those MMO games with chat rooms. I speak from experience - both mine and my brother's with raising gamer girls.

IPCop is a pretty simple install and has web interface (inside your LAN, not on internet). I replaced my burned out router with an old 800mHz Celeron (P3) 256Meg box. I used an old 10BaseT ethernet car for the DSL/WAN side interface.

My only warning is that the IPCop install disk erases everything on the machine - it will warns you too.

---

