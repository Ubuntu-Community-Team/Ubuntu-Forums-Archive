---
title: "Should my dns server be detected on the interent?"
date: 2010-07-07
forum: Server Platforms
---

### Post by mattc9305 on 2010-07-07
I have got a free domain from 'dyndns.com' which is xxxx.dyndns.org.  I have set up a dns server so that within the network "[www.xxxx.dyndns.org]("http://www.xxxx.dyndns.org")" is a webpage that I have set up.  However if I try this using an external connection the webpage isn't found.  When I change the web page to simply "xxxx.dyndns.org" the webpage works fine.  
 
Should this be this way or should my dns server be able to redirect the traffic that is coming into my network eg. [http://*something*.xxxx.dyndns.org.](http://*something*.xxxx.dyndns.org.)
 
Thanks.

---

### Post by scanzano on 2010-07-07
I'm not quite sure I understand your question to the full extent but I am guessing there has to be some kind of static route that has to be implemented. Sorry if that doesn't help you.

---

### Post by mattc9305 on 2010-07-07
Thanks, but I mean if I have the dns server set to direct [www.xxx.dyndns.org]("http://www.xxx.dyndns.org") to say 192.168.1.6.  This works within the network, but if I try this externally the webpage isn't found.

---

### Post by restorator on 2010-07-07
**WWW.**xxx.dyndns.org is actually a different address than xxx.dyndns.org 
Even though "WWW" is commonly used on the net it is not necessarily the same domain anymore than blah.xxx.dyndns.org is. On your server you have to edit your apache configs to alias www (or * for anything) AND you dyndns settings to the domain you are using (xxx.dyndns.org)

---

### Post by mattc9305 on 2010-07-07
Thanks for the info! ;)

---

### Post by mattc9305 on 2010-07-07
But when purchasing a domain name you can apply for secondary dns, what sort of primary dns server would you need if not using their primary dns?
 
If I have a www A record set up on my dns server, a www alias in apache and xxxx.dyndns.org is being directed to that dns server then why shouldn't it work?

---

### Post by restorator on 2010-07-08
You are using Dyndns services for your DNS for this domain (xxx.dyndns.org, which is already an alias of dyndns.org) therefore your www entries need to be made at the root dns server, which in this case is dyndns if they allow that. 

By the way, if you were running your own functional dns server you would need to have at least two static IP's setup with your root nameservers and those entries where the domain is registered. As you are using dyndns this does not appear to be the case. 

For the most part, unless you are running several servers and a lot of hosting it is really not neccessary to use your own nameservers anymore, and if you dont fully understand what you are doing it is really not advisable. I usually use godaddy, (where my domains are purchased) for my dns services as they are pretty darn reliable and fast (I would never use them for hosting though, thats quite unreliable) and I just point them to wherever I have them hosted. Then I have my local computers network connections DNS settings to the opendns servers, and with this setup when I make a change in the records it usually propogates within a few minutes. With that reliaibity why would I want to bother with my own and the risks involved anyway?

---

