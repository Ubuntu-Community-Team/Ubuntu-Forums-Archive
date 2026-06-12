---
title: "[SOLVED] Reference new server by name"
date: 2008-07-06
forum: Server Platforms
---

### Post by fballem on 2008-07-06
I have a new server, which I installed using instructions provided in: [http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html) and it appears to work.

I have WebAdmin enabled, and if I enter the IP address directly, then I can access the server (I have to setup a security certificate exception, but that's straight forward).

I have probably missed a step (or misunderstood a step), but how do I reference the server by name?

I am a newbie, so please be merciful!

Many thanks,

---

### Post by fjgaude on 2008-07-06
Go into the /etc/hosts file and add the name and IP address to the list:

frank@sunshine:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 sunshine

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.101 moonlight
192.168.45.128 happystar
192.168.1.104 stardust

That should do what you wish.

---

### Post by fballem on 2008-07-06
> **fjgaude said:**
> Go into the /etc/hosts file and add the name and IP address to the list:

frank@sunshine:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 sunshine

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.101 moonlight
192.168.45.128 happystar
192.168.1.104 stardust

That should do what you wish.

Thanks - I assume that I need to do this for any workstation in the house.

Many thanks,

---

### Post by fjgaude on 2008-07-06
Yes, for any workstation that you wish to be able to use server names, in addition to IP addresses to access.

---

### Post by mbeach on 2008-07-06
if you are trying to connect to the new server from an 'old' machine on the network, it could be a matter of sending the hostname to whatever is acting as the DHCP server on your network.  

edit the /etc/dhcp3/dhclient.conf file, uncommenting the 
send host-name "<yourservername>"

placing the appropriate hostname in place of <yourservername>

not sure if you need to restart networking afterwards or not - if so:
sudo /etc/init.d/networking restart

I suppose Its a matter of opinion and circumstance if its a better option to edit the hosts files of all other machines on the network.

[EDIT: looks like I may not be quite up to speed with Hardy - and also assumed you were using dhcp to get the ip address]

---

### Post by fballem on 2008-07-07
> **mbeach said:**
> if you are trying to connect to the new server from an 'old' machine on the network, it could be a matter of sending the hostname to whatever is acting as the DHCP server on your network.  

edit the /etc/dhcp3/dhclient.conf file, uncommenting the 
send host-name "<yourservername>"

placing the appropriate hostname in place of <yourservername>

not sure if you need to restart networking afterwards or not - if so:
sudo /etc/init.d/networking restart

I suppose Its a matter of opinion and circumstance if its a better option to edit the hosts files of all other machines on the network.

[EDIT: looks like I may not be quite up to speed with Hardy - and also assumed you were using dhcp to get the ip address]

DHCP is provided by a router, not a server. The new server has an IP Address that is not assigned by DHCP. Unfortunately, the router does not have facilities for defining names for local servers. Fortunately, this is a very small environment, so it is not unreasonable to edit the file on the workstations.

The primary reason for the LAMP server is as a learning environment. New to Linux, but having fun.

Thanks,

---

