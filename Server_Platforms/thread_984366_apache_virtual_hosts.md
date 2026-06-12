---
title: "apache virtual hosts?"
date: 2008-11-16
forum: Server Platforms
---

### Post by rslrdx on 2008-11-16
Hi, and TIA,

I'm trying to figure out if apache virtual hosts is what i need, I got a LAMP server that hosts an intranet app, which for some reasons needs to be open to the outside world (internet) and my problem with that is that i have other web aplications hosted on this same server which do not need to be reachable from outsite, to give an example, phpmyadmin, so, my question is, is apache virtual hosts a good way to block people from seeing these webapps? 

I'm just concerned about security, and i see no reason to have an app like phpmyadmin reacheable from outside. vpn is not an option on this particular case.

Thanks,
Rodrigo.

---

### Post by djamu on 2008-11-16
Hi

well there's a couple of options.
when using vhosts, you could use .htaccess files to limit connectivity

or you could use vmware server to completely isolate a server connected to the outside..
using a different subnet / IP that routes to the outside.
database can be shared on the original host via a second virtual NIC.
( or you can do this reversed > set up a virtual machine for your intranet and the.. just depends on the load ).

The second option is pretty easy if you don't want to spend much time figuring things out... I suggest you use JEOS ( ubuntu version made specifically for VMware ) >[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

make sure you do setup a local NTP server to sync any ( virtual ) machine involved .. as vmware clocks tend to drift ( I'm pretty sure you won't like clock skew errors in your database & logs ).. 
vmware tools can do this to .. but NTP is better ...

---

### Post by rslrdx on 2008-11-16
> **djamu said:**
> Hi

well there's a couple of options.
when using vhosts, you could use .htaccess files to limit connectivity

or you could use vmware server to completely isolate a server connected to the outside..
using a different subnet / IP that routes to the outside.
database can be shared on the original host via a second virtual NIC.
( or you can do this reversed > set up a virtual machine for your intranet and the.. just depends on the load ).

The second option is pretty easy if you don't want to spend much time figuring things out... I suggest you use JEOS ( ubuntu version made specifically for VMware ) >[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

make sure you do setup a local NTP server to sync any ( virtual ) machine involved .. as vmware clocks tend to drift ( I'm pretty sure you won't like clock skew errors in your database & logs ).. 
vmware tools can do this to .. but NTP is better ...


Hi, Sadly I dont have a box to use for VM, and i had completelly forgotten about the .htaccess file

In any case, i've never used Apache Vhosts before, so I'd also like to confirm that this is how it works. :confused:

any other suggestions?

---

### Post by mikkoko on 2008-11-17
VirtualHosts are the right way to do this.

You have a couple of ways to separate the applications:

- You can create one VirtualHost for your public IP address and a second one for your internal IP address. 

- Or create the VirtualHosts for different ports, like :80 for the public and :8080 for the internal webapp. 

The Apache vhosts doc has good examples on these, and more:
[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

I'd suggest you to forget htaccess. If you have a vhost listening on a port that could be accessed from the Internet, use your firewall to block access to it.

---

### Post by Dedoimedo on 2008-11-17
Hello,

Virtualhost is a good solution.

What more, you can create a virtual interface (like eth0:1) and give it a private address and then "host" all internal traffic to the virtual container only for this IP. It will be unreachable from outside.

So you can have a single physical interface, with a virtual extension, example: eth0 220.110.0.0 and eth0:1 10.0.0.1.

Create two virtual hosts for each IP ... and Bob's your uncle.

You can also make sure the routing is prohibited between the two subnets using iptables. Simply drop any request between the two in any which direction.

See my Apache guide (sig); it might help you.

Dedoimedo

---

