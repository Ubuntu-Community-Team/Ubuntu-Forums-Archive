---
title: "netcat localhost 22: connection timed out"
date: 2018-01-08
forum: Server Platforms
---

### Post by flutz on 2018-01-08
I finally upgraded my server from 10.04 LTS to 14.04 LTS because some new programmes were not able to run anymore, but since then I have trouble starting my license servers (flexnet licenses). After trying and sniffing a lot, I found out that my server has problems with identifying itself:
When I try to contact "myself" via netcat, I get the following response:

root@hs1:~# nc -vz localhost 22
nc: connect to localhost port 22 (tcp) failed: Connection timed out



If I try the same to contact another one of my servers (indy3), i get the following:
root@hs1:~# nc -vz indy3 22
Connection to indy3 22 port [tcp/ssh] succeeded!


The /etc/hosts file can identify itself either as localhost or as hs1 and indy3 as my second server (###.###.### by me to mask my IP address):
127.0.0.1       localhost
132.###.###.###  hs1
132.###.###.###  indy3

Trying to contact hs1 from indy3 works fine:
fabian@indy3:~$ nc -vz hs1 22
Connection to hs1 22 port [tcp/ssh] succeeded!

So, in short: hs1 can contact others, others can contact hs1 but it cannot contact itself?
Trying the ping command also works fine:

root@hs1:~# ping hs1
PING hs1 (132.###.###.###) 56(84) bytes of data.
64 bytes from hs1 (132.###.###.###): icmp_req=1 ttl=64 time=0.102 ms
64 bytes from hs1 (132.###.###.###): icmp_req=2 ttl=64 time=0.106 ms
64 bytes from hs1 (132.###.###.###): icmp_req=3 ttl=64 time=0.106 ms
64 bytes from hs1 (132.###.###.###): icmp_req=4 ttl=64 time=0.105 ms
^C
--- hs1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.102/0.104/0.106/0.012 ms


So why can't hs1 contact itself? This in itself would not disturb me, but the fact that it doesn't work might be a symptom to a deeper problem i don't see and which might also be the problem why I'm having connection issues with my license servers.

Does anybody know my prolem?

---

### Post by flutz on 2018-01-08
P.S. If I use the servers IP-address instead of "localhost", it also results in a timeout.

---

### Post by LHammonds on 2018-01-09
Why install 14.04 rather than 16.04?

---

### Post by flutz on 2018-01-09
I didn't reinstall the whole system but made a dist-upgrade from 10.04 to 12.04 and 12.04 to 14.04. As we have some older programmes that might cause trouble on 16.04, I stopped at 14.04

---

### Post by flutz on 2018-01-09
I just checked and I also can't connect from hs1 to itself via ssh (ssh username@myserver), it just times out. Yet I can connect to any other server from my server and from any other server to myserver

---

### Post by LHammonds on 2018-01-09
That is completely understandable.  Was just curious.

Since this was in-place upgrades, I don't think I can help you.  I have only installed new OS versions and configure them to take over for the older version.  I found that in-place upgrades of major versions are just too unpredictable due to the additional software installed on top of the OS.

I understand why people do it when they only have a bare-metal install (physical server).  However it is possible to completely test a full migration using virtualization...such as installing VirtualBox on your PC to install a new OS, then the various required application software and then replicate the same configuration and eventually migrate the data to have an exact duplicate of production to test it out...once the software is tested and procedure for doing the upgrade is documented/tested, then the bare-metal server can be re-installed with confidence and without any residual upgrade issues.

Good luck getting her working.

EDIT: Check the SSH logs or use ssh connection with verbose output to see if you can glean additional info.

LHammonds

---

### Post by Max303 on 2018-01-11
What's the value of ListenAddress in /etc/ssh/sshd_config on your "localhost"?

---

### Post by LHammonds on 2018-01-11
I just installed a fresh 14.04.5 LTS server and fully patched it.  Here are the defaults so you can compare:

```
root@ubuntu:/# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty
```

```
root@ubuntu:/# uname -a
Linux ubuntu 4.4.0-109-generic #132~14.04.1-Ubuntu SMP Tue Jan 9 21:46:42 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

```

root@ubuntu:/# vi /etc/ssh/ssh_config

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

---

