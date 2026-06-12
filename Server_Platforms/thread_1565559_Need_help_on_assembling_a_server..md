---
title: "Need help on assembling a server."
date: 2010-09-01
forum: Server Platforms
---

### Post by hockey97 on 2010-09-01
Hi, there is the manual of my server board:[http://www.supermicro.com/manuals/motherboard/MCP55/MNL-H8QM3i-2.pdf](http://www.supermicro.com/manuals/motherboard/MCP55/MNL-H8QM3i-2.pdf)

Here is a manual for my server case: [http://www.supermicro.com/manuals/chassis/2U/SC828_10a.pdf](http://www.supermicro.com/manuals/chassis/2U/SC828_10a.pdf)


It's my first time assembling a server. I looked at the manuals. I can't seem to find how to install a hard drive. All I see in the manuals it says to put put the hard drive in the slidable trays and pop it in. I need to connect a sata hard drive to the board but don't know how.

---

### Post by Joe of loath on 2010-09-01
Do you have all the cables? It should just be a case of screwing the drive into a caddy and locating the slot on the mobo for the sata cables, then connecting it all up. The sata ports are below the battery, along the edge of the board.

That is a sexy motherboard btw! I want one just for gaming and numbercrunching, hehe

---

### Post by hockey97 on 2010-09-01
ya, I just figured it out. By just looking around and trying stuff. 

I am totally new to sata. I unscrewed the dummy drive and screwed in my new hard drive in it and slide it in. Then in the back of where you slide the hard drive their is a circuit board that has a sata connector. So I just got the sata wires and wired them from there to the server board.

I followed the motherboard manual where it would say sata 1 sata 2 etc. The thing is I got 6 drive slots and 6 wires. So when I got to 4  sata wires and the last two wires I connected it on another array  like there is 2 groups of sata connectors  there is the first 6 connectors and then additional like another 8 on the server board. so sata group 1 is what I think I am supposed to connect all hard drive bays too. yet the last 2 sata wires couldn't reach so I put it on the sata group 2 making it a sata 1 and sata 2 in the 2nd group.


I am now working on the led and power switches. I would like to know is there anything else from having to connect the sata wires and power to hard drives. I notice there is only 2 duplex power connectors to the circuit board in the back of the hard drive bay.

any other wires? I think I still have to connect the dvd drive and also there is 2 long wire cables and I don't know what those are for.

---

### Post by hockey97 on 2010-09-01
I just tested the server. I only notice the power supply fans running and their own leds are on. I then see the front leds for power etc very dull light and nothing happens. The case fans won't run nore anything else. Seems like I am having some type of problem getting power to the server board.

---

### Post by hockey97 on 2010-09-02
Hi, I finally got it to work. The only thing now that isn't working is the hard drive. I assume it's not getting power. I never plug in any power. I assumed the hard drive tray would provide it directly. I only plugged in 2 duplex power connectors from the power supply to the back panel of the hard drive bay.

---

