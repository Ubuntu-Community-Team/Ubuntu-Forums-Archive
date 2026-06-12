---
title: "GUFW Rules"
date: 2013-03-16
forum: Security
---

### Post by Luddite Savant on 2013-03-16
Hi, I've just set up GUFW as a firewall and I've setup some rules for what it should allow. 

The preconfigured rules only allow you to select from 6 bittorrent clients, skype & ubuntu one to set permissions for. Can I assume from this that that's all I would need to set rules for? If not how do I go about adding other applications. I've checked out the simple & advanced rules tabs & simple gives me the option to write in 'Port or Service' - will it recognise whatever I type in, for example if I want to set rules for TOR or for a distributed computing project what do I need to type into the box?

Another thing is when I add a rule - say for ubuntu one it displays in the list of rules as "456/udp             Allow In                   Anywhere", etc with no indication as to what rule or port number relates to what application. Doesn't seem to be a way to get it to display Ubuntu One Allow In, etc instead & I can see it becoming very confusing if I need to set a lot of rules. Is there an easy way to make sense of this and to be clear as to what applications rules ar set for?

Thanks

By the way I'm on Ubuntu 12.10

---

### Post by Soul-Sing on 2013-03-16
rules are service related for TCP:
25 SMTP
80 HTTP
110 POP3
443 HTTPS
67and 68 DHCP
53 DNS
-----------------------------------
53 DNS udp
are some examples of allowed (if you need them)[COLOR="#FF0000"][SIZE=4] outbound traffic[/SIZE][/COLOR]. the last ones are nec. for internet access.

---

### Post by maglinu on 2013-03-16
I think 67 and 68 are UDP allow out (if you want outbouund ports set to default deny).

I've not found an application specific firewall for ubuntu.

There is Leopard Flower - but it has no deb package that I know of - so you'd need to build it.

---

### Post by Ms. Daisy on 2013-03-17
What is your plan?  Are you using the default setting which is denying all incoming and allowing all outgoing?

Unless you are running services you do not need to allow any in.

---

### Post by Luddite Savant on 2013-03-27
Thanks guys, looks like I'll just need to keep a note of what ports are for what & what apps are allowed through firewall.
Yes, I'm blocking all incoming & allowing all outgoing, just allowing bittorrent. Wated to be able to allow other apps like distributed computing but can't see how to.

---

