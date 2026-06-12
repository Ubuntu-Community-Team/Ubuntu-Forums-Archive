---
title: "MyDNS Help?"
date: 2009-12-19
forum: Server Platforms
---

### Post by woolyg on 2009-12-19
Hi all,
I'm hoping someone can help me. I'm trying to set up a home web server for testing and hosting a small site. The server is all configured (or so I think), ISPConfig3 is installed, along with MyDNS, and locally, I can see the server on its IP address. When I type my external static IP, I can see the home page.

I've registered a .net name, and registered ns1.mysite.net and ns2.mysite.net to be the DNS servers for it. That was 4 days ago, so the propogation of this info should be done by now.

I've set the mysite.net site up in ISPConfig3, and created NS listings for the site. The NS listings just arent resolving, when I type the URL of the site into a browser, or try to nslookup the DNS.

Can anyone point me in the right direction? I'm quite new to Ubuntu (<6mths) so please be patient if my questions seem rudimentary..

Thanks
WoolyG

---

### Post by madverb on 2009-12-19
Is port 53 open to the server?

---

### Post by woolyg on 2009-12-19
Is there an easy way to check?

I did run an iptables command from a resource I found online regarding port 53, but I'm unsure if it's opened properly.

It's definitely open (UDP) on my router.
For the record, I'm running ubuntu 9.10 in a virtual machine for testing, initally..

Thanks,
WoolyG

---

### Post by madverb on 2009-12-19
telnet <ip or fqdn of server> 53

---

### Post by woolyg on 2009-12-19
From my base machine to the ubuntu machine, telnet on 53 works (from command line, opens up a blank box) and does not give an error in connection.

Is there another diagnostic step I might move on to? Any other ideas?

Thanks,
WoolyG

---

### Post by BkkBonanza on 2009-12-20
When you try nslookup do you also try specifying (last) the ip of the dns server to use for lookup? Usually you would not but if you do and it works then it indicates that your DNS registrar settings are not correct. If it doesn't work then you know the issue is about the DNS server config (depending on message) or connection to it.

If you determine that the registrar settings are the problem then be aware that setting the NS records are not the same as other DNS records. There is a separate place for NS records and you need to specify IP not ns1.mysite.net.

---

