---
title: "[SOLVED] Apache2 VirtualHosts not working"
date: 2008-11-03
forum: Server Platforms
---

### Post by Mickeysofine1972 on 2008-11-03
Hi guys

I did an upgrade from hardy to ibex at the weekend and everything seemed fine until I tried to view a couple of staged sites I have on this machine.

The virtuall hosts havent been changed and all ppoint to the right locations, I checked the permissions hadent been changed on the folders and they are correctly owned and have read/write/execute (776 to be precise).

I am running php5 and using mod_rewrite which are all enabled in the mods-enabled folder too.

I have checked all the normal settings but this still doesn't display anything but the default "it works" file.

Please help!

Mike

---

### Post by Mickeysofine1972 on 2008-11-03
Sorted it myself:

Added 

NameVirtualHost *:80 

to the top of all my old virtual hosts. It appears the newer version doesnt let you get away with not having this

Mike

---

### Post by tchalvakspam on 2008-11-14
My upgrade to Intrepid Ibex added a ports.conf to the apache files,
containing the lines 
NameVirtualHost:80
Listen 80

(and some ssl stuff).

this gave the error:  [warn] NameVirtualHost *:80 has no VirtualHosts
when I restarted apache, and sent all my pre-existing virtualhost entries to the default /var/www/ localhost location.

My solution ended up being making the NameVirtualHost and default virtual host match port settings by:

Stripping the :80 port reference from the NameVirtualHost *:80 line in ports.conf and also stripping the :80 port reference from the default virtual host <VirtualHost *:80> as well, so now both look like:

NameVirtualHost *

and ...

<VirtualHost *>

And now my other virtualhosts are working again.

The launchpad bug for this is here:
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/268868](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/268868)

---

