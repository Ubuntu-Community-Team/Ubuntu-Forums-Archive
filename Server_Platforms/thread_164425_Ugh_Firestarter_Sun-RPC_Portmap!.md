---
title: "Ugh Firestarter Sun-RPC Portmap!"
date: 2006-04-22
forum: Server Platforms
---

### Post by 1derphull on 2006-04-22
OK, set up Firestarter, it is in my startup programs list. Followed the instructions I read in this [HOWTO ]("http://ubuntuforums.org/showthread.php?t=129798&highlight=firestarter+startup").

Now I'm looking at my "Active Connections", I see something a little unsettling:

Source 127.0.0.1  Destination 127.0.0.1 Port 32770 Sun-RPC Portmap

Wtf is the deal? 




I also have a service "lpp" (linux progress patch?) running on 127.0.0.1 for both source/destination. I'm assuming this is OK.

I'm also running gaim and firefox, no worries there.

---

### Post by RavenOfOdin on 2006-04-22
32769 and 32770 are in my Netstat list all the time, as are ports 631 and 68. I don't figure them to be anything really bad.

Just as long as you don't enable connections to them from any outside address I'd say you're all right.

---

### Post by 1derphull on 2006-04-22
Thanks! :D

---

