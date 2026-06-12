---
title: "ubuntu 18.10 domain join error"
date: 2019-01-30
forum: Server Platforms
---

### Post by digitalquake on 2019-01-30
Hello

I've been trying to join the latest build of ubuntu to our AD but when I do the join I get a different error depending on the process


I've tried ```
net ads join -k
``` or via ```
realm join example.com
```

Either way it fails
The first time it complains about ```
Host is not configured as a member server.
```
The second time it says ```
realm: Couldn't join realm: Necessary packages are not installed: sssd-tools sssd libnss-sss libpam-sss adcli
```
But all the software is installed.

Do I need to manually add the machine to the windows AD before joining it?

---

### Post by volkswagner on 2019-01-30
The error says your SAMBA config does not show as a member.
Can you post your samba config?
Post output of:
```
testparm -s
```

---

### Post by digitalquake on 2019-01-31
Hi Volkswagner

I've copied it from a working build

```
root@cam-mgmt:/home/user# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    dedicated keytab file = /etc/krb5.keytab
    kerberos method = system keytab
    log file = /var/log/samba/log.%m
    max log size = 50
    netbios name = LDNCAM-MGMT
    realm = DOMAIN.COM
    server string = Samba Server Version %v
    workgroup = DOMAIN
    idmap config * : backend = tdb
root@cam-mgmt:/home/user# 


```

Tried to create manually the account but cant' get around with that

---

### Post by volkswagner on 2019-01-31
Did you notice the output of testparm?
```
Server role: ROLE_STANDALONE
```

You can try adding:
```
security = ADS
```

and/or

```
server role = member server
```

---

### Post by digitalquake on 2019-02-01
Hmm pretty sure I had security = ADS in the file.

I'll try to change the role. thanks!

---

