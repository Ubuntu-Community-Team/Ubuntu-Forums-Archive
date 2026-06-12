---
title: "is setting up your own home dns server legal?"
date: 2008-11-27
forum: The Cafe
---

### Post by EnGorDiaz on 2008-11-27
im doing it soon going to cost me some money though but thats not hard to get but guys free internet for me:P but hard to maintain

but my questions is this perfectly legal with all the craptacular companys out there reinacting two girls 1 cup with there customers

---

### Post by Comzee on 2008-11-27
Have you researched this? IPS own the Internets infrastructure. You have to route through their hubs to grab a WAN IP. I'm not saying there isn't a sophisticated hack that might be able to get you free internet, but you would have to bypass any initial host hubs to get to the infrastructure, not even sure if it's possible.

And in some crazy off chance that you actually bypassed an ISP and got onto the internet it would be illegal. Your using their infrastructure and bandwidth.

---

### Post by init1 on 2008-11-27
I've researched this before, and I believe you can, but I'm not sure it would do what you're thinking of.

---

### Post by mr.propre on 2008-11-27
I don't see why it would be illegal. It's useless for home users but not illegal. I only see one reason why you should use a local DNS server at home and thats for a website test environment. A company will probably only use a DNS server for some sort of intra net.

---

### Post by steveneddy on 2008-11-27
> **EnGorDiaz said:**
> im doing it soon going to cost me some money though but thats not hard to get but guys free internet for me:P but hard to maintain

but my questions is this perfectly legal with all the craptacular companys out there reinacting two girls 1 cup with there customers

It is legal to set up your own DNS server.

You will not receive **free** internet.

Everyone has to pay someone else for access to the backbone.

Your cable company or phone company run the service to your home and if you don't pay them for internet access, they shut you off and your pathway to the internet vanishes.

BTW - if you stopped and added some punctuation and correct grammar you post would be easier to read. Besides, it's what the cool kids are doing.

---

### Post by xpod on 2008-11-27
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

---

### Post by steveneddy on 2008-11-27
> **EnGorDiaz said:**
> I'm doing it soon! Going to cost me some money, though, but thats not hard to get. But guys, free internet for me:P! But hard to maintain.

But my questions is this:

**Perfectly legal with all the craptacular companys out there [COLOR=Blue]reenacting[/COLOR] two girls 1 cup with there customers?**
{what does that mean?}


See?

---

### Post by EnGorDiaz on 2008-11-27
well if i set it up correctly i might be able to get free internet its going to take me time but i will do it:P

---

### Post by v8YKxgHe on 2008-11-27
> well if i set it up correctly i might be able to get free internet its going to take me time but i will do it:P 

Simple answer, no - you wont. There is more to the Internet than DNS. DNS just translates a name into an IP address, so you don't have to remember random numbers to access, say, Google.

---

### Post by EnGorDiaz on 2008-11-27
> **steveneddy said:**
> It is legal to set up your own DNS server.

You will not receive **free** internet.

Everyone has to pay someone else for access to the backbone.

Your cable company or phone company run the service to your home and if you don't pay them for internet access, they shut you off and your pathway to the internet vanishes.

BTW - if you stopped and added some punctuation and correct grammar you post would be easier to read. Besides, it's what the cool kids are doing.

i see what your saying but hmmmm what i wanted to do is set up a gateway to the internet that will connect without me having an isp i make my own isp kind of crazy isnt it:P

---

### Post by mips on 2008-11-27
> **EnGorDiaz said:**
> i see what your saying but hmmmm what i wanted to do is set up a gateway to the internet that will connect without me having an isp i make my own isp kind of crazy isnt it:P

No, that is not possible unless you become an ISP and that will cost you more than being a normal isp user & have legal implications for you.

---

### Post by EnGorDiaz on 2008-11-27
> **mips said:**
> No, that is not possible unless you become an ISP and that will cost you more than being a normal isp user & have legal implications for you.
well hmm i might just set up the home network as i wanted to before maybe make a website but i will be still trying to do this well one day maybe i can make a way to do it but i might just set up a standard dns with secure connections (ipcop anyone)

---

### Post by steveneddy on 2008-11-27
> **EnGorDiaz said:**
> i see what your saying but hmmmm what i wanted to do is set up a gateway to the internet that will connect without me having an isp i make my own isp kind of crazy isnt it:P

So instead of paying an ISP for internet access, you will have to pay an upstream provider for access to the next level up on the internet, which is expensive.

There is no way that you will get free internet, legally, from your house.

Just because you get the internet at your home does not mean that the main gateway to the internet is in a box outside of your bedroom.

The gateway to the internet is in a large building in a city that is probably far away from you. 

You only pay to get on your ISP's network. 

The only way to get internet that you don't pay for yourself is to dial up a number with your modem that you know the user name and password for.

You will be able to host your own web page and serve files to the internet with your own DNS server, but there is not free internet, anywhere.

It's good to know that you are curious about these things, though. You may be the next ISP in your area. You never know. 

Set up your DNS server and play around with a web page and get into the nuts and bolts. Knowing that will make you a lot of money in the future.

---

### Post by Circus-Killer on 2008-11-27
you are a very stubborn man. again, you will not succeed. there is so much more to this. but from my lack of knowledge, i still know that isp's have to pay for not only access, but more importantly for the group of ip addresses that they use to assign to their customers.

ie. you would also have to pay for your ip addresses. but besides that, i am 99% sure you will not succeed at this. at least with your cost objectives (free). in my opinion, though my knowledge of this is extremely lacking, you will not succeed.

---

### Post by EnGorDiaz on 2008-11-27
> **Circus-Killer said:**
> you are a very stubborn man. again, you will not succeed. there is so much more to this. but from my lack of knowledge, i still know that isp's have to pay for not only access, but more importantly for the group of ip addresses that they use to assign to their customers.

ie. you would also have to pay for your ip addresses. but besides that, i am 99% sure you will not succeed at this. at least with your cost objectives (free). in my opinion, though my knowledge of this is extremely lacking, you will not succeed.

no my cost objective isnt "free" im experimenting on impulse i love trying new things out

---

### Post by eternalnewbee on 2008-11-27
> you are a very stubborn man. again, you will not succeed.
Stubbornness can be a very good thing, you know.... (nomyterysmileytochoose)

---

### Post by xpod on 2008-11-27
> AMD Athlon(tm) XP 899.219 MHz 256 KB, GeForce 7300 GT

Forgive me if i`m wrong but is`nt the 256KB(ram?) listed in your sig supposed to be 256MB??

---

### Post by eldragon on 2008-11-27
simply put: before even trying to understand what you want to accomplish, you will need to read a crapload of books about the subject :D

---

### Post by steveneddy on 2008-11-27
> **EnGorDiaz said:**
> no my cost objective isnt "free" im experimenting on impulse i love trying new things out

> **EnGorDiaz said:**
>  but guys free internet for me

OK

Good luck learning.

Most of the info you seek can be found on the internet.

---

### Post by FlyingIsFun1217 on 2008-11-27
> **xpod said:**
> Forgive me if i`m wrong but is`nt the 256KB(ram?) listed in your sig supposed to be 256MB??

It's probably something like the FSB.

And this thread looks like one of those thats on the FAIL blog.

FlyingIsFun1217

---

### Post by doorknob60 on 2008-11-27
> **xpod said:**
> Forgive me if i`m wrong but is`nt the 256KB(ram?) listed in your sig supposed to be 256MB??

I'm guessing L2 cache. Not positive though.

---

### Post by EnGorDiaz on 2008-11-27
ok guys my plan is this im getting an adls2+ voip plan im setting up the server and making a network im going to use ipcop on a copbox and other programs to mask and shield my ip adresses on my computers i will be setting up a website and making a dynamic dns i will set up a little isp like connection or emulate it

the hole point and challenge i want to do here is now emulate my own connection and let some ppl connect to my server safely yes it seems crazy

---

### Post by mr.propre on 2008-11-27
You know 'network management/manager' is an occupation, may I advice you to learn it. In most countries in Europe there allot of shortcomings in that sector and it's quite interesting. Because honestly, I thing you don't know what you are talking about and don't even know how the TCP/IP protocol works.

I did ICNA 1 (Cisco) and planning to go for the whole package after I get my degree in ICT-programming.

---

### Post by adaptr on 2008-11-27
> **EnGorDiaz said:**
> im doing it soon going to cost me some money though but thats not hard to get but guys free internet for me:P but hard to maintain

but my questions is this perfectly legal with all the craptacular companys out there reinacting two girls 1 cup with there customers

TRANSLATION:
> im doing it soon going to cost me some money though but thats not hard to getMoney not hard to get ? Okay.

> but guys free internet for meEhm.. you just said you HAVE money, why steal others out of their legitimate chance to sell you some consumer internet ?

> but my questions is this perfectly legalIs WHAT legal ? Being allowed onto the public internet with your level of ignorance ? I'd have to look that one up, but my first impulse would be "no".

---

### Post by adaptr on 2008-11-27
> **EnGorDiaz said:**
> i see what your saying
Trust me, you really, seriously don't. 

> but hmmmm what i wanted to do is set up a gateway to the internet that will connect without me having an isp i make my own ispYour lack of understanding of what an ISP is, or, indeed, what "the internet" is, is staggering beyond ken.

> kind of crazy isnt it:PThat's sort of the point I am making, yes.

---

### Post by collinp on 2008-11-27
> **EnGorDiaz said:**
> ok guys my plan is this im getting an adls2+ voip plan im setting up the server and making a network im going to use ipcop on a copbox and other programs to mask and shield my ip adresses on my computers i will be setting up a website and making a dynamic dns i will set up a little isp like connection or emulate it

the hole point and challenge i want to do here is now emulate my own connection and let some ppl connect to my server safely yes it seems crazy

Simple Answer: ISPs are massive. You are not going to be able to setup a ISP without a massively powerful internet connection, massive server clusters, and you have to *buy* the internet connection through one of the larger providers. Do not try it. Also, having your IP masked = no one being able to access your internet. Learn what a ISP really is and what a server really is. Plain and simple, what you want will not work.

P.S. Add some better grammar and punctuation into your posts so people can read it easier.

---

### Post by p_quarles on 2008-11-27
It's perfectly possible to create your own wide area network, but it requires owning the physical means of data transmission. No wires from one computer to the next, no network. In other words, it's possible but is completely unrealistic to expect it to go very far or very fast without an investment far beyond what even wealthy individuals are capable of.

Thread closed, as it has devolved into flaming.

---

