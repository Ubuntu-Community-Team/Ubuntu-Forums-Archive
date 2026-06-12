---
title: "Provisioning Scripts?"
date: 2017-08-18
forum: Server Platforms
---

### Post by codycoder2 on 2017-08-18
Does anyone know of any open source scripting tools to automate the provisioning of Ubuntu Server?

For example, after install


[LIST]
[*]updates
[*]install a list of packages
[*]create users
[*]create folders
[*]custom config (like apache, bind, ssh and so on).
[/LIST]

I find myself doing the same things over and over again and I figure someone must have a (even slightly) more automated option out there.

---

### Post by LHammonds on 2017-08-18
I use VMware vSphere so all my servers are virtual.  I create a "master" server with a dedicated IP that I will never use for any other server.  Once it is fully configured as a base-line server, I then convert it to a template.

I deploy from template, then change the host, hostname and IP.  Then all that is left is changing it into whatever specific application server I need it to be.

I thought about utilities that track /etc and other things but I just don't roll out a ton of servers so I don't bother.  I only maintain a dozen Linux servers (and a 100 Windows servers)

LHammonds

---

### Post by TheFu on 2017-08-21
cobbler
ansible
chef
puppet

There are many others - search "cobbler vs" and "ansible vs" to find other, similar tools.

---

