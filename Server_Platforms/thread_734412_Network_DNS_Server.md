---
title: "Network DNS Server"
date: 2008-03-24
forum: Server Platforms
---

### Post by Dr Small on 2008-03-24
I have Bind9 installed on my server along with Webmin which I thought may help in assisting me understand it, but it has not.

I would like to create domains (for LAN only) that each network computer can connect to the DNS server and fetch the domain. But the configuration seems confusing and can't really figure out how to make the domains point to an IP address.

Any information would be greatly appreciated :)

Dr Small

---

### Post by ikonia on 2008-03-24
your doing this the right way by just using dns for internal domain resolution if your new to it, kudos to you for approaching it well.

The best thing I can advise is the oreilly bind book, it's an excellent book no questions of it, bind/dns is a big topic and very individual/network specific, so to walk someone through it would be quite interactivce.

---

### Post by Dr Small on 2008-03-24
Thanks for the recommendation, but is there any other guides out there that I could perchance read for free? I am sure there is, but probably not as detailed as that book is, I am sure.

Probably if I just understood the concept of how it all worked (from behind the curtain) and saw a few examples on how to setup a network domain for the DNS server, I would be good to go :)

I just started using OpenDNS, so in aroused my interest again once more in DNS for the network :D

Dr Small

---

### Post by Dr Small on 2008-03-24
Ok, so I have figured most of it out on my own while in Webmin and have setup a private domain that I can reach and so can my sister's machine on the local network. I have that down honky dory.

Now my next question,
Let's say that I setup all the machines on the lan to use the network DNS server, and each machine can fetch the private domains and reach the destination. But let's say the attempt to reach ubuntuforums.org. I want them to pass thru opendns.org as the outside DNS server if the domain is not a local one.

In Webmin I see "Other DNS Server" and I added the 2 OpenDNS IP addresses into it, restarted bind, yet when I go to ubuntuforums.org, it is not passing thru OpenDNS.

The question is, Why? ... and how could I make it do it?

Dr Small

---

### Post by Mr. C. on 2008-03-25
Programs on your system will use low-level resolver libraries, which will in turn use the DNS server specified in your /etc/resolv.conf file.

If you are running your own DNS server, it can resolve names for your private zones, and forward requests for everything else to another remote DNS server.  This is not the same as adding a secondary name server to the resolv.conf resolver configuration file (eg. used only if / when the primary server is unreachable and queries time out).

So you need to configure your DNS server to be authoritative for *your zones*, but to forward requests offsite for all other requests.  Review Forwarding here:

[http://www.isc.org/sw/bind/arm93/Bv9ARM.ch01.html#id2546254](http://www.isc.org/sw/bind/arm93/Bv9ARM.ch01.html#id2546254)

Note that your DNS server will cache results, so that forwarding will not take place once an entry is cached (until the record expires).

I can't give you help re: Webmin, as I don't use it.  I work on the raw configuration file and zone files directly.

---

