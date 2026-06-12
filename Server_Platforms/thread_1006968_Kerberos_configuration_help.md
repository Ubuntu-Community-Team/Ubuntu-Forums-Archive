---
title: "Kerberos configuration help"
date: 2008-12-09
forum: Server Platforms
---

### Post by benander on 2008-12-09
Hi,

I'm getting the following error. The admin server restarts fine but then gives me the error message below.

> root@me-desktop:/etc# /etc/init.d/krb5-admin-server restart
 * Restarting Kerberos administrative servers kadmind                                                                root@me-desktop:/etc# kadmin
Authenticating as principal root/admin@LOCAL.NETWORK with password.
kadmin: Cannot contact any KDC for requested realm while initializing kadmin interface
root@me-desktop:/etc# 


here is a copy of my krb5.conf

> [libdefaults]
default_realm = LOCAL.NETWORK

[realms]

LOCAL.NETWORK = {
  kdc = me-desktop.syslab.com
  kpasswd_server = me-desktop.syslab.com
  admin_server = me-desktop.syslab.com
  master_kdc = me-desktop.syslab.com
  default_domain = syslab.com
}


[domain_realm]
syslab.com = LOCAL.NETWORK
.syslab.com = LOCAL.NETWORK

[login]
krb4_convert = false
krb4_get_tickets = false

kinit = {
forwardable = true 
krb5_runaklog = true
}

pam = {
forwardable = true
}


Any ideas as to why I am getting this error message or any other helpful tips in general?

---

### Post by benander on 2008-12-09
also when I try kinit me (princ I added earlier), I get the following

> root@me-desktop:/etc/init.d# kinit me
kinit(v5): Cannot resolve network address for KDC in realm LOCAL.NETWORK while getting initial credentials


---

### Post by benander on 2008-12-09
also when I try 

> root@me-desktop:/etc/init.d# ./krb5-kdc restart


nothing happens and when I do a 
> ps -ef | grep krb5-kdc 
nothing shows up.

---

### Post by deejross on 2009-08-10
I too have this problem and I count 6 other threads just like this one with no answers. What's up with the lack of help from the community these days?

Anyways, I was following [Ubuntu's Help Page]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto"), which is garbage. It uses the OLD method for authenticating against an AD server (NTLM).

I ended up using [another guide]("http://wiki.randompage.org/index.php/DistOS:Linux:Debian:Samba") to set this up. But when you follow that guide, you will still have the same problem with kinit.

To fix that problem, you simply need to add the domain controller's ip and fully qualified domain name to your /etc/hosts file. So for example:
```
10.0.0.1   dc1.example.com
```

Hope that helps!

---

