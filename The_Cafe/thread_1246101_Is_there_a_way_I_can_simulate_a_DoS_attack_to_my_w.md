---
title: "Is there a way I can simulate a DoS attack to my webserver?"
date: 2009-08-21
forum: The Cafe
---

### Post by dragos240 on 2009-08-21
Hi,

I want to preform a DoS attack on my webserver, or at least simulate it. To see if my server can handle it. But how can I do this??:confused:

---

### Post by ssam on 2009-08-21
ab (apache benchmark)
[http://httpd.apache.org/docs/2.0/programs/ab.html](http://httpd.apache.org/docs/2.0/programs/ab.html)

---

### Post by LowSky on 2009-08-21
I don't think this is a great thing to be discussing on the forums. a how to DoS a server is a bad thing, try searching that website that does web searches and starts with a 'G'

---

### Post by JohnFH on 2009-08-21
> **LowSky said:**
> I don't think this is a great thing to be discussing on the forums. a how to DoS a server is a bad thing, try searching that website that does web searches and starts with a 'G'

I disagree.  He only wants to know how to _simulate_ one internally.  I've also got a webserver and I'll like to know how to protect against this too.

---

### Post by dragos240 on 2009-08-21
Yes, it is merely a DoS *SIMULATION*. And it is completely internal, and to my own webserver. This is for testing purposes, and is for the prevention of such attacks.

---

### Post by nomnomnom on 2009-08-21
I can get your server DDoS'ed. Just drop me a PM of when, and how severe you want it to be.

---

### Post by hessiess on 2009-08-21
Routers are designed to drop any packets if it is receving them faster than it can send them on, a DDoS attack works by flooding your pipe (available bandwidth) with so much junk that the good packets get dropped, unfortunately the only thing that can be done about it is to buy more bandwidth.

---

### Post by schauerlich on 2009-08-21
1) Get another computer
2) Use google to figure out how to DoS people
3) Aim your lazor
4) Fire your lazor
5) ????
6) PROFIT

---

### Post by moocow1452 on 2009-08-21
Put up a "leaked" schematic and specs on the iTablet, and post it to digg.com. If it survives that, it can survive anything.

---

### Post by bear24rw on 2009-08-21
> **moocow1452 said:**
> Put up a "leaked" schematic and specs on the iTablet, and post it to digg.com. If it survives that, it can survive anything.

lol digg does take down servers all the time..

---

### Post by schauerlich on 2009-08-21
1) Put your IP address on 4chan.
2) Tell them you have CP
3) wait
4) ????
5) PROFIT

---

### Post by moocow1452 on 2009-08-21
> **EDavidBurg said:**
> 1) Put your IP address on 4chan.
2) Tell them you have CP
3) wait
4) ????
5) PROFIT
Ok, you win. I can't beat that.

---

### Post by RiceMonster on 2009-08-21
> **EDavidBurg said:**
> 1) Put your IP address on 4chan.
2) Tell them you have CP
3) wait
4) ????
5) PROFIT

lmao

/thread

---

### Post by blithen on 2009-08-21
> **EDavidBurg said:**
> 1) Put your IP address on 4chan.
2) Tell them you have CP
3) wait
4) ????
5) PROFIT
xD I knew something like this would happened...
Messed up thing is it would probably work. : |

---

### Post by nomnomnom on 2009-08-21
Actually, if you're going to DDoS suicide via 4chan, just post your IP and say you have naked pictures of BOXXY. 

You will never get online again =]

---

### Post by schauerlich on 2009-08-21
> **nomnomnom said:**
> Actually, if you're going to DDoS suicide via 4chan, just post your IP and say you have naked pictures of BOXXY. 

You will never get online again =]

Boxxy <3333

---

### Post by RiceMonster on 2009-08-21
Thanks a lot guys, I had forgoten about Boxxy. It was such a nice thing to forget. I blame you for making me remember this horror.

---

### Post by LowSky on 2009-08-21
Gnomes are horrible at business plans...lol
Phase one: collect underpants
Phase two: ???
Phase three: Profit

---

### Post by nomnomnom on 2009-08-21
> **EDavidBurg said:**
> Boxxy <3333

Rofl xD

---

### Post by nomnomnom on 2009-08-21
> **RiceMonster said:**
> Thanks a lot guys, I had forgoten about Boxxy. It was such a nice thing to forget. I blame you for making me remember this horror.

Like you wouldn't ....

---

### Post by schauerlich on 2009-08-21
> **nomnomnom said:**
> Rofl xD

You've inspired me to update my sig.

---

### Post by nomnomnom on 2009-08-21
> **EDavidBurg said:**
> You've inspired me to update my sig.

Lmfao. It needs the picture tho...

[IMG]http://www.perthstreetbikes.com/39024/sport-bike-turning-circles/boxxy-trolling.jpg[/IMG]

---

### Post by schauerlich on 2009-08-21
> **nomnomnom said:**
> Lmfao. It needs the picture tho...

Updated. :D

---

### Post by nomnomnom on 2009-08-21
> **edavidburg said:**
> updated. :d


xDDDDDDDD

---

### Post by mkljun on 2011-01-11
There's a tool working on LAN only and is called ddosim:

[https://sourceforge.net/projects/ddosim/](https://sourceforge.net/projects/ddosim/)

[http://stormsecurity.wordpress.com/2009/03/03/application-layer-ddos-simulator/](http://stormsecurity.wordpress.com/2009/03/03/application-layer-ddos-simulator/)

---

