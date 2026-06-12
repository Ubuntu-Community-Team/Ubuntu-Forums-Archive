---
title: "Is there a good guide how to setup Ubuntu VMs that utilize an LDAP server for login?"
date: 2020-12-08
forum: Server Platforms
---

### Post by kevdog on 2020-12-08
Hi guys.  A lot of sysadmin people who are knowlegeable. 

I run a dockerized open-ldap installation for a different project.  

As a side exploratory project -- is it possible to run a couple of Ubuntu VM's that could use an ldap server that has user accounts, that would would sync usernames, UIDs GIDs across the 2 systems?  Is this easy to set up?

---

### Post by Tadaen_Sylvermane on 2020-12-09
I am far from experienced but wouldn't bridging the vms so they exist on the physical lan be the quick answer here? Then they are no different than any other machine on the lan?

---

### Post by kevdog on 2020-12-10
I'm sorry -- a little confused by what you mean.  Openldap is for user authentication and to ensure consistent UID/GIDs across systems.  How would bridging VMs solve this solution?

---

### Post by SeijiSensei on 2020-12-10
I believe you can configure the PAM authentication service to use LDAP rather than /etc/passwd. Take a look at [https://wiki.debian.org/LDAP/PAM](https://wiki.debian.org/LDAP/PAM).

---

### Post by TheFu on 2020-12-10
Yes, an ldap server with the POSIX UID schema can be used by any number of client machines.  Users are not copies or sync'd. The user queries to the LDAP server ask the server, as needed. In general, this happens based on the **getent passwd** and **getend group** commands (and system calls).

I've setup access to LDAP on my work network from a few shared desktops, but I didn't setup the ldap.  The LDAP server was part of another tool which required it. I did have to modify the ldap schema, adding and filling posix fields and queries so any Unix client can use it for authentication. There are different security layers for network encryption and admin access that can be used or not. I setup guest-only access, so clients couldn't change passwords.  The "POSIX" layer is basically a schema that implements the passwd and group file data, but inside the LDAP DB.

For our needs, it was as close to 1-userid per person as possible. It wasn't SSO and we had to train users to only to reset passwords using a specific front-end, not what each application, OS, webapp provided. I didn't move service/daemon accounts into LDAP. Those were all local.  I did setup NFS for all the user's HOME directories, since we didn't assume they'd sit behind the same desktop system from day to day, but wanted their personal HOME files to be available regardless.  NFS, autofs and LDAP all work together for that result.  

These capabilities have been part of Unix for 30+ yrs thanks to using NIS (before LDAP), but alas, some new decisions by Canonical with snap packages are breaking these choices which enterprises have used for decades. If you are trying to learn how to deploy these things inside an enterprise, definitely use LDAP+autofs+NFS so you can learn what breaks and why.

---

### Post by Tadaen_Sylvermane on 2020-12-10
I was referring to network bridging. Then the vms are viewed as just another machine on the lan. At that point configuration is no different than anything else.

---

### Post by kevdog on 2020-12-13
What does autofs actually do?

I've got one of my test virtual machine communicating with the ldap server. I'm going to see if I can use the PAM module for authentication.  Frankly I'm actually shocked by how many microservices I'm running within docker that have capabilities to use ldap.  For example just tied in my syncthing authorization with ldap.

---

### Post by TheFu on 2020-12-13
> **kevdog said:**
> What does autofs actually do?
 

It mounts pre-cofigured file systems on-demand, with the mount options we control, to the mount locations we specify. Any attempt to access the location tells autofs to mount it.  Then, when no processes are sng te storage, after a timeout period, it is atomatically un-mounted.

This is very useful for storage that isn't available 100%, so any USB devices and any network storage are ideal for autofs. There isn't a performance hit using autofs, unlike the gio or gvfs methods, snce a real mount gets invoked wth the options we specify.

systemd-mount attempted something like this, but only got half done. It doesn't mount which is a pain for usb storage.

---

