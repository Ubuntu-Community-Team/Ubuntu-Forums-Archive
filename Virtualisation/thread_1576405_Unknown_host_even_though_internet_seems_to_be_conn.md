---
title: "Unknown host even though internet seems to be connected."
date: 2010-09-17
forum: Virtualisation
---

### Post by vibhajha on 2010-09-17
Hi,
 
I am linux beginner and virtual box beginner too. I have installed virtual box on windows XP and I am using guest box as Linux (ubuntu) with GNOME. At first time when the installation got completed I was able to connect to Internet. But now I am not able to.
When I check my host connections. It does show me virtual box host as connected. I checked checked ubuntu connections and there also internet seems to be connected. Please find both the image attachments.
Also I installed driver for virtual box. Please see the attachment for that too.
 
It's do or die situation for me, I am trying to set this connection up and running since a week. 
Please help.
[IMG]http://i54.tinypic.com/2u60ehd.jpg[/IMG]
[IMG]http://i55.tinypic.com/mujq80.jpg[/IMG]
[IMG]http://i53.tinypic.com/2ntfuwk.jpg[/IMG]
 
Thanks and Regards,
Vibha Jha.

---

### Post by CharlesA on 2010-09-18
How is networking set for the Virtual Machine?

Bridged, Host-only, or NAT?

It looks like the ping is returning localhost(127.0.0.1) instead of what the real IP should be.

---

### Post by vibhajha on 2010-09-20
Hi CharlesA,

It is Host Only.

Regards,
Vibha.

---

### Post by srhart on 2010-09-20
Host only is incorrect. You need to set it to either:

NAT - assuming the ubuntu client machine's network card is set to DHCP, it will then get a 10.x.x.x address from the internal VirtualBox DHCP server - or -

Bridged - this will allow the ubuntu client machine to source an IP address from the local network DHCP server i.e. the same server that your host machine got it's address from.

I would recommend NAT in your situation.

Good luck

---

### Post by vibhajha on 2010-09-20
How can i enable NAT?

I tried bridge, but even my host network is not working in bridged configuration.

---

### Post by CharlesA on 2010-09-20
NAT or Bridged should work fine. Select NAT instead of Bridged to switch it to NAT.

---

