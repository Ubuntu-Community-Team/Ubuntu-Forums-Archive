---
title: "How to find out a servers IP Address"
date: 2010-02-11
forum: Server Platforms
---

### Post by mjfroggy on 2010-02-11
OK

I was a weird question but for some reason my local server here is not reachable when I type on the hostname so I am wanting to know if I am on the machine via ssh (I have a monitor and keyboard plugged into the tower)

How do I figure out what the servers IP address is? I have ubuntu server 9.10 and I looked at the etc/host, etc/hostname files and they have the correct server hostname

Thanks

---

### Post by pirateghost on 2010-02-11
sudo ifconfig

that will give you the ip address.

your local DNS needs to have entries for the servers if you want to be able to use hostname to find them on your network

---

### Post by mjfroggy on 2010-02-11
ty and would I be correct in thinking the broadcast is the ip that I would get to the server with?

What if their is only a subnet mask ip listed?

---

### Post by jowilkin on 2010-02-11
> **mjfroggy said:**
> ty and would I be correct in thinking the broadcast is the ip that I would get to the server with?

What if their is only a subnet mask ip listed?

Broadcast is the address used for broadcast traffic, you likely will not use it.  You want the address listed next to "inet addr:".  If there is only a subnet mask listed then the server likely does not have an ip address assigned to it.

---

### Post by mjfroggy on 2010-02-11
thank you

is there a comman to get an ipaddress for the server (this is on a network which functions behind a router)

---

### Post by joberly on 2010-02-11
Are you looking for the internal address of the server? Or the external IP that the router gets?

ifconfig - will get you the IP address of the interface of whatever machine you are currently on/logged into.

sudo nmap -sP 192.168.1.0/24 - will get you IP addresses of every device on the network 192.168.1.* (including host names if they are defined)

Simply going to [www.whatismyip.com](www.whatismyip.com) will get you the external IP.

---

### Post by mjfroggy on 2010-02-11
thank you I figured out what I needed

---

