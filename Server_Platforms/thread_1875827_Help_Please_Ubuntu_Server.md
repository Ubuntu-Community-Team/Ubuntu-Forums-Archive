---
title: "Help Please Ubuntu Server"
date: 2011-11-05
forum: Server Platforms
---

### Post by sligoman on 2011-11-05
Hi All

Have a bit of a problem.. Have a Ubuntu server thats been running for a bout a year and half with no problem. The server is running through a BT Business Router with various ports forwarded. 

I can't access my websites from my WAN but if go to someone else's house I can connect to the my websites through WAN

if I type [http://www.sligo-man.com](http://www.sligo-man.com)  all I get is The connection was reset. The connection to the server was reset while the page was loading.

I have searched to no avail maybe some could help me out on this one.

Thanks in advance

Liam

---

### Post by volkswagner on 2011-11-05
It sounds like NAT setting on your router/firewall.
Check those settings at your router.

---

### Post by CharlesA on 2011-11-05
Are you trying to access the sites from inside your network from their domain name?

Most routers don't do that.

---

### Post by sligoman on 2011-11-05
Hi There Thanks for the replies.

[I][B]It sounds like NAT setting on your router/firewall.
Check those settings at your router. [/B][/I]

Yes I have had a good route around in the nat setting but still not able to view website over WAN

***Are you trying to access the sites from inside your network from their domain name***

I can get to website if I type ipadrress/sligo-man.com

Just can't fathom this one out and I bet it is really a simple solution..

---

### Post by sligoman on 2011-11-05
Just to add:

I can connect to the server with local ip 192.168.1.5 but not with the public ip 81.149.219.88 if that is any help to some one who can solves this for me

---

### Post by CharlesA on 2011-11-05
I'd say make sure you have port forwarding set up correctly and also make sure you are trying to access it from outside the local network.

---

### Post by volkswagner on 2011-11-05
As already mentioned, this issue is likely with NAT.

If you don't have apache or any other firewall (software or hardware_ specifically blocking ip 81.149.219.88, than I'd really double/triple check your NAT.  Maybe reset router/pwr cycle.

Does the request from 81.149.219.88, reach the apache access log.

---

### Post by sligoman on 2011-11-05
Hi All

Would just like to thank everyone for the response to my query the problem has now been solved.. I did take everyones advice and checked the NAT settings.

Unfortunately there was a problem with the router itself and not the settings. A friend of mine gave me a duplicate router and was setup exactly the same as the old router and bingo every thing works as normal now.

So once again thanks for all your help and sugestions.

Regards

Liam

---

