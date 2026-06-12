---
title: "Point a domain to my server"
date: 2009-03-29
forum: Server Platforms
---

### Post by timboellis on 2009-03-29
I have ubuntu just installed I also have a domain of [www.mydomain.co.uk](www.mydomain.co.uk)

All I want is for the e-mails to continue pointing towards my current server / hosting company however I want my [www.mydomain.co.uk](www.mydomain.co.uk) to point towards my Ubuntu server on my static ip 1.2.3.4 the domain is registered through 123reg.co.uk any help at all?

---

### Post by hyper_ch on 2009-03-29
well, you say you have a static IP. Do you have a static public IP?

Then can you set dns info  at 123reg.co.uk like a entries, c entries, mailserver entries?

---

### Post by dacorr on 2009-03-29
if the IP is dynamic then you will need to use DDNS, dyndns.org is one of many that provide it.

---

### Post by timboellis on 2009-03-29
> **hyper_ch said:**
> well, you say you have a static IP. Do you have a static public IP?

Then can you set dns info  at 123reg.co.uk like a entries, c entries, mailserver entries?

Yes it is a static WAN address and LAN address, 

So am i right in saying that i need to set my name servers to 123reg.co.uk in the first instance then set the www A name in DNS to my IP?

Then do i set the IP of my current server on the @ A name on DNS then my mail will still work through my other host?

---

### Post by hyper_ch on 2009-03-29
well, if you have a static IP then you have one problems less to worry about.

Now, can you use your domain registrars nameservers to create the a (et al.) records? If not, have a look at [http://www.everydns.net](http://www.everydns.net) - I use that on two small enterprises servers. That works fine. You can set all the things there.

So once you have set the nameserver entries correctly, then you'll just need to forward port 80 (http) and other (e.g. 22 for ssh) from your modem/router to your actual server.

And then you'll just need to wait a bit until the dns entry has propagated... should take less than 24h.

You can set multiple mailserver entries with different priorities. By default it will try the one with the highest priority and if that's not available go down the ladder. So you can still point the mail server entry to your other host however you must ensure that your other host still accepts mail for that domain name.

---

### Post by timboellis on 2009-03-29
> **hyper_ch said:**
> well, if you have a static IP then you have one problems less to worry about.

Now, can you use your domain registrars nameservers to create the a (et al.) records? If not, have a look at [http://www.everydns.net](http://www.everydns.net) - I use that on two small enterprises servers. That works fine. You can set all the things there.

So once you have set the nameserver entries correctly, then you'll just need to forward port 80 (http) and other (e.g. 22 for ssh) from your modem/router to your actual server.

And then you'll just need to wait a bit until the dns entry has propagated... should take less than 24h.

You can set multiple mailserver entries with different priorities. By default it will try the one with the highest priority and if that's not available go down the ladder. So you can still point the mail server entry to your other host however you must ensure that your other host still accepts mail for that domain name.
Okay thanks for that signed up changed my name server but stuck where it is asking for 

Add a record:
Fully Qualified Domain Name: 	
Record Type: 	
Record Value: 	
If MX Record, MX Value:

---

### Post by hyper_ch on 2009-03-29
ok, first make an a record

A means it points to an IP.

so make an A entry and use as FQDN   yourdomain.com   and as ip your public static wan addres.

Then make a CNAME entry and use as FQDN "www.yourdomain.com" and as record value "yourdomain.com"

And finally make a mx entry. You can use as FQDN "yourdomain.com" or "mail.yourdomain.com" (but I'd go for the first one). Select this thime "MX" and enter the domain to where it shall go e.g. "yourdomain.com" or "yourotherisp.com". As priority you can enter different values there. The lower the value the higher the priority in the check

---

### Post by BkkBonanza on 2009-03-29
If you want to keep your mail going to their current location then don't alter the records for email. Just add an A record for your name/ip and a CNAME record for www. For these two resord types MX doesn't matter. 

There are plenty of tutorials around about setting domain records and what the different types mean. There is likely a tutorial on your domain registrar or use google, it's faster than asking questions here.

---

### Post by windependence on 2009-03-30
To do this you just want to point your A record and CNAMEs at your server, and keep your MX records (for mail) pointed at your current e-mail host. Simple as that.

-Tim

---

