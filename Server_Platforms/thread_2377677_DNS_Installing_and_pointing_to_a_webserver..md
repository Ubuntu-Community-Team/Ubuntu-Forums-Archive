---
title: "DNS Installing and pointing to a webserver."
date: 2017-11-15
forum: Server Platforms
---

### Post by clivebiddulph on 2017-11-15
Task test a new web sever setup :-  
So I setup a new VM running the O.S and made the changes in wordpress. went to test it and the page directs to the live server.
So created a a DNS 192.168.6.103   and tried to point the domain to 192.168.6.106  hoping the dns would resolve to my test server.
It will not and I keep getting errors.
dig  returns   :-
dig @192.168.6.103   xxx.co.nz
;;->> HEADER<<-opcode: QUERY, status : SERVFAIL, id 51300
 
nslookup  xxx.co.nz 
returns 
server :    192.168.6.103
Address    192.168.6.103#53

version 14.04  ( yes I know it old, the task is to upgrade it but need to test my base before I test the upgrade )

any ideas welcome.

so summery point to an dev site without effecting live site, so can tst the upgrades and changes.   website runs wordpress.

---

### Post by wildmanne39 on 2017-11-15
*Thread moved to **Server Platforms for a more appropriate fit**.*

Is this a class assignment or work assignment?

---

### Post by clivebiddulph on 2017-11-15
work, I am testing the upghrade from 14.04 to 16  but need to test wordpress, with the new php as well. So step one, get a site running using the current version then do the upgrade in place, see if that works. If it failes need to build new server and test everything first. Thank you ( yes we own the domain and is a live site which is why I need to test it off the internet ).

---

### Post by SeijiSensei on 2017-11-15
Create a new fully-qualified name for the site like test.xxx.co.nz.  Add an A record for that name to your DNS and point it to the new server's IP.  Edit the web server configuration on the new server to answer requests for test.xxx.co.nz.  If you're using Apache, the easiest way to do this is to add a 
```
ServerAlias    test.xxx.co.nz
```
to the configuration inside the <VirtualHost> container.  Now point a browser at [http://test.xxx.co.nz/](http://test.xxx.co.nz/).

---

### Post by clivebiddulph on 2017-11-16
been testing added  
xxx.xxx.co.nz.           IN       A       192.168.6.106

restarted machine
dig xxx.xxx.co.nz
Got answer
->>Header<<- opcode Query, status: SERVFAIL, id 29651

this machine can ping the 192.168.6.106  0.463 ms

so there must be somthing else I have done wrong tested the zone file no errors 
named-checkconf    no errors
got error in the named-checkzone now, so will fix that and carry one looking, 

Thank you SeijiSensei  for your help

---

### Post by SeijiSensei on 2017-11-17
Is this server authoritative for the xxx.co.nz domain?  You can set up a local server to answer queries for the domain as long as all the clients use it as their nameserver.  Otherwise you should be making changes to the authoritative nameserver.

---

