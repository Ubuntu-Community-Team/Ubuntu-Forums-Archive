---
title: "Server is working, but i need some advice"
date: 2013-01-23
forum: Server Platforms
---

### Post by nightfly13 on 2013-01-23
Dear community...
 
I have my hosting server working...
 
On my domain registar i add an A Record and now everithing and my both sites are working, but i still having my dinamic IP's on A Recorrds.... So, for what i know i must use an thirdparty service to avoid the sites go offline when my dynamic IP change....
 
What you advice??? DynDns (payed), no-ip or other????
 
On the A Records on Domain registar, when i add one more A Record, i need to set there my own external IP, so, my external IP is dynamic, so one of my questions is, when i subscribe a service on DynDNS or no-ip they gave me any IP adrres to use when i setup an A record on my domain registar???? Or i must still using my dysnamic external IP??? How this works???? Can you give me some help to clarify this doubts???
 
Best Regards
João

---

### Post by spynappels on 2013-01-23
DynDNS will allow you to select a domain name which they will always resolve to your current IP. You should be able to use the domain name in your A records.

---

### Post by nightfly13 on 2013-01-23
I have 3 site to host in one server, should DynDNS Pro [http://dyn.com/dns/dyndns-pro/](http://dyn.com/dns/dyndns-pro/) enought ???? I'm looking for advice because i don't know this kind of services, and i don't want subcribe a useless service for my needs...
 
 
Best Regards
João

---

### Post by nightfly13 on 2013-01-23
I have 3 site to host in one server, should DynDNS Pro [http://dyn.com/dns/dyndns-pro/](http://dyn.com/dns/dyndns-pro/) enought ???? I'm looking for advice because i don't know this kind of services, and i don't want subcribe a useless service for my needs...

Free no-IP service had the same features and service proposes????

Best Regards
João

---

### Post by spynappels on 2013-01-23
You only need one to point to your Dynamic Public IP, and use that domain name in the A records for each of your websites.

---

### Post by nightfly13 on 2013-01-23
Ok... Thank you very much for your reply and support....
 
**Only one more question...**
[COLOR=black][FONT=Tahoma]On this moment, and to have my 2 sites working i add an A Record like you told me, i already do that!!! ... But the problem is, when i add an A Record, is asking me for an IP in this moment i had my dynamic IP from my home, so, adding for example the domain name of no-IP (I Already create) i need the IP of that domain created by me on no-IP, that’s right???? How can i know the IP of that domain name previous created on no-IP??? Ping the no-IP domain name???? Is the IP result of pinging no-IP domain name previously created, the necessary IP to add on my domain name registrar when i add an A Record????[/FONT][/COLOR]
 
 
Best Regards
João

---

### Post by spynappels on 2013-01-24
Hmm, ok, I see what's happening there.

What you should do there is create a CNAME record for www.<<your-domain>> and add the No-IP domain name there. I think you can leave the A record blank.

---

### Post by nightfly13 on 2013-01-25
It's working, both sites... The cnames solve me the problem... 
 
Now i'm gessing i will have some more fights with ftp, mail and Create a DNS nameserver... But 1 step at each time ;)
 
Thank you very much for your help
 
Best Regards
João

---

