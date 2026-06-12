---
title: "Ubuntu with PRI + Ras modem card"
date: 2009-02-25
forum: Server Platforms
---

### Post by drzolo on 2009-02-25
Hey guys,

I've got a dilemma.

Here is a bit of background:
We have a PRI line running to our server room. I believe it is 24 channel 64kb/s per channel. This is will be used for dialing in with 33.6kb/s modems to the server room. With maximum 23 (24?) lines up at the same time.

Now I've been searching on the internet for a RAS Card with 24 modems on it, and I only found 2-3 models. One does not support Ubuntu (the card is RH9 certified only), and the other one costs about $10k. I wonder if anybody has experience with this type of problem. We could consider stand alone solution.

I've had a crazy idea. Install regular PRI/T1 card into the server. If Ubuntu/Linux could identify each channel, and maybe create a entry in /dev/ directory for every channel.. like /dev/channelXX ... Then it might be possible to use some kind of modem emulator (Null modem??) and have it listen on the /dev/channelXX to communicate with each channel then the whole thing could be accomplished without expensive RAS card.
It is a crazy idea, but it might be possible?

If not, which RAS card do you use?

THANKS!
:guitar:

---

