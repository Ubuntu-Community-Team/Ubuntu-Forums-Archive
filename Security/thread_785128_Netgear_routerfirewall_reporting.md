---
title: "Netgear router/firewall reporting"
date: 2008-05-07
forum: Security
---

### Post by kafkaian on 2008-05-07
I have tried to look through these and various other forum threads but probably have not defined the problem correctly.

My router/firewall (Netgear FR114p) is reporting: [COLOR="Red"]Wed,Attempt to access blocked sites - Source:192.168.0.2,LAN - Destination: dubya-dubya-dubya.blocked_site-dot-com....[/COLOR]. I have blocked certain sites through the Netgear firewall using keywords and keep getting this report once or twice every few days when I'm online. I am using 192.168.0.2 on my network and have not made the searches its reporting, so what's going on?

I've looked inside my cache and examined various cookies but can't find anything associated with the search so am puzzled but worried at the same time that someone has got in through an insecure port.

Any advice on what this is and what I should consider would be very much appreciated. Thanks in advance

Ian

---

### Post by kafkaian on 2008-05-07
Any links to appropriate research would also be appreciated. A definition of what could be happening would also be great

---

### Post by brian_p on 2008-05-07
> **kafkaian said:**
> I have tried to look through these and various other forum threads but probably have not defined the problem correctly.

My router/firewall (Netgear FR114p) is reporting: [COLOR="Red"]Wed,Attempt to access blocked sites - Source:192.168.0.2,LAN - Destination: dubya-dubya-dubya.blocked_site-dot-com....[/COLOR]. I have blocked certain sites through the Netgear firewall using keywords and keep getting this report once or twice every few days when I'm online. I am using 192.168.0.2 on my network and have not made the searches its reporting, so what's going on?

I've looked inside my cache and examined various cookies but can't find anything associated with the search so am puzzled but worried at the same time that someone has got in through an insecure port.

Any advice on what this is and what I should consider would be very much appreciated. Thanks in advance

Ian

It is a possibility that in accessing a particular website that the blocked URL is also accessed. For example, I have never typed [http://ad.media-servers.net](http://ad.media-servers.net) but it is there in firefox's history. Try typing the URL in the address bar of your browser.

---

### Post by kafkaian on 2008-05-07
> **brian_p said:**
> It is a possibility that in accessing a particular website that the blocked URL is also accessed. For example, I have never typed [http://ad.media-servers.net](http://ad.media-servers.net) but it is there in firefox's history. Try typing the URL in the address bar of your browser.

Thanks Brian, I'll check, but one url is a google search term that I would never search for whilst the other is a site that has been included in the search. I've also thought that it could be image access from a site embedded into say a forum.

Hmmm, curious

---

### Post by Monicker on 2008-05-07
> **kafkaian said:**
> Thanks Brian, I'll check, but one url is a google search term that I would never search for whilst the other is a site that has been included in the search. I've also thought that it could be image access from a site embedded into say a forum.

Hmmm, curious

You could try running Wireshark or tcpdump to get some more information about this.  Just let them run for a day.  Do a ring buffer which does a new files every hour, and then you can know which file to look at by the timestamp from your router.  The "follow tcp stream" option is very useful.  Perhaps filter on just port 80 to start, to minimize the size of the captures, and then remove the filter if that does not catch it.

---

### Post by kafkaian on 2008-05-07
> **Monicker said:**
> You could try running Wireshark or tcpdump to get some more information about this.  Just let them run for a day.  Do a ring buffer which does a new files every hour, and then you can know which file to look at by the timestamp from your router.  The "follow tcp stream" option is very useful.  Perhaps filter on just port 80 to start, to minimize the size of the captures, and then remove the filter if that does not catch it.That sounds an excellent idea. I will give it a try. Thanks Monicker

---

