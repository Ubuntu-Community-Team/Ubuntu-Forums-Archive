---
title: "Is my RCA broadband modem compromised?"
date: 2012-05-07
forum: Security
---

### Post by johnnydoe on 2012-05-07
When observing requests via wireshark:
Tested in 3 different live cd's, just after it boots up and there should be no processes taking place.

When my wired connection is connected from my laptop directly to the modem, I observe all kinds of traffic from foreign ip addresses...lots of them are on blacklists.

When I connect from my computer to my Netgear router, to my modem I do not see any packets and requests occurring.

Is my modem compromised or does my service provider have bad filtering?  Is my Netgear router really stopping all these requests or can I just not see them anymore?

My modem is being rented as part of my cable plan.  What should I do about this?

---

### Post by OpSecShellshock on 2012-05-07
I don't think it's an indication that the modem is compromised. Everything that is connected to/accessible from the web directly is being scanned and probed constantly. Your router is likely just not allowing the requests through, which is to be expected since you haven't allowed them.

I am assuming here that the traffic is being initiated from the other IP addresses rather than yours. Are connections successfully being established?

---

### Post by CharlesA on 2012-05-07
Just keep using the router. It's likely you have a ton of connections hitting your modem, but that's probably because there are bots on the internet that do port scans and trying to break into services.

EDIT: Ninja'd. ;)

---

### Post by johnnydoe on 2012-05-07
Thanks for the assurances!  I'm new to really analyzing the packets that wireshark shows me.  I just noticed all the random ip addresses that are initiating from the other ip addresses.  

I'm not sure how to tell if they have been successfully established.  I can run wireshark again while connected directly to modem and paste the results (I don't know what information is safe and needed to post).   :-s

---

### Post by OpSecShellshock on 2012-05-07
Basically it should tell you whether the requests are going out or coming in, so your IP address will either be the source or the destination. If you are only seeing your IP as the destination, and never the source, you're probably fine. If something comes in, and the next line down is you connecting back to them, you may want to take a closer look. Even then you might just be sending a response that says "nothing there!"

---

