---
title: "Blocking suspicious IP's from auth.log"
date: 2007-03-01
forum: Server Platforms
---

### Post by mikestefff on 2007-03-01
I was looking through my auth.log and surprisingly there were tons and tons of login requests on all different ports through ssh. It appears to be robot activity and I was wondering how exactly do you ban IPs from accessing the system completely? Is there a way to autoban these people/bots trying to gain access? And is it a bad idea to completely ban an ip address?

Thanks

---

### Post by Mr. C. on 2007-03-01
Mikestefff,

The most secure method is to only allow access to those IPs/users that actually need the service.

If you want SSH available over the internet, be prepared for thousands of attempts to gain access.  If your system is securely configured, you have no worries; you'll just see lots of bot / script-kiddie failures.

Use your firewall (i hope you have one) to allow access to SSH and other services only to IPs you want to allow access, and deny all the rest.

Don't try to spend your time blocking various IPs - they change frequently, and in the end, you accomplish very little.  There are things like DenyHosts that will automatically configure firewall rules, but in the end, you end up suffering as ALL IP traffic ends up going through large firewall rules chains.

I block/unblock ports for things like SSH as necessary, and allow access to certain IPs/IP ranges.

Some firewalls have the ability to configure rules based on failed attempts, but this may not be worth it.

Configure your SSH server securely, and don't worry about the rest.

---

### Post by mikestefff on 2007-03-01
Two things..
1. how do i go about specifying the allowed IP's for ssh?
2. since i would be accessing the machine from my home network, which will change IP every once in a while, how can i amend the list if I become blocked because of an IP change?

thanks..

---

### Post by Mr. C. on 2007-03-01
1) A number of ways:

 a) Firewall

Configure your firewall to allow only certain IPs.

 b)  /etc/ssh/sshd_config

AllowUsers YOURUSERNAME
PermitRootLogin no
Protocol 2

 c) TCP Wrappers (/etc/hosts.allow /etc/hosts.deny)

 If your ssh was built with TCP Wrappers (do an ldd of your sshd program to see, and look for a libwrap....).  If it does, learn about /etc/hosts.allow and /etc/hosts.deny  (man sshd_config hosts.allow hosts.deny).

 And use a strong password!

2)  The best you can do here is to configure your firewall to allow a certain IP range that your provider uses for your connection.  This will eliminate an enormous number of IPs from having access, while giving you the freedom to access your system with various IPs.

---

### Post by mikestefff on 2007-03-01
Well I am running a website off my server though. Is it possible to configure the firewall to allow only certain IPs but just for port 22? I have never setup a firewall on linux yet.

---

### Post by Mr. C. on 2007-03-02
Absolutely, and advised!

You will configure your firewall to allow all port 80 (web) traffic in to your system.  You configure port 22 (ssh) for only the IPs you desire.  Same for other services (FTP, SMTP, IMAP, POP, etc.).

This stuff is trivial with even the cheapest hardware appliances (often misnamed "routers"); they might cost all of < $50 US.

This should be the first thing you learn about - how to properly install and configure a firewall.

User's systems are hit thousands of times per day by various hackers.  Your firewall log (as you've seen with your auth log) will verify this.

---

### Post by mikestefff on 2007-03-02
Can i use /etc/host.allow and /etc/host.deny to block sshd traffic? it seems easiest

---

### Post by Mr. C. on 2007-03-02
Yup.

---

### Post by MJN on 2007-03-02
Any manual effort will be far from sufficient - you want to stop them within a minimum period of time and unless you're going to sit there waiting for 'em...
 
Try **fail2ban** instead - it will block IPs after a customisable number of failed attempts and for a customisable length of time. Defaults are something like 3 times and for 10 minutes - by this time they'll have moved on to someone else (I can confirm the bots don't hang around).
 
Mathew

---

