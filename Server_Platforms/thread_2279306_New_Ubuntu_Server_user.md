---
title: "New Ubuntu Server user"
date: 2015-05-22
forum: Server Platforms
---

### Post by chris384 on 2015-05-22
Hi guys, I'm a new user to Ubuntu in general

I've been given an opportunity through my place of work to have a space on the server rack in the data centre

I've got a 1u space and got my hard ware all sorted. I've just been given the confirmation of my IP allocation this afternoon, so it's time to configure the software this weekend

I'll be using Ubuntu server, but installing and configuring it at home prior to taking the hardware to the data centre next week. I'm using this as a great opportunity to learn about this black art of running a server.

I won't be doing anything complicated or fancy to start with. Just using it to try setting up a file server for example, and a mail server.

My question is are there any obvious things to look out for during the installation being that I'm doing that part at home.

---

### Post by SeijiSensei on 2015-05-22
Will the machine be using DHCP to get its address when in production?  If not, you should [set up a static IP]("https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing") in /etc/network/interfaces that works with your home network, then just change it to the real address when you install the server.

If the file server will be supporting both Windows and Linux clients, you should install both Samba and nfs-kernel-server.  Use the latter to export shares with NFS to the Linux clients.

Setting up a mail server isn't the easiest of tasks.  I'd put that off until you get everything else up and running.  You can always add it when the machine is installed.  Installing Postfix itself isn't that hard, but you'll soon be dealing with spam and malware-infested messages once the server is visible on the Internet.  Mail servers that offer POP or IMAP services are a target for "dictionary attacks" where villains try to grab accounts by running automated login attempts with dozens or even hundreds of possible usernames.  I've been in the email business for nearly twenty years, and though my servers are pretty hardened by now, new forms of spam appear all the time that slip past my extensive SpamAssassin ruleset.  Viruses are actually a lot easier to block.

One important rule-of-thumb:  Never post an email address on a web page unless you're ready to handle the deluge of spam it will receive once it has been grabbed by spammers.  They run automated programs that work like search engine "spiders" and scoop up anything of the form [email]user@domain.name[/email] and add them to their spam lists.  If you register a domain, expect to see spam for common addresses like [email]info@example.com[/email] or [email]webmaster@example.com[/email] once your registration is published.  Spammers watch for new domains, too.

---

### Post by chris384 on 2015-05-22
thanks for the reply.

Initially the server will be pretty basic. Just sat in a rack with me learning on it via ssh

I've been given an allocation of 8 ip's so the option is there for me to be able to assign 5 other devices, or services to IP's should I so desire

Think I may hang fire on the mail server idea for now, and just carry on using my hosted domain email

---

### Post by SeijiSensei on 2015-05-22
One alternative would be to forward mail sent to your hosted service back to the server.

There are few reasons you'll need for those extra IPs unless you are hosting SSL sites.  Then you'd want to allocate one to each site. You can use "aliasing" on the adapter to handle those additional IPs like this:
```

auto eth0
iface eth0 inet static
address 10.10.10.9
netmask 255.255.255.248
broadcast 10.10.10.15
gateway 10.10.10.1

auto eth0:0
address 10.10.10.10

auto eth0:1
address 10.10.10.11

[etc.]

```

Note the unusual netmask and broadcast addresses.  If, as I'm guessing, you were allocated an IP subnet with eight addresses, you really can only use six of them as you mentioned.  The first one is the "network" address and the last one the "broadcast" address.  In the example above we have
```

10.10.10.8 - network address for the subnet 10.10.10.8/29
10.10.10.9-14 - available addresses
10.10.10.15 - broadcast address for the subnet

```

---

### Post by chris384 on 2015-05-23
> **SeijiSensei said:**
> One alternative would be to forward mail sent to your hosted service back to the server.

There are few reasons you'll need for those extra IPs unless you are hosting SSL sites.  Then you'd want to allocate one to each site. You can use "aliasing" on the adapter to handle those additional IPs like this:
```

auto eth0
iface eth0 inet static
address 10.10.10.9
netmask 255.255.255.248
broadcast 10.10.10.15
gateway 10.10.10.1

auto eth0:0
address 10.10.10.10

auto eth0:1
address 10.10.10.11

[etc.]

```

Note the unusual netmask and broadcast addresses.  If, as I'm guessing, you were allocated an IP subnet with eight addresses, you really can only use six of them as you mentioned.  The first one is the "network" address and the last one the "broadcast" address.  In the example above we have
```

10.10.10.8 - network address for the subnet 10.10.10.8/29
10.10.10.9-14 - available addresses
10.10.10.15 - broadcast address for the subnet

```


yeah I've got 5 usable ones

first in the range is my network address xxx.xx.x.216
2nd one has been assigned to the server xxx.xx.x.217
last one is the broadcast address xxx.xx.x.223

checking the info looks like they've also given me an IPv6 address as well

---

