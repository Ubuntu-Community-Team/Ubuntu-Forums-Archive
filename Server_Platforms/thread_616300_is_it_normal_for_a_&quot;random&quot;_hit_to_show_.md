---
title: "is it normal for a &quot;random&quot; hit to show up in firestarter?? help"
date: 2007-11-18
forum: Server Platforms
---

### Post by LinuxSoundMan on 2007-11-18
i noticed i got a hit not too long ago from dhcp.insightbb.com. there was an ip i believe before that address and i will post it if necessary. i was just wondering if it was normal. and further does it matter?  am trying to tighten uo security. ive already gotten rid of samba. do i need ssh on my system. i am not running a server. any help and/or advice would be nice. kind regards.

---

### Post by ddrichardson on 2007-11-18
Not sure why removing samba would help you here, if you need ssh then keep it if not then remove it.

Insight are an ISP, [here]("http://whois.domaintools.com/insightbb.com"). No idea why their DHCP server would ping you, but unless you have a DHCP client/server open on that port then they wont get a connection.

This is the second time you've suggested SAMBA is a security risk, and I really am not sure why - it's just a protocol. You could suggest that TCP/IP is a risk as crackers could connect to you using it - ofcourse you wouldn't be able to access without it.

What is it that you are trying to tighten up? Ubuntu is pretty secure by default, closed ports etc. Unless you have a particularly easy to crack set of passwords then I'm unsure why you are so worried.

A machine needs to be of use to be cracked. Typically, most cracked systems are aimed at Storm/Botnet users using Linux as a server with a poor security policy or the millions of honeypot unpatched windows systems.

There aren't many Linux vulnerabilities and in any case because of its design it is a lot more secure anyway. Even if someone got something on your account, it would only affect that account.

---

