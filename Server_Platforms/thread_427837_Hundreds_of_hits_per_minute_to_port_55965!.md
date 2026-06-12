---
title: "Hundreds of hits per minute to port 55965!"
date: 2007-04-29
forum: Server Platforms
---

### Post by stealth17 on 2007-04-29
[LEFT]I recently installed firestarter and the log is going nuts with hits to port 55965. The weird thing is they are almost all unique WAN IP addresses.

I am also behind a router which the only ports being forwarded are 3389, 6464, and 22.

This is on an Ubuntu 7.04 AMD64 computer, which I am sharing internet to one other (windows) computer located at 192.168.0.2

Thanks.
[/LEFT]

---

### Post by earobinson on 2007-04-29
bit torrent trafic?

---

### Post by stealth17 on 2007-04-29
> **earobinson said:**
> bit torrent trafic?

hmmm you may be onto something. I don't have any torrent clients running, but I did earlier today. When I closed azureus I don't think it closed completely. If you look closely at the screenshot, there is a empty space between the firestarter icon and the NIC icon. Perhaps it is still running then? I will have a look at ps aux and see what I can come up with.

Thanks.

---

### Post by earobinson on 2007-04-29
no prob, UDP and the high port numbers is what made me guess. Let us know how it goes

---

### Post by stealth17 on 2007-04-29
> **earobinson said:**
> no prob, UDP and the high port numbers is what made me guess. Let us know how it goes

hmmm I killed what looked to be something with azureus and that empty icon space is now, but the log is still showing tons of hits to that same port.

Here is an output of my processes, maybe I am missing something :confused:

[http://pb.theoverclocked.com/42](http://pb.theoverclocked.com/42)

---

### Post by Chancellor on 2007-04-29
I am not positive, but I think sometimes remote bittorrent clients still try your IP, even after close your bt client... in case all you did was reboot or something.

---

### Post by earobinson on 2007-04-29
hum, can you cut and paste the output of a netstat?

---

### Post by stealth17 on 2007-04-29
> **Chancellor said:**
> I am not positive, but I think sometimes remote bittorrent clients still try your IP, even after close your bt client... in case all you did was reboot or something.

That would make sense.. I was kinda wondering that myself...

> **earobinson said:**
> hum, can you cut and paste the output of a netstat?

sure: [http://pb.theoverclocked.com/43](http://pb.theoverclocked.com/43)

---

### Post by seshomaru samma on 2007-04-29
I think it's Azureus.
I have 2 machines behind a router, one is Dapper one is Etch
Dapper has Azureus and Etch doesn't. On Dapper I get hundreds of hits at that port and on Etch I get none. Even when Azureus is off.
You can see it visually with 'etherape' - it can look quite scary...

---

### Post by stealth17 on 2007-04-29
> **seshomaru samma said:**
> I think it's Azureus.
I have 2 machines behind a router, one is Dapper one is Etch
Dapper has Azureus and Etch doesn't. On Dapper I get hundreds of hits at that port and on Etch I get none. Even when Azureus is off.
You can see it visually with 'etherape' - it can look quite scary...

Wow you guys really nailed it. That etherape view is pretty scary [attach]31267[/attach]

I was confused as to why I was getting so many hits on that port when my router did not have it setup as a port forward. I started poking around the config and look at what I found: [attach]31268[/attach]

:lolflag:

So after I turned UPnP off, the hits went down to about 5/min all UDP. Much better. Although I still don't like how azureus causes that. Shouldn't I not be getting any though if the router is supposed to be blocking the port now?

Thanks :popcorn:

---

### Post by earobinson on 2007-04-29
glad to know it works now!

---

