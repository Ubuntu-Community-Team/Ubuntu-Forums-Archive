---
title: "Caching update/install lib/package server"
date: 2008-04-23
forum: Server Platforms
---

### Post by nghianghesi on 2008-04-23
hi Linux Pros :)
My LAN have many machine, and I want to use Linux as basis
So, there's big update/install lib demand
It's better to set up an server that will get lib if first time request and cach it for after uses. 
For ex:my LAN have desktop A, B and server C
A request lib1 via Package manager, C will get lib1, return to A and cach lib1 on local, 
B request lib1, C will return lib1 to B
C request lib1, C use lib1 in local
How to config that C server

Thanks
Nghia Nguyen.

---

### Post by bluefrog on 2008-04-23
The easiest is to install apt-cacher on a server/machine and set the other machine to go through it to get the installation packages.

So as an example:
1 server/machine called cache-the-debs (with IP 10.0.0.1)
plenty of machines/servers named the-machines.

** on get-the-debs install apt-cacher
tweak it's conf (/etc/apt-cacher/apt-cacher.conf
) file if you want to change the directory where it will store the packages, and tweak /etc/default/apt-cacher to AUTOSTART=1

** restart the apt-cacher service

** on the-machines and on get-the-debs
tweak the apt-get sources.list of all machines with get-the-debs name if you have DNS working or with its IP so that all lines look like:

deb [http://get-the-debs:3142/](http://get-the-debs:3142/)...

James Dupin

---

