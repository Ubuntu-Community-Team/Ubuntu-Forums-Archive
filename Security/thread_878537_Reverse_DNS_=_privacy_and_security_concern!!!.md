---
title: "Reverse DNS = privacy and security concern!!!"
date: 2008-08-03
forum: Security
---

### Post by pedja_portugalac on 2008-08-03
After ubuntu default install I checked my ports and services at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

All ports appears to be closed, which is not great thing, but shields up couldn't find any Reverse DNS associated to me, which is generally a good thing. 
> 
Your Internet connection has no Reverse DNS

Many Internet connection IP addresses are associated with a DNS machine name. (But yours is not.) The presence of "Reverse DNS", which allows the machine name to be retrieved from the IP address, can represent a privacy and possible security concern for Internet consumers since it may uniquely and persistently identify your Internet account — and therefore you — and may disclose other information, such as your geographic location.

When present, reverse DNS is supported by Internet service providers. But no such lookups are possible with your current Internet connection address (xxx.xx.xx.xxx.). That's generally a good thing.

After installing firestarter, to put me in Stealth mode, and allowing just DHCP, HTTP and HTTPS as the only allowed outbound traffic policies, I get an Reverse DNS address which didn't change even after rebooting cable modem or computer and in my opinion that's very bad for the privacy and security! 

My question is, what can we do now? I really don't like idea that any visited site can see where I am and what,s my f,n  Reverse DNS! Maybe the default install of ubuntu is safer for our privacy and security? :( :confused:

---

### Post by pedja_portugalac on 2008-08-03
It have nothing to do with default install. It's my laptop hardware or whatever in question. I reinstalled fresh ubuntu and it comes again:

> The text below might uniquely
identify you on the Internet

Your Internet connection's IP address is uniquely associated with the following "machine name":

xxx.xx.xxx.xx.cpe.netcabo.pt

The string of text above is known as your Internet connection's "reverse DNS." The end of the string is probably a domain name related to your ISP. This will be common to all customers of this ISP. But the beginning of the string uniquely identifies your Internet connection. The question is: Is the beginning of the string an "account ID" that is uniquely and permanently tied to you, or is it merely related to your current public IP address and thus subject to change?

The concern is that any web site can easily retrieve this unique "machine name" (just as we have) whenever you visit. It may be used to uniquely identify you on the Internet. In that way it's like a "supercookie" over which you have no control. You can not disable, delete, or change it. Due to the rapid erosion of online privacy, and the diminishing respect for the sanctity of the user, we wanted to make you aware of this possibility. Note also that reverse DNS may disclose your geographic location.

If the machine name shown above is only a version of the IP address, then there is less cause for concern because the name will change as, when, and if your Internet IP changes. But if the machine name is a fixed account ID assigned by your ISP, as is often the case, then it will follow you and not change when your IP address does change. It can be used to persistently identify you as long as you use this ISP.

There is no standard governing the format of these machine names, so this is not something we can automatically determine for you. If several of the numbers from your current IP address (xxx.xx.xx.x) appear in the machine name, then it is likely that the name is only related to the IP address and not to you. But you may wish to make a note of the machine name shown above and check back from time to time to see whether the name follows any changes to your IP address, or whether it, instead, follows you.

Just something to keep in mind as you wander the Internet.

**I think I'll put back my firestarter with all policies of restrictions I had before, rkhunter, chkrootkit and even wireshark to fight those sharks! :mad: This guys are spying all of us! On my old home computer no Reverse DNS and on 2 years old laptop Acer Aspire 9410Z it spy!** :mad:

---

### Post by kerry_s on 2008-08-03
just read it carefully, it tells you what it is and what it's for.

remove your ip, so the hackers don't find you-> your current IP address (213.xx.etc..

> Uses

The most common uses of the reverse DNS are:

    * The original use of the rDNS was primarily for network troubleshooting tools, such as traceroute, ping, and the "Received:" trace header field for SMTP e-mail, web sites tracking users (especially on Internet forums), etc.

    * One e-mail anti-spam technique is to check the domain names in the rDNS to see if they are likely from dialup users, dynamically assigned addresses, or other inexpensive internet services. Owners of such IP addresses typically assign them generic rDNS names such as "1-2-3-4-dynamic-ip.example.com." Since the vast majority, but by no means all, of e-mail that originates from these computers is spam, many spam filters refuse e-mail with such rDNS names. [2][3]

    * A Forward Confirmed reverse DNS (FCrDNS) verification can create a form of authentication showing a valid relationship between the owner of a domainname and the owner of the server that has been given an IP address. While not very thorough, this validation is strong enough to often be used for whitelisting purposes, mainly because spammers and phishers usually can't pass verification for it when they use zombie computers to forge domains.


---

### Post by pedja_portugalac on 2008-08-03
Very strange thing. I turn off, this morning, my computer and cable modem. When I wake up and check again shilds up test, it tell me no reverse DNS. :)

---

### Post by kerry_s on 2008-08-03
> **pedja_portugalac said:**
> Very strange thing. I turn off, this morning, my computer and cable modem. When I wake up and check again shilds up test, it tell me no reverse DNS. :)

but i know your rdns, because you left it here, i told you to remove it.
you need to read up on rdns and what it does and why it's used by the isp.
you need to read more carefully and try and understand what your reading.

(will remove pic later)

---

### Post by pedja_portugalac on 2008-08-04
> **kerry_s said:**
> but i know your rdns, because you left it here, i told you to remove it.
you need to read up on rdns and what it does and why it's used by the isp.
you need to read more carefully and try and understand what your reading.

(will remove pic later)

How can I remove it? 
There's nothing coming from google when I search "removing rdns". Any idea, where can I learn about it or how can I remove it?

Thanks.

PS. I use simple desktop edition Ubuntu, no server or mail server.

---

### Post by kerry_s on 2008-08-04
> **pedja_portugalac said:**
> How can I remove it? 
There's nothing coming from google when I search "removing rdns". Any idea, where can I learn about it or how can I remove it?

Thanks.

PS. I use simple desktop edition Ubuntu, no server or mail server.


your not understanding, there's nothing you can do, your isp uses that as a address for you, with out that you get no internet.

[http://en.wikipedia.org/wiki/Reverse_DNS_lookup](http://en.wikipedia.org/wiki/Reverse_DNS_lookup)

edit your other post and remove your ip, see pic.

i'll remove all pics later.

---

### Post by pedja_portugalac on 2008-08-05
> **kerry_s said:**
> your not understanding, there's nothing you can do, your isp uses that as a address for you, with out that you get no internet.

[http://en.wikipedia.org/wiki/Reverse_DNS_lookup](http://en.wikipedia.org/wiki/Reverse_DNS_lookup)

edit your other post and remove your ip, see pic.

i'll remove all pics later.

OK. Thank You. I didn't understand well and also didn't saw it inside the above post. But my question still remain, if the shields up site could discover my rdns than any other site I visit can do the same? Isn't it true?

---

### Post by kerry_s on 2008-08-05
> **pedja_portugalac said:**
> OK. Thank You. I didn't understand well and also didn't saw it inside the above post. But my question still remain, if the shields up site could discover my rdns than any other site I visit can do the same? Isn't it true?

yes, there suppose to, that's how they secure the connection between you and the site, any site. i did notice yours does have your full ip address in it, which is not a good thing, but if that's how your isp provides service to you the only thing you can do is ask them to change that, which i doubt they will. rdns is a normal thing, it's part of internet service, if you want to hide your ip you can use a proxy service, but most tend to be slow and unreliable. if your not doing nothing wrong, there is really no need to go to those lengths.

---

### Post by pedja_portugalac on 2008-08-05
> **kerry_s said:**
> yes, there suppose to, that's how they secure the connection between you and the site, any site. i did notice yours does have your full ip address in it, which is not a good thing, but if that's how your isp provides service to you the only thing you can do is ask them to change that, which i doubt they will. rdns is a normal thing, it's part of internet service, if you want to hide your ip you can use a proxy service, but most tend to be slow and unreliable. if your not doing nothing wrong, there is really no need to go to those lengths.

No, I ain't doing nothing wrong but this is a privacy threat. For example, one week ago, I was commenting actual political situation in my country, I was born in Serbia. After few comments against actual president Mr Boris Tadic I couldn't open those sites anymore, worst, I couldn't open another patriotic site hosted in Austria and chkrootkit warned me about possible sniffer on eth0. Going through proxy server allowed me to browse again those sites but my freedom of speech and my privacy were hurt! They control digital and most of the printed media and I am against those totalitarian regimes and systems. That said, my ISP is part of the same global mafia, mind controllers and "manufacturers of vegetable" ...

Anyway, Thank You for Your Time.

---

