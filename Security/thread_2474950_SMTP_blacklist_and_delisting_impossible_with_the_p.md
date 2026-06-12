---
title: "SMTP blacklist and delisting impossible with the postmaster"
date: 2022-05-12
forum: Security
---

### Post by gigi1335 on 2022-05-12
Hello,

On a mail server, I have messages to @bigpond.com recipients that remain in the queue. Indeed, from my server, if I try to connect to the MX of bigpond.com, I have :

```
$ telnet extmail.bigpond.com 25
Trying 203.36.172.106...
Connected to extmail.bigpond.com.
Escape character is '^]'.
550 5.7.1 Connection refused - IB115. 51.159.156.147 is blacklisted. If you believe this to be in error, please contact [email]postmaster@bigpond.com[/email]
Connection closed by foreign host.
```

I have contacted [email]postmaster@bigpond.com[/email] and [email]postmaster@telstra.com[/email] (the host of bigpond.com) for a delisting request but I have no answer for 1 week.

1) Do you know how to proceed in this kind of situation?

2) does the code IB115 have a known meaning ?

3) is there a French or English forum concerning postmaster questions and in particular around blacklisting problems?

Thank you in advance for your help.

Gilles

---

### Post by TheFu on 2022-05-12
The bigpond email admin team has complete control.  I've been blocked once but also routinely block subnets due to spamming.

I also block 51.158.0.0/15 from email after receiving hundreds of spam messages from there. I won't unblock it, regardless of the request.  
In short, get a better host than Scaleway. One that doesn't allow spammers to thrive.

---

### Post by gigi1335 on 2022-05-13
Hello and thanks a lot for your answer.

I understand your position to protect your users from spam and we are trying our best to do the same thing. However, our 2 SMTP IPs are really clean and secured as you can see at [https://multirbl.valli.org/lookup/51.159.156.147.html](https://multirbl.valli.org/lookup/51.159.156.147.html) and [https://multirbl.valli.org/lookup/51.159.52.96.html](https://multirbl.valli.org/lookup/51.159.52.96.html).
In fact, Scaleway had problems with spam few days ago and IP subnet was blocked by UCE Protect Level 3 but it is no more the case. Futhermore, Scaleway has reacted to make spam to stop each time there were an attack. At least, could you please delist our 2 IP since we are not responsible of other IPs and since it is not easy to change of hosting provider ?

Thanks in advance for your comprehension.

Gilles

---

### Post by wildmanne39 on 2022-05-13
> At least, could you please delist our 2 IP since we are not responsible of other IPs and since it is not easy to change of hosting provider ?
You are able to post on the forum so your IP address is not blocked here unless you are using a VPN or proxy to get around your IP address being banned here but I do not believe that to be the case, I checked with an outside source and your IP address has no hits as being toxic or having spam associated with it but TheFu was referring to his personal server as IP addresses that he blocks and has nothing to do with the forum, if you have an issue your IP provider you need to take it up with them and please do not post there name or links to them or anything of the such that may be considered spam.:o

---

### Post by TheFu on 2022-05-13
> **wildmanne39 said:**
>  I checked with an outside source and your IP address has no hits as being toxic or having spam associated with it but TheFu was referring to his personal server as IP addresses that he blocks and has nothing to do with the forum 

Exactly, but if the spam was sufficient for me to notice on my 20 little domains, it must have been really bad.  

My stance on spam and email handling follows ... 

I don't have the exact date when the block was entered, but it was 1-2 yrs ago and just for SMTP, not web or any other protocols. I just checked.  My email gateway blocks a number of TLDs completely just because of the spam amount from those and that I don't expect to ever get any useful email from any systems using those TLDs.  I can do that with very little real risk of missing important communications, ISPs cannot.

I block email and web traffic separately.  Sending lots of spam email results in a block for the entire subnet.  Attacking my websites sufficiently (usually through obvious, automatic, methods), gets the attacking IP subnet blocked.
There are 380 subnets blocked for spam.
There are 7000+ subnets blocked for website attacks. Some are /8 (5) and /10 (25) areas of the internet. Those are huge blocks, generally originating in countries known for illegal system attacks.

Reputation matters.  Large providers have a very difficult task, since they have thousands and thousands of people to trust not to spam the world. The best blocklists are dynamic.  A few times, I've seen gmail blocked for a few hours with a dynamic blocklist, so everyone gets put on them from time to time.  I bet when that happened, the gmail spam team was all woke up and started figuring out who offended.

I run tiny domains - that are fairly niche.  Most of my domains just provide information and aren't commercial. There's little need for any email contact, though the 5 expected addresses are handled.  I dislike spam with a passion. One of my domains was blocked by a regional ISP for 5 yrs. I had a business at the time, but wasn't able to email 80% of my customers.  Initially, I tried to get my IP removed every month for 2 yrs, then I gave up.  The solution was to use a paid email forwarding provider.   I just looked, I have whitelisted about 20 email domains.  They could spam me, relentlessly. I know the people running those domains personally, so if that happens, I can pick up the phone and talk with them.

OTOH, I cannot think of any good reason to allow .buzz or .click domain emails, so I don't. I'm seeing next to zero spam these days. At least if there is a blocked message, the sender is told and if they have a legitimate purpose, they can call and leave a message. If they don't have a phone number or won't leave a compelling message, too bad. My email servers and phone lines don't need to support their marketing desires.

Most of the large ISPs have an automated website to get delisted from their spamming block list.  The same applies for Spamhaus. [https://www.spamhaus.org/pbl/removal/](https://www.spamhaus.org/pbl/removal/) That's where I'd spend my time.

---

### Post by gigi1335 on 2022-05-17
Thanks all for your answers. 

Sorry but I still don't understand why 2 IPs where SMTP is secured like ours (as you can see at [https://multirbl.valli.org/lookup/51.159.156.147.html](https://multirbl.valli.org/lookup/51.159.156.147.html) and [https://multirbl.valli.org/lookup/51.159.52.96.html](https://multirbl.valli.org/lookup/51.159.52.96.html)), why they are blocked since its entire subnet is blocked since some subnet neighbors have got spam in the past (like 51.158.0.0/15 subnet).

I have contacted [EMAIL="postmaster@bigpond.com"]postmaster@bigpond.com[/EMAIL] and [EMAIL="postmaster@telstra.com"]postmaster@telstra.com[/EMAIL] (the host of bigpond.com) for a delisting request but I have no answer for 2 weeks.

1) Do you know how to proceed in this kind of situation?

2) does the code IB115 have a known meaning ?

3) is there a French or English forum concerning postmaster questions and in particular around blacklisting problems?

Thank you in advance for your help.

Gilles

---

### Post by SeijiSensei on 2022-05-17
Blocking entire subnets because of bad behavior by some neighbors is pretty common I think. I've had issues with a mail server on Linode being refused by some providers solely because of its IP address, even with SPF and DKIM implemented. In one case it was because a bad actor had used the IP before it was assigned to me. Have you considered simply asking your provider to change your IP address? You're more likely to resolve this problem on your end rather than expecting bigpond to respond to you.

Have you looked up your IP addresses at places like mxtoolbox.com? You might get some clues.

---

### Post by gigi1335 on 2022-05-18
Thanks for your answer.

In fact, changing IP with my provider will not solve the problem since it is entire subnet and even sometimes AS which are blocked.

I checked : [https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3a51.159.156.147&run=toolpage](https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3a51.159.156.147&run=toolpage) and the IP is not in any blacklist. No problem also here : [https://multirbl.valli.org/lookup/51.159.156.147.html](https://multirbl.valli.org/lookup/51.159.156.147.html) (even with the FCrDNS Test)

Are there other free checks at mxtoolbox I have to do ? When I click on "Solve Email delivery problem", I am redirected to [https://mxtoolbox.com/c/products/deliverycenter?source=toolhandler-dmarc](https://mxtoolbox.com/c/products/deliverycenter?source=toolhandler-dmarc) which advertise  MxToolbox Delivery Center" which costs $129 per month...

Thanks in advance for your help.

Gilles


> **SeijiSensei said:**
> Blocking entire subnets because of bad behavior by some neighbors is pretty common I think. I've had issues with a mail server on Linode being refused by some providers solely because of its IP address, even with SPF and DKIM implemented. In one case it was because a bad actor had used the IP before it was assigned to me. Have you considered simply asking your provider to change your IP address? You're more likely to resolve this problem on your end rather than expecting bigpond to respond to you.

Have you looked up your IP addresses at places like mxtoolbox.com? You might get some clues.

---

### Post by CharlesA on 2022-05-18
> **gigi1335 said:**
> Thanks for your answer.

In fact, changing IP with my provider will not solve the problem since it is entire subnet and even sometimes AS which are blocked.

I checked : [https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3a51.159.156.147&run=toolpage](https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3a51.159.156.147&run=toolpage) and the IP is not in any blacklist. No problem also here : [https://multirbl.valli.org/lookup/51.159.156.147.html](https://multirbl.valli.org/lookup/51.159.156.147.html) (even with the FCrDNS Test)

Are there other free checks at mxtoolbox I have to do ? When I click on "Solve Email delivery problem", I am redirected to [https://mxtoolbox.com/c/products/deliverycenter?source=toolhandler-dmarc](https://mxtoolbox.com/c/products/deliverycenter?source=toolhandler-dmarc) which advertise  MxToolbox Delivery Center" which costs $129 per month...

Thanks in advance for your help.

Gilles

Hi,

I used this site to get my DKIM/SPF/DMARC junk set up for my domains - or at least to test it to make sure it's set up correctly.

[https://www.learndmarc.com/](https://www.learndmarc.com/)

I don't know if that's your issue (and likely isn't, based on the error returned when you used telnet), but it might be a place to start.

---

### Post by SeijiSensei on 2022-05-18
> In fact, changing IP with my provider will not solve the problem since it is entire subnet and even sometimes AS which are blocked.

You need a new provider. Try [Linode](https://www.linode.com/).

---

### Post by gigi1335 on 2022-05-19
Thanks again for all your answers. One unanswered question : is there a **forum concerning** **postmaster questions** and in particular around blacklisting problems and IP reputation ?

Thanks in advance for your help.

Gilles

---

### Post by gigi1335 on 2022-06-03
I finally obtained delisting from own blacklist of [email]posmaster@bigpond.com[/email]. Thanks all for your answers !

---

