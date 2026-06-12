---
title: "MX records on no-ip"
date: 2009-04-18
forum: Server Platforms
---

### Post by izziere on 2009-04-18
Hi all. I am able to use my qmail setup to send mail, but cannot receive due to DNS problems, I believe. I get the following information in the bounceback:

Sorry, I couldn't find a mail exchanger or IP address. (#5.4.4)

I am running Apache and qmail on the same machine. My webhost name is xyz.no-ip.org.  My server name is xyz, giving me qmail server address of xyz.xyz.no-ip.org  A nice snappy email address!!

Anyway, when I am adding the MX record on no-ip, should I be adding the server as xyz.xyz.no-ip.org or just xyz.no-ip.org?  Both are accepted, but both result in the same mail delivery failure.

I recognise it could be because the sending mail systems have DNS caches but am impatient, particularly as I am not sure which I should be using!

Many thanks

---

### Post by brianhenson on 2009-04-19
izziere, 

What I done in the past with no-ip is add the actual no-ip hostname as the mx record.  So as an example we will use the xyz.no-ip.com as the host.  On the server I would setup the domain to be xyz.no-ip.com and create my emails under that.  Once that is setup the host should be added to the no-ip servers so go and update the domain to have the same hostname as the mx record and wait a bit and try it out from gmail or other email service.  


Brian

---

### Post by FarehamWeather on 2009-04-19
do you need a payed account to do that ?

---

### Post by brianhenson on 2009-04-19
I cannot say for right now but when I did it, it was part of the free package.

---

### Post by izziere on 2009-04-20
> **brianhenson said:**
> izziere, 

What I done in the past with no-ip is add the actual no-ip hostname as the mx record.  So as an example we will use the xyz.no-ip.com as the host.  On the server I would setup the domain to be xyz.no-ip.com and create my emails under that.  Once that is setup the host should be added to the no-ip servers so go and update the domain to have the same hostname as the mx record and wait a bit and try it out from gmail or other email service.  


Brian

Bingo.  Thanks - you're a star

---

### Post by brianhenson on 2009-04-20
Glad I could help

---

