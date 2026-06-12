---
title: "Connecting to the Internet in 8.10"
date: 2009-03-19
forum: Server Platforms
---

### Post by Utemetsu on 2009-03-19
Hi, I'm looking for a quick-and-probably-dirty way to connect my 8.10 server to the internet. It has the ethernet card, and it's plugged into the router. I have a hostname from Dyndns.com, and I'm fairly certain that my IP here is static -- I've also added lines to /etc/network/interfaces to reflect that; I think, as well as to /etc/hosts ...

Now, how do I connect the machine to the internet, and how do I know that it is indeed connected? (at present, sudo-apt get update does nothing but print a bunch of errors of not finding index files)


cheers,
Utemetsu

---

### Post by strife242 on 2009-03-19
First find out if you have LAN access by pinging your gateway.

ping <gw ip address>

If you get a response all is well, if not then something with your IP settings is wrong.

If this works, use the same command to ping either a hostname or an IP address you know of on the Internet. If this doesn't work but the first test did then something is probably not configured within your router.

If only IP addresses respond but not hostnames add your DNS servers to /etc/resolv.conf

Actually, this last bit may be the cause of apt-get not working as (afaik) they try to access repositorys using hostnames and not IP addresses.

---

### Post by Utemetsu on 2009-03-19
Would the gateway address be the IP of the router?


In /etc/hosts/interfaces there are a few IPs...I have no idea what each represent:

address
netmask
network
broadcast
gateway

---

### Post by Utemetsu on 2009-03-20
I pinged my router (which I'm assuming is the gateway) and got 0% packet loss. Now, It doesn't seem to be able to read hosts from the internet proper. (I tried pinging [www.google.com](www.google.com) ... I got bupkiss)

---

### Post by Alterax on 2009-03-20
Have you put an entry into /etc/resolv.conf with the IP addresses of your DNS servers?

---

### Post by Alterax on 2009-03-20
> **Utemetsu said:**
> Would the gateway address be the IP of the router?


In /etc/hosts/interfaces there are a few IPs...I have no idea what each represent:

address
netmask
network
broadcast
gateway

address is the ip address for your server
netmask is the subnet mask.  Usually 255.255.255.0
network is the first three octets of your ip address, followed by 0
  (example:  If your router is 192.168.1.1, your network would be 192.168.1.0.
Broadcast is the same as network, but replace 0 with 255
gateway is the address of your router.

Then as I mentioned a moment ago, add a DNS server entry into /etc/resolv.conf:

```
nameserver 208.67.222.222
```
(example above uses the OpenDNS servers).  That translates domain names into IP addresses.

Once that is done, restart your networking:```

sudo /etc/init.d/networking restart
```

And you should be all set.

---

### Post by Utemetsu on 2009-03-20
Thanks for the help. I'm fully connected to the internet now and I'm configuring the server. THANKS FOR ALL THE HELP EVERYONE!


Cheers,
Utemetsu

---

