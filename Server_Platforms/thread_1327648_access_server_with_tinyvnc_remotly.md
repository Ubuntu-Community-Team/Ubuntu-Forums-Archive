---
title: "access server with tinyvnc remotly"
date: 2009-11-15
forum: Server Platforms
---

### Post by fabianus on 2009-11-15
Hello all !

I try to access my ubuntu 9.04 server remotly (with tiny vnc). 
The problem is that I do not have any physical acces to it (and I'll never have as it is a hosted server). 

So what I tried is to setup a tunnel with ssh but I get this error : 

2009-11-15 22:26:14	Local port 5900 forwarding to 127.0.0.1:5900
2009-11-15 22:26:14	Allocated pty (ospeed 38400bps, ispeed 38400bps)
2009-11-15 22:26:14	Started a shell/command
2009-11-15 22:27:50	Opening forwarded connection to 127.0.0.1:5900
2009-11-15 22:27:50	Forwarded connection refused by server: Connect failed [Connection refused]


Could anybody help me to setup the server in a manner that I may access its desktop remotly ? 

Thanks a lot for any help !

Regards, 
Fabianus

---

### Post by hessiess on 2009-11-15
Why not just use plain SSH with a command line.

---

### Post by fabianus on 2009-11-15
Hello hessiess, 

thanks for your interest. Because I would like to run the openERP client on the server. 

Regards, 
Fabianus

---

### Post by hessiess on 2009-11-15
> **fabianus said:**
> Hello hessiess, 

thanks for your interest. Because I would like to run the openERP client on the server. 

Regards, 
Fabianus

Just reading up on openERP, it would appear that there is a web interface available for it.
> 
A web interface 'eTiny' is also available using the Turbogears web framework.

[http://en.wikipedia.org/wiki/OpenERP](http://en.wikipedia.org/wiki/OpenERP)

Have you considered using that instead?

VNC is slow enough just going over a local network with no other traffic.

---

### Post by fabianus on 2009-11-15
Hello hessiess, 

yes, I'll do that. But as far as i know I need the client first in order to set things up. 

Regards, 
Fabianus

---

### Post by Lars Noodén on 2009-11-16
@fabianus: is the ssh server set to allow port forwarding?

What is the specific syntax you are using?

You must find the correct port number to forward to on the remote host.  IIRC to do that, add the display number to 5900. Check the instructions for tinyvnc to be sure.  

e.g.
ssh -L 1234:localhost:5902 openerp.example.org

Just a guess

---

