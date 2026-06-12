---
title: "[IPv6] Aren't we giving away too large IPv6 address blocks? (IPv4 problem, v.2?)"
date: 2010-05-27
forum: The Cafe
---

### Post by mgol on 2010-05-27
One of main reasons of the IPv4-exhaustion problem was a reckless strategy of providing large organisations and companies (like IBM) with Class A IP address blocks. One could think the same mistake won't happen again with IPv6 implementation.

Meanwhile, I got into the [Polish IPv6 Task Force site](http://www.pl.ipv6tf.org/wiki/index.php/Pule_adres%C3%B3w_sTLA_IPv6_w_Polsce) (English translation [under this link](http://translate.google.com/translate?js=y&prev=_t&hl=pl&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.pl.ipv6tf.org%2Fwiki%2Findex.php%2FPule_adres%25C3%25B3w_sTLA_IPv6_w_Polsce&sl=pl&tl=en)) where I saw that many large companies in Poland (like Aster City) was given blocks with 32-bit mask (if I think correctly, it gives them 2^96 = almost 8 * 10^28 addresses each) - quite a lot. One large company, Telekomunikacja Polska (Polish Telecom) even got a block with 21-bit mask!

Is there anything I don't see here or we're again being reckless?

---

### Post by McRat on 2010-05-27
I don't know much about TCP/IP, but I often wondered why they just didn't use two bytes (one source, one destination) in the header for COUNTRY field, and that way each country gets 4 billion addys.

There has always been extra room in the header.

But perhaps that would be too much like the telephone system and confuse people.

---

### Post by JDShu on 2010-05-27
> **mgol said:**
> 
Meanwhile, I got into the [Polish IPv6 Task Force site]("http://www.pl.ipv6tf.org/wiki/index.php/Pule_adres%C3%B3w_sTLA_IPv6_w_Polsce") (English translation [under this link]("http://translate.google.com/translate?js=y&prev=_t&hl=pl&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.pl.ipv6tf.org%2Fwiki%2Findex.php%2FPule_adres%25C3%25B3w_sTLA_IPv6_w_Polsce&sl=pl&tl=en")) where I saw that many large companies in Poland (like Aster City) was given blocks with 32-bit mask (if I think correctly, it gives them 2^96 = almost 8 * 10^28 addresses each) - quite a lot. One large company, Telekomunikacja Polska (Polish Telecom) even got a block with 21-bit mask!

Is there anything I don't see here or we're again being reckless?

I did a quick calculation and in order to use up all the IPv6 addresses if each company uses 2^96 addresses, then we'll need about over 4.2 billion companies. Now I have no idea how many large companies there are in the world, but my bet is that we don't have that many.

---

### Post by mgol on 2010-05-27
> **JDShu said:**
> I did a quick calculation and in order to use up all the IPv6 addresses if each company uses 2^96 addresses, then we'll need about over 4.2 billion companies. Now I have no idea how many large companies there are in the world, but my bet is that we don't have that many.

Some of them are given more like this mentioned Polish Telecom.

Anyway, I can think about future different IP addresses usage than the usual computer/mobile internet connection. Maybe this number is unreachable, but still - why any company in the world would need 2^96 addresses or at least anything a bit close to that number? I though the whole point of IPv6 was to maximize the number of free addresses as much as possible. I don't think any company in the world would need more than 2^32 addresses, even giving them 2^64 would be a lot too many and in this case we would need 2^64 companies to feel this up; this **is** an unreachable number.

---

### Post by JDShu on 2010-05-27
Indeed, it seems unnecessary, I agree. But I don't think we'll have a problem with address shortages for a long time. By then, I guess we'll be switching to IPv8 :P

---

### Post by exodus_ on 2010-05-27
I came across an interesting site that explains it in terms of how many possible addresses there would be in "plain numbers"

> 
[DevDevin]("http://http://geekswithblogs.net/devdevin/archive/2008/03/25/120750.aspx")How many IP addresses does IPv6 support? Well, without knowing the exact implementation details, we can get a rough estimate based on the fact that it uses 128 bits. So 2 to the power of 128 ends up being 340,282,366,920,938,000,000,000,000,000,000,000,000 unique IP addresses.


That's a whole lot of address space!

[Here is my source]("http://http://itknowledgeexchange.techtarget.com/whatis/ipv6-addresses-how-many-is-that-in-numbers/")

---

### Post by mgol on 2010-05-27
> **JDShu said:**
> Indeed, it seems unnecessary, I agree. But I don't think we'll have a problem with address shortages for a long time. By then, I guess we'll be switching to IPv8 :P

The whole point is so that we _never_ have to switch again (at least not before leaving the Earth ;)). 2^128 adresses means 6,7e17 addresses per mm^2 of Earth surface - I don't think we will ever reach such minimization. ;)

Giving away such large blocks may, however, result in the need to switch again.

---

### Post by mgol on 2010-05-27
> **exodus_ said:**
> I came across an interesting site that explains it in terms of how many possible addresses there would be in "plain numbers"



That's a whole lot of address space!

[Here is my source]("http://http://itknowledgeexchange.techtarget.com/whatis/ipv6-addresses-how-many-is-that-in-numbers/")

Once You discover companies that will have trouble having 2^24 clients get 2^96 address blocks, instead of:
340 282 366 920 938 463 463 374 607 431 768 211 456
You get:
72 057 594 037 927 936
A bit less. That being, counting 2^128 as the number of potentially available addresses seem like a lie - again, overwhelming majority of them will be made unusable.

---

### Post by BoneKracker on 2010-05-27
The answer is, "no, we're very probably not giving away blocks that are too large".

I actually sat down and did the math once.  Then I tried to find a way to express how large the IPv6 address space is, in a way that people could actually grasp it.  Here goes:

There is so much IPv6 address space that every human that will be living on the planet in 2030 could have their own personal address space the size of the present-day Internet.

In fact, I vaguely recall that it was more like "... their own personal address space 1x10^25 as large as the present-day Internet).  Somebody can do the math and correct me (just do it right).

I remember trying to conceive of a computing paradigm that could exhaust this address space, and the only thing I could think of would be some kind of grid-computing that actually required each memory location to have it's own unique network address.

So, I don't think they are being reckless.  On the contrary, I think people are going to have to get over their deep-seeded conception of network address space as a constrained resource.

---

### Post by aklo on 2010-05-27
Not very sure about IP v6...but they maybe using some "subnetting" which you cannot see simply from the ip address given....

---

### Post by mgol on 2010-05-27
> **BoneKracker said:**
> There is so much IPv6 address space that every human that will be living on the planet in 2030 could have their own personal address space the size of the present-day Internet.

In fact, I vaguely recall that it was more like "... their own personal address space 1x10^25 as large as the present-day Internet).  Somebody can do the math and correct me (just do it right).

If we assume all 2^128 addresses are available and that they will be about 10 000 000 000 people in 2030, then each of them will be able to have more than 8e18 (8 * 10^18) block sized as full IPv4 range. If we assume that companies which obtained 2^96 addresses are able to use at most 2^24 of them, each of them will get "only" 0,16% of IPv4 range (a bit over 7 mln per person).

Maybe I am exaggerating but numbers provided in articles like one of mentioned above are hardly close to reality with such distribution.

---

