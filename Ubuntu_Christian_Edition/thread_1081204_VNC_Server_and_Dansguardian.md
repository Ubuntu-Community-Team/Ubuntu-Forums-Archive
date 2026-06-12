---
title: "VNC Server and Dansguardian"
date: 2009-02-26
forum: Ubuntu Christian Edition
---

### Post by Hunter_and_Gatherer on 2009-02-26
Hello,

I'm new with Ubuntu CE but not really new with Ubuntu or Linux. I installed Ubuntu CE on a older Laptop for my daughter. The Laptop should be in an other room, so it should be possible to use the remote desktop with VNC.

My problem is that it is only possible to connect from my PC to the Laptop when I disable DansGuardian via Parental Control. Is there any setting in DansGuardian that blocks port 5900 or vnc?

WAN and LAN on the Laptop is working.

I tried to connect from Ubuntu 8.10.

Kind regards,

Hunter_and_Gatherer

---

### Post by stevotower on 2009-03-24
Yes, the UbuntuCE dansguardian configuration, if I recall correctly, uses firehol to configure the firewall to be totally closed off to the outside world.  I haven't run the ubuntuCE DG GUI in a couple of years, so I don't remember if you can configure the firewall with it or not.  If not, modifying the firehol config (/etc/firehol/firehol.conf) is actually pretty easy.  You would just want to modify the lines like:

[FONT="Courier New"]interface eth0 INET
    [INDENT]policy drop
    protection strong
    client all accept[/INDENT][/FONT]

to 

[FONT="Courier New"]interface eth0 INET
    [INDENT]policy accept
    client all accept[/INDENT][/FONT]

which would essentially disable any firewall protection, which should be fine if you keep the laptop behind your router firewall, but not fine if it goes out in public.

or 

[FONT="Courier New"]interface eth0 INET
    [INDENT]policy drop
    protection strong
    client all accept
    server "vnc" accept[/INDENT][/FONT]
Which would leave the firewall up and poke a hole just for vnc.  Not really a good idea for public use either, but better than the first choice.  Best would be opening only ssh and tunneling vnc.  

The firehol manual online is very good, as well.

Hope this helps,
Steve

---

### Post by wineman on 2009-04-30
> **Hunter_and_Gatherer said:**
> Hello,
it should be possible to use the remote desktop with VNC.

. Is there any setting in DansGuardian that blocks port 5900 or vnc?


firstly, you must add an iptables rule, to allow port 5900 INTO your daughter's pc, into the /etc/firehol/firehol.conf file (write it simply as a terminal iptables command.

secondly, it's not DG that blocking, it's firehol. DG is there simply as a CONTENT filter (info is on a deeper level of intricacy) than a packet filter (such as iptables)

The iptables command should read something like this:

#on xterm
$ iptables -A INPUT -p tcp --dport 5900 -j ACCEPT

#in /etc/firehol/firehol.conf
iptables -A INPUT -p tcp --dport 5900 -j ACCEPT

hope this helps.

---

