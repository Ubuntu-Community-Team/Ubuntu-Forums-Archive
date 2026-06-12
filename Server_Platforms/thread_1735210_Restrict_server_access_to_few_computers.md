---
title: "Restrict server access to few computers"
date: 2011-04-21
forum: Server Platforms
---

### Post by JoyceBabu on 2011-04-21
I want to configure a remote internet facing server as git server. I would like to restrict access to the server to a few systems (access is restricted to select computers, not users). 

I first thought of using ssh key, but the key can be copied to another system hence that alone is not sufficient. 

I am having a dynamic IP, so simple IP based firewall blocking is also not possible. 

I was thinking about the possibility of using both SSH Key and IP based access. Is it possible to update the firewall rule whenever my ip gets changed?

Thanks

---

### Post by HermanAB on 2011-04-21
Howdy,

Maybe you should look into the old technique of 'port knocking'.  You connect to one service in order to gain access to another:
[http://www.portknocking.org/](http://www.portknocking.org/)

Something like this has been done for many years with mail servers in the form of pop-before-smtp.

---

### Post by JoyceBabu on 2011-04-22
Thank you for the tip on Port Knocking, Herman.

Can I restrict connections based on MAC address?

---

### Post by SeijiSensei on 2011-04-22
> **JoyceBabu said:**
> I am having a dynamic IP, so simple IP based firewall blocking is also not possible.

It doesn't matter what the server's IP is.  What matters is whether the clients' IPs are known and reliably static.  Then you just write rules for the source IPs you want to permit, like:

```
iptables -A INPUT -i eth0 -s 10.10.10.10 -j ACCEPT
[similar rules for other IPs]
iptables -A INPUT -i eth0 -j REJECT
```

You can't use MAC addresses because the server can't see them at all.  If all the machines were on the same network, you could use reverse ARP to check MACs, but that only works within a single subnet, not over the Internet.  (If you're curious about ARP, run "arp -a" on a machine that's connected to a network.  You'll get a list of IPs and corresponding MACs.)

---

### Post by JoyceBabu on 2011-04-23
Thank you SeijiSensei

I can't update iptables directly because I am having a dynamic IP.

CSF had an option to resolve dynamic IP, but looks like it works only in kernel 2.6.20 and above (I am having 2.6.18)

If I configure OpenVPN correctly, will I be able to use the reverse arp check?

> **SeijiSensei said:**
> It doesn't matter what the server's IP is.  What matters is whether the clients' IPs are known and reliably static.  Then you just write rules for the source IPs you want to permit, like:

```
iptables -A INPUT -i eth0 -s 10.10.10.10 -j ACCEPT
[similar rules for other IPs]
iptables -A INPUT -i eth0 -j REJECT
```

You can't use MAC addresses because the server can't see them at all.  If all the machines were on the same network, you could use reverse ARP to check MACs, but that only works within a single subnet, not over the Internet.  (If you're curious about ARP, run "arp -a" on a machine that's connected to a network.  You'll get a list of IPs and corresponding MACs.)

---

### Post by TheFu on 2011-04-23
> **JoyceBabu said:**
> I want to configure a remote internet facing server as git server. I would like to restrict access to the server to a few systems (access is restricted to select computers, not users). 

I first thought of using ssh key, but the key can be copied to another system hence that alone is not sufficient. 

I am having a dynamic IP, so simple IP based firewall blocking is also not possible. 

I was thinking about the possibility of using both SSH Key and IP based access. Is it possible to update the firewall rule whenever my ip gets changed?

Thanks

The way I'd do this (and I have), is to 
a) setup key-based ssh remote access
b) disable password based connections
c) Move the ssh listener to a non-standard port
d) Install and configure fail2ban, so any failed attempts are automatically banned in the firewall for 5 min, or an hour, or a month, or forever.
e) setup the ~/.ssh/config file on your client machine to make access to the server easy.

If you have a good idea which subnets the clients will come from, you can block access from everywhere else, if you like, but that really isn't needed with fail-2-ban running.

Whatever you do, don't allow password-based remote connections.

---

### Post by JoyceBabu on 2011-04-24
Thanks for all the replies. I was able to solve the issue using CSF itself (I was wrong about the above mentioned issue). I have setup a dynamic dns account with one of the providers and configured CSF to update my ip every one minute. I have also setup key based login to make it more secure.

---

