---
title: "basic mail server questions involving domain names"
date: 2009-01-27
forum: Server Platforms
---

### Post by whoop on 2009-01-27
I've had next to none experience with mail servers in general; so I have to very stupid questions (so bare with me).

1: If I want a local mail server which just sends and receives local mail, what domain do I use? In tutorials you see f.i. example.com, yourdomain.com, domain.com, example.local. These are off course examples. .local could be technically usable (is my guess) but it is not even supported by ubuntu cause it conflicts with avahi. So could anybody give me a real example?

2: If I was to use a real FQDN (like mynewmailsever.com) how would other users/providers/networks find my server? Is it like you have to provide a static IP address to the registrar where you got the domain name, and they add it to a main dsn server (just another guess)?

---

### Post by Maheriano on 2009-01-27
From what I understand from your question, you have 3 options:

1. Instead of using a domain, you could simply use your machine's IP but this isn't very efficient and hard to remember, especially if you expect other people to send you mail.
2. Register a domain name and point its name servers to your IP, costing you money for annual domain registration.
3. Go to a free registrar like [www.dyndns.com](www.dyndns.com) to get a free domain name and point it to your IP.

The domain registration will only work if your IP doesn't change or if you keep updating it when it does.

---

### Post by whoop on 2009-01-28
> **Maheriano said:**
> From what I understand from your question, you have 3 options:

1. Instead of using a domain, you could simply use your machine's IP but this isn't very efficient and hard to remember, especially if you expect other people to send you mail.
2. Register a domain name and point its name servers to your IP, costing you money for annual domain registration.
3. Go to a free registrar like [www.dyndns.com](www.dyndns.com) to get a free domain name and point it to your IP.

The domain registration will only work if your IP doesn't change or if you keep updating it when it does.

Thanks Maheriano, this answers some of my questions. I do have follow ups though :-(

1. If you would register a domain, who would link the IP to the domain 
name?
2. I would still like to see a real world example of a local FQDN.

---

### Post by Maheriano on 2009-01-28
> **whoop said:**
> Thanks Maheriano, this answers some of my questions. I do have follow ups though :-(

1. If you would register a domain, who would link the IP to the domain 
name?
2. I would still like to see a real world example of a local FQDN.

I don't know what a FQDN is but when you buy a domain name (or get a free one from dyndns), you can then log in and manage that domain. Here's an image of my control centre for my domain and the nameservers I have redirected them to:

[IMG]http://www.danmaher.com/images/Screenshot.jpg[/IMG]

I have it hosted (for now) somewhere remotely so I have to go to my hoster and ask them what their nameservers are. They told me the addresses are ns1.hostgo.com and ns2.hostgo.com. So I then log into my registrar (domain provider) and edit the domain to point to those nameservers. If you were hosting your own sites, you would enter your computer's IP here instead (what I'll eventually do).

---

### Post by ramsam on 2009-01-29
Hey Whoop,

Could you provide me with he steps to set up a mail server?
If you could direct me to a link which explains the entire procedure.

thanks,
ramsam

---

### Post by BlakeM on 2009-01-30
Hi,

I'm a bit of a noob like you. I want to be able to have my own email address like [email]example@example.com[/email]. I'm about to register a domain but I'm still reading up on it.

If you want to have your own mail server instead of using your ISPs or having it hosted elsewhere, here's a good Linux mail server howto: 

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Google Linux Mail server

---

### Post by whoop on 2009-02-10
> **ramsam said:**
> Hey Whoop,

Could you provide me with he steps to set up a mail server?
If you could direct me to a link which explains the entire procedure.

thanks,
ramsam
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by HermanAB on 2009-02-10
Here you go, it takes about 20 minutes to install Citadel:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

Cheers,

Herman

---

