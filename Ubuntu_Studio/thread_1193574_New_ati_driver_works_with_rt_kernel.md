---
title: "New ati driver works with rt kernel"
date: 2009-06-21
forum: Ubuntu Studio
---

### Post by markbuntu on 2009-06-21
In case anyone was wondering....

The latest Catalyst 9.6 driver, fglrx8.62.4 works with the rt kernel. They finally put the rt patch in the right place. I have only tested this myself on Hardy amd64 with the 2.6.24rt kernel but results should be the same for others.

This driver does not work with the 2.6.29 or 2.6.30 kernel without jumping through a few hoops but it can be done.

Be sure to read the release notes to make sure your card is supported before using this driver. Anything before the HD2400 is not.

regards,
mark

---

### Post by NoVista on 2009-06-21
> Be sure to read the release notes to make sure your card is supported before using this driver. Anything before the HD2400 is not. Hay Mark it may not be supported, but wondered if it would still work with older cards like my x800AIW.
At the moment I can't risk an ATI meltdown, with no recent partition backup at hand.

---

### Post by markbuntu on 2009-06-22
Definitely not. This driver ONLY works for rv600 and rv700 cards which is the HD2400 pro, HD3xxx and HD4xxx series.

---

### Post by NoVista on 2009-06-22
Thanks.

---

### Post by Vigh on 2009-11-03
hi you couldn't point us to a guide, for jumping through those hoops for setting up the latest ati driver with the latest rt kernel? all good ive got my graphics working with rt-kernel now

---

