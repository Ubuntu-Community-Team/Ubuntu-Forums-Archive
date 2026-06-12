---
title: "*nix name resolution"
date: 2007-05-21
forum: Server Platforms
---

### Post by Dudsmacka2 on 2007-05-21
I am familiar with how name resolution works in the wintel world (NetBIOS and such) and was curious how it work in the *nix world.  

Does the machine report the name to the network's DNS server and is then accessible by the domain name or does it have to be configuring on the DNS server itself?

---

### Post by mbradlcu on 2007-05-22
> **Dudsmacka2 said:**
> I am familiar with how name resolution works in the wintel world (NetBIOS and such) and was curious how it work in the *nix world.  

Does the machine report the name to the network's DNS server and is then accessible by the domain name or does it have to be configuring on the DNS server itself?

The way we have our network setup is DNS has to be configured for all the machines on our network. Domain names setup on a client machines aren't know to the other clients,, Clients can have other clients host names specified in the /etc/hosts file. I'm not aware of how a client would advertise and update DNS, if anyone knows more about this please let me know.

---

### Post by Mr. C. on 2007-05-22
There are a number of lookup tables in *nix environments.  Hostname lookups are specified via the file /etc/nsswitch.conf with a line such as:
```

hosts:      files dns
```

This example indicates that the files table (/etc/hosts) should be used, and if no entry found, use DNS.  Failure will occur if not DNS entry is found.  Additional lookup tables can be added, such as NIS/NIS+, etc.  See:
```

man nsswitch.conf
```

for more info.

---

