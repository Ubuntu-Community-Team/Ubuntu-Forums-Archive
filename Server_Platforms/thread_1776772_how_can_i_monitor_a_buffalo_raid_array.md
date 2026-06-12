---
title: "how can i monitor a buffalo raid array"
date: 2011-06-06
forum: Server Platforms
---

### Post by collisionystm on 2011-06-06
I have 10.04 server with a linkstation raid 5 attached via usb. What is the best way to monitor the drives for a failure? Its at a remote site

---

### Post by collisionystm on 2011-06-07
its morning in america.... bump.....

---

### Post by ruffEdgz on 2011-06-07
I did some searching and found this: [http://www.smallnetbuilder.com/content/view/30670/75/](http://www.smallnetbuilder.com/content/view/30670/75/)

Is that the RAID5 Linkstation that you are somewhat taking about?

If it is, then any hardware RAID is kind of hard to manage without being there to check up on it in person. We use mostly hardware RAID5 setups on Dell machines and I need to go in every so often to make things are going well (and we have other people in operations that help out with that as well).

I did notice in the link above that one 'con' about the product was remote web access. Can that linkstation be connected not just to you server via USB but to the internet or to the local box? If so, then maybe something in there could help send notifications on the status of the hardware or whatnot.

Another idea would be to see if you could not raid the drives and then software raid them (defeats the purpose of having a hardware RAID linkstation but would help you monitor them).

Cheers!

Just thought I would put that out there.

---

