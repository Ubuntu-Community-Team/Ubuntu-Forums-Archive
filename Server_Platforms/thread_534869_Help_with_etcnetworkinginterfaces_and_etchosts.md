---
title: "Help with /etc/networking/interfaces and /etc/hosts"
date: 2007-08-25
forum: Server Platforms
---

### Post by ljohnston on 2007-08-25
I am about two months into using Ubuntu Linux in desktop form on both my desktop pc and my laptop.  I now have a spare tower, and have just installed Ubuntu's LAMP on it.  However, I am a novice, and having great difficulty configuring a server.  I thought it would be cool to host my own web page.  

The trouble I run into is this:  when I try to set a static IP address for the server, it loses all connectivity to the internet, and I can no longer access it from the outside via SSH or puTTY.  However, if I set /etc/networking/interfaces to retrieve the IP automatically via DHCP, I can access my server via SSH and puTTY.  While this works, it isn't ideal.  Lastly, I am having trouble assigning a name to my server that is accessible from the outside.  I am guessing this is done via /etc/hosts.

I'm sure most of the trouble I am having is because of my lack of knowledge about the way IP addresses work, but I was hoping someone could give me some pointers or a place that can put me in the right direction.  Help me learn!

---

### Post by koenn on 2007-08-25
> **ljohnston said:**
> I am having trouble assigning a name to my server that is accessible from the outside.  I am guessing this is done via /etc/hosts.
It's either done through DNS, or from /etc/hosts _on the machine that wants to access your serve_r, not on* your* server. obviously, DNS is the preferred method. 
You might want to check dynDNS ( [http://www.dyndns.com/](http://www.dyndns.com/) ) and you may need to forward port 80 on he router that connects you to the internet. There are some threads around that explain this. 

for your static IP address : show the contents of the interfaces file - not much anyone can do without at least having a look there first.

---

### Post by southernman on 2007-08-25
Yes, you assign your hostname in /etc/hosts and /etc/hostname. But without someone (DNS server) to resolve the name for you... it won't work. As koenn suggested you can use dyndns or zoneedit for this type of service.

You can use this as a template:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.xxx
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
network 192.168.1.0



These three little files are a mere drop in the bucket for what you need. Check out the stickies in this subforum and read, read, read.

Good luck..

---

### Post by ljohnston on 2007-08-26
Thanks for the help!  I will read and explore a few of these options and post a reply if I have any other questions along the way.

---

