---
title: "How disable PS3:s autonomous internet traffic?"
date: 2007-08-23
forum: Server Platforms
---

### Post by anders_ps3 on 2007-08-23
As you see I had a hard time to find a catchy title for this:

I run Kubuntu on a Sony PS3 behind a Netgear ADSL router using factory settings (allow all outgoing, block all incoming).

But when I switch OS and use the PS3 for games, HD movies etc, I would like to block *all* (outgoing&outgoing) internet traffic. The reason is simply that I want to be sure that the PS3 cannot
- make updates without me able to prevent it
- send logs about the games I play, the films I see
- etc

In short, I would like to prohibit all non-Kubuntu running internet traffic, without having to cut the line physically every time i feel for a car race.

Any ideas?

---

### Post by a9k on 2007-08-23
While running PS3 in game more, you aren't in Ubuntu so there is little we can do but....

Here's a whacky idea. If you can change the MAC-ID of the ethernet interface on the PS3 when it is under kubuntu AND if the PS3 reverted the MAC-ID when rebooted into game mode THEN the box would appear as two different boxes to your Netgear ADSL router. 

With 2 different MACs, you could monkey with the DHCP part of the Netgear and hand out two different 'fixed' ip addresses. If that works, you might be able to block one of those ips from the internet using whatever tools Netgear has these days.

---

### Post by anders_ps3 on 2007-08-23
Thanks, I'll check out your if statements
/A

---

