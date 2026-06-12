---
title: "Cannot Bind IPs"
date: 2011-03-22
forum: Server Platforms
---

### Post by Bashed on 2011-03-22
I am setting up a squid3 proxy for my office. I'm having  trouble with the /etc/network/interfaces file...

It says the file is automatically generated and, instead, to edit  /etc/network/interfaces.template, a form which is entirely foreign to  me.  I've setup the two primary IPs successfully, and wonder how I can  get the rest of the IPs binded properly.

Tried the IP Network Fix... the command was not recognized.

Ubuntu 10.10
OpenVZ VPS Platform

---

### Post by a9k3d on 2011-03-26
Are you running squid in an openVZ server? I hope not!

I had nothing but trouble with squid in openVZ server. It would lock up the whole host machine. I had to put squid on the host directly non virtual.

I'm also wondering what is generating your network configuration? Are you running a ubuntu desktop server with openVZ and then trying squid in a VE?

---

