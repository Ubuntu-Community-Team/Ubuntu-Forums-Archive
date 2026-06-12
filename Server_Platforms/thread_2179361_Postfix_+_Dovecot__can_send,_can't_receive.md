---
title: "Postfix + Dovecot : can send, can't receive"
date: 2013-10-07
forum: Server Platforms
---

### Post by Malalo on 2013-10-07
Hi guys !
Wow it's been a long time.

So I installed a Ubuntu Server 12.04 so I can host my websites and I thought I'd also locally manage my e-mails for both my domains. Let's call them dom1.com and dom2.com and focus on dom1.com (I'll get back to dom2 later).
Apache2 works great and after reading a lot I setup everything to host both websites on separate virtual hosts and it's all A-Okay. 

Then I tried setting up Postfix. Now I knew at that time that my ISP blocks port 25 outbound (I didn't know it also blocked inbound). So I tried to use port 587 instead. It works if I use a relay at "smtp.myisp.net:587". Still, I'm quite happy it works. But I can't *receive* anything. I tried from my Hotmail and Gmail accounts to send an e-mail to *user@dom1.com* but Hotmail gives a failure after 48 hours and Gmail still hasn't shown anything yet but I haven't received anything either.
Does anyone know of an easy (and free) way to bypass this block on port 25 ? Because I'm sure Hotmail and Gmail are trying to reach my mail server on port 25...

I don't think it has to do with any config files on my server but I can post them if you wish. 

As for dom2.com, I'd like to have a "catch-all" address so than *anything*@dom2.com is redirected to [email]me@dom2.com[/email]. How do I do that ?

More info : 
- I'm using NO-IP since my ISP doesn't offer static IP addresses (so maybe something could be done with this). 
- I *could* use Gmail's services but I really want to host everything from my server at home.
- My router has port 25 opened and NAT'ed towards my server the same way as ports 80, 110 and 143 are. 
- From my LAN the command "telnet *servername* 25" shows "220 mail.dom1.com ESMTP Postfix (Ubuntu)"

---

### Post by Malalo on 2013-10-09
Updates :
- I saw that NO-IP  provides a service named "Mail Reflector", that can receive mails on port 25 and re-direct them to your mail server on whatever port you want. 40$/year/domain. So 80$ yearly just to receive e-mails... ugh...
- My ISP told me they could provide a VPN connection for my server, directly to their backbone. Therefore I could have all ports open and a static IP address. Free of charge. Only drawback, the VPN connection is somewhat shaky and can go down to about 25% banwidth for small periods of time. Should I take the risk ? I'd also have to start UFW I guess, since I'd have a direct WAN connection...

---

### Post by Malalo on 2013-10-15
I took the risk.
Closing thread.

---

