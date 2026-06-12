---
title: "Unable to ping hostname"
date: 2008-09-24
forum: Server Platforms
---

### Post by satimis on 2008-09-24
Hi folks,


Machine-1
OpenVZ
Ubuntu 8.04 Hardy - Host
Ubuntu 8.04 Hardy - Guests


Machine-2
Xen
Debian Etch - Host
Debian Etch - Guests


Both machines together with their guests are working.  They can ping and ssh-connect each other on IP.  But they can't ping nor ssh connect each and others (both local and remote machines) on hostname.  I have been playing around on hosts, hostname, resolv.conf, mailname, etc. for 2 days without a solution.  Please help.  TIA


B.R.
satimis

---

### Post by cdenley on 2008-09-24
> **satimis said:**
> Hi folks,


Machine-1
OpenVZ
Ubuntu 8.04 Hardy - Host
Ubuntu 8.04 Hardy - Guests


Machine-2
Xen
Debian Etch - Host
Debian Etch - Guests


Both machines together with their guests are working.  They can ping and ssh-connect each other on IP.  But they can't ping nor ssh connect each and others (both local and remote machines) on hostname.  I have been playing around on hosts, hostname, resolv.conf, mailname, etc. for 2 days without a solution.  Please help.  TIA


B.R.
satimis

How do you want the hostnames to be resolved? You can add an entry for each host on each host's /etc/hosts file, or you can create a DNS server, create a DNS record for each host, then configure each host to use your DNS record. You could also install a samba server and install/configure winbind on each host.

---

### Post by satimis on 2008-09-25
Hi cdenley,


Thanks for your advice.


> **cdenley said:**
> How do you want the hostnames to be resolved? You can add an entry for each host on each host's /etc/hosts file, 

Yes.

Your advice works.  But there will a long list if running 100 guests on each machine.


> 
or you can create a DNS server, create a DNS record for each host, then configure each host to use your DNS record. You could also install a samba server and install/configure winbind on each host.
Any pointer on both of them.  I expect learning something new to me.  TIA


B.R.
satimis

---

### Post by cdenley on 2008-09-25
Well, I think the easiest would be to use winbind, and resolve names like windows.

To enable a client to resolve netbios names
[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

To make a computer broadcast a netbios name, just install samba
```

sudo apt-get install samba

```

---

### Post by satimis on 2008-09-25
> **cdenley said:**
> Well, I think the easiest would be to use winbind, and resolve names like windows.

To enable a client to resolve netbios names
[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

To make a computer broadcast a netbios name, just install samba
```

sudo apt-get install samba

```
Noted with thanks


satimis

---

