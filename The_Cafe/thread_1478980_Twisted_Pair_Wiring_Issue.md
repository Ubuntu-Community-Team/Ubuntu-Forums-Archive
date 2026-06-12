---
title: "Twisted Pair Wiring Issue"
date: 2010-05-10
forum: The Cafe
---

### Post by SeanTater on 2010-05-10
I'm not thinking this directly relates to Ubuntu so I posted this in the Café..
It's a question about wiring cat5e/twisted pair and setting up a network in an extremely
confined space.

My house was wired with cat5e network cable, but the blue/blue-white wire pair was used for telephone and the rest were bundled in the junction box outside. Since I recently got my networking certification and I had to read on the wiring and connections, etc. I realized that only two pairs out of the four were necessary for 10/100 Ethernet. This means that I could connect 10/100 Ethernet and leave the telephone untouched. So I connected two wire pairs from two cables to make a crossover cable: green to orange and green-white to orange-white. I don't think it matters whether I used crossover or straight-through though, from what I've heard most NICs and switches will detect it and resolve the issue. Anyway - it works, and it's very speedy. (I went from 30-50KB/s using 802.11g, which is very congested here, to ~11 MB/s using 100mbps Ethernet.)

So - that's the summary.. But here's the question:
What if I wanted to connect more than two computers via that cable box? There isn't room for a hub or switch, (there's barely room for the wires). Is it possible I could create a half-duplex network of three or more switches/computers by some connection arrangement (maybe all similar colors, like all green-stripes together, same for green, orange, and orange-stripe) or is it a lost cause?

Thanks in advance for the help! (Even if it's just to tell me I'm nuts!)

---

### Post by Phrea on 2010-05-10
Sir, you're nuts !

---

### Post by 98cwitr on 2010-05-10
what do you mean there's no room for a switch? Just put one in the attic or basement, run some more cabling and new wall blocks and you're set...stop being cheap :)

Btw you're nuts for thinking of running multiple lan connections off the same wire...talk about crosstalk (pun intended) ad hoc though at best...but you're missing a fundamental flaw in your logic: tell me...how're two IP addresses going to get assigned to two machines from a single cable modem?

Now if you had a box with a few dual port NICs in it you could turn that into a router of sorts...but still, a single wire from the modem to the router is required.

---

### Post by CharlesA on 2010-05-10
That's not the way to be doing it.

A better way would to be just run the cable from the computers to a central spot, put a router there an hook up a cable/dsl modem and connect that to the junction from there.

If you are pulling your own cable, there should be plenty of room in a wall or attic for 4 or 5 cables. It is only when you get up to having runs of 10-40 cables it gets complicated.

---

