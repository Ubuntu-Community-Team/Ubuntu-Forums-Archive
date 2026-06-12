---
title: "Strengthening WEP security?"
date: 2013-03-23
forum: Security
---

### Post by Stonecold1995 on 2013-03-23
If I need to set up my computer in an adhoc network using WEP, it will be very vulnerable to the aircrack suite.  However I read from the man page of airuncloak-ng that some WIPS can help prevent simple attacks against the protocol:

> DESCRIPTION       airuncloak-ng is a tool that removes wep cloaking from a pcap file. Some WIPS (actually one) can actively "prevent" cracking a WEP key by inserting chaff (fake wep frames) in the air to fool aircrack-ng. In some rare cases, cloaking fails and the key can be
       recovered without removing this chaff. In the cases where the key cannot be recovered, use this tool to filter out chaff.


       The program works by reading the input file and selecting packets from a specific network.  Each selected packet is put into a list and classified (default status is "unknown"). Filters are then applied (in the order specified by the  user)  on  this  list.
       They  will  change  the status of the packets (unknown, uncloaked, potentially cloaked or cloaked).  The order of the filters is really important since each filter will base its analysis amongst other things on the status of the packets and different orders
       will give different results.


       Important requirement: The pcap file needs to have all packets (including beacons and all other "useless" packets) for the analysis (and if possible, prism/radiotap headers).

Is there a way I can set up my computer to send out these fake WEP frames, so that only airuncloak-ng could crack into it?

---

### Post by SeijiSensei on 2013-03-23
Why not just use WPA2?

---

### Post by na5h on 2013-03-24
Is there a specific reason why you can't use WPA2? WEP is not considered very secure by today's standards...there are plenty of programs out there for cracking WEP...

 edit: I just read from an unconfirmed source about the FBI showing that WEP could be cracked in less than 3 minutes using freely available tools....and this happened as far back as 2005!

---

### Post by Stonecold1995 on 2013-03-24
I want WEP for two reasons.  One is that the internet is down for me, so I'm forced to use a 3G mobile broadband through USB, and I want to set up my computer as an adhoc network so other computers in my house can connect to it, and adhoc seems to only support WEP.  The second reason is similar, but using adhoc even when I get my home internet back up so that I can use my Nintendo DS (which only supports WEP encryption).

I'm not going to be sending any sensitive information or anything, and even if I was, I'm using a VPN.  And as for my Nintendo DS, what sensitive information could be intercepted from IT?

The only reason I want slightly more secure WEP is so no one leeches off the very limited bandwidth the 3G mobile USB provides (and MAC address filtering does not provide that much protection).

> **na5h said:**
> edit: I just read from an unconfirmed source about the FBI showing that WEP could be cracked in less than 3 minutes using freely available tools....and this happened as far back as 2005!
Yeah I know.  I cracked my own WEP before in just 90 seconds (I think it was exactly 91 iirc).  I was using airodump-ng (capturing IVs), aireplay-ng (causing the router to release more IVs), and aircrack-ng (brute force weak IVs) on a laptop.  Hell, even most smart phones today can crack into WEP!

---

### Post by na5h on 2013-03-25
Can you disable the SSID broadcast?

---

### Post by Stonecold1995 on 2013-03-25
> **na5h said:**
> Can you disable the SSID broadcast?
That protection is too weak.  I want to be able to have a little resistance from aircrack and related programs.

---

### Post by besial on 2013-03-25
Do not use the DS. Look at installing hostap, dnsmasq, and/or dhcp3- server (pereferably on a seperate unused computer/laptop, or if you have too, on the computer with the 3G card) as a router. Do not use WEP. Dont even mess around with it. Stick with WPA2.

---

### Post by SeijiSensei on 2013-03-25
Can you limit connections to the router by MAC address?  Though it's not foolproof, it would certainly help protect against random intruders.

---

### Post by Stonecold1995 on 2013-03-25
> **besial said:**
> Do not use the DS. Look at installing hostap, dnsmasq, and/or dhcp3- server (pereferably on a seperate unused computer/laptop, or if you have too, on the computer with the 3G card) as a router. Do not use WEP. Dont even mess around with it. Stick with WPA2.
I am well aware of the weaknesses of WEP.  Any computer which is connected via WEP is also using a VPN which is encrypted with 128-bit blowfish, and as for the DS there is very little sensitive information it could be sending.  As I said, I am not worried about snooping of data, I am worried about leeching of my limited data plan.

> **SeijiSensei said:**
> Can you limit connections to the router by MAC address? Though it's not foolproof, it would certainly help protect against random intruders.
Possibly.  How would I do that, and how much protection would it provide (i.e. if someone spoofs a vaild MAC address, will they also be able to connect or only if I am disconnected)?



I don't just want a bunch of answers saying not to use WEP, I just want to know if I can harden it from brute-force cracking by transmitting fake WEP frames.  Is there or is there not a program which is capable of doing this?

This is only temporary, I'm not going to be using WEP as my only security for very long.  I already change my WEP key every day, sometimes several times per day, but I would like to be able to slow down any brute-force attack just a little more.

---

### Post by SeijiSensei on 2013-03-25
Your router should enable you to specify permitted MACs.  An easy solution is to connect all your devices then look at the list of MACs in the router's software.  Some routers let you create a permission list; otherwise you would just copy the addresses into the form for permitted addresses.

MACs can be spoofed, but from the little I've read it's harder than exploiting WEP.  I imagine you'd need to be monitoring the radio when the device requests an address via DHCP.  Using static addresses on the client devices might avoid the need to broadcast the MACs entirely.  I suspect it would be pretty hard to exploit this method in that situation, but you should do some research and not trust my rather uninformed speculation.

---

### Post by haqking on 2013-03-25
> **SeijiSensei said:**
> Your router should enable you to specify permitted MACs.  An easy solution is to connect all your devices then look at the list of MACs in the router's software.  Some routers let you create a permission list; otherwise you would just copy the addresses into the form for permitted addresses.

MACs can be spoofed, but from the little I've read it's harder than exploiting WEP.  I imagine you'd need to be monitoring the radio when the device requests an address via DHCP.  Using static addresses on the client devices might avoid the need to broadcast the MACs entirely.  I suspect it would be pretty hard to exploit this method in that situation, but you should do some research and not trust my rather uninformed speculation.


Spoofing a MAC and cracking WEP are equally as "easy" and both take about 30 seconds.

To the OP for radio security where you have to use WEP, there isnt alot you "can" do other than whats been said.

Use MAC address filtering (though it is easy to overcome)
Use a strong key and change it often (rotation)
Dont use DHCP and use statics where possible
Use a custom subnet to limit the amount of available IP so only the machines you have and want can connect.

These are all trivial to overcome, but that being said how likely is it that someone is close to you who will steal your WIFI or if they were going to would actually bother that much to get past the above.

---

### Post by Stonecold1995 on 2013-03-25
> **haqking said:**
> Spoofing a MAC and cracking WEP are equally as "easy" and both take about 30 seconds.

To the OP for radio security where you have to use WEP, there isnt alot you "can" do other than whats been said.

Use MAC address filtering (though it is easy to overcome)
Use a strong key and change it often (rotation)
Dont use DHCP and use statics where possible
Use a custom subnet to limit the amount of available IP so only the machines you have and want can connect.

These are all trivial to overcome, but that being said how likely is it that someone is close to you who will steal your WIFI or if they were going to would actually bother that much to get past the above.
How much protection does sending out fake WEP frames provide then?  From the manpage of airuncloak-ng only it can defeat fake WEP frames, which would mean very good protection from any skiddy type "point and click" WEP cracker like fern-wifi-cracker.

> **SeijiSensei said:**
> Your router should enable you to specify permitted MACs. An easy solution is to connect all your devices then look at the list of MACs in the router's software. Some routers let you create a permission list; otherwise you would just copy the addresses into the form for permitted addresses.

MACs can be spoofed, but from the little I've read it's harder than exploiting WEP. I imagine you'd need to be monitoring the radio when the device requests an address via DHCP. Using static addresses on the client devices might avoid the need to broadcast the MACs entirely. I suspect it would be pretty hard to exploit this method in that situation, but you should do some research and not trust my rather uninformed speculation.
I'm not using a router.  I'm using my computer connected to 3G for adhoc Wi-Fi.

---

### Post by haqking on 2013-03-25
> **Stonecold1995 said:**
> How much protection does sending out fake WEP frames provide then?  From the manpage of airuncloak-ng only it can defeat fake WEP frames, which would mean very good protection from any skiddy type "point and click" WEP cracker like fern-wifi-cracker.


I'm not using a router.  I'm using my computer connected to 3G for adhoc Wi-Fi.

Chaff (fake WEP frames or cloaked) was proposed for legacy WEP devices (WIPS) it will add about 10 seconds of security ;-)

There is no security for WEP, it was never meant to be (wired equivalence), update your firmware to support WPA or WPA2 or devices, or go with what youve got and hope for the best.

Peace

---

### Post by CharlesA on 2013-03-25
I can only speak for myself, but my laptop has some nifty "turn wireless NIC into wireless AP" software, but I'm running Win7 on it. There should be something like that for Linux.

I agree with haqking's assessment. Using WEP is just slightly above having no security at all.

---

### Post by haqking on 2013-03-26
> **CharlesA said:**
> I can only speak for myself, but my laptop has some nifty "turn wireless NIC into wireless AP" software, but I'm running Win7 on it. **There should be something like that for Linux**.
.

There is, always has been there hasnt there ?

[http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)

---

### Post by WhaleVPS on 2013-03-26
I think you are going to have to go with a case of "Who cares?"

Just monitor who is on your wireless and hope for the best.

---

### Post by CharlesA on 2013-03-26
> **haqking said:**
> There is, always has been there hasnt there ?

[http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)

Yep. Nice howto as well.

> **WhaleVPS said:**
> I think you are going to have to go with a case of "Who cares?"

Just monitor who is on your wireless and hope for the best.

No. Just no. If you are just going to depend on people to be honest, why have any security at all?

---

