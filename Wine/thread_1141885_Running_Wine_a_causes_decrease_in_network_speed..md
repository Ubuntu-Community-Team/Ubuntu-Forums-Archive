---
title: "Running Wine a causes decrease in network speed."
date: 2009-04-28
forum: Wine
---

### Post by Mmmbopdowedop on 2009-04-28
Wasn't quite sure what to name this thread or whether to post it here or not, but this is what i've got;

When i'm running World of Warcraft via Wine, both my processors idle at around 60% or so, this is fine for as I can still have my computer function at what appears normal speed, but when sending a file, well, downloading a file from another computer on the network via Apache (Which is running on the computer running WoW), I have a huge drop in speeds.

When WoW is minamized and not focused, I get a network speed of 1mb/s+, but when it's focused, the network speed drops and the file downloading on the other computer drops to a speed of around 60kb/s.

I've tried changing the Priority on Apache, Wineserver & WoW itself, but by doing this I only managed to gain around 200kb/s speed whilst it's active, hoping someone could throw me something that could help my problem, thanks. :)

--------------------------------------

Whilst proof-reading this, I decided to try a speedtest.net test, here's what I got;

**Whilst WoW is active;**
[IMG]http://www.speedtest.net/result/462290241.png[/IMG]

**Whilst WoW is minamized **
[IMG]http://www.speedtest.net/result/462289310.png[/IMG]

So it appears it's causing a huge loss in network connection, this is going over wireless, but as i'm not that tech savvy(?) i've no idea how I could sort this.

---

### Post by Mmmbopdowedop on 2009-04-29
Would this be better suited posted in a different forum?

Like Networking or something? /shrug

---

### Post by asdfoo on 2009-04-29
if your drivers aren't very good and they use a lot of cpu maybe that is why?

---

### Post by Mmmbopdowedop on 2009-04-29
Well I got my Wireless drivers from compiling Madwifi and my graphics are the proper nVidia drivers. Maybe it is them that suck, I just find it odd, that while both my processors are at ~60% my system is incapable of sending an upstream of more than 200kbps over the network, yet, I can run everything else I can think of perfectly fine. I can even have multiple WoW clients open without a problem with system speed.

I use the network for streaming videos over so it's kind of a nuisance really to have to close WoW for a while, guess i'll just have to let this problem stay. ;/

Hay well. :(

---

### Post by asdfoo on 2009-04-29
> **Pey Tudor said:**
> Well I got my Wireless drivers from compiling Madwifi and my graphics are the proper nVidia drivers. Maybe it is them that suck, I just find it odd, that while both my processors are at ~60% my system is incapable of sending an upstream of more than 200kbps over the network, yet, I can run everything else I can think of perfectly fine. I can even have multiple WoW clients open without a problem with system speed.

I use the network for streaming videos over so it's kind of a nuisance really to have to close WoW for a while, guess i'll just have to let this problem stay. ;/

Hay well. :(

oprofile (system wide profiler) might give you more information

---

