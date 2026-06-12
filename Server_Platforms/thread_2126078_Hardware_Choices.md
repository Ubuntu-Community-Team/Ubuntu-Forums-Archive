---
title: "Hardware Choices"
date: 2013-03-15
forum: Server Platforms
---

### Post by 1egoman on 2013-03-15
[CENTER]----- I didn't think this forum may be the best place to post this, or it may need to be moved to the hardware section. I wan't very sure where to put it. If this really doesn't fit with Ubuntu forums, just let me know and remove the thread. -----[/CENTER]

I have $175 to spend to upgrade my server computer.

**The Current Specs:**
- Phenom II X3 700e 
- 2GB ram
- old, crappy motherboard 

**The Current Server Does:**
- Apache hosting 3 web sites
- Samba hosting all my projects
- Hosting a 12 person Minecraft server

I'm thinking about:
 NOTE: I do realize these are desktop parts, and I am putting them in a server because its all I can afford.

- Core i3 3220
 ([http://www.newegg.com/Product/Product.aspx?Item=N82E16819116775](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116775))

- ASRock B75 PRO3-M 
 ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813157329](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157329))

- Some G skill Ram I have laying around (4GB)

Can anyone say if these parts are Ubuntu server compatible, and if they are overkill for what I want to do?
Thanks.

---

### Post by tgalati4 on 2013-03-15
There are a lot of used Dell PowerEdge servers for sale.  They are loud, but if you have a closet to put them in, they would perform better than janky desktop hardware.

---

### Post by 1egoman on 2013-03-16
However, part of my money I can spend is in Newegg gift cards, and I don't really think I could afford a server for $100. If I'm wrong, please let me know.

---

### Post by tgalati4 on 2013-03-16
Most of the decent servers I have seen are in the $300 range, but sometimes I see them for $150 and missing parts like hard drive or RAM, which newegg sells.

---

### Post by gordintoronto on 2013-03-16
Why do you want to upgrade? What is your current motherboard? What is the limiting factor (bottleneck) with a Minecraft server? (Surely there are Mincecraft forums?) Exactly what G-Skill RAM do you have?

If you have trouble answering these questions, run this command:
sudo lshw > myconfig.txt
then have a look at what's in there. The motherboard ID should be right at the top.

It's possible an SSD would be a better place to put your money.

If the G-Skill RAM is an appropriate speed, installing it seems like a no-brainer.

The motherboard you mentioned has an underwhelming approval rating on Newegg. I know, Newegg ratings are not all that reliable, but still...

You also might want to post your message on PCMech.com

---

