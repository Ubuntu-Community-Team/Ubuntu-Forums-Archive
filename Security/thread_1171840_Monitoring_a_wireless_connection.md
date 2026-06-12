---
title: "Monitoring a wireless connection"
date: 2009-05-27
forum: Security
---

### Post by osjak on 2009-05-27
Reading all the news about big and scary botnets taking over the world, I have asked myself if I am really sure that my home computers are free of this plague. So I decided to monitor my network a bit and ran into a small problem. Here is what my network looks like:
```

           ________
Modem <-> |        |<------wire------> Desktop (Ubuntu)
          | Router |
          |        |<------wire------> Server (Debian)
           --------
               ^ - - - - wireless - -> Desktop (Windows XP)

```
I use the Ubuntu desktop, where I have two network cards installed. So I fired up the Wireshark with one card in promiscuous mode to see what's going on. I can see my wired communications, but (surprise!) not wireless. **Any idea how I can pick up on what is being transferred over the air without installing an additional wifi card on my desktop?** 

Router: Linksys WRT54GS v6

---

### Post by DGortze380 on 2009-05-27
> **osjak said:**
> Reading all the news about big and scary botnets taking over the world, I have asked myself if I am really sure that my home computers are free of this plague. So I decided to monitor my network a bit and ran into a small problem. Here is what my network looks like:
```

           ________
Modem <-> |        |<------wire------> Desktop (Ubuntu)
          | Router |
          |        |<------wire------> Server (Debian)
           --------
               ^ - - - - wireless - -> Desktop (Windows XP)

```
I use the Ubuntu desktop, where I have two network cards installed. So I fired up the Wireshark with one card in promiscuous mode to see what's going on. I can see my wired communications, but (surprise!) not wireless. **Any idea how I can pick up on what is being transferred over the air without installing an additional wifi card on my desktop?** 

Router: Linksys WRT54GS v6

Your diagram is likely wrong.

Modem -> Router -> Switch -> Ubuntu Desktop
                   Switch -> Debian Server
                   Switch -> XP (Wireless)

Because you're likely using a switch (built into your router), you will only be able to see communications between a certain machine and the switch. Wireless traffic of course can be sniffed.

---

### Post by osjak on 2009-05-29
Thank you, DGortze380. Yes, I have much to learn on network operations. I just hoped there was a work around, but it seems there is none.

---

### Post by DGortze380 on 2009-05-29
> **osjak said:**
> Thank you, DGortze380. Yes, I have much to learn on network operations. I just hoped there was a work around, but it seems there is none.

Since it's a small network, the work around for your wired connections would be to introduce a hub into the network.

-> modem -> router -> switch -> hub -> (all wired devices)

You still won't get wireless traffic in that model unless you sniff it. You'd need a separate WAP plugged into the hub to get wireless traffic on a wired sensor.

---

### Post by statistic on 2009-05-29
> **DGortze380 said:**
> Since it's a small network, the work around for your wired connections would be to introduce a hub into the network.

-> modem -> router -> switch -> hub -> (all wired devices)

You still won't get wireless traffic in that model unless you sniff it. You'd need a separate WAP plugged into the hub to get wireless traffic on a wired sensor.

The interesting part is finding an actual hub. Everywhere I've been to buy a hub has only been a switch that they call a hub for ancient people that don't know what a switch is. They're hard to come by. I know of a security firm that will buy you a top of the line switch with as many ports as the hub that you give them. I held on to the one my uni was throwing out though :P.

---

### Post by DGortze380 on 2009-05-29
> **statistic said:**
> The interesting part is finding an actual hub. Everywhere I've been to buy a hub has only been a switch that they call a hub for ancient people that don't know what a switch is. They're hard to come by. I know of a security firm that will buy you a top of the line switch with as many ports as the hub that you give them. I held on to the one my uni was throwing out though :P.

Yeah, when you find them, buy them up. They're out of date and hard to find, but have a lot of uses, especially in security.

---

