---
title: "email server setup help question"
date: 2010-10-22
forum: Server Platforms
---

### Post by rcayea on 2010-10-22
Hey everyone,

I had emailed my domain hosting company asking them to help me set up my email server so that I would control/handle email.

Lets say my hosting company is called hosting1

I bought a domain and ip address through hosting1 

When I asked them to help setup the email server they sent me this question:

"Please let us know the IP/host to point your MX record to (this would be the address of the email server you have created)"



My question is, can I respond and say use my ip address I bought through hosting1 or do they want me to give them another static ip address (maybe one I would have to purchase through my ISP???)

I am not sure because I already use the hosting company's webmail for my email.

Thanks,
Randy

---

### Post by rcayea on 2010-10-23
Bump. Thanks.

---

### Post by paulsp on 2010-10-23
You have several options to handle e-mail. Basically:

[LIST]
[*]Use the server of the provider where your website is hosted.
[*]Use an external service, like Google Apps
[*]Set up an e-mail server on your own always-on computer (either at home/office, or at a rented server hosting provider).
[/LIST]
What is your plan / situation? If you want to use 'your own' e-mail server, then you need the actual computer that is going to host this. Or do you have this already?

---

### Post by rcayea on 2010-10-23
Thanks for the help.

My plan is to be able to set up my own email "service" I guess I would call it. Something where myself and my friends/relatives can have email accounts. I want to do this for security and just plain old fun. 

Right now my webhosting company does have email service but my friends and family, when they create accounts, have to tell me the password. I want to setup where it is like gmail or yahoo for example. Someone can just log on and create an account and for security I won't know everyones account info/password. 

I do have Ubuntu Server on a stand alone box. Right now all I have on it is samba and I am sharing files throughout my home with it. It is working well, minus, the typical issues - but that is way off point.

What you are saying is I would need to purchase an additional IP address from my ISP?

---

### Post by SeijiSensei on 2010-10-24
An MX record is a type of DNS entry that tells SMTP servers where to send mail for a domain.  This machine must be publicly visible and have an SMTP listener on port 25.  Best practice requires that the server have a static IP address with matching forward and reverse DNS resolution as well.  (If mail.example.com points to 192.168.1.1, then 1.1.168.192.in-addr-arpa must point back to mail.example.com.)

If your machine is behind a firewall, you'll need to set up forwarding of port 25 to your server.

---

