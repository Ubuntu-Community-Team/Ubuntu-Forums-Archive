---
title: "Help with PSU connections?"
date: 2008-02-04
forum: The Cafe
---

### Post by igknighted on 2008-02-04
I am putting together a new server box, and my board is for a dual xeon setup.  I have an 8pin cpu power connector and a 4pin connector on the board, and only a single 4/8pin detachable coming out of the PSU.  I have plugged it into the 8pin, as from what I gather it should power both CPUs, but when I hit the power switch, it spins up and i get a series of 8 beeps that repeats, but no booting.

Do I need to use the other 4-pin CPU power input on the board?  Might I have another issue that is unrelated?  The only thing I could think of was it didn't like my raid card, but I pulled that out and nothing changed.  Any thoughts would be helpful.

PS... its for my office, we are migrating an old Netware 4 file server over to linux

---

### Post by Lostincyberspace on 2008-02-04
could you take a picture of the problems or put up a link to where we can see it. 

Also do you have a server psu if you don't then you might not have the right connector.

---

### Post by ~LoKe on 2008-02-04
Read the motherboard manual to find out what the beep codes mean in your case.  8 beeps is usually a video error (bad video card, improperly seated, etc).  Pull the card out and see if it boots.

---

### Post by igknighted on 2008-02-04
> **~LoKe said:**
> Read the motherboard manual to find out what the beep codes mean in your case.

It's an OEM board bought online, didn't come with a manual and since I don't know which OEM the board came from, I can't get a manual.  Google showed a lot of people asking and no one knowing.  It's a gigabyte, so I'm looking for a similar board and what the beep code might mean.

Here's a pic, all connections are along the top.  Main power (24pin) in upper right, 8pin in middle (both shown with connections) and in the upper right is the unconnected 4pin.

EDIT: Turns out I can't count, thats 7 beeps.  The only bios I can find to offer that many beeps is AMI, where 7 is a virtual mode exception error.  No idea what this means.

---

### Post by ~LoKe on 2008-02-04
So your PSU has 24pin/8pin/4pin connectors?  Why haven't you plugged the 4pin into the mobo next to the CPU?

---

### Post by igknighted on 2008-02-04
> **~LoKe said:**
> So your PSU has 24pin/8pin/4pin connectors?  Why haven't you plugged the 4pin into the mobo next to the CPU?

No, its one 8/4 adjustable connector (shown plugged in to the 8pin).  I tried it as a 4 pin connector in the 4pin one too.  No change.

---

