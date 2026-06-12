---
title: "Drive accessibility after another drive on the same channel has failed?"
date: 2009-01-17
forum: Server Platforms
---

### Post by handy on 2009-01-17
It is my understanding that if a drive fails on an IDE channel (bus) either Primary or Secondary, then the other drive be it Master or Slave can often become inaccessible.

Can anyone confirm this for me?

This then begs the question, do SATA controllers suffer from the same fate?

The answers to those two questions have quite some impact on the reliability of soft RAID.

If these are in fact real problems then does this make hardware RAID cards the most reliable option?

Do all hardware RAID cards protect each individual drive from the hardware failure of other drives in the array.  I expect that they do.

---

### Post by handy on 2009-01-17
I'll post the following link to the [*_FreeNAS knowledge base_*]("http://www.freenaskb.info/kb/?View=entry&EntryID=259"), which states that if a drive sharing the IDE bus (Primary or Secondary are two separate buses) goes down it will usually make the other drive inaccessible.  It highly recommends using only one drive/bus.  As in a fault tolerant RAID setup (RAID levels 1,5), one disk going down can be handled but two can not.

So my question stands, do SATA controllers behave the same way as IDE?

This is a very important question I think.

---

### Post by handy on 2009-01-19
I've done quite a bit of reading from searching the web, & still haven't found any pertinent information regarding how a SATA controller with more than one drive under its control, handles the situation when one of those drives fails?

---

