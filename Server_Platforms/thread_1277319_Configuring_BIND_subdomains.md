---
title: "Configuring BIND subdomains"
date: 2009-09-28
forum: Server Platforms
---

### Post by lasouthside on 2009-09-28
[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG] 				**Help ! Need To Configure Subdomains for Local Server on LAN** 			
 			 			 		   		 		 		Please help !!! I need to create subdomains to one domain but i don't know how.....
Somebody who knows please explain how works, and what i must to do.....

:confused:
Thenk's Allot.

---

### Post by Bachstelze on 2009-09-28
If both the top domain and the subdomain are to be handled by the same nameserver, just change your $ORIGIN:

$ORIGIN sub.dom.ain.

foo IN A 123.45.67.89


will make foo.sub.dom.ain resolve to 123.45.67.89

---

### Post by lasouthside on 2009-09-28
> **Bachstelze said:**
> If both the top domain and the subdomain are to be handled by the same nameserver, just change your $ORIGIN:

$ORIGIN sub.dom.ain.

foo IN A 123.45.67.89


will make foo.sub.dom.ain resolve to 123.45.67.89



i don't understant ....please tell me step by step what must to do.......

I have 1 domein configurate and i want to make 1 subdomain, but i don't know how,.....i serch in google but i don't understand.....if you are kind to tell me what must to to step by step I appreciate !

Once again thenk's allot ! you are the man.

---

