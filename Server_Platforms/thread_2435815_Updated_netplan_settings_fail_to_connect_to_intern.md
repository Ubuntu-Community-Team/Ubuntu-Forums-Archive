---
title: "Updated netplan settings fail to connect to internet"
date: 2020-01-26
forum: Server Platforms
---

### Post by biznizb1zn1z on 2020-01-26
I am running Ubuntu Server 18.04. The server is connected to a router running in bridge mode by ethernet cable. The file I'm using under /etc/netplan uses these settings. 
```

network:
   version: 2
   renderer: networkd
   ethernets:
      enps20:
          dhcp4: no
          addresses: 
             - 192.168.1.137/24
          gateway4: 192.168.1.1
          nameservers: 
                    addresses: [8.8.8.8, 8.8.4.4] 

```
The error message when I login is
```
Failed to connect to https://changelogs.ubuntu.com/note-release-lts. Check your internet or proxy settings
```
I did do sudo netplan try beforehand and it didn't encounter an issue. 
What am I missing? Is there a problem with my settings?

---

### Post by TheFu on 2020-01-26
```
- 192.168.137/24
```
looks incorrect. Missing an octal?

I don't know if it matters or not, but dhcp4 isn't capitalized here.

---

### Post by biznizb1zn1z on 2020-01-27
Good eye, unfortunately those both were errors made in my copying. Thanks for the new term though. I'll edit it so it's correct.

---

### Post by slickymaster on 2020-01-27
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2020-01-27
> **biznizb1zn1z said:**
> Good eye, unfortunately those both were errors made in my copying. Thanks for the new term though. I'll edit it so it's correct.


it isn't clear. Did this fix the issue or not?

Here's a working, simple, setup (I used copy/paste, so no chance of mistake):
```
$ more /etc/netplan/50-cloud-init.yaml 
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            addresses:
            - 172.22.22.90/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "1.1.1.1", "1.0.0.1" ]
                search: []

```
After changing anything, be certain to tell netplan to reload the config.

YAML is very picky about indentation and being consistent with it. Note the exact indentation in mine.

---

### Post by beduntu on 2020-01-29
Try this

```

network:
   version: 2
   renderer: networkd
   ethernets:
      enps20:
               addresses: 
               - 192.168.1.137/24
               gateway4: 192.168.1.1
               nameservers: 
                      addresses: 
                      - 8.8.8.8
                      - 8.8.4.4 

```

And obviously renew netplan configuration:

```
$ sudo netplan apply
```

Yaml indentation and how to indent is a nightmare. 

B-)

---

### Post by biznizb1zn1z on 2020-02-02
Update: without changing any settings after starting the server after having it shut off for awhile (we had attempted restarting before but it wasn't for an extended amount of time) the internet began to work again.
Solved, I guess. Thanks for your help to everyone that replied.

---

### Post by LHammonds on 2020-02-03
If you made no changes, the problem might be external to that server.  Make sure that IP address is not being used elsewhere on your LAN or you will run into more issues.

---

