---
title: "Firewall hits from mutiple ports and IPs, HELP"
date: 2009-09-15
forum: Security
---

### Post by kyle787 on 2009-09-15
Okay so I need more help I set up UFW with

[HTML]
sudo ufw default deny
sudo ufw logging on
sudo ufw enable 
[/HTML]

But recently my firewall (running firestarter and UFW) has been blocking connections from source xxx.xxx.x.108 to destination xxx.xxx.x.255 the protocol is UDP and the service is Samba (SMB) and is using ports 137 and 138.  And I just got another hit from 0.0.0.0 to 255.255.255.255 using port 67 protocol UDP using DHCP.
1.  Should I be concerned? 
2.  If I should be what should I do?
3.  Should I just close ports 67, 137, and 138?

Thanks for your help I provided pretty much everything I know.

---

### Post by lovinglinux on 2009-09-15
If you don't have any server running and listening to those ports, then they are already closed. Besides, since the firewall blocked the connections, why bother?

Running Firestarter and UFW at the same time is not a good idea. They are both firewall managers, which means they simply allow you to create the iptables rules without knowing the commands. Besides, when you apply a new rule with one of them, the rules created by the other are probably overwritten. Nevertheless, using both might result in some conflicts. I recommend using only UFW. If you need a GUI then install GUFW.

Another thing that you need to consider is if you really need a firewall. Unless you have a server like samba, ssh or something else listening to ports and you want to limit the access to specific machines (from your lan for example), then a firewall is probably not necessary. Ubuntu comes with no server by default, so all ports a virtually closed and all connection attempts on any port will be refused. No firewall needed in this case.

I recommend reading [Unbuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial, since it explains the differences between Windows and Linux mindsets.

---

### Post by kyle787 on 2009-09-15
> **lovinglinux said:**
> If you don't have any server running and listening to those ports, then they are already closed. Besides, since the firewall blocked the connections, why bother?

Running Firestarter and UFW at the same time is not a good idea. They are both firewall managers, which means they simply allow you to create the iptables rules without knowing the commands. Besides, when you apply a new rule with one of them, the rules created by the other are probably overwritten. Nevertheless, using both might result in some conflicts. I recommend using only UFW. If you need a GUI then install GUFW.

Another thing that you need to consider is if you really need a firewall. Unless you have a server like samba, ssh or something else listening to ports and you want to limit the access to specific machines (from your lan for example), then a firewall is probably not necessary. Ubuntu comes with no server by default, so all ports a virtually closed and all connection attempts on any port will be refused. No firewall needed in this case.

I recommend reading [Unbuntu Security]("http://ubuntuforums.org/showthread.php?t=765421") tutorial, since it explains the differences between Windows and Linux mindsets.

Thank you, but how do I protect my computer against hackers with out a firewall?  Is there something else that I'm missing? Do I need to install another program to protect against hackers?

---

### Post by lovinglinux on 2009-09-15
> **kyle787 said:**
> Thank you, but how do I protect my computer against hackers with out a firewall?  Is there something else that I'm missing? Do I need to install another program to protect against hackers?

They can't hack you if you do not have a server listening to a port. Let's say you just have installed Ubuntu and didn't installed any additional applications. If you go to a firewall testing site, like [PC Flank](http://www.pcflank.com/scanner1.htm) or [ShieldsUP](https://www.grc.com/x/ne.dll?bh0bkyd2) and scan all your ports, like a hacker would do (not with the same program of course), the test will report that all your ports are closed. Which means any connection attempt from a remote computer will be refused. So, nobody can access your computer from the outside, even if you are not running a firewall. The firewall simply closes a port that is open to the outside when you have a server listening to the port. But your ports are all closed, then why do you need a firewall?

A firewall is indispensable on Windows, because it comes with several services which listen to several ports on a default installation. Ubuntu comes with no service listening to any ports. So they are all closed. Unless you open a port, by installing a server like ssh or samba, then a firewall is not needed, since all unrequested incoming connections will be refused anyway.

---

### Post by sopadeajo on 2009-09-16
"They can't hack you if you do not have a server listening to a port"

I do not believe this is true.There are probably fifty different ways to hack. One could probably be as simple as port 80 and http.

---

### Post by wojox on 2009-09-16
There was no mention of port 80 being open.

Like lovinglinux said without a service listening there's no worry. 

Go pick up a TCP/IP book and read it yourself.

---

### Post by __p1n__ on 2009-09-16
> **wojox said:**
> ...
Like lovinglinux said without a service listening there's no worry ...


That's not strictly true.  An unfiltered packet will be processed by ip_rcv_finish and get dropped inside ip_route_input owing to the port being closed.  A filtered packet will get dropped at the netfilter hook before ip_rcv_finish is called.

It never hurts to protect the kernel ;)

---

### Post by lovinglinux on 2009-09-16
> **__p1n__ said:**
> That's not strictly true.  An unfiltered packet will be processed by ip_rcv_finish and get dropped inside ip_route_input owing to the port being closed.  A filtered packet will get dropped at the netfilter hook before ip_rcv_finish is called.

It never hurts to protect the kernel ;)

As far as I understand, they both will be dropped, just at different levels right?

Would you mind elaborating a little bit more, with an example of which case the attacker could gain control to your machine?

---

### Post by The Cog on 2009-09-16
> **kyle787 said:**
> But recently my firewall (running firestarter and UFW) has been blocking connections from source xxx.xxx.x.108 to destination xxx.xxx.x.255 the protocol is UDP and the service is Samba (SMB) and is using ports 137 and 138.  And I just got another hit from 0.0.0.0 to 255.255.255.255 using port 67 protocol UDP using DHCP.
1.  Should I be concerned? 
Yes. For two separate reasons:

Firstly, you are running both firestarter and UFW. Since you aren't running any listening services it doesn't really matter, but both these firewalls are designed to configure iptables. Running both is likely to produce conflicts between the two sets of instructions so you don't actually know what firewall rules are finally in effect. This will matter if you do ever install a service that needs protecting.

Secondly, you have another computer on your network. It seems to be issuing DHCP requests. If you're not aware of another computer being connected to your home network, you should investigate further.

---

### Post by kyle787 on 2009-09-16
> **The Cog said:**
> Yes. For two separate reasons:

Firstly, you are running both firestarter and UFW. Since you aren't running any listening services it doesn't really matter, but both these firewalls are designed to configure iptables. Running both is likely to produce conflicts between the two sets of instructions so you don't actually know what firewall rules are finally in effect. This will matter if you do ever install a service that needs protecting.

Secondly, you have another computer on your network. It seems to be issuing DHCP requests. If you're not aware of another computer being connected to your home network, you should investigate further.

Thank you I was really confused did some Googling but you fully explained it.  I removed firestarter and got GUFW I think its called cause I'm not the greatest and using the terminal and for more serious things I like something that I can really see what I'm doing.
And I have 3 other computers and the network so that would explain it..

---

### Post by ApEkV2 on 2009-09-16
> **kyle787 said:**
> Thank you, but how do I protect my computer against hackers with out a firewall?  Is there something else that I'm missing? Do I need to install another program to protect against hackers?

Ubuntu already has a firewall built in. Firestarter for example is just a program to configure that firewall. 
So you don't have to do anything. If you just installed Ubuntu (and keep it updated) that alone is pretty much impenetrable.

---

