---
title: "Inital Server Security Best Practice"
date: 2014-03-13
forum: Server Platforms
---

### Post by ally2 on 2014-03-13
Good afternoon guys :)

I am working on a Ubuntu Server project my progress so far is I have installed the operating system in a RAID1 configuration I have enabled the root account, updated the packages, configured a static IP address and have installed SSH for remote access the server is currently running headless.

My next challenge is securing the box and as we speak I am probably being hacked to death :D as I have no security or hardening on there at the moment. The questions I have are below.

When dealing with a fresh server install what are the first things you do / lockdown this would be a great help!

1) Root Access best approach should I disable the root account and setup a user with admin privilages
2) SSH best approach to secure? change the port number? key authentication? 
3) Firewall best iptables or UFW? I want something easy to configure
4) Fail2ban? any good noob freindly guides
5) On Red Hat derivatives you have chkconfig is there a similar utility for Ubuntu to view all services

Any guides / best approaches on basic server hardening / securing would be greatly appreciated

---

### Post by sandyd on 2014-03-13
> **ally2 said:**
> Good afternoon guys :)

I am working on a Ubuntu Server project my progress so far is I have installed the operating system in a RAID1 configuration I have enabled the root account, updated the packages, configured a static IP address and have installed SSH for remote access the server is currently running headless.

My next challenge is securing the box and as we speak I am probably being hacked to death :D as I have no security or hardening on there at the moment. The questions I have are below.

When dealing with a fresh server install what are the first things you do / lockdown this would be a great help!

1) Root Access best approach should I disable the root account and setup a user with admin privilages
2) SSH best approach to secure? change the port number? key authentication? 
3) Firewall best iptables or UFW? I want something easy to configure
4) Fail2ban? any good noob freindly guides
5) On Red Hat derivatives you have chkconfig is there a similar utility for Ubuntu to view all services

Any guides / best approaches on basic server hardening / securing would be greatly appreciated
2) Key authentication, also force SSH to only work through key authentication
3,4) I normally recommend [CSF (ConfigServer Security & Firewall)]("http://configserver.com/cp/csf.html") which is easy to setup, and includes LFD (login failure detection)
5. ```
initctl show-config
```

---

### Post by Lars Noodén on 2014-03-13
1) Root is usually disabled on Ubuntu in favor of having one or more dedicated admin users.

2) SSH can benefit from key authentication, many recommend it.  Changing ports is more debatabe and you will still get probed, just maybe not as much.  A scan of the machine will still show what's on which port.

3) UFW is a front end for iptables.  If you start to get complex rules then maybe you can work directly with iptables but otherwise UFW is fine for most purposes.

5) Ubuntu for now uses Upstart, it will move to systemd.  All the services you have are listed in /etc/init/ and the old scripts that have not been converted to Upstart are in /etc/init.d/

---

### Post by ally2 on 2014-03-13
Many Thanks guys are there any blogs / guides on initial security configuration best practices with everything in one place? that would be a useful reference to have i'm also going to document all my work

---

### Post by nerdtron on 2014-03-15
Is your server going to face the public internet of just sit on your local network?
If it is just a private server, even without a firewall, you'll be fine.

---

