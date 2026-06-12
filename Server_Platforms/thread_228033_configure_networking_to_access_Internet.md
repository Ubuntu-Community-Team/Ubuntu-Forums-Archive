---
title: "configure networking to access Internet??"
date: 2006-08-02
forum: Server Platforms
---

### Post by tlyczko on 2006-08-02
I'm new to Ubuntu and Linux, but not to the general concepts involved, due to working a lot with Windows XP Pro and Windows Server.

I'm following a guide to set up Ubuntu 6.06 LTS for VMware, from:
[http://www.proxmox.com/cms_proxmox/cms/front_content.php?client=1&lang=1&idcat=11](http://www.proxmox.com/cms_proxmox/cms/front_content.php?client=1&lang=1&idcat=11)

It contains information about how to set up networking, and I have the following so far:

in the interfaces file:

# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.0.21
netmask 255.255.255.0
gateway 172.16.0.1 

in the resolv.config file
search essexarc.local (name of the Windows domain in DNS)
nameserver 172.16.0.11

I also added the external ISP's DNS server addresses to resolv.config.

restarted networking, but apt-get update says it can't connect to the internet, it gives 'connection refused 111' messages, ubuntu recognized all the hardware fine, no errors etc.

This server is behind a firewall too, but other Windows servers can get to the Internet for updates and such on port 80.

I looked at man interfaces but didn't see anything that jumped out at me.

What am I missing or not doing??

Thank you, Tom

---

### Post by tlyczko on 2006-08-02
Now I am getting messages about temporarily not able to resolve instead of connection refused 111 messages.

Should I update my sources.list or is there something else I should do to enable apt-get to work properly??

Thank you, Tom

---

### Post by michaluxa on 2006-08-02
Hi Tom,

I have not had a look at the guide you are following but what I could suggest are the following tests:

1. does pinging the gateway (router) work?  i.e. ping 172.16.0.1 
2. if yes try pinging an external IP i.e. ping 64.233.167.104 (google)
3. if yes try pinging a host name i.e. ping google.com

if 1. fails: hardware problem or networking not properly installed
if 2. fails: firewall problem
if 3. fails and 2 doesn't: DNS problem

I also find your internal IP address choice a bit unusual: 172.16.0.1. 
I am used to something like 192.168.0.1 or 192.168.1.1 for a router, but I am no networking expert - it might be perfectly o.k.

See how your test go...

It might help if you could describe your network setup a bit more in detail.

Cheers,

---

### Post by tlyczko on 2006-08-03
Hi, I discovered it's to do with the firewall, its configuration needs some changes. Thank you for pointing me in the right direction.
BTW the IPs you're used to are Class C reserved IPs, the ones we have are Class B reserved IPs.
Thanks, Tom

---

### Post by tlyczko on 2006-08-03
Well, we set the firewall to allow Internet access for the needed IP range but nothing yet...Thanks for your help, though. Tom

---

