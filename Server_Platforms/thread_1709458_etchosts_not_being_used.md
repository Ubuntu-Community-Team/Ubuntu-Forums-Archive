---
title: "/etc/hosts not being used"
date: 2011-03-18
forum: Server Platforms
---

### Post by nicolasdiogo on 2011-03-18
hello,

i have my laptop (kubuntu 10.10) as a development system using KVM.
i would like to test apache2 configuration - that means that i have to use DNS to call the server by name rather then its local IP.

thus, i have added an entry in my laptop /etc/hosts like:

> 
...

192.168.133.17  myprojdomain.com [www.myprojdomain.com](www.myprojdomain.com)

...

however, when i run firefox, it gets the website of the internet??
i have checked with nslookup and it gives me the Internet IP (which is not what i want).

i have checked this article [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

and gone through the section 'Name Resolution'

my configuration file /etc/nsswitch.conf seems to be looking my local /etc/hosts first..

> 
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4


does anyone know how i can troubleshoot this?


thanks,

---

### Post by wongo888 on 2011-03-18
I seem to recall an issue once with Firefox or some other browser caching DNS results. 

Did you try it in a different browser?

Maybe disable or flush the FF cache? 

Also, my understanding is that nslookup only interrogates DNS servers and it doesn't normally do a lookup on etc/hosts at all. You might want to double check that info though.

---

### Post by SeijiSensei on 2011-03-18
nslookup ignores the host file and talks directly to the default nameservers.

---

### Post by volkswagner on 2011-03-18
Did you edit the host file on the server, client, or both?

---

### Post by hawk2010 on 2011-03-21
You have to configure /etc/nsswitch.conf so that it first looks at files and then try DNS . My nsswitch.conf looks like below 
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

---

### Post by nicolasdiogo on 2011-03-21
thanks guys,

i am using firefox and KDE browser too.
my nsswitch.conf is defined as suggested and my server has the domain name defined on its own /etc/hosts file.

but it only worked after a full reboot.

many thanks for your suggestions.
i really thought that i have forgotten something obvious.


Nicolas

---

