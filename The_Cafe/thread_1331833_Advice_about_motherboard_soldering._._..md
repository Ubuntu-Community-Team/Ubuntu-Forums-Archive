---
title: "Advice about motherboard soldering. . ."
date: 2009-11-19
forum: The Cafe
---

### Post by pi.boy.travis on 2009-11-19
Hi!

A buddy of mine just bought a new fan assembly for his video card.  He managed to get the fan mounted properly, but there is not enough room for the heat sink.  The neighboring PCI slot is the offending space hog.  He doesn't want to modify the heat sink, so he asked me to un-solder and remove that PCI slot.  He claims that he will not need it, and he can always have it put back if he does.

OK, I do tons of soldering, but I am a little nervous about working on a motherboard.  Let's face it, the robot that built the board is better at soldering than me!  Secondly, I don't know it there will be some kind of issue with the board.  Will the BIOS complain?  Will I sever some kind of power lead by removing the connector?  It is a PCI 1.0 slot, not the larger 2.0, but naturally I have no schematic.  

So, my question is, even if I successfully unsolder the connector without creating any shorts, will it still work?

Thanks.  Any advice would be appreciated.

---

### Post by Skripka on 2009-11-19
> **pi.boy.travis said:**
> Hi!

A buddy of mine just bought a new fan assembly for his video card.  He managed to get the fan mounted properly, but there is not enough room for the heat sink.  The neighboring PCI slot is the offending space hog.  He doesn't want to modify the heat sink, so he asked me to un-solder and remove that PCI slot.  He claims that he will not need it, and he can always have it put back if he does.

OK, I do tons of soldering, but I am a little nervous about working on a motherboard.  Let's face it, the robot that built the board is better at soldering than me!  Secondly, I don't know it there will be some kind of issue with the board.  Will the BIOS complain?  Will I sever some kind of power lead by removing the connector?  It is a PCI 1.0 slot, not the larger 2.0, but naturally I have no schematic.  

So, my question is, even if I successfully unsolder the connector without creating any shorts, will it still work?

Thanks.  Any advice would be appreciated.

EDIT-
I wouldn't touch it with a 10 foot pole.

---

### Post by alphaniner on 2009-11-19
I think it would be possible, because I don't believe there are any internal connections in a PCI slot.  IOW, it is already a 'dead end'.  But I would be damn sure that you really want to do this before attempting it, and maybe practice on a junker or two.

---

### Post by Zoot7 on 2009-11-19
I'd imagine it's just plug for connections already on the motherboard. Somehow I don't see the connector being responsible for pulling unused connections to either Vcc or ground or anything like that.

So I can't see why it *wouldn't* work, as long as you went at the connections with something like a scalpel afterwards.

---

### Post by cariboo on 2009-11-19
+1 to alphaniner's advice, and use as low a wattage soldering iron as you can get away with, I use a 25 watt. Also put a new tip on the soldering iron if you haven't changed it in a while.

---

### Post by alphaniner on 2009-11-19
Also, when I googled this, there were a few mentions of removing the plastic frame first to make it so you can remove the leads individually.  I didn't think much of it at the time, but it seems like it would make things a whole lot easier.

---

### Post by tom66 on 2009-11-19
Can't you just reorder the cards (put the space-hogger at the bottom of the stack, and all other cards above it) so you can fit them in? Or did I misunderstand?

Motherboard soldering is very difficult, get a good tip on your iron and make sure you've got a temperature control. If you fry a trace you could permanently destroy the motherboard, or worse, cause an intermittent fault.

---

### Post by alphaniner on 2009-11-19
The issue is with a video card, chances are as good as not that there's only one PCIe slot.

---

### Post by Simon17 on 2009-11-19
> **cariboo907 said:**
> +1 to alphaniner's advice, and use as low a wattage soldering iron as you can get away with, I use a 25 watt. Also put a new tip on the soldering iron if you haven't changed it in a while.

Bad idea. If you use a low power iron, you're going to heat up other parts of the board before you can melt all of the solder.

---

### Post by dullard on 2009-11-19
Oops. Double post.

P.T.O.

---

### Post by dullard on 2009-11-19
> **dullard said:**
> +1

AND don't forget the solder sucker:
[http://www.mptools.co.uk/products.asp?partno=633609](http://www.mptools.co.uk/products.asp?partno=633609)

(and don't hold the heat there too long... be deft of touch!)

---

### Post by The Funkbomb on 2009-11-19
It's his motherboard so if you break it, no harm no foul.  He asked you to do it.

Personally, I wouldn't even touch it.

---

### Post by cariboo on 2009-11-19
Don't even attempt to use a solder sucker, you could suck the traces right off the board use [solder wick]("http:///www.globalsources.com/manufacturers/Solder-Wick.html") instead, especially if you you are using a high wattage soldering iron.

---

### Post by pi.boy.travis on 2009-11-19
OK, this is crazy, but it worked.  I looked at the solder joints, but I didn't feel that I could successfully remove the connector with the given equipment.  So, after some measuring, we saw that we only needed about a millimeter of space.  We decided to *sand* the PCI connector.  Yeah, we took some sandpaper, and whittled away the top two millimeters.  And lo and behold, the fan is working!

---

