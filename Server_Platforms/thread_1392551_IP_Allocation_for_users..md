---
title: "IP Allocation for users."
date: 2010-01-28
forum: Server Platforms
---

### Post by akshayy on 2010-01-28
hey guys, I have a ubuntu server 8.10 running on my dedicated server. How do I allocate IPs for users ? I have 3 IPs and 3 users running, I want each user to use a Single unique IP for all inbound and outbound traffic !! Also disallow a user from using the IP other then the one allocated to him.

I tried to work out a solution using Iptables, but it does not work I suppose!

Regards.

---

### Post by John Rivera on 2010-01-28
With my experience I would say that what you try to get is not simply possible unless you got 3 network cards in server, one for each user.

This is plainly due to how connections go. Your dedicated server probably has one ethernet adapter and IP address into what those 3 client computers connect to...

So you can't change IP address for each of these 3 clients unless they each also connect to server via own network adapter.

I am not sure what you try to get done with this, but if you want to prevent from folder access that is done via user rights management (chmod)

---

### Post by songshu on 2010-01-28
> **John Rivera said:**
> With my experience I would say that what you try to get is not simply possible unless you got 3 network cards in server, one for each user.

This is plainly due to how connections go. Your dedicated server probably has one ethernet adapter and IP address into what those 3 client computers connect to...

So you can't change IP address for each of these 3 clients unless they each also connect to server via own network adapter.

I am not sure what you try to get done with this, but if you want to prevent from folder access that is done via user rights management (chmod)

you could put multiple IP's on a single network card or several virtual interfaces on a single card each having its own IP, this would not be the problem.
The usefulness doesn't deem to hit me either though, it might help if you would explain the reason for this setup. you would like to filter on ip adress i presume on the network some where i guess.

VLAN would be the thing you would be looking for if you want to set several virtual eth0, eth1 etc...

[https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)

---

### Post by Skaperen on 2010-01-28
> **akshayy said:**
> hey guys, I have a ubuntu server 8.10 running on my dedicated server. How do I allocate IPs for users ? I have 3 IPs and 3 users running, I want each user to use a Single unique IP for all inbound and outbound traffic !! Also disallow a user from using the IP other then the one allocated to him.

I tried to work out a solution using Iptables, but it does not work I suppose!

Regards.Basically, IP addresses are associated with the system, not with users.

If you can limit usage so only one user is logged on at a time (could make sense at the console/desktop screen), you could have a script that sets only that one IP address to be in use at that time.  This won't allow other users to login via SSH and be limited to their IP address.

Another option is to run 3 virtual machines with a 4th IP for the whole system (not these 3 users) so you can manage it.  Each user runs in their own virtual machine.

---

### Post by akshayy on 2010-01-29
Thanks for the replies guys. This is a shared server, with my friends. We just wanted to make sure we don't end up using other guys IP and overlap, in basic internet applications that run on top of fluxbox. firefox, ftp client, custom network apps also, that we program for learning/testing integrated with our desktop applications. Apache vhosts helps for web sites, but for other apps, I have no idea.

Creating VM is a good idea, but its bit complicated and also we thought its a overhead and not efficient as just plain sharing.

---

### Post by lisati on 2010-01-29
> **Skaperen said:**
> Basically, IP addresses are associated with the system, not with users.

I'm inclined to agree: on my home network IP addresses tends to be associated with a particular piece of hardware, not who happens to be using it at the time.

I'd be more inclined to look into a scheme based around a combination of user privileges and current workload, but don't currently have any nuggets to offer about how it might be done.

---

### Post by BkkBonanza on 2010-01-29
If what you want is separation of resource/privileges then your best bet is installing openvps (or similar). It's very easy to install and get going and then you can each have a vps to provide total separation for each user. It's very efficient. Loss is a few percent typically. This is used by VPS hosting providers all over the net to provide low budget private servers for users and works really well. A more efficient and fancier install would be Virtuozzo but it costs a lot whereas openvps is the free open source version of this. 

It will probably take you less time to install that then try to figure out some half baked approach to trying to limit what is otherwise system resources. For that you would need to allocate interfaces based on user. I know **Wicd** (and perhaps Network Manager) can do that easily but it's not robust - any user with intention can work around whatever you do.

BTW what the user above says about needing more network adapters is pure hogwash. He shouldn't be replying with bad info about what he apparently doesn't know enough about.

---

