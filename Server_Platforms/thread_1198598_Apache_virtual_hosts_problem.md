---
title: "Apache virtual hosts problem"
date: 2009-06-27
forum: Server Platforms
---

### Post by jordn on 2009-06-27
Hey all!

I am new familiar with Ubuntu,having used it almost daily for the past 9 months, but i am new to using it in a server environment, specifically Apache.

I have 3 domains, for simplicitys sake domain1,domain2, and domain3. I have been searching google and i found out that to host 3 websites from 1 IP you need to use something called virtual hosts. i have got as far as pointing the domains to the IP address of my server, installing apache2 and attempting to create a virtualhosts.conf file for domain1. i followed this guide:

[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

as far as i can tell, when i use my web browser to navigate to domain1, apache acknowleges the request because it displays the "it works!" text, but it obviously isn't looking up the virtual hosts conf file i created, which leads me to believe i either did it wrong, or apache doesn't realise its there (i did it even more wrong! :P )

Can anyone give me a few pointers, or point me in the direction of an up to date working guide?

thanks in advance!

---

### Post by R.Bucky on 2009-06-27
I host three domains from my home server. I wrote a tutorial on the config. [here]("http://buckycomputing.net/blog/hosting-2-domains-with-1-server/").

---

### Post by jordn on 2009-06-28
Hey there, i was following your guide, i have 3 domains and 1 IP address.

I configured all the virtual hosts, but when i type in the domain names into my browser (e.g. domain1, domain2, domain3) i only get the HTML files loaded from domain1. I have specified different documentroots in the virtualhost configuration. I also get this message when restarting apache:

*Restarting web server apache2
[Sun Jun 28 11:18:28 2009] [error] (EAI 2) Name or service not known: Could not resolve host name *.80 -- ignoring!
[Sun Jun 28 11:18:28 2009] [error] (EAI 2) Name or service not known: Could not resolve host name *.80 -- ignoring!
[Sun Jun 28 11:18:38 2009] [error] (EAI 2) Name or service not known: Could not resolve host name *.80 -- ignoring!
[Sun Jun 28 11:18:38 2009] [error] (EAI 2) Name or service not known: Could not resolve host name *.80 -- ignoring!
[ OK ]


any ideas?

EDIT: in my excitement that it parcially worked, i think i clicked my my link a bit too much, and now it seems to have defaulted back to "it works!" even though it now doesn't. any help would be hot.

---

### Post by jordn on 2009-06-28
after looking through some articles on the net, a lot of them mention using a DNS server called bind, and some mention using ISPconfig.

I don't think that i am using bind, and i do not have ISPconfig installed. can anyone shed some light on this?

anything would greatly be appreciated.

---

### Post by Iowan on 2009-06-29
[Another]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") article that might be helpful.  For a small network, DNSMasq is supposed to be easier to set up.

---

