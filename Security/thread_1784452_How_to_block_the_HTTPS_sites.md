---
title: "How to block the HTTPS sites"
date: 2011-06-17
forum: Security
---

### Post by suresh_vandiyur on 2011-06-17
I want block https sites if suppose block the http it will opening in https. how block the sites please help me

Thank you,

Regards,
Suresh

---

### Post by crispy_420 on 2011-06-17
Can you block the outgoing port on your router? That would be the simplest method I guess.

http = 80
https = 443

---

### Post by suresh_vandiyur on 2011-06-17
> **crispy_420 said:**
> Can you block the outgoing port on your router? That would be the simplest method I guess.

http = 80
https = 443

if we block like this all the https sites will be blocked. i want block some of the particular sites only like the. how to do this. please help me

Thank you,

Regards,
Suresh

---

### Post by crispy_420 on 2011-06-17
Most routers give you the option of blacklisting some sites. There are ways to do it on the PC too but that means each PC will need this to be done. Let your network hardware do the work for you. Maybe a service such OpenDNS may also be an option if you would like to block entire types of sites (porn, social networking, etc.) and I think they let you manually adjust blocked sites as well.

Worst case scenario you could build a gateway server to control content too.

---

### Post by suresh_vandiyur on 2011-06-17
> **crispy_420 said:**
> Most routers give you the option of blacklisting some sites. There are ways to do it on the PC too but that means each PC will need this to be done. Let your network hardware do the work for you. Maybe a service such OpenDNS may also be an option if you would like to block entire types of sites (porn, social networking, etc.) and I think they let you manually adjust blocked sites as well.

Worst case scenario you could build a gateway server to control content too.
I have tried that also its blocking only http only not blocking the https. please let me know any other way to do this. please help me

Thank you,

Regards,
Suresh

---

### Post by crispy_420 on 2011-06-17
What router do you have?

---

### Post by suresh_vandiyur on 2011-06-17
> **crispy_420 said:**
> What router do you have? we can't do this thing in my router because its a home router.  any application for that please tell me.

Thank you,

Regards,
Suresh

---

### Post by crispy_420 on 2011-06-17
I have had some pretty basic home routers that have had this capability. Is it only a few sites or many? You may be able to block by IP address and that would cover all transactions (http, https, ftp, etc.). 

So what router?

An application would only stop that single PC's access. Why not stop all access network wide? An application can be bypassed many ways. In fact anything suggested could be bypassed as you can never block 100%, ask many foreign governments country wide attempts.

---

### Post by suresh_vandiyur on 2011-06-17
> **crispy_420 said:**
> I have had some pretty basic home routers that have had this capability. Is it only a few sites or many? You may be able to block by IP address and that would cover all transactions (http, https, ftp, etc.). 

So what router?

An application would only stop that single PC's access. Why not stop all access network wide? An application can be bypassed many ways. In fact anything suggested could be bypassed as you can never block 100%, ask many foreign governments country wide attempts.
Only few sites only. am using linksys WRT120N router. please help me.

Thank you,

Regards,
Suresh

---

### Post by crispy_420 on 2011-06-17
After looking at the manual for that unit that approach may not be feasible with that unit. You block by URL but not IP on that unit so https just skips past this. So the next option would be use a third party such as OpenDNS. They can block lots of types of content but they also let you define your rules by IP address (up to 25 addresses for a free account I think). The only software you need to install on your system is a client that keeps you in sync with their DNS servers.

---

### Post by suresh_vandiyur on 2011-06-17
> **crispy_420 said:**
> After looking at the manual for that unit that approach may not be feasible with that unit. You block by URL but not IP on that unit so https just skips past this. So the next option would be use a third party such as OpenDNS. They can block lots of types of content but they also let you define your rules by IP address (up to 25 addresses for a free account I think). The only software you need to install on your system is a client that keeps you in sync with their DNS servers.

In this opendns free account i think there no ip blocking option. please help me

Thank you,

Regards,
Suresh

---

### Post by crispy_420 on 2011-06-17
I re-read my source and I'm sorry but the info I gave was not 100% correct. From reading up further you will need different networking hardware with better features to be successful. 

The next option to save money would be to build your own router out of a old PC. Something like IPCop or pfSense can make use of old hardware that would normally get thrown away. Here is a list of options:

[http://distrowatch.com/search.php?category=Firewall#distrosearch](http://distrowatch.com/search.php?category=Firewall#distrosearch)

Sorry but I don't know if I could help further. Maybe someone else can chime in with something I missed or overlooked.

---

### Post by suresh_vandiyur on 2011-06-17
> **crispy_420 said:**
> I re-read my source and I'm sorry but the info I gave was not 100% correct. From reading up further you will need different networking hardware with better features to be successful. 

The next option to save money would be to build your own router out of a old PC. Something like IPCop or pfSense can make use of old hardware that would normally get thrown away. Here is a list of options:

[http://distrowatch.com/search.php?category=Firewall#distrosearch](http://distrowatch.com/search.php?category=Firewall#distrosearch)

Sorry but I don't know if I could help further. Maybe someone else can chime in with something I missed or overlooked. For the pfsense or IP Cop i need the separate system i can install along with ubuntu. please help me.

Thank you,

Regards,
Suresh

---

### Post by crispy_420 on 2011-06-17
Need a separate system. Really old hardware should work with the only real requirement being two NICs.

---

### Post by suresh_vandiyur on 2011-06-17
> **crispy_420 said:**
> Need a separate system. Really old hardware should work with the only real requirement being two NICs.
Ok. After installation any configuration file is available. because i heard we configuration file pf sense. please help.

Thank you,

Regards,
Suresh

---

### Post by crispy_420 on 2011-06-17
Sorry but I have not used this in a months and even then it was just to mess around. They have many support options and info at their site though.

---

### Post by suresh_vandiyur on 2011-06-17
> **crispy_420 said:**
> Sorry but I have not used this in a months and even then it was just to mess around. They have many support options and info at their site though.

Thanks for your reponse.

Thank you,

Regards,
Suresh

---

