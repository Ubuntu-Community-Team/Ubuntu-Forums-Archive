---
title: "PC connecting to strange IPS all the time"
date: 2008-02-26
forum: Security Discussions
---

### Post by damatta on 2008-02-26
Hello.

Recently I have noticed  connections being established to some of these ips : 200.182.35.* at port 80. They seem to be hosted in Brazil, where I reside.
At first I thought that was normal but I was not able to gather further information on those hosts. What let me bewildered is that it happens on my WinXP too and seems to happen regardless to what site I visit. IT may or may not happen if I visit ubuntu.com for instance.
Would it happen to be some of my ISP's traffic policy or another annoying AKAMAI host? I'm really worried about privacy issues, I don't want pple sniffing my online transactions.

Thanks in advance.

---

### Post by k_grdn on 2008-02-26
Hi,

Run netstat -pant, try and establish who's connecting to who, are you hosting any services on port 80:?

If not block the port with iptables or kill the apache daemon listening on that port.

If you are hosting any sites just block access to regular offending hosts.

Regards,

k_grdn

---

### Post by damatta on 2008-02-26
There is no service running, no daemon listening for inbound connections from the internet. This is kinda eerie that my Pc is connecting to those hosts. Tried putting the ip 200.182.35.16 in the browser and strange text is displayed. I tried sniffing with wireshark but no readable text shows up on the output. What could this be, since it happens on XP and ubuntu

---

### Post by julian67 on 2008-02-26
are you running tor?

---

### Post by damatta on 2008-02-26
Thank you people for your promptly help
I'm not runing tor.
Blocking that IP range didn't hurt my connection at all. I wonder if my ISP could be behind this, as many reliable sites such as google.com causes me to connect to those hosts.

---

### Post by julian67 on 2008-02-26
that ip possibly belongs to [Akamai_Technologies]("http://en.wikipedia.org/wiki/Akamai_Technologies")

> Akamai transparently mirrors content (usually media objects such as audio, graphics, animation, video) stored on customer servers. Though the domain name is the same, the IP address points to an Akamai server rather than the customer's server. The Akamai server is automatically picked depending on the type of content and the user's network location.

In addition to image caching, Akamai provides services which accelerate dynamic and personalized content, J2EE-compliant applications, and streaming media to the extent that such services frame a localized perspective.

but I'm not completely sure about it, you perhaps need to do some research on that IP address if you can. If it is Akamai then it's not much to worry about (except the bigger issue of companies you might be expected to trust letting 3rd parties handle your requests. Alarmingly I've heard this is a method even used by banks, paypal etc though I don't know for sure).

---

### Post by damatta on 2008-02-26
Thank you, I'm prone to believe it belongs to AKAMAI, since lsof | grep 200.182.35. displayed all these connections being handled by firefox. What I still find strange is why this connection is established if the original request was to, lets say, kaspersky.com and I still can also see my PC connected to kaspersky.com:80
Is it possible that some of the content on the website redirects to AKAMAI in such a manner?

---

### Post by julian67 on 2008-02-26
> **damatta said:**
> Thank you, I'm prone to believe it belongs to AKAMAI, since lsof | grep 200.182.35. displayed all these connections being handled by firefox. What I still find strange is why this connection is established if the original request was to, lets say, kaspersky.com and I still can also see my PC connected to kaspersky.com:80
Is it possible that some of the content on the website redirects to AKAMAI in such a manner?

sounds as simple as kasperky are a customer of akamai and akamai mirror their content. Most users will never notice that the're not really connected to what they think they're connected to, but to a mirror. It's supposed to be a transparent mirror and to most people it *is *transparent.

---

### Post by brabo on 2008-02-27
maybe you could whois the ip and see what that says?

grtz,
brabo.

---

### Post by julian67 on 2008-02-27
that only gives the usual isp details. what is more interesting is to google the ip range and also make a search such as 200.182.* akamai

---

### Post by damatta on 2008-02-27
The ip range indeed belongs to AKAMAI, not much to worry I guess.
Thanks everybody

---

