---
title: "a secure server - limits on functionality?"
date: 2008-03-04
forum: Server Platforms
---

### Post by Uaine on 2008-03-04
I'm a bit new to running a web-connected server, and searched the forums trying to find an answer to this question, but did not find any help.

I'm configuring an Ubuntu server right now, and trying to decide what functionality to give it. The most important function it will serve is as a web server.  However, there are lots of other things I want it to do.  My problem is, with many different functionalities providing many possible attack vectors, I wonder how much functionality I can add to it, and still have a *secure* server.

In addition to being a LAMP webserver, I would also like for the server to run:
DHCP and IP masquerading for home network
samba file/printserver
NFS
mail server
webmin (w/ IP restricted access)
SSH (w/ IP restricted access)

With properly configured iptables, can my server do all this and still be secure?  Will I be able to keep it secure even if one of the computers on the home network becomes compromised?

---

### Post by rickyjones on 2008-03-04
> **Uaine said:**
> I'm a bit new to running a web-connected server, and searched the forums trying to find an answer to this question, but did not find any help.

I'm configuring an Ubuntu server right now, and trying to decide what functionality to give it. The most important function it will serve is as a web server.  However, there are lots of other things I want it to do.  My problem is, with many different functionalities providing many possible attack vectors, I wonder how much functionality I can add to it, and still have a *secure* server.

In addition to being a LAMP webserver, I would also like for the server to run:
DHCP and IP masquerading for home network
samba file/printserver
NFS
mail server
webmin (w/ IP restricted access)
SSH (w/ IP restricted access)

With properly configured iptables, can my server do all this and still be secure?  Will I be able to keep it secure even if one of the computers on the home network becomes compromised?

I don't think a firewall is what you wish to look at, except to configure things so that iptables ignores NFS requests from the outside world. That would make it secure (NFS as an example here).

Personally, if you wish to have several network services and you wish to keep them secured then the first thing you need to do is separate them. One application, one server. Invest in a good piece of hardware and run vm-ware.

That way you can individually secure each server and and use differing iptables configurations that would encompass everything in a much more detailed way. Otherwise you are trying to hack together a firewall that will be overworked.

Just my opinion.

-Richard

---

### Post by Stephen_at on 2008-03-04
A lot depends on, as has been said elsewhere, how you connect to the internet.

If you have an ADSL router running NAT then only ports forwarded from the router to your server will be externally visible.

So, if like you me, you only forward HTTP(S) and a few other services then the NAT router acts as a primary firewall.

SSH can be locked down using hosts.allow and hosts.deny (my hosts.deny tarpits ssh connections unless they are from a specific restricted list of addresses)

Postfix can be secured to only allow access from specific networks or authenticated sessions and there are some good tutorials on how to do this (and a couple of good sites to test your mailserver security)

Locking down parts of your website can be done using AuthUserFile and things like that (and I know things like AWSTATS can be locked down to specific viewing IP addresses).

I'm moving over from an old Suse box which does pretty much what you are proposing (apart from the fact that I let the router do NAT) and has been doing it for the best part of 5 years now and has (apart from a hole in phpbb2) not been compromised.

---

### Post by Oldsoldier2003 on 2008-03-04
> **Stephen_at said:**
> A lot depends on, as has been said elsewhere, how you connect to the internet.

If you have an ADSL router running NAT then only ports forwarded from the router to your server will be externally visible.

So, if like you me, you only forward HTTP(S) and a few other services then the NAT router acts as a primary firewall.

SSH can be locked down using hosts.allow and hosts.deny (my hosts.deny tarpits ssh connections unless they are from a specific restricted list of addresses)

Postfix can be secured to only allow access from specific networks or authenticated sessions and there are some good tutorials on how to do this (and a couple of good sites to test your mailserver security)

Locking down parts of your website can be done using AuthUserFile and things like that (and I know things like AWSTATS can be locked down to specific viewing IP addresses).

I'm moving over from an old Suse box which does pretty much what you are proposing (apart from the fact that I let the router do NAT) and has been doing it for the best part of 5 years now and has (apart from a hole in phpbb2) not been compromised.
I concur with your analysis of the scenario, I run a similar setup, though i did install Bastille and configure IPtables to allow me some more flexibility, I found a nice script that allows me to block ranges of ip addresses easily by simply modifying a text file and restarting iptables.

---

