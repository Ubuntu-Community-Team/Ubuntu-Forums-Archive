---
title: "SQUID Authentication via Website or other Programm?"
date: 2010-01-29
forum: Server Platforms
---

### Post by ICEB3AR on 2010-01-29
Hi there.
 
Sorry if it's to trivial, but google has not delivered that what i wanted.
I would like to configure Squid and DansGuardian that way, that it's a Proxy with Authentication via Website. 
That means: A new Notebook gets about DHCP the Network-Information like IP-Adress etc.. When he now tries to open a Internet connection it should check if he's authenticated and if not he should get (if this try is from a browser) a login screen in http. It should also not be possible to have internetconnection without being logged in.
The clients are Windoze, Mac and Linux
 
My question now. What programms/deamons are there for doing this authentication. Would you decide for another Programm instead of Squid?
 
Thanks for any hints.

---

### Post by kewlrichie on 2010-01-29
A google search for "squid authentication" came up with tons of results for basic authentication on squid. However if your going to use it with dansguardian i believe you would have to check the dans config /etc/dansguardian/dansguardian.conf and look for "authplugin" and enable it by uncommented. I would try the "proxy basic" option which uses this config /etc/dansguardian/authplugins/proxy-basic.conf and that should let you use the squid authentication while using dansguardian. please take these as helpful hints and not rock solid advice. I did use squid and dans in a production environment and it works very well but with no authentication

---

### Post by ICEB3AR on 2010-01-29
Sorry i don't know why i haven't read till the end :D i was confused, beacuse i wanted to use authentication about a website.

---

