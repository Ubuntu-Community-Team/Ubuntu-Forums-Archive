---
title: "Cannot  connect  to samba from windows thouroughly confused..."
date: 2009-11-21
forum: Server Platforms
---

### Post by mramsey on 2009-11-21
OK here is the gist of my issue:

I have Ubuntu 8.04 lts server installed. I am using Webmin for most of the administration.

I believe I have the network configured correctly because I see the server in windows when I view all network devices. When I try to map a drive to \\192.168.1.186\homes windows says:

```
Windows cannot access \\192.168.1.186\homes
Check the spelling of the name. Otherwise, there might be a problem with your network.

Error code: 0x80070043
The network name cannot be found
```

There are no firewall rules currently set and I can ping the server. Any thoughts on what to do next?? :-k

---

### Post by capscrew on 2009-11-21
> **mramsey said:**
> OK here is the gist of my issue:

I have Ubuntu 8.04 lts server installed. I am using Webmin for most of the administration.

I believe I have the network configured correctly because I see the server in windows when I view all network devices. When I try to map a drive to \\192.168.1.186\homes windows says:

```
Windows cannot access \\192.168.1.186\homes
Check the spelling of the name. Otherwise, there might be a problem with your network.

Error code: 0x80070043
The network name cannot be found
```

There are no firewall rules currently set and I can ping the server. Any thoughts on what to do next?? :-k

The user never mounts a share such as \\192.168.1.186\homes.

the [homes] section of the smb.conf file is so that you mount YOU individual share.  It would look like this for the user johnsmith: ```
\\192.168.1.186\johnsmith
```

See [_**[COLOR="DarkSlateGray"]here [/COLOR]**_]("http://oreilly.com/catalog/samba/chapter/book/ch06_01.html") See the *6.1.1 The [ homes] Share* section

---

