---
title: "Samba 4 Share Asking For Password"
date: 2017-06-21
forum: Server Platforms
---

### Post by Kirk Schnable on 2017-06-21
Hi All,

I recently set up a new server with Samba 4, and am having some difficulty getting my old configuration working.  I did some Googling and came across several guides for configuration and took some elements from each of them, but I'm still getting a password prompt when I browse to the Samba share on a Windows 10 machine.  I tried entering bogus credentials like "." for the username and password, as well as actual credentials like "root" and my root password, but I can't seem to get on the share from Windows 10.  On my Linux machines, I can browse to smb://server.ip/ and it loads right up without any password request.

I am pasting my configuration below, wondering if anyone has any suggestions on what to tweak or some idea what I'm doing wrong?  This is the third or forth iteration of my config from stealing configs from other "Samba asking for password" threads around the web.

All I want to achieve are read-only, completely public Samba shares which do not ask for a password from any Windows or Linux client.

Thank you!
Kirk

```
[global]
    workgroup = SAMBA
    security = user
    map to guest = Bad Password
    log file = /var/log/samba/log.%m
    max log size = 1000
    passdb backend = tdbsam


[Videos]
    comment = Videos
    path = /mnt/nfs/Media/Videos/
    browsable = yes
    public = yes
    guest ok = yes
    read only = yes
    force user = nobody
    force group = nogroup


[Documents]
    comment = Documents
    path = /mnt/nfs/Documents/
    browsable = yes
    public = yes
    guest ok = yes
    read only = yes
    force user = nobody
    force group = nogroup
```

---

