---
title: "lighttpd and wordpress hostname resolve issue"
date: 2010-06-27
forum: Server Platforms
---

### Post by vladoportos on 2010-06-27
Hello all,

I'm trying to get wordpress to work with lighttpd and my home test server... 

<name>.dnsalias.org as my IP is not static... 

When I install wordpress ( via apt-get ) and set it up through install script like this:

bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress <name>.dnsalias.org
It is accessible from outside of my network but not from local one where the sever ip is 10.0.0.200

From outside it is using correctly domain <name>.dnsalias.org  but from inside
when I try to use ip 10.0.0.200 from other pc on net it will not work..a s it still using <name>.dnsalias.org in all links...

Also I would like to have it in <name>.dnsalias.org/wordpress as I have another test site in <name>.dnsalias.org/<test_Site> which by thee way works from inside and outside of my network.... its just wordpress ...

I have followed this guide: [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress) but its for apache...

I spend whole night searching for some solution and now I'm dead tired and you are my last hope ...( ....Obi Wan Kenobi ) 

So does someone running wordpress in setup like I described above, if yes, could you please share the secret with me ?

Thanks all, I'm off the bad half delirious...
VladoPortos

---

### Post by Ryan Dwyer on 2010-06-27
It's because your dnsalias.org domain resolves to your external address. Most routers will not forward a packet on an external address if it came from inside the network.

The solution is to either add an entry in each machine's hosts file or add a local DNS server.

---

### Post by vladoportos on 2010-06-28
yes you are right, I had my sleep and when I woke up I realized the issue is between keyboard and chair :lolflag:  

I edited C:\Windows\System32\drivers\etc\hosts on my win 7 pc and now it works, it nicely resolve the url to local network...

I will go ahead and fight the wordpress install again :) as it is unusual with using apt.... all the folders are somewhere else and some stupid soft links are being created all around the system...

cheers all ! ):P

---

