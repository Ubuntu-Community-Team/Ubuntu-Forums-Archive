---
title: "Exotic MythTV hardware"
date: 2006-09-14
forum: The Cafe
---

### Post by Grey on 2006-09-14
I am currently an unemployed software engineer fresh out of university, so I am penniless, but I have been thinking about what to do when I actually have money again.  One thing I have really been considering is getting an exotic mythtv setup going.  I recently constructed a mythtv box for my girlfriend...  She has a ASUS Pundit-AH1 that runs both the frontend and the backend, and it's working marvelously.  However, I am thinking that I can do improvements to the setup when I build my own.  The box is quite quiet, except for an annoying hiss from the power supply, but I think it could be a lot quieter if some more exotic hardware were used.

The thing is, the frontend doesn't need to be that powerful.  It needs to be able to stream media over the network from the backend, and powerful enough to run some games ala snes9x.  It needs to have "just enough" power.  Which leads me to consider something very much like this (I might like to increase the network speed to gigabit and increase the onboard memory however):

[http://www.glomationinc.com/products_9312-sx.html](http://www.glomationinc.com/products_9312-sx.html)

Has anyone ever tried anything like this?  Has anyone had any success with running mythtv on ARM hardware?  Do you think it's powerful enough?  200MHz is quite powerful when you are talking about an ARM CPU.

I was thinking that I could install Debian on it, and I wouldn't need hard drives or optical drives.  I could just boot the kernel from flash memory and run the root file system from an NFS share on the central server.  The small form factor would be a boon in that I could construct a simple case for it, and just tape it to the back of my TV or something.

---

### Post by Shay Stephens on 2006-09-14
I don't have anything to offer but moral support, but I like the way you're thinking.  That could be very cool, fit in a small space, and not make much sound.  Probably not be too expensive either.

I am really jones'n for a myth tv setup right now, but lack the hardware and time to do anything about it.

---

### Post by mips on 2006-09-14
I'm not that familair with ARM cpu's except that thyare used a lot in embedded applications. Dunno how good linux support is.

Maybe do a google search for **mini-ITX** to find small form factor x86 based boards. Stuff like **VIA Eden**, **AMD Geode** etc. might be a good option.

---

### Post by Grey on 2006-09-14
Yeah, mini-itx was going to be my backup plan if I couldn't get an ARM board I liked.  ;)    I was actually very much considering this:
[http://www.mini-itx.com/store/?c=27](http://www.mini-itx.com/store/?c=27)

Except that I would prefer to have gigabit ethernet.  But yes, I was considering that as well.  ;)

---

### Post by emperor on 2006-09-14
> **Grey said:**
> Yeah, mini-itx was going to be my backup plan if I couldn't get an ARM board I liked.  ;)    I was actually very much considering this:
[http://www.mini-itx.com/store/?c=27](http://www.mini-itx.com/store/?c=27)

Except that I would prefer to have gigabit ethernet.  But yes, I was considering that as well.  ;)

The MythTV frontend only uses requires about 5 Mbps per stream for SDTV, so a standard 100 Mbps connection may be all that is needed.

---

### Post by Grey on 2006-09-14
I would also prefer s-video/composite output.  The gigabit ethernet would be more for general filesystem operations.  Since the host server would also be responsible for maintaining the root filesystem, I could see bandwidth being something of an issue, if I were doing something more disk intensive than watching a movie.  (Not exactly sure what, but I'm sure I would have need at some point)

---

### Post by teet on 2006-09-14
If I wanted a small quiet frontend, I would look into getting a via processor.

When I was looking for parts for my myth box a few months ago I considered going with a via for awhile (decided against it eventually since I was going to have a single frontend/backend machine).  They should have plenty of power for a backend, don't consume much power, and best of all don't put out a lot of heat.

[http://www.tomshardware.com/2002/06/05/via/index.html](http://www.tomshardware.com/2002/06/05/via/index.html)

-teet

---

