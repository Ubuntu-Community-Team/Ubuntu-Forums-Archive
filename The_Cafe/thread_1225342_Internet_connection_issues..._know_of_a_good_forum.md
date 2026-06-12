---
title: "Internet connection issues... know of a good forum?"
date: 2009-07-28
forum: The Cafe
---

### Post by BattlePanic on 2009-07-28
The cable internet connection at work has become intermittent over the past couple of weeks -- Power-cycling modems/routers etc doesn't seem to help.  The internet is not completely unreachable, rather, just sporadic periods of slowness and timeouts.  I've been charged with figuring out what's wrong.

Anyone know of a good forum for troubleshooting general internet connection problems?

---

### Post by eldragon on 2009-07-28
call your isp

---

### Post by wojox on 2009-07-28
Check out the router manufactures website. What are you using? Cisco I hope.

---

### Post by BattlePanic on 2009-07-28
> **eldragon said:**
> call your isp

Talked to the ISP.  Apparently everything is fine according to measurements on their end although I've heard this from an ISP only to eventually discover that there was in fact problems on their side.

> **wojox said:**
> Check out the router manufactures website. What are you using? Cisco I hope.

It's a Linksys/Cisco WRT54G.  The router is about two years old

I'm not in a position to play around with the hardware until next week since the business is currently depending on the connection, slow as it is.  In the meantime I'm hoping to gather as much knowledge as I can and any pointers to a networking-related forum would be great.

---

### Post by wojox on 2009-07-28
I've got the WRT54G2 I'd recommend going to the Syslink site and look for a firmware update. It'll be a file to download and then log on to your router [http://192.168.1.1/](http://192.168.1.1/) Click Administration > Firmware Upgrade and upload the file. When you get the chance.

---

### Post by xpod on 2009-07-28
> The cable internet connection at work has become intermittent over the past couple of weeks -- Power-cycling modems/routers etc doesn't seem to help. The internet is not completely unreachable, rather, just sporadic periods of slowness and timeouts. I've been charged with figuring out what's wrong.

You could try using [OpenDNS](https://www.opendns.com/start/) rather than your ISP`s DNS.It narrows things down a bit if nothing else.

---

### Post by BattlePanic on 2009-08-29
Just a follow-up.  I got a chance to upgrade the router firmware and the issue seems to have been resolved.

---

### Post by pwnst*r on 2009-08-29
i strongly suggest DDWRT or Tomato for your firmware.

---

### Post by gletob on 2009-08-29
I'm going to do something:

Answer your actual question and not try to diagnose your connection.  Even if you've got your problem solved.

[http://www.dslreports.com/forums/all](http://www.dslreports.com/forums/all)

I know it's called dsl reports but they have forums for Cable, DSL, and FTTH

---

### Post by pwnst*r on 2009-08-29
> **gletob said:**
> I'm going to do something:

Answer your actual question and not try to diagnose your connection.  Even if you've got your problem solved.

[http://www.dslreports.com/forums/all](http://www.dslreports.com/forums/all)

I know it's called dsl reports but they have forums for Cable, DSL, and FTTH

lol, i was going to offer that link since i've been a member for years, but saw that his issue got fixed.

great site for connection tests of all kinds.

---

### Post by BattlePanic on 2009-09-01
> **pwnst*r said:**
> i strongly suggest DDWRT or Tomato for your firmware.

Sadly, I'm working with one of the newer versions of the WRT54G which isn't linux-based.  I use Tomato on my router at home and like it a lot.

gletob, thanks for the tip on dslreports I'll be checking there next time I have a problem.

---

