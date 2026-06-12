---
title: "Resolv FQDN don't work"
date: 2011-03-28
forum: Server Platforms
---

### Post by flavy on 2011-03-28
Hi.

I have a problem with my FQDn resolution on Ubuntu 10.04 server
I don't understant why.

I search on lot of forum, faq and all...

I have a Active directory domain with XP/Vista/7/Ubuntu dsk an server.

I have 2 Ubuntu server
One with the name Titan
Other with the name narcisse

My DNs is on the 2003 server.
t2si.local

All my desktop are in DHCP, and all look work fine

On my Ubuntu server i can't resolve FQDN

On titan if in ping narcisse
#root@Titan Ping narcisse   ---> 172.16.3.22 OK
#root@titan Ping narcisse.t2si.local ---> unknow Host....

On Narcisse Same error when I ping titan....

On all my DHCP desktop that wotking.

I have edit my /etc/resolv.conf

The lines are :
nameserver 172.16.3.1 (My real name server)
domain t2si.local
search t2si.local

I have edit my /etc/hosts
127.0.0.1 localhost
127.0.1.1 Titan.t2si.local Titan (or narcisse.t2si.local narcisse)

I test my dns
#root@titan nslookup narcisse.t2si.local >
servername 172.16.3.1
domain t2si.local
Canonical name narcisse.t2si.local
IP 172.16.3.34.....

The same for narcise to titan




I don't understand why.

some help please

---

### Post by SeijiSensei on 2011-03-28
You need to add static entries for your Linux hosts to the Active Directory nameserver.

---

### Post by flavy on 2011-03-28
I do.

for exemple :

narcisse is my mirror server

I have a static hoste(A) in my DNS server 2003 172.16.3.34 Narcisse
I have a alias mirror who is attach to my static host Narcisse

On titan in can ping narcisse and mirror on the same ip
Ping narcisse ---> OK
Ping Mirror ----> OK

Nslookup mirror.t2si.local
FQDN 172.16.3.1
canonical name Narcisse.t2si.local

But when i ping mirror.t2si.local   ---> host Unknow.

And it is the same for windows host
Gaia is a xp
gaia ping all FQDN

But my ubuntu ping gaia but not gaia.t2si.local

---

### Post by Fire_Chief on 2011-03-28
It's because you are using a .local domain suffix. The Avahi service in Ubuntu grabs this and uses it by default.

See this thread for a more extensive explaination
[http://ubuntuforums.org/showpost.php?p=4468587&postcount=9]("http://ubuntuforums.org/showpost.php?p=4468587&postcount=9")

The quickest fix is to disable or uninstall Avahi on your Ubuntu systems.

Cheers!

---

