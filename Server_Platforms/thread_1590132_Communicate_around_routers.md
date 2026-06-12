---
title: "Communicate around routers?"
date: 2010-10-07
forum: Server Platforms
---

### Post by kevin11951 on 2010-10-07
Network Diagram:

```

Router A (10.0.0.1/24):
|	PC1 - 10.0.0.2
|	PC2 - 10.0.0.3
|	PC3 - 10.0.0.4
\/
Router B (10.0.1.1/24):
	PC4 - 10.0.1.2
	PC5 - 10.0.1.3
	PC6 - 10.0.1.4

```

Is it possible for PC1/2/3 to communicate directly with PC4/5/6?

Router B is a DDWRT router, so I should be able to so something...  Right?

There is no way for me to remove either of the routers right now, so I am looking for a shortcut to make them both into one big subnet so I can use LAN applications like LAN games across all of them.

---

### Post by BobVila on 2010-10-07
I don't have any direct experience with DDWRT routers, but, from what I read, you should be able to make it operate like a switch and disable routing functionality. If that's the case, you could give it an ip in the 0.x range and keep everything in one subnet.

---

### Post by kevin11951 on 2010-10-07
> **BobVila said:**
> I don't have any direct experience with DDWRT routers, but, from what I read, you should be able to make it operate like a switch and disable routing functionality. If that's the case, you could give it an ip in the 0.x range and keep everything in one subnet.

Well, the way its setup, I can't.  It is setup as a wireless repeater, and when I do that, it makes it into a wireless-to-wireless router.

---

### Post by littlegreiger on 2010-10-07
You could try setting the DD-WRT router up as a repeater bridge by following this how-to
[http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge)

From my understanding of your question, that's what you want to do.

Your network should then look like this:
```
 
Router A (10.0.0.1/24)
|   PC 1 (10.0.0.3)
|   PC 2 (10.0.0.4)
|   PC 3 (10.0.0.5)
\/
DD-WRT Repeater Bridge (10.0.0.2)
    PC 4 (10.0.0.6)
    PC 5 (10.0.0.7)
And so on

```

---

### Post by kevin11951 on 2010-10-07
> **littlegreiger said:**
> You could try setting the DD-WRT router up as a repeater bridge by following this how-to
[http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge)

From my understanding of your question, that's what you want to do.

Your network should then look like this:
```
 
Router A (10.0.0.1/24)
|   PC 1 (10.0.0.3)
|   PC 2 (10.0.0.4)
|   PC 3 (10.0.0.5)
\/
DD-WRT Repeater Bridge (10.0.0.2)
    PC 4 (10.0.0.6)
    PC 5 (10.0.0.7)
And so on

```

Well, I got it to work...  Thank you.

That said, it took me all day and now I want a chicken sandwich... ;)

Stupid chicken... ;)

---

