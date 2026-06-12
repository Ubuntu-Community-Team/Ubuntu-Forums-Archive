---
title: "[SOLVED] Cannot resolve local network names, /etc/hosts ignored?"
date: 2008-11-28
forum: Server Platforms
---

### Post by leandromartinez98 on 2008-11-28
Dear all, I've configured a local network (in order to build a cluster). Everything is working fine, except for the fact that the none of the machines can resolve the hostnames of the other machines in the local network. I've already searched many forums and the most standard solutions do not work. Here is the situation. For example, one of the machines is

hostname:  node002    ip:  192.168.0.002

(the IP is provided to the nodes by fixed-ip dhcp, and it worked perfectly during instalagion of Ubuntu Server on the nodes, including the fact that the nodes found by themselves the hostname).

Results, when giving this command from the master node:

[PHP]% ping node002
ping: unknown host node002[/PHP]

[PHP]% ping 192.168.0.002
PING 192.168.0.002 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=0.125 ms[/PHP]

[PHP]% nslookup node002
Server:		143.106.51.37
Address:	143.106.51.37#53

** server can't find node002: NXDOMAIN[/PHP]

[PHP]% nslookup 192.168.0.002
Server:		143.106.51.37
Address:	143.106.51.37#53

** server can't find 192.168.0.002: NXDOMAIN[/PHP]

[PHP]% ssh node002
ssh: Could not resolve hostname node002: Name or service not known[/PHP]

[PHP]% ssh 192.168.0.002  
leandro@node002:~% (it works)[/PHP]

---> I can ssh to and from the nodes using IPs, and even my parallel
     applications run fine.


This is my /etc/hosts file:

[php]
127.0.0.1	localhost
10.106.51.133	barao.iqm.unicamp.br	barao
192.168.0.100     barao
192.168.0.001     node001
192.168.0.002     node002

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/php]


This is the /etc/nsswitch.conf:

[php]
passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
[/php]



This files seem to be OK according to other discussions I've read.

Anyway, it seems that ping, ssh, and all other services are
ignoring the /etc/hosts file. Anyone has any clue on what can be
the problem?

Thank you very much,
Leandro.

---

### Post by MJN on 2008-11-28
> **leandromartinez98 said:**
> Anyway, it seems that ping, ssh, and all other services are ignoring the /etc/hosts file.
 
I trust **ping localhost** doesn't work either then?
 
Just to check, these hosts files are on all the machines right? Or at least the machine you're testing from/on?
 
Mathew

---

### Post by leandromartinez98 on 2008-11-28
> **MJN said:**
> I trust **ping localhost** doesn't work either then?
 
Just to check, these hosts files are on all the machines right? Or at least the machine you're testing from/on?
 
Mathew


No, no, ping localhost works on all machines. The /etc/hosts file is
on the machine in which I'm doing the tests (and in all machines
as well). In the master node, which
is called "barao", the "ping barao" works. In the nodes, the
"ping node002" (for example), also works. The problem is really
name resolution within the machines of the local network. 

The master node has two network cards. Maybe this has something to
do with the problem, so here is my /etc/network/interfaces file:

[php]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The secondary network interface
auto eth1 eth0
# The primary network interface
iface eth0 inet static
	address 10.106.51.133
	netmask 255.255.255.192
	network 10.106.51.128
	broadcast 10.106.51.191
	gateway 10.106.51.129
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 143.106.51.37
	dns-search iqm.unicamp.br

iface eth1 inet static
	address 192.168.0.100
	netmask 255.255.255.0
[/php]

I'm not sure if this has something to do with the problem because
the nodes only have one network card and they have exactly the same
problem.

Thanks,
Leandro.

---

### Post by MJN on 2008-11-28
Can the nodes ping each other by name? Or do the symptoms apply equally to all machines?
 
I'm stumped. I would say that /etc/hosts must be being consulted given that the resolution of localhost and the machine name is working, but why no other names..?
 
Mathew

---

### Post by leandromartinez98 on 2008-11-28
> **MJN said:**
> Can the nodes ping each other by name? Or do the symptoms apply equally to all machines?
 
I'm stumped. I would say that /etc/hosts must be being consulted given that the resolution of localhost and the machine name is working, but why no other names..?
 
Mathew


FOUND THE PROBLEM! Something I would not imagine never, and probably it would be better that it didn't lead to a problem, but your suggestion of pinging the nodes between them led to the solution! Actually the problem occurred for all machines, the nodes could not ping themselves by name, but they could by IP. Then, now I went to a node to ping some other node in order to post ther result:

[php]
node001% ping node002
ping: unknown host node002
[/php]

as expected. Then, by IP:

[php]
node001% ping 192.168.0.002
192.168.0.002
PING 192.168.0.002 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=0.112 ms
[/php]

And it works. Now, note the ping report:

PING 192.168.0.002 **(192.168.0.2)**

It says that the IP of the node is equivalent to "192.168.0.2", that
is, the "002" can be changed by "2" (of course). 

Now I noticed that, and then I went to /etc/hosts, and changed
the "002" by "2", meaning:

192.168.0.2 node002

And, now:

[php]
node001% ping node002
PING node002 (192.168.0.2) 56(84) bytes of data.
64 bytes from node002 (192.168.0.2): icmp_seq=1 ttl=64 time=0.121 ms
[/php]

It works!

Well, conclusion:

[B]When your IP contains zeroes to the left, don't put the zeroes in the
/etc/hosts file, because then the IP is not recognized.[/B]

Thank you very much for the good thoughts and the chat! I'm marking this thread as solved.

Leandro.

---

### Post by lswb on 2008-11-28
> **leandromartinez98 said:**
> FOUND THE PROBLEM! 

Well, conclusion:

[B]When your IP contains zeroes to the left, don't put the zeroes in the
/etc/hosts file, because then the IP is not recognized.[/B]

Thank you very much for the good thoughts and the chat! I'm marking this thread as solved.

Leandro.

Man, who would have thought it? I'm certainly going to file that away for future reference. Wonder why the leading zeroes aren't parsed properly. Even if it's being read as octal, 002 and 2 are still the same.

---

### Post by MJN on 2008-11-28
So **ping barao** from one of the nodes worked all along then? You said the problem existed for all configurations!
 
I must admit it did look a little odd you adding leading zeroes to the IP addresses but figured it didn't matter given the direct pings were working. Obviously it does!
 
Mathew

---

### Post by leandromartinez98 on 2008-11-28
> **MJN said:**
> So **ping barao** from one of the nodes worked all along then? You said the problem existed for all configurations!
 
I must admit it did look a little odd you adding leading zeroes to the IP addresses but figured it didn't matter given the direct pings were working. Obviously it does!
 
Mathew

Yes, "ping barao" worked. Actually it didn't, because the /etc/hosts
file of the nodes didn't have the corresponding line. But obviously that
was not part of that problem. Sorry about the unprecise
information.

Actually in my ingnorance I didn't know that these zeroes were "leading" zeroes, I thought that .1 was different from .001, that is why I was putting them all the time. Now I changed that on the dhcp configuration files as well, maybe this zeroes could be causing trouble in other places.

Thanks,
Leandro.

---

