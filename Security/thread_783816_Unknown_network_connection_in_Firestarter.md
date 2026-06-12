---
title: "Unknown network connection in Firestarter"
date: 2008-05-06
forum: Security
---

### Post by barboachtraner on 2008-05-06
I happened to notice that Firestarter currently shows an active connection on port 40890 to 78.140.145.71. When I enter that address in Firefox, it resolves to [http://letitbit.net/](http://letitbit.net/), apparently a Russian file uploading site I've never seen or visited before. I never saw this connection before, so I'd really like to know what this is... Someone in #ubuntu told me it could be a leftover connection from torrent seeding, and I was running torrents earlier in the day, but not at the moment I checked Firestarter.

---

### Post by Koori23 on 2008-05-06
are you using Transmission as your torrent client? The reason I ask is Transmission (when you exit the program) doesn't exit, you have to kill it by using *sudo killall transmission-gtk*

I had the same problem.

---

### Post by barboachtraner on 2008-05-06
> **Koori23 said:**
> are you using Transmission as your torrent client? The reason I ask is Transmission (when you exit the program) doesn't exit, you have to kill it by using *sudo killall transmission-gtk*

I had the same problem.

I use Deluge, although often times it won't respond when I try to close it and I have to press Force Quit in the dialog box that comes up, which I assume kills the process.

---

### Post by patsymcox on 2008-09-19
The same happens to me, You got any cure?

---

### Post by lovinglinux on 2008-09-19
When you close or kill Deluge, the connections will be closed too. If you watch the network monitor in the gnome panel you will see that the network activity stops immediately. 

I read somewhere that Firestarter can show you connections as active, even if they are already closed, specially after running a torrent client like Deluge.

I have observed this myself. One or two connections remain listed as active, even if I turn of my modem. These connections are also listed as active using iptstate to monitor connections, but not using iptraf.

If you are really concerned about them you can stop your modem and reboot. Once you are logged in again the connection will be gone, then you can connect to ISP again to retrieve a new IP if you have a dynamic one (most likely). With this new IP there is no way to the persistent connection to get to you again, unless is your machine that is originating it.

---

### Post by chongzivalve0809 on 2008-09-22
a professional [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) China manufactuer and supplier,established in 1983The main product is:cast steel [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm),forged steel gate valve ,pressure seal gate valve,plate [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm).  BFV Valve also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT .[gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) manufacturer website:[www.valvesupplier.net/forged-steel-gate-valves.htm](http://www.valvesupplier.net/forged-steel-gate-valves.htm)

---

