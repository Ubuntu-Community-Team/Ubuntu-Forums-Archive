---
title: "Error with hostname"
date: 2019-02-27
forum: Server Platforms
---

### Post by gaaz85 on 2019-02-27
Hi.

Actually i have a problem with my server.

When I launch the command ```
hostname
``` and ```
hostname -f
```. Ubuntu indicate different name of hostname.

This hostnames are in the hosts file. But I need to be like this.

Does anyone know why this happens?.

Best kind regards.



Does anyone know why this happens?Does anyone know why this happens?

---

### Post by jeremy31 on 2019-02-27
Moved to Server platforms

---

### Post by gaaz85 on 2019-02-27
jeremy31. Sorry and thanks.

---

### Post by darkod on 2019-02-27
We can't see anything in your first post. Please post the output of the following command in CODE tags (that allows the output to be easily readable).
```
cat /etc/hosts
```

---

### Post by TheFu on 2019-02-28
The manpage for hostname should clear up any differences in the hostname command output:```

       -f, --fqdn, --long
              Display  the FQDN (Fully Qualified Domain Name). A FQDN consists
              of a short host name and the DNS domain  name.  Unless  you  are
              using  bind  or NIS for host lookups you can change the FQDN and
              the DNS  domain  name  (which  is  part  of  the  FQDN)  in  the
              /etc/hosts  file. See the warnings in section THE FQDN above und
              use hostname --all-fqdns instead wherever possible.
```


There is the simple hostname and the FQDN which is the hostname.domainname
Different releases set the value for each in different ways.  I don't remember which release does it which way, but /etc/hostname, /etc/domainname, and /etc/hosts are involved.

Also, if avahi is being used, then that adds in other aspects to be considered.

---

