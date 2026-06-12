---
title: "security question"
date: 2008-12-13
forum: Server Platforms
---

### Post by pshootr on 2008-12-13
Hi, I just set up an 8.10 server for home use as a file server. My network consists of a cable modem connected to a linksys router, and two windows pc's connected to the router, as well as the new 8.10 file server. I know that a router works as a very good hardware firewall but, question is, should I implement extra means of security some how? And if so what would be recommended? Thanks

---

### Post by lavinog on 2008-12-13
One could argue that you always want a software firewall along side a router, but I have found many non-technical people don't understand what they are doing and either allow everything, thus defeating the purpose, or block everything thus preventing applications from working properly.
This is mostly on the windows side, since many non-tech people use windows. Some will even block windows update because their firewall calls it something that they don't recognize.

An argument for a software firewall would be that if one computer on your network is infected, your router will not protect your other computers from it.

---

### Post by pshootr on 2008-12-14
> **lavinog said:**
> One could argue that you always want a software firewall along side a router, but I have found many non-technical people don't understand what they are doing and either allow everything, thus defeating the purpose, or block everything thus preventing applications from working properly.
This is mostly on the windows side, since many non-tech people use windows. Some will even block windows update because their firewall calls it something that they don't recognize.

An argument for a software firewall would be that if one computer on your network is infected, your router will not protect your other computers from it.

Thank you. Good point about a networked pc being infected. Could you tell me please what you mean by "infected" do you mean by a virus? Or do you mean when a network pc has been hacked from a user on the internet? Thanks

---

### Post by Dr Small on 2008-12-14
I do not believe a firewall needs to be enabled while behind a NAT router/firewall. It complicates things. For home usage, relying on the NAT firewall is always the easiest choice; otherwise you will be fighting to get access to local machines and cause problems there. (I have done this).

If though, you are on a hostile network, or a network with many different types of machines with different people you do not trust, then I highly recommend a firewall under no circumstances; whether or not you are behind a NAT firewall or not.

But for the common home network that is behind a pre-established firewall and the family need to use file sharing and the sort, then individual firewalls complicate things.

Dr Small

---

### Post by HermanAB on 2008-12-14
The root of the problem is that Windows systems listen on many documented and undocumented ports, with many documented and undocumented bugs.  Therefore it makes sense to run the Windows firewall software in an attempt to block things that you don;t know about and cannot shut down.

Linux is different in that the network stack is very secure and pretty much bug free.  Linux systems only listen on a port if there is a server for that service installed.  A quick scan with top and nmap will show all listeners and you can terminate unwanted services easily.

Most Linux systems by default have no listeners enabled, so it is easy to control the security of a Linux system.  You can do a default Ubuntu install and plug the machine directly into the internet and it will be perfectly secure - don't try that with a default Windows install.

Now consider that most 'firewall' devices such as Linksys, Cisco and others are actually dinky little Linux systems.  So if Linux needed a firewall, then these firewalls would have needed firewalls in an endless iteration...

Hope that helps to explain things a bit.

Cheers,

Herman

---

### Post by hictio on 2008-12-14
Personally, I do run a firewall on all of my boxes.
It takes a minute to set it up, and its another layer of security.

---

