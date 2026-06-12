---
title: "Samba join active directory domain"
date: 2020-01-15
forum: Server Platforms
---

### Post by pg123 on 2020-01-15
Hello,
  I'm trying to join a Windows domain with samba on an ubuntu 18.04 server and so far I didn't get it to work.

I'm able to do the kinit and I see the token with klist but when I try to join like this:
```
net ads join -U Administrator@d1.lan -d3
```

I get an error message
```
DNS Update for zfs1.d1.lan failed: ERROR_DNS_UPDATE_FAILED
DNS update failed: NT_STATUS_UNSUCCESSFUL
```

With debug options, there's a lot more details but I don't see any information that could give a hint about what's the problem.

If I don't follow that procedure and install and use realm join, I can join just fine and I can see my Windows users so I know it's possible. The problem in that case is that samba doesn't seem to understand how to use that connection to do the authentication because the attempts to connect to a shared directory fails. It tries to connect as guest even when I explicitly provide username and password information from the Windows machine. If I add a user with smbpasswd then it works fine so the share itself is working.

The test environment is pretty simple, I have 1 Windows server 2019 that is used as AD and the client for testing the smb connection. I also have 1 Ubuntu 18.04 machine that I'm trying to just join to the domain.

I followed the procedure described in this document: [https://discourse.ubuntu.com/t/service-sssd/11579](https://discourse.ubuntu.com/t/service-sssd/11579)

I'll include a few of the key configuration files in case there's a problem in one of them.

```
cat resolv.conf
nameserver 192.168.0.60
domain d1.lan
search d1.lan
```

```
cat hosts
127.0.0.1       localhost
192.168.0.40 zfs1.d1.lan zfs1
```

```
cat /etc/chrony/chrony.conf
server 192.168.0.60 iburst
keyfile /etc/chrony/chrony.keys
driftfile /var/lib/chrony/chrony.drift
logdir /var/log/chrony
maxupdateskew 100.0
rtcsync
makestep 1 3
```

```
# cat /etc/sssd/sssd.conf
[sssd]
services = nss, pam
config_file_version = 2
domains = D1.LAN

[domain/D1.LAN]
id_provider = ad
access_provider = ad

# Use this if users are being logged in at /.
# This example specifies /home/DOMAIN-FQDN/user as /root.  Use with pam_mkhomedir.so
override_homedir = /home/%u
use_fully_qualified_names = False

# Uncomment if the client machine hostname doesn't match the computer object on the DC.
# ad_hostname = mymachine.myubuntu.example.com

# Uncomment if DNS SRV resolution is not working
# ad_server = dc.mydomain.example.com

# Uncomment if the AD domain is named differently than the Samba domain
# ad_domain = MYUBUNTU.EXAMPLE.COM

# Enumeration is discouraged for performance reasons.
# enumerate = true
```

```
cat /etc/samba/smb.conf
[global]

workgroup = D1
client signing = yes
client use spnego = yes
kerberos method = secrets and keytab
realm = D1.LAN
security = ads
log level = 3
```

```
cat /etc/krb5.conf
[libdefaults]
        default_realm = D1.LAN
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true

[realms]
        D1.LAN = {
                kdc = 192.168.0.60
                admin_server = 192.168.0.60
        }
[domain_realm]
        .d1.lan = D1.LAN
        d1.lan  = D1.LAN
```

---

### Post by LHammonds on 2020-01-16
With a DNS update failure, are you sure it is trying to resolve DNS from the remote AD server or is it trying to resolve it locally itself?

Also, you might need to ensure the FQDN of the AD/DNS server is resolvable from Ubuntu.  Ubuntu knowing the IP might not be enough, it might require knowing the FQDN.

Sorry I can't be much more help, all of my Linux boxes are silos to themselves and I consider them more secure by NOT joining Windows. (yeah yeah, I know, not as easy to admin centrally)

LHammonds

---

### Post by pg123 on 2020-01-17
> **LHammonds said:**
> With a DNS update failure, are you sure it is trying to resolve DNS from the remote AD server or is it trying to resolve it locally itself?

I'm pretty sure. My resolv.conf points to the AD and if I dig I get an answer from it. Also, the linux machine is already in the AD DNS.

```
# dig ad1.d1.lan

; <<>> DiG 9.11.3-1ubuntu1.11-Ubuntu <<>> ad1.d1.lan
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28884
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;ad1.d1.lan.                    IN      A

;; ANSWER SECTION:
ad1.d1.lan.             3600    IN      A       192.168.0.60

;; Query time: 0 msec
;; [COLOR=#ff0000]SERVER: 192.168.0.60[/COLOR]#53(192.168.0.60)
;; WHEN: Fri Jan 17 09:37:37 EST 2020
;; MSG SIZE  rcvd: 55


```


> **LHammonds said:**
> Also, you might need to ensure the FQDN of the AD/DNS server is resolvable from Ubuntu.  Ubuntu knowing the IP might not be enough, it might require knowing the FQDN.

That seems to resolve correctly for both the client and server. I can ping both with the fullname or shortname.
```
# ping -c1 ad1.d1.lan
PING ad1.d1.lan (192.168.0.60) 56(84) bytes of data.
64 bytes from 192.168.0.60: icmp_seq=1 ttl=128 time=0.303 ms

--- ad1.d1.lan ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.303/0.303/0.303/0.000 ms
# ping -c1 zfs1.d1.lan
PING zfs1.d1.lan (192.168.0.40) 56(84) bytes of data.
64 bytes from zfs1.d1.lan (192.168.0.40): icmp_seq=1 ttl=64 time=0.018 ms

--- zfs1.d1.lan ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.018/0.018/0.018/0.000 ms

```
> **LHammonds said:**
> Sorry I can't be much more help, all of my Linux boxes are silos to  themselves and I consider them more secure by NOT joining Windows. (yeah  yeah, I know, not as easy to admin centrally)

I have a few hundred users in the AD that will need access to the file servers. I don't think creating local samba accounts for each of them on all of our server would be easy, unless there's another way to go about it.

Thanks for the input.

---

### Post by pg123 on 2020-01-20
On the test setup I have, eth0 is an ip address that allows for the system updates and package installation and eth1 is the internal network where the communication between client and server should be done.

For some reason, it seems that having eth0 up was causing the problem.
Since this is a test environment, I install all my updates and packages and I shut eth0 down before trying to join the domain and that seems to work.

---

### Post by LHammonds on 2020-01-24
Ah, so it was a multi-nic routing issue.  While eth0 was active, traffic was trying to route through that gateway?

---

