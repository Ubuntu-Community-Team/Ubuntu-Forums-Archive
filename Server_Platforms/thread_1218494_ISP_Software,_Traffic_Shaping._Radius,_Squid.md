---
title: "ISP Software, Traffic Shaping. Radius, Squid"
date: 2009-07-20
forum: Server Platforms
---

### Post by esz on 2009-07-20
Hi,

sorry for my bad english. I am planing to start an ISP busines and deliver Internet via WIFI to the villages around my house. I need a little help on that. I have very good experience with Ubuntu on desktops, so i will give it a try on a server. I need a litle advise about Radius software.

Can someone give me a direction where i can find some informations on ISP software. As mentioned in the title i am interested in three - four services running on the server.

1. RADIUS via WIFI
2. Bandwith managment and in adition packet shaping if the bandwith exceeded my internet link.
3. Very agressive Proxy server.
4. FTP
5. Any sugestions


Thank you for your help.

---

### Post by samcamfilms on 2009-07-20
Use mikrotik.

If ya broke use pfsense

---

### Post by dragos2 on 2009-07-21
> **esz said:**
> Hi,

sorry for my bad english. I am planing to start an ISP busines and deliver Internet via WIFI to the villages around my house. I need a little help on that. I have very good experience with Ubuntu on desktops, so i will give it a try on a server. I need a litle advise about Radius software.

Can someone give me a direction where i can find some informations on ISP software. As mentioned in the title i am interested in three - four services running on the server.

1. RADIUS via WIFI
2. Bandwith managment and in adition packet shaping if the bandwith exceeded my internet link.
3. Very agressive Proxy server.
4. FTP
5. Any sugestions


Thank you for your help.

You need a server with 2 nics, one wireless and one normal (choose quality ones).

You can:
1. Buy no IP and set NAT
2. Buy an IP range and use router.

1. Don't know that.
2. Squid or Varnish + network utilities like ntop, ngrep, tcpdump, ISPConfig
3. ? Do you know what is that ? You mean cache server ?
4. You can set one fast with Ubuntu.

---

### Post by esz on 2009-07-22
Thank you. I will start working on that and post my experiencie here.

> 3. ? Do you know what is that ? You mean cache server ?
Yes. A chache proxy like squid. I did not know that squid can do bandwith managment.

I was thinking about freebsd, but i see that the ubuntu community is mutch more freindly. My choice is ubuntu now.

---

### Post by dragos2 on 2009-07-22
> **esz said:**
> Thank you. I will start working on that and post my experiencie here.


Yes. A chache proxy like squid. I did not know that squid can do bandwith managment.

I was thinking about freebsd, but i see that the ubuntu community is mutch more freindly. My choice is ubuntu now.

Yes Squid can do that. You can try varnish too - it performs better - some ISP's changed
to varnish now.

---

### Post by esz on 2009-07-22
> Use mikrotik.

If ya broke use pfsense

hej samcamfilms. pfsense looks realy nice. Do you have some experience on that, that you could post here? 

Regarding mikrotik. I dont know the prices for the microtik devices. It looks expencive. What are the benefits of mikrotik? What devices could i buy?

Maybe i forgot to mention that i want to make the internet as cheap as possible for the people around me. Here are villages and there is no broadband for them. I have to spend a lot of money for wifi antennas and the peaople here are not rich.

Maybe someone has experience on that what are cheap and damn good antennas or how to make own one. I dont want to use one antenna per client..

---

### Post by chadk5utc on 2009-08-07
With wireless signals you are dealing with 2.4Ghz(this is considered microwave) typically. Range depends a lot on having clear "Line of Sight" because the frequency is so high. Quality antennas are Key to success for many reasons. Trying to build an antenna for this frequency range is possible for some one with experience and necessary knowledge in this type of design but for most people its easier to just buy antennas and my reason for saying this is:
1. High SWR on an antenna = Shorter Range
2. High SWR on an antenna = Signal Loss Very Fast
3. High SWR on an antenna = Shorter Life Expectancy of Wireless card 
4. your not likely to be able to build an antenna with the same quality and gain as one thats commercially made, approximately $60.00 (US) for 15-20db gain 120 degree Sector antenna 
5. The greater the distance between the actual wireless transmitter and the antenna also = Signal Loss this is why commercial high gain antennas are worthwhile
6. 1 Antenna per Client makes it much easier to regulate who can access your service (unless your giving it away)

Some one earlier mentioned MikroTik and I would agree that you should at least look into it or others as viable options for a commercial Access Point and then some type of compatable wireless card for the customers

  Hopefully this helps a little

---

