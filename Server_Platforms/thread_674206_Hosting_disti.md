---
title: "Hosting disti ?"
date: 2008-01-21
forum: Server Platforms
---

### Post by stonneway on 2008-01-21
Hi Chaps,

Slightly OT but i thought you chaps might now.

Has anyone seen a disti configured for basic site and email hosting out of the box? Something that does for hosting sites and email what IPCOP and SMOOTHWALL do for firewalls.

Doesnt need to be massively feature rich, just php/apache/email/mysql etc with a simple easy to use interface etc.

Olly

---

### Post by compiledkernel on 2008-01-21
This will take care of the email, etc type stuff. 

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

you want a firewall outside of that too? 

Just setup iptables on the box and use somethign like fwbuilder to build the firewall rules.

---

### Post by stonneway on 2008-01-21
Yeah, theres loads on Howtoforge, but I'm after a disti that does it out of the box by design, ie install it and get a web based logon and start configuring. 

I actually am after something like IPCop or Smoothwall or Untangle but for web/email hosting.

Olly

---

### Post by compiledkernel on 2008-01-21
There really isnt an "OoTB" solution that im aware of thats ubuntu based to do this. If your looking for something like that, its going to be a hard thing to do most certainly. 

its really just easier to build it yourself, and then go. 

I assume by doing this you wish to avoid having to edit configuration files, and live on somewhat default setups. In the case of a webserver, such an idea is really NOT avisable to do. 

[http://wiki.contribs.org/Main_Page](http://wiki.contribs.org/Main_Page) - SME server does this, but its based on CentOS/Redhat

[http://www.yoper.com/](http://www.yoper.com/) - Yoper does the similar. 

But again, neither of these are more complete solutions than just sitting down to an ubuntu machine and learning the ropes a little to get it going. Its not all that hard.

---

