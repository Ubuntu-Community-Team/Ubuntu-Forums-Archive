---
title: "Samba4 DNS Update Problem"
date: 2013-09-13
forum: Server Platforms
---

### Post by addictedboy on 2013-09-13
Hello,

I installed the samba4 and configured it according to samba4 wiki guide. I installed it with Bind9 as dns-backend. Everything is working fine, I joined several machines and they are also abled to login with their domain usernames. However, whenever I am running samba_dnsupdate query it is showing this - 

```
root@openserver:~# samba_dnsupdate --verbose --all-names
IPs: ['192.168.1.5', '192.168.2.5']
Ignoring unknown parameter "server role"
Ignoring unknown parameter "server services"
Calling nsupdate for A nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
nexus.world.        900    IN    A    192.168.1.5

Ignoring unknown parameter "server role"
Ignoring unknown parameter "server services"
; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for A openserver.nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
openserver.nexus.world.    900    IN    A    192.168.1.5

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for A gc._msdcs.nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
gc._msdcs.nexus.world.    900    IN    A    192.168.1.5

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for CNAME 21e8caca-daba-43d8-99b0-4056c9f434d3._msdcs.nexus.world openserver.nexus.world
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
21e8caca-daba-43d8-99b0-4056c9f434d3._msdcs.nexus.world. 900 IN    CNAME openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _kpasswd._tcp.nexus.world openserver.nexus.world 464
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kpasswd._tcp.nexus.world. 900    IN    SRV    0 100 464 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _kpasswd._udp.nexus.world openserver.nexus.world 464
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kpasswd._udp.nexus.world. 900    IN    SRV    0 100 464 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._tcp.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.nexus.world. 900    IN    SRV    0 100 88 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._tcp.dc._msdcs.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.dc._msdcs.nexus.world. 900 IN SRV 0 100 88 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV 0 100 88 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._tcp.default-first-site-name._sites.dc._msdcs.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.default-first-site-name._sites.dc._msdcs.nexus.world. 900 IN SRV0 100 88 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._udp.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._udp.nexus.world. 900    IN    SRV    0 100 88 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.nexus.world.    900    IN    SRV    0 100 389 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.dc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.dc._msdcs.nexus.world. 900 IN SRV    0 100 389 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.gc._msdcs.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.gc._msdcs.nexus.world. 900 IN SRV    0 100 3268 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.pdc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.pdc._msdcs.nexus.world. 900 IN SRV    0 100 389 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV 0 100 389 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.dc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.dc._msdcs.nexus.world. 900 IN    SRV 0 100 389 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.gc._msdcs.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.gc._msdcs.nexus.world. 900 IN    SRV 0 100 3268 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.d5e39e12-99f7-41da-ac70-821c5c60511d.domains._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.d5e39e12-99f7-41da-ac70-821c5c60511d.domains._msdcs.nexus.world. 900IN SRV 0 100 389 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _gc._tcp.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_gc._tcp.nexus.world.    900    IN    SRV    0 100 3268 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for SRV _gc._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_gc._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV    0 100 3268 openserver.nexus.world.

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for A nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
nexus.world.        900    IN    A    192.168.2.5

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for A openserver.nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
openserver.nexus.world.    900    IN    A    192.168.2.5

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Calling nsupdate for A gc._msdcs.nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
gc._msdcs.nexus.world.    900    IN    A    192.168.2.5

; Communication with 127.0.1.1#53 failed: operation canceled
response to SOA query was unsuccessful
Failed nsupdate: 1
Failed update of 24 entries

```


Can anyone help me here?

---

### Post by addictedboy on 2013-09-20
Any one can help me out here?

---

### Post by lingpanda on 2013-09-20
I'm not sure what you're asking. It looks to me like you may have a few issues. Did you set in interfaces namerservers 127.0.1.1? It should be your dns IP. Also a few parameters in your smb.etc file are wrong.

---

### Post by addictedboy on 2013-09-24
Sorry for replying so late, I didn't set 127.0.1.1 in my nameserver. Here is my configuration file - 

```

root@openserver:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address    192.168.1.5
    netmask    255.255.255.0
    network    192.168.1.0
    gateway    192.168.1.2
    broadcast 192.168.1.255
    dns-nameservers 192.168.1.5 192.168.1.4
    dns-search nexus.world
    dns-domain nexus.world

auto eth1
iface eth1 inet static
    address    192.168.2.5
    netmask    255.255.255.0
    network    192.168.2.0
    broadcast 192.168.2.255
    dns-domain nexus.world
    dns-search nexus.world

```

This is my smb.conf, it is a default file which gets generated when we setup the server as AD, I have not modified it.

```


root@openserver:~# cat /usr/local/samba/etc/smb.conf
# Global parameters
[global]
        workgroup = NEXUS
        realm = NEXUS.WORLD
        netbios name = OPENSERVER
        log level = 3
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate
        idmap_ldb:use rfc2307 = yes
        template shell = /bin/bash


[netlogon]
        path = /usr/local/samba/var/locks/sysvol/nexus.world/scripts
        read only = No


[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No


[profiles]
        path = /home/serveradmin/profiles/
        read only = No
root@openserver:~#



```

---

### Post by lingpanda on 2013-09-24
> **addictedboy said:**
> Sorry for replying so late, I didn't set 127.0.1.1 in my nameserver. Here is my configuration file - 

```

root@openserver:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address    192.168.1.5
    netmask    255.255.255.0
    network    192.168.1.0
    gateway    192.168.1.2
    broadcast 192.168.1.255
    dns-nameservers 192.168.1.5 192.168.1.4
    dns-search nexus.world
    dns-domain nexus.world

auto eth1
iface eth1 inet static
    address    192.168.2.5
    netmask    255.255.255.0
    network    192.168.2.0
    broadcast 192.168.2.255
    dns-domain nexus.world
    dns-search nexus.world

```

This is my smb.conf, it is a default file which gets generated when we setup the server as AD, I have not modified it.

```


root@openserver:~# cat /usr/local/samba/etc/smb.conf
# Global parameters
[global]
        workgroup = NEXUS
        realm = NEXUS.WORLD
        netbios name = OPENSERVER
        log level = 3
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate
        idmap_ldb:use rfc2307 = yes
        template shell = /bin/bash


[netlogon]
        path = /usr/local/samba/var/locks/sysvol/nexus.world/scripts
        read only = No


[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No


[profiles]
        path = /home/serveradmin/profiles/
        read only = No
root@openserver:~#



```

Please list the contents of your hosts file. /etc/hosts

---

### Post by addictedboy on 2013-09-24
My /etc/hosts file is -

```

root@openserver:~# cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost
127.0.1.1       openserver.nexus.world  openserver
192.168.1.5     openserver.nexus.world  openserver
192.168.1.4     backup


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters




```

---

### Post by lingpanda on 2013-09-24
> **addictedboy said:**
> My /etc/hosts file is -

```

root@openserver:~# cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost
127.0.1.1       openserver.nexus.world  openserver
192.168.1.5     openserver.nexus.world  openserver
192.168.1.4     backup


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters




```

That's what I thought. Try this

```

127.0.0.1        localhost     openserver
192.168.1.5     openserver.nexus.world  openserver
192.168.1.4     backup


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

127.0.1.1 is used if you do not specify an address for your system. Delete the lines in your hosts and reboot server.

---

### Post by addictedboy on 2013-09-25
Thanks for your help. I made the changes in my hosts as suggested. However, while running the samba_dnsupdate query I am getting this now -

```

root@openserver:/usr/local/samba/private# samba_dnsupdate --verbose --all-names
not adding non-broadcast interface tun0
IPs: ['192.168.1.5', '192.168.2.5']
ldb_wrap open of secrets.ldb
Ignoring unknown parameter "server role"
Ignoring unknown parameter "server services"
Calling nsupdate for A nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
nexus.world.            900     IN      A       192.168.1.5

Ignoring unknown parameter "server role"
Ignoring unknown parameter "server services"
dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for A openserver.nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
openserver.nexus.world. 900     IN      A       192.168.1.5

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for A gc._msdcs.nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
gc._msdcs.nexus.world.  900     IN      A       192.168.1.5

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for CNAME 21e8caca-daba-43d8-99b0-4056c9f434d3._msdcs.nexus.world openserver.nexus.world
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
21e8caca-daba-43d8-99b0-4056c9f434d3._msdcs.nexus.world. 900 IN CNAME openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _kpasswd._tcp.nexus.world openserver.nexus.world 464
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kpasswd._tcp.nexus.world. 900  IN      SRV     0 100 464 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _kpasswd._udp.nexus.world openserver.nexus.world 464
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kpasswd._udp.nexus.world. 900  IN      SRV     0 100 464 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._tcp.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.nexus.world. 900 IN      SRV     0 100 88 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._tcp.dc._msdcs.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.dc._msdcs.nexus.world. 900 IN SRV 0 100 88 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV 0 100 88 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._tcp.default-first-site-name._sites.dc._msdcs.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.default-first-site-name._sites.dc._msdcs.nexus.world. 900 IN SRV0 100 88 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _kerberos._udp.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._udp.nexus.world. 900 IN      SRV     0 100 88 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.nexus.world. 900     IN      SRV     0 100 389 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.dc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.dc._msdcs.nexus.world. 900 IN SRV    0 100 389 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.gc._msdcs.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.gc._msdcs.nexus.world. 900 IN SRV    0 100 3268 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.pdc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.pdc._msdcs.nexus.world. 900 IN SRV   0 100 389 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV 0 100 389 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.dc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.dc._msdcs.nexus.world. 900 IN SRV 0 100 389 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.gc._msdcs.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.gc._msdcs.nexus.world. 900 IN SRV 0 100 3268 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _ldap._tcp.d5e39e12-99f7-41da-ac70-821c5c60511d.domains._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.d5e39e12-99f7-41da-ac70-821c5c60511d.domains._msdcs.nexus.world. 900IN SRV 0 100 389 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _gc._tcp.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_gc._tcp.nexus.world.   900     IN      SRV     0 100 3268 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for SRV _gc._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_gc._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV 0 100 3268 openserver.nexus.world.

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for A nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
nexus.world.            900     IN      A       192.168.2.5

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for A openserver.nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
openserver.nexus.world. 900     IN      A       192.168.2.5

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Calling nsupdate for A gc._msdcs.nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
gc._msdcs.nexus.world.  900     IN      A       192.168.2.5

dns_tkey_negotiategss: TKEY is unacceptable
Failed nsupdate: 1
Failed update of 24 entries


```

It is showing TKEY is unacceptable. Following are the few more details, bind version is 9.9.3-P2. My named.conf.options file -

```

root@openserver:/etc/bind# cat named.conf.options
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                 8.8.8.8;
                 8.8.4.4;
         };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        // tkey-gssapi-keytab "/usr/local/samba/private/dns.keytab";
        allow-query { any; };
        allow-recursion { any; };
        dnssec-validation no;
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        tkey-gssapi-keytab "/usr/local/samba/private/dns.keytab";
};
root@openserver:/etc/bind#

```

My named.conf.local file -

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
include "/usr/local/samba/private/named.conf";

```

This is my dns.keytab - 
```

root@openserver:/etc/bind# klist -k /usr/local/samba/private/dns.keytab
Keytab name: FILE:/usr/local/samba/private/dns.keytab
KVNO Principal
---- --------------------------------------------------------------------------
   1 DNS/openserver.nexus.world@NEXUS.WORLD
   1 dns-openserver@NEXUS.WORLD
   1 DNS/openserver.nexus.world@NEXUS.WORLD
   1 dns-openserver@NEXUS.WORLD
   1 DNS/openserver.nexus.world@NEXUS.WORLD
   1 dns-openserver@NEXUS.WORLD
   1 DNS/openserver.nexus.world@NEXUS.WORLD
   1 dns-openserver@NEXUS.WORLD
   1 DNS/openserver.nexus.world@NEXUS.WORLD
   1 dns-openserver@NEXUS.WORLD
root@openserver:/etc/bind# ls -l /usr/local/samba/private/dns.keytab | grep -i dns.keytab
-rw-rw-rw- 1 bind bind 787 Sep  7 13:10 /usr/local/samba/private/dns.keytab
root@openserver:/etc/bind#

```

---

### Post by lingpanda on 2013-09-25
Try this. Taken from Wiki. I'm using the internal DNS so I may be of little help with Bind.

[h=2]samba_dnsupdate and nsupdate return dns_tkey_negotiategss: TKEY is unacceptable[/h] Check if AppArmor prevents Bind from writing to /var/tmp directory. 


 [h=2]New added DNS entries are not resolvable[/h] If you have problems with resolving new added DNS entries using the BIND9 DLZ interface, you maybe want to check the following: 
Files in 'samba/private/dns/sam.ldb.d/' are hardlinks to 'samba/private/sam.ldb.d/'. Maybe you've copied/moved it across filesystems and the hardlinking got lost and you're now running with two different copies of the databases at the moment (You can test this by adding a new DNS entry, e. g. by 'samba-tool'. If you can't resolve it, check if the inodes differ). 
If you 'ls -i' on the two folders, you should see, that the following files have the same inodes (what indicates, that they are hard-linked): 
 # ls -lai .../samba/private/sam.ldb.d/
17344368 -rw-rw---- 2 root named  4251648 11. Nov 18:27 DC%3DDOMAINDNSZONES,DC%3DSAMBA,DC%3DEXAMPLE,DC%3DCOM.ldb
17344370 -rw-rw---- 2 root named  4251648 11. Nov 18:27 DC%3DFORESTDNSZONES,DC%3DSAMBA,DC%3DEXAMPLE,DC%3DCOM.ldb
17344372 -rw-rw---- 2 root named   421888 11. Nov 17:53 metadata.tdb

# ls -lai .../samba/private/dns/sam.ldb.d/
17344368 -rw-rw---- 2 root named 4251648 11. Nov 18:27 DC%3DDOMAINDNSZONES,DC%3DSAMBA,DC%3DEXAMPLE,DC%3DCOM.ldb
17344370 -rw-rw---- 2 root named 4251648 11. Nov 18:27 DC%3DFORESTDNSZONES,DC%3DSAMBA,DC%3DEXAMPLE,DC%3DCOM.ldb
17344372 -rw-rw---- 2 root named  421888 11. Nov 17:53 metadata.tdb
If the files in the two folders have different inode numbers, then they aren't hard-links. To fix this, run 
 # samba_upgradedns --dns-backend=BIND9_DLZ
This will recreate the DNS files with correct hard links and permissions. 
Then restart Bind.

---

### Post by addictedboy on 2013-09-26
Thank you very much lingpanda. The problem is solved. I don't understand what really solved the problem, I did following -

1) When I checked the hardlink, it was correct -

```


root@openserver:~# ls -lai /usr/local/samba/private/sam.ldb.d/
total 37008
1579035 drwxr-x--- 2 root bind     4096 Sep 26 11:00 .
1573933 drwxr-xr-x 7 root root     4096 Sep 26 11:31 ..
1579040 -rw------- 1 root root 14319616 Sep 26 11:02 CN=CONFIGURATION,DC=NEXUS,DC=WORLD.ldb
1579041 -rw------- 1 root root 10391552 Sep 26 11:02 CN=SCHEMA,CN=CONFIGURATION,DC=NEXUS,DC=WORLD.ldb
1579053 -rw-rw---- 2 root bind  4251648 Sep 26 11:30 DC=DOMAINDNSZONES,DC=NEXUS,DC=WORLD.ldb
1579054 -rw-rw---- 2 root bind  4251648 Sep 26 11:07 DC=FORESTDNSZONES,DC=NEXUS,DC=WORLD.ldb
1579039 -rw------- 1 root root  4251648 Sep 26 11:02 DC=NEXUS,DC=WORLD.ldb
1579036 -rw-rw---- 2 root bind   421888 Sep 26 11:30 metadata.tdb
root@openserver:~# ls -lai /usr/local/samba/private/dns/sam.ldb.d/
total 25692
2492240 drwxrwx--- 2 root bind    4096 Sep 26 11:00 .
2492239 drwxrwx--- 3 root bind    4096 Sep 26 11:00 ..
1579100 -rw-rw---- 1 root bind 7139328 Sep 26 11:00 CN=CONFIGURATION,DC=NEXUS,DC=WORLD.ldb
1579101 -rw-rw---- 1 root bind 8949760 Sep 26 11:00 CN=SCHEMA,CN=CONFIGURATION,DC=NEXUS,DC=WORLD.ldb
1579053 -rw-rw---- 2 root bind 4251648 Sep 26 11:30 DC=DOMAINDNSZONES,DC=NEXUS,DC=WORLD.ldb
1579054 -rw-rw---- 2 root bind 4251648 Sep 26 11:07 DC=FORESTDNSZONES,DC=NEXUS,DC=WORLD.ldb
2492241 -rw-rw---- 1 root bind 1286144 Sep 26 11:00 DC=NEXUS,DC=WORLD.ldb
1579036 -rw-rw---- 2 root bind  421888 Sep 26 11:30 metadata.tdb



```

2) I still run the command samba_upgradedns --dns-backend=BIND9_DLZ. It replaced the named.conf file present in /usr/local/samba/private/named.conf with the original one. So I edited the file and commented the 9.8.0 line and uncommented the bind 9.9.0 ad dns zone database.

3) I stopped the apparmor and modified the file /etc/apparmor.d/usr.sbin.named and added the following entry in it 

/var/tmp/** rw

4)after that I restarted samba, apparmor, winbind and bind and run the following dns update command and this is what I got
```


root@openserver:~# samba_dnsupdate --verbose --all-names
not adding non-broadcast interface tun0
IPs: ['192.168.1.5', '192.168.2.5']
ldb_wrap open of secrets.ldb
Ignoring unknown parameter "server role"
Ignoring unknown parameter "server services"
Calling nsupdate for A nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
nexus.world.        900    IN    A    192.168.1.5


Ignoring unknown parameter "server role"
Ignoring unknown parameter "server services"
Calling nsupdate for A openserver.nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
openserver.nexus.world.    900    IN    A    192.168.1.5


Calling nsupdate for A gc._msdcs.nexus.world 192.168.1.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
gc._msdcs.nexus.world.    900    IN    A    192.168.1.5


Calling nsupdate for CNAME 21e8caca-daba-43d8-99b0-4056c9f434d3._msdcs.nexus.world openserver.nexus.world
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
21e8caca-daba-43d8-99b0-4056c9f434d3._msdcs.nexus.world. 900 IN    CNAME openserver.nexus.world.


Calling nsupdate for SRV _kpasswd._tcp.nexus.world openserver.nexus.world 464
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kpasswd._tcp.nexus.world. 900    IN    SRV    0 100 464 openserver.nexus.world.


Calling nsupdate for SRV _kpasswd._udp.nexus.world openserver.nexus.world 464
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kpasswd._udp.nexus.world. 900    IN    SRV    0 100 464 openserver.nexus.world.


Calling nsupdate for SRV _kerberos._tcp.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.nexus.world. 900    IN    SRV    0 100 88 openserver.nexus.world.


Calling nsupdate for SRV _kerberos._tcp.dc._msdcs.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.dc._msdcs.nexus.world. 900 IN SRV 0 100 88 openserver.nexus.world.


Calling nsupdate for SRV _kerberos._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV 0 100 88 openserver.nexus.world.


Calling nsupdate for SRV _kerberos._tcp.default-first-site-name._sites.dc._msdcs.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._tcp.default-first-site-name._sites.dc._msdcs.nexus.world. 900 IN SRV    0 100 88 openserver.nexus.world.


Calling nsupdate for SRV _kerberos._udp.nexus.world openserver.nexus.world 88
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_kerberos._udp.nexus.world. 900    IN    SRV    0 100 88 openserver.nexus.world.


Calling nsupdate for SRV _ldap._tcp.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.nexus.world.    900    IN    SRV    0 100 389 openserver.nexus.world.


Calling nsupdate for SRV _ldap._tcp.dc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.dc._msdcs.nexus.world. 900 IN SRV    0 100 389 openserver.nexus.world.


Calling nsupdate for SRV _ldap._tcp.gc._msdcs.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.gc._msdcs.nexus.world. 900 IN SRV    0 100 3268 openserver.nexus.world.


Calling nsupdate for SRV _ldap._tcp.pdc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.pdc._msdcs.nexus.world. 900 IN SRV    0 100 389 openserver.nexus.world.


Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV 0 100 389 openserver.nexus.world.


Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.dc._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.dc._msdcs.nexus.world. 900 IN    SRV 0 100 389 openserver.nexus.world.


Calling nsupdate for SRV _ldap._tcp.default-first-site-name._sites.gc._msdcs.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.default-first-site-name._sites.gc._msdcs.nexus.world. 900 IN    SRV 0 100 3268 openserver.nexus.world.


Calling nsupdate for SRV _ldap._tcp.d5e39e12-99f7-41da-ac70-821c5c60511d.domains._msdcs.nexus.world openserver.nexus.world 389
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_ldap._tcp.d5e39e12-99f7-41da-ac70-821c5c60511d.domains._msdcs.nexus.world. 900    IN SRV 0 100 389 openserver.nexus.world.


Calling nsupdate for SRV _gc._tcp.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_gc._tcp.nexus.world.    900    IN    SRV    0 100 3268 openserver.nexus.world.


Calling nsupdate for SRV _gc._tcp.default-first-site-name._sites.nexus.world openserver.nexus.world 3268
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
_gc._tcp.default-first-site-name._sites.nexus.world. 900 IN SRV    0 100 3268 openserver.nexus.world.


Calling nsupdate for A nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
nexus.world.        900    IN    A    192.168.2.5


Calling nsupdate for A openserver.nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
openserver.nexus.world.    900    IN    A    192.168.2.5


Calling nsupdate for A gc._msdcs.nexus.world 192.168.2.5
Outgoing update query:
;; ->>HEADER<<- opcode: UPDATE, status: NOERROR, id:      0
;; flags:; ZONE: 0, PREREQ: 0, UPDATE: 0, ADDITIONAL: 0
;; UPDATE SECTION:
gc._msdcs.nexus.world.    900    IN    A    192.168.2.5



```

---

### Post by lingpanda on 2013-09-26
Glad to hear it's working. However I do still notice it shows 
Ignoring unknown parameter "server role"
Ignoring unknown parameter "server services"

I looked at your smb.conf file and it seems fine with both those entries. I'm not sure about that however. I'm puzzled.

---

### Post by addictedboy on 2013-09-26
Yes, I am also not sure why it comes, since when I run testparm, it looks ok. It will be using old version of testparm, I think. 

```

root@openserver:~# samba-tool testparm
Press enter to see a dump of your service definitions


# Global parameters
[global]
        workgroup = NEXUS
        realm = NEXUS.WORLD
        netbios name = OPENSERVER
        server role = active directory domain controller
        log level = 3
        name resolve order = bcast, lmhosts, host, wins
        template shell = /bin/bash
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate
        idmap_ldb:use rfc2307 = yes


[netlogon]
        path = /usr/local/samba/var/locks/sysvol/nexus.world/scripts
        read only = No


[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No


[profiles]
        path = /home/serveradmin/profiles/
        read only = No
root@openserver:~#



```

---

