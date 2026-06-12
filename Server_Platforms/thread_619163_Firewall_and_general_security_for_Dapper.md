---
title: "Firewall and general security for Dapper"
date: 2007-11-21
forum: Server Platforms
---

### Post by twill30 on 2007-11-21
Just recently got a new box running 6.06 LTS through 1&1 (price=good vs. support=not great). Intention is to use it for hosting around six sites (no e-commerce) and for serving some simple development repositories using subversion (just day-to-day projects -- no real sensitive info etc).

Just a few quick questions about security (new to Ubuntu but not Linux).

Not running a large network and not wishing to spend hours administering the server each week, would the following be considered a 'safe' and sensible baseline approach:

[LIST=1]
[*]**Firewall:** Use 1&1's Cisco hardware firewall configured to deny all except a simple Apache set-up on port 80 and SSH via another port of choice (22 or other). We are not planning to use a software based FW such as iptables as we understand the 1&1 firewall will be sufficient?

[*]**Updates:** Subscribe to the Ubuntu update RSS feed and regularly patch using aptitude update and upgrade.

[*]Disable root login and restrict SSH2 access to named users only (regular FTP and Telnet disabled).

[*]Run RKHunter regularly (can you use 1.3.0 for 6.06 or only one of the older versions -- 1.3.0 is not available in the standard repositories?)
(We've tried running Tiger John but it always hangs halfway through)

[*]Install/configure Fail2Ban

[*]Install/configure mod security for Apache

[*]Install/configure/regularly check Logwatch

[*]Set root password for MySQL and only allow local connections

[*]Disable register globals in PHP

[*]Install/configure MySecureShell for SFTP to individual sites

[*]chmod home folders to 700

[*]Use a SSL for accessing svn repository
[/LIST]

Basically, we're trying to install a sensible and secure set-up (i.e. we don't want to expose ourselves to the possibility of anyone being able to upload foreign files etc to our system) whilst keeping admin to a minimum...

Have we missed anything obvious, or would this set-up/workflow seem sensible?

Long post but hopefully it might help others looking for similar batch delivery of answers...

---

### Post by nocturn on 2007-11-21
> **twill30 said:**
> 
[LIST=1]
[*]**Updates:** Subscribe to the Ubuntu update RSS feed and regularly patch using aptitude update and upgrade.

[*]Run RKHunter regularly (can you use 1.3.0 for 6.06 or only one of the older versions -- 1.3.0 is not available in the standard repositories?)
(We've tried running Tiger John but it always hangs halfway through)
[/LIST]



You can compile the rkhunter package from their site (easy and fast).
I'm monitoring both updates (apt) and rkhunter through Nagios, which is something you really need on a server.  (Zabbix and ZenOSS are also very nice).

---

### Post by twill30 on 2007-11-21
Thanks for the reply. Could you let me know how to do the 'quick and fast' get and compile of the latest RKHunter? Once I've done it once I'll know how...

Did the rest of the steps look OK to you (v. useful to get a seasoned user's viewpoint)?

---

### Post by PilotJLR on 2007-11-21
I also think your list looks good... a Cisco firewall is fine; iptables won't offer you anything more unless you are concerned about an attack from your own lan (are there users on your lan?). An IPS box would be even better.

Also consider installing tripwire as a last step, once everything else is configured. You can then determine if anything gets altered after your setup.

---

### Post by nocturn on 2007-11-21
> **twill30 said:**
> Thanks for the reply. Could you let me know how to do the 'quick and fast' get and compile of the latest RKHunter? Once I've done it once I'll know how...

Did the rest of the steps look OK to you (v. useful to get a seasoned user's viewpoint)?

I'm not sure out of my head any more.  I think untar, ./configure; make; make install does it.  Make sure you have build-essentials installed though.

For Nagios integration, look for the rootkit plugin on NagiosExchange.

---

### Post by nocturn on 2007-11-21
The list looks good, but I do recommend automated monitoring (like Nagios) because I know from experience that doing it manually is prone to errors and oversights.

---

### Post by otake-tux on 2007-11-21
you should also use the software based firewall just to add that extra layer.
run a password cracker on everything to see how good your passwords are.

of course; I'm quite paranoid so maybe that's just me.

---

