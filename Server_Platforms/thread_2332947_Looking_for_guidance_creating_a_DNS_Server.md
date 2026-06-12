---
title: "Looking for guidance creating a DNS Server"
date: 2016-08-05
forum: Server Platforms
---

### Post by Curlyp on 2016-08-05
Hello Community,

I am new to LINUX and I'm trying to get an understanding of it and what I want it to do for me.  I've been reading several forums and watching YouTube videos regarding DNS, but I'm having trouble grasping it.  I feel it might be that LINUX is a bit of a learning curve; and the fact that these DNS guides leave out information that a typical LINUX user would know.  I'm not looking for someone to "hand-hold me", but looking for guidance and help with that I want to do.

So, my overall task is to host my own web server.  Instead of paying someone for a DNS name (example, curlyphome.com), I figured I would setup my own DNS server.  Now, I know there are free DNS places like NoIP, but I don't want a name with their extension, ex., curlyphome.getsmile.com

First thing I did was create a LINUX VM using the ubuntu 16.04.1 server distro.  I installed apache2 for the web service, PHP, and MySQL.  I then installed bind9 using the following command: sudo apt-get install bind9.  After that, i'm kind of lost.  The four to five guides I have read show different steps and are not in sync. A couple other parts of the setup that I don't fully understand is the /etc/network/interfaces and the /etc/hosts.  Some of the guides configure the /etc/network/interfaces and the /etc/hosts differently, while some make changes to the /etc/hosts.

If I could get some guidance and help, I would really appreciate it.

Thank you all in advance!

---

### Post by darkod on 2016-08-05
From what you wrote I didn't understand whether you already have a registered domain or not???

The thing is you can't simply "invent" a domain and say it's yours. You have to use an official registrar, and that way it's assured that two people can't "buy" the same domain.

Most registrars would offer you some kind of DNS, so it might not be really necessary to make your own DNS server.

But if you do want to create your own DNS server, this is a good place to start: [https://help.ubuntu.com/lts/serverguide/dns.html](https://help.ubuntu.com/lts/serverguide/dns.html). It has good and short basic info how to configure bind.

In general you don't need to touch the server's /etc/hosts for setting up DNS, and the /etc/network/interfaces is used for the network settings, not for setting up DNS service. In there you only set up the server IP address, netmask, gateway, and which DNS servers should the server use (not to be confused with the DNS service it will offer). In theory when you have bind on the server you can use it for DNS resolving.

---

### Post by Curlyp on 2016-08-05
> **darkod said:**
> From what you wrote I didn't understand whether you already have a registered domain or not???

The thing is you can't simply "invent" a domain and say it's yours. You have to use an official registrar, and that way it's assured that two people can't "buy" the same domain.

Most registrars would offer you some kind of DNS, so it might not be really necessary to make your own DNS server.

But if you do want to create your own DNS server, this is a good place to start: [https://help.ubuntu.com/lts/serverguide/dns.html](https://help.ubuntu.com/lts/serverguide/dns.html). It has good and short basic info how to configure bind.

In general you don't need to touch the server's /etc/hosts for setting up DNS, and the /etc/network/interfaces is used for the network settings, not for setting up DNS service. In there you only set up the server IP address, netmask, gateway, and which DNS servers should the server use (not to be confused with the DNS service it will offer). In theory when you have bind on the server you can use it for DNS resolving.

Hi darkod - thanks for your reply.

No, I do not have a registered domain name.  I was under the impression that setting up a DNS server would allow me to have my own domain name without purchasing one.  I take it that is completely incorrect?  On the other hand, I may have a complete misunderstanding what what a DNS server does.  Based on your experience, does hosing your own web server (with apache2) require a DNS server?

Since I am using the LINUX server as a web server, should I reconfigure the /etc/network/interfaces to set the IP as static?  I've already reserved the computer's IP and the VM's IP through my router so it doesn't change with DHCP.

Thanks again!

---

### Post by darkod on 2016-08-05
1. No, setting up DNS server does not allow you to own a domain. You have to purchase one with a registrar/reseller. The DNS server is telling the clients the IP where to find the web server when they type the domain name in the browser. This basic functionality can usually be found in the registrar control panel so you don't need to bother with it.

2. Hosting with apache2 or any other web server does not require DNS strictly speaking. But the domain does need a DNS server which will contain the A records with the IP of the web server.

3. I always set static IP on servers but you can keep it as dhcp with reservation if you prefer. But you have to consider that your server at home has private IP and as such is not reachable from the internet. You have to forward port 80 on your router to your server private IP and in the DNS A record use the router public IP (which might be dynamic and might be changing from time to time). That's why hosting on dynamic public IP is more complex...

---

### Post by Curlyp on 2016-08-05
> **darkod said:**
> 1. No, setting up DNS server does not allow you to own a domain. You have to purchase one with a registrar/reseller. The DNS server is telling the clients the IP where to find the web server when they type the domain name in the browser. This basic functionality can usually be found in the registrar control panel so you don't need to bother with it.

2. Hosting with apache2 or any other web server does not require DNS strictly speaking. But the domain does need a DNS server which will contain the A records with the IP of the web server.

3. I always set static IP on servers but you can keep it as dhcp with reservation if you prefer. But you have to consider that your server at home has private IP and as such is not reachable from the internet. You have to forward port 80 on your router to your server private IP and in the DNS A record use the router public IP (which might be dynamic and might be changing from time to time). That's why hosting on dynamic public IP is more complex...

Ah, wow, I have been completely misguided then! Okay, then I won't worry about setting up a DNS server.  It doesn't sound like it's needed for anything I am trying to accomplish.

What is the best practice for setting static IP on my web server?  Once I set it on the server, should I keep my router's DHCP reservation?  Correct, I was under the impression that I will have to forward port 80 so my web server can be reachable outside of my network.  So, lets say my server's IP address is 154.163.300.400, once I forward port 80, anyone I give my IP too will be able to reach my site.  However, if I pay for a domain name, then I can configure it to be curlypshome.com.  Besides paying for the domain name, the only other way to get some type of FQDN is to use something like NoIP.com?

---

### Post by darkod on 2016-08-05
I don't know about NoIP offers in details. They might offer FQDN without actually purchasing a domain.

And yes, after forwarding port 80 and assuming your ISP is not blocking it, any person knowing your public IP can access the site. You can use NoIP to automatically detect the dynamic IP when it changes so that traffic goes to your server correctly.

After you set static IP on the server it doesn't matter much if you keep the reservation on the router or not. It will not query the router for dhcp lease. But make sure to select static IP outside the dhcp range. To avoid possibility of duplicates.

---

### Post by Curlyp on 2016-08-05
> **darkod said:**
> I don't know about NoIP offers in details. They might offer FQDN without actually purchasing a domain.

And yes, after forwarding port 80 and assuming your ISP is not blocking it, any person knowing your public IP can access the site. You can use NoIP to automatically detect the dynamic IP when it changes so that traffic goes to your server correctly.

After you set static IP on the server it doesn't matter much if you keep the reservation on the router or not. It will not query the router for dhcp lease. But make sure to select static IP outside the dhcp range. To avoid possibility of duplicates.


Thanks for all the info.  I really appreciate it.

Yes, you are right about NoIP, I can use it to keep my dynamic IP "Static" in the sense.

To configure my server with a static IP, I perform the following:

sudo nano /etc/network/interfaces

auto lo eth0
iface lo inet loopback
iface eth0 inet static
address xxx.xxx.xxx.xxx(enter your ip here)
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx(enter gateway ip here,usually the address of the router)

then I perform a manual reset of the next with the following command:sudo /etc/init.d/networking restart

Is this correct?

---

### Post by darkod on 2016-08-05
Usually people group the auto with the interface, and you need to specify which dns servers to use (for example google dns). Something like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address x.x.x.x
   netmask 255.255.255.0
   gateway x.x.x.x
   dns-nameservers 8.8.8.8 8.8.4.4
```

When you restart the networking service or the whole server, it will use the new IP.

---

### Post by Curlyp on 2016-08-05
> **darkod said:**
> Usually people group the auto with the interface, and you need to specify which dns servers to use (for example google dns). Something like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address x.x.x.x
   netmask 255.255.255.0
   gateway x.x.x.x
   dns-nameservers 8.8.8.8 8.8.4.4
```

When you restart the networking service or the whole server, it will use the new IP.

Great!  Thank you for all your help.

---

