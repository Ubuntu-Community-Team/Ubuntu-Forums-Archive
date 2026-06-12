---
title: "Ubuntu Update Server Pool"
date: 2008-12-02
forum: Server Platforms
---

### Post by swpx5LFj on 2008-12-02
In order to create a firewall restriction rule on the IP address of my ubuntu server machine, I would like to know if there are some IP addresses pools that point to canonical infrastructure.

Today I have a rule like this:

*$Server_IP -> ANY on port 80 and 443*

And I would like to change it in something like:

*$Server_IP -> $Update_Pool_Addresses on port 80 and 443*

Any suggestion?

Tnx in advance

---

### Post by Masuran on 2008-12-02
I don't know of a list of offical IP adresses, but check your sources.list
Some I know of right now: 

* archive.canonical.com
* archive.ubuntu.com
* security.ubuntu.com

---

### Post by swpx5LFj on 2008-12-02
I see...
As in many source file there are lots of mirror servers as indicated by you using the * before addresses.

I can't use host in my firewall rules system (as usual) and the IP address of a mirror can change during time ... uhm ... !

---

### Post by cdenley on 2008-12-02
> **d0minique said:**
> I see...
As in many source file there are lots of mirror servers as indicated by you using the * before addresses.

I can't use host in my firewall rules system (as usual) and the IP address of a mirror can change during time ... uhm ... !

You can either assume the IP's won't change, create a script that creates your iptables rules based on the IP addresses of the mirrors at the time the script is run and run the script daily, or create your own mirror and use that on the server you're trying to restrict.

---

### Post by swpx5LFj on 2008-12-02
I'm talking about enterprise firewall solutions not an iptable script based firewall... anyway

may be interesting the suggestion of mirroring ... not applicable but interesting

---

