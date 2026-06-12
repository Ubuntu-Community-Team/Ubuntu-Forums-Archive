---
title: "tftpd-hpa upgrade failing in Ubuntu 10.04 Server"
date: 2011-02-18
forum: Server Platforms
---

### Post by Z.K. on 2011-02-18
I recently did a apt-get update, apt-get upgrade and I get errors involving the tftpd-hpa.  I was wondering if anyone knows why it would be giving me these errors.  

Errors:
> 
 apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  tftpd-hpa
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
69 not fully installed or removed.
Need to get 0B/44.8kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
/etc/default/tftpd-hpa: 9: Syntax error: Unterminated quoted string
tftpd-hpa failed to preconfigure, with exit status 2
(Reading database ... 82607 files and directories currently installed.)
Preparing to replace tftpd-hpa 5.0-11ubuntu2 (using .../tftpd-hpa_5.0-11ubuntu2.1_i386.deb) ...
/etc/default/tftpd-hpa: 9: Syntax error: Unterminated quoted string
dpkg: error processing /var/cache/apt/archives/tftpd-hpa_5.0-11ubuntu2.1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tftpd-hpa_5.0-11ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


/etc/default/tftpd-hpa:
```

# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
#TFTP_DIRECTORY="/var/lib/tftpboot"
#TFTP_ADDRESS="0.0.0.0:69"
TFTP_ADDRESS=192.168.0.2:69"
#TFTP_OPTIONS="--secure"
TFTP_DIRECTORY="/tftpboot"
TFTP_OPTIONS="-l -s /tftpboot"
RUN_DAEMON="yes"

```

Thanks,
:confused:

---

### Post by kwahamot on 2012-10-23
I'm having this problem too now. Is there a solution? It's actually blocking all other upgrades and apt-get install actions.

---

