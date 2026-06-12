---
title: "Ubuntu server 10.04 Security"
date: 2011-11-10
forum: Server Platforms
---

### Post by Katu Mala on 2011-11-10
Hi all,
 
May I please know how secure is Ubuntu TLS (10.04)?
 
What do I do before and after the installation process to maintain security, and when the server (software) operating system is up-and-running in the network (meaning, the server can be accessed via the intranet or Internet).
 
What are the least known softwares and basic techniques to apply to build a near secure Ubuntu server.
 
 
Thank you all,
 
Katu :)
.......

---

### Post by Dangertux on 2011-11-10
Wow -- that's a loaded question if I've ever seen one, securing a server is so very highly dependent on what services you intend to run its not even funny. So the best I can do for you here is to give you some basic guidelines, and if you want to elaborate on what you want this server to do, I can probably give you better advice or at least more  specific advice.

1 -- Strong credentials : No matter what, if it takes a password, it needs to be strong (32+ characters upper case, lower case, numbers, special characters and white space) hashed as strongly as the service allows and salted of course. In the case of things like SSH that accept keys these are always preferable.

2 -- Least privileges : Make sure whatever service you're running has the bare minimum to do what it needs and nothing more. No services running as root.

3 -- Seperation of resources : chroots, and preferably virtualization should be used to seperate your assets as much as possible. "Never put all your eggs in one basket" comes to mind.

4 -- Hardened configurations : Again this is service specific, but make sure your configurations are in the best interest of security. For instance you wouldn't want an SSH server allowing root login, or an FTP server that allows anonymous users to write and execute files, likewise you wouldn't want a web server that allows PUT unless its restricted in some way.

5 -- Mandatory Access Controls : SELinux , Apparmor , GRSec whatever your poison they are good and need to be implemented on your mission critical applications at the very least. Preferably everything.

6 -- Logical firewalling : Obviously you can't just block traffic to services, however you can block some people from utilizing services they don't need (whitelisting/blacklisting). Also rate limiting to defeat brute force attacks against authentication based services is a good idea as well. Utilizing a firewall to confine potential compromise is also a smart idea. 

7 -- Keep your server patched : just do it, security patches are important. If it's out of date, it's as good as owned.

8 -- Restrict who can make changes to it : If you're the only admin nobody else should have administrative access to the server, if they do this needs to change. If there are multiple admins, make sure they are accountable for what they are doing with their credentials

9 -- Physical Security : Partially goes back to number 8 , but also make sure that someone can't just sit down next to your server and fire up a console. Locks, keys, access rosters/logs, these are good things to have.

10 -- Monitoring : Monitor your server, whether you install an IDS or are just watching your logs, know what its doing and what's being done to it.  Many sysadmins can stop a crack from happening if they paid more attention to their logs. Email alerts are cute, but automated log auditors don't catch everything.

Hope this helps.

---

### Post by ibutho on 2011-11-10
Its as secure as the sysadmin makes it. To make the system more secure, look at enabling the firewall, checking for rootkits using rkhunter or chkrootkit, disable or uninstall services you do not need or use. Also make sure you do not have services that login remotely as root.

---

### Post by Katu Mala on 2011-11-11
Hello Dangertux,
 
Thank you very much for the needed information. I believe that would be enough and I need to apply them now.
 
I call when I need your help, I know you will help.
 
Thank you again,
 
Katu :)
.......

---

### Post by Katu Mala on 2011-11-11
Hi ibutho,
 
Thank you very much and I appreciate your help.
 
 
Katu :)

---

### Post by boetzie on 2011-11-12
check out this site as well: 
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

