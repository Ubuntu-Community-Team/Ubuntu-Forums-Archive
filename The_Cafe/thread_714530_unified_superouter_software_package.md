---
title: "unified superouter software package"
date: 2008-03-03
forum: The Cafe
---

### Post by herrdoktor330 on 2008-03-03
Hey ubuntu folks!

I was thinking about turning one of my PCs into a super-router, capable of the following tasks:
1) the obvious stuff (firewall, DHCP server, WLAN AP, WEP/WPA/WPA2)
2) super-security (anti-phishing, protocol anomoly detection, IP spoofing prevention, SSL, intrusion prevention)
3) parental controls
4) enterprise level networking (openVPN)
5) firewall scripts for blocking P2P apps (there will be no limewire in a house of mine)

and the ringer...

6) integrated IP blocking (ala PeerGuardian)

Now, I was looking at software made for the linksys and other firmware hackable routers. But none that I have found include the IP blocking that I would like to do at the router level for that "added security feeling".

I would really like to make this a reality, as I think it would be a killer way to have a homegrown router with all the features one would really like. But I wasn't able to find any projects like this in my hour of searching sourceforge or googling. The best I could find was PacketProtector. But does anyone know of any projects going on that does all of this in a linux distribution or binary package (.deb)? Specifically item #6.

Or is there no advantage to running an IP Blocking software at the router level.

Inquiring minds want to know.

---

### Post by saulgoode on 2008-03-03
I don't know if they will satisfy your needs, but have you looked into either [Smoothwall]("http://www.smoothwall.org/") or [IPcop]("http://ipcop.org/")?

---

### Post by mips on 2008-03-04
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)
You can add more stuff to the above quite easily.

[http://www.xorp.org/](http://www.xorp.org/)
[http://www.vyatta.com/](http://www.vyatta.com/)

---

### Post by hyper_ch on 2008-03-04
I'd read up here if one of those suits you:

[http://www.howtoforge.com/ubuntu6.06_firewall_gateway](http://www.howtoforge.com/ubuntu6.06_firewall_gateway)

[http://www.howtoforge.com/debian_ebox](http://www.howtoforge.com/debian_ebox)

[http://www.howtoforge.com/nat_iptables](http://www.howtoforge.com/nat_iptables)

---

### Post by herrdoktor330 on 2008-03-04
Wow! Thanks guys! I'm definatly going to look into those links.

But the thing I've been debating the most is the pros/cons of running IP Blocking software at the router level.

Do you all think that it's "over the top" paranoia? Or do you think running the blockers at the client level is a better way to go.

Here's why I'm asking: I run IPlist (or otherwise known as IPBlock) on my Ubuntu installs and PeerGuardian on my windows installs. But it seems like I block traffic on the client that I wouldn't normally get. An example: A roommate will be on Myspace (Limelight Networks LLC) ... but my IPBlock will catch the inbound pings on my computer not using myspace/steam/xbox live/ or anything having to do with that. So it makes me think that these pings are going through to all computers behind my router. So... it makes me think that if I blocked that traffic at the router, then none of it would be a concern. Leaving me to block port 80 on the client for the more clandestine things I like to do.

Does that sound like a good idea? Or am I just wanting to over-do it?

BTW... thanks for all the feedback.

---

### Post by herrdoktor330 on 2008-03-04
Just to get back with you folks:

IPCop seemed pretty cool. I might try that if I want to "take it easy".

But I think my most likely option is to go with the ubuntu 6.06 nat/firewall instructions to see what I can put together. The thread that mips recommended seemed really insightfull. The howtoforge that hyper_ch was really good too. I think you've both given me a couple good references.

Big ups to all of you.

---

