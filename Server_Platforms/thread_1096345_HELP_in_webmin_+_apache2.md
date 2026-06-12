---
title: "HELP in webmin + apache2"
date: 2009-03-14
forum: Server Platforms
---

### Post by mshtawythug on 2009-03-14
guys please help me 
i have webmin and apache2 
i created a master zone in DNS let say its name is "foo"
and i created an address "me.foo"
and i created all the other record NS and so one
now my problem is this:
i created a virtual server in apache2 and give it the same ip of the me.foo
and i need to log into it from firefox this means that i need to use the NS that i ve created to return the ip of me.foo and this ip should log me into the virtual server how can i do it pleaaaaaaaaaaaaaaassssseeee help its urgent 
and thanx in advance

---

### Post by windependence on 2009-03-15
You most likely do not need a nameserver if you are just going to host a web site. Use the nameservers and DNS from your domain registrar. That's what they are there for.

-Tim

---

