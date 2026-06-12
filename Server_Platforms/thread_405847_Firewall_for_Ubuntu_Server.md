---
title: "Firewall for Ubuntu Server"
date: 2007-04-10
forum: Server Platforms
---

### Post by himurakenshin on 2007-04-10
I just set up a server running ubuntu server 6.10 and I was wondering how to setup a firewall (is one required or is it built it)

thanks

---

### Post by heimo on 2007-04-10
I think it's convenient to have firewall configured on my servers, kind of extra layer of security. Doesn't hurt anyone.

Linux - the kernel - has netfilter built into it. You can do a *lot* with it. iptables is a command line tool to make changes / rules - and you can also use graphical interfaces like firestarter.
[http://www.netfilter.org/](http://www.netfilter.org/)

Here's guide to get started with iptables:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by az on 2007-04-10
> **himurakenshin said:**
> I just set up a server running ubuntu server 6.10 and I was wondering how to setup a firewall (is one required or is it built it)

thanks

That depends on your needs.

You don't need a firewall for the sake of having a firewall.  That's useless.  Just follow security best-practices and don't run any services (don't run anything that listens to the network) unless you need to.  That means don't even run ssh unless you absolutely need it.

If you need to run something like ssh, you may want to run a firewall or some sort of script to protect yourself.  You may want to forbid any ip address other than your IP address (from which you will be sshing into your box remotely) to ssh into the server - use a firewall.  Other options are utilities like fail2ban which will ward off brute-force attacks.

You may need a firewall if you have problems with ddos attacks, for example.

You certainly need to keep up-to-date with security updates -that's a must, but a firewall is meant to address a specific need.

---

