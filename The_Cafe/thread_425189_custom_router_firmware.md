---
title: "custom router firmware"
date: 2007-04-27
forum: The Cafe
---

### Post by raffytaffy on 2007-04-27
i rescently bought a Netgear FVS114 router. It seems to function "ok" meaning i can forward ports and it does what a router is supposed to do....almost. the problem im having is it looses connection every few hours. To fix this i have to reboot the router..i suppose its not that big a deal..but i can get quite annoying. Before i came here i went straight to the source..the netgear forums..and posted a similar question...they told me that the problem may lie in the MTU setting in the router. So i played around with the MTU setting as suggested. tried every setting possible from 1500 down to 0 . by decreasing 2 and doin my usuall tasks. the problem persisted. so now i came here for an alternate solution ..hopefully...does anyone here know what can be done..perhaps custom firmware ( ive been searching for some to no avail ) ??:confused:

---

### Post by agurk on 2007-04-27
I had the same problem with two Netgear RP614 until about a year ago, when they after two years FINALLY released a firmware that solved the problem.
Some advise I can give you, other than waiting for a firmware that fixes it, is to disable stuff you don't need, for example SPI (stateful packet inspection), VPN tunnels and such, in the hope of easing the load on the poor thing.
But really, if you recently bought it, you might be able to return it. As I said, I had to wait two years for that RP614 fix, and there's no guarantee you'll ever see one and that's simply unacceptable.
If you're looking for an alternative, one router that I'm really pleased with is my [Dlink DGL-4300](http://games.dlink.com/products/?pid=370), it has worked beautifully from day one. It's available without wireless as well (DGL-4100). I've disabled its SPI and "gaming" features since I'm not interested in those but just want a reliable, sturdy router.

---

### Post by Astinsan on 2008-02-07
its a old topic but I will tell you what the issue is. Almost all home routers have heat issues. Some are not obvious ... like the bit torrent lockups or disconnects.  Then there is the WIFI reboot crap (d-link 514 comes to mind) All you need to do is very simple. 

Put heat sinks on the processor chips and or microcontrolers. 

I have fixed D Link routers DI-514 version 1 and 2 by doing this. I have fixed Netgears, linksys (first wrk router had this issue) Most of the time it is the marvel chipset that has the issues. My guess is some where there is a incorrect spec on max temp. Most of these items are designed in a lab where there is decent air flow. Not behind a desk or on a window ledge in the sun light. Firmware will not help you fix this issue. 

Everyone is invited to check it out for yourself. Hope someone gets some use out of this.

---

