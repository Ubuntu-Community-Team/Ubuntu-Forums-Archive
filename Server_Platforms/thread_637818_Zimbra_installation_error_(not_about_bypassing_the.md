---
title: "Zimbra installation error (not about bypassing the version problem)"
date: 2007-12-11
forum: Server Platforms
---

### Post by lexarrow on 2007-12-11
Hi all,

I'm having trouble installing Zimbra after I bypassed the version problem. Now it gets stuck when it tries to install the packages. Here's the full error log:
```
root@alex-laptop:~# /root/install.sh
hostname: Unknown host
hostname: Unknown host

Operations logged to /tmp/install.log.8154
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-cluster...NOT FOUND
    zimbra-core...NOT FOUND


PLEASE READ THIS AGREEMENT CAREFULLY BEFORE USING THE SOFTWARE.
ZIMBRA, INC. ("ZIMBRA") WILL ONLY LICENSE THIS SOFTWARE TO YOU IF YOU
FIRST ACCEPT THE TERMS OF THIS AGREEMENT. BY DOWNLOADING OR INSTALLING
THE SOFTWARE, OR USING THE PRODUCT, YOU ARE CONSENTING TO BE BOUND BY
THIS AGREEMENT. IF YOU DO NOT AGREE TO ALL OF THE TERMS OF THIS
AGREEMENT, THEN DO NOT DOWNLOAD, INSTALL OR USE THE PRODUCT.

License Terms for the Zimbra Collaboration Suite:
  http://www.zimbra.com/license/zimbra_public_eula_2.1.html


Press Return to continue

Checking for prerequisites...
    NPTL...FOUND
    sudo...FOUND sudo-1.6.8p12-5ubuntu2
    libidn11...FOUND libidn11-1.0-0
    curl...FOUND curl-7.16.4-2ubuntu1
    fetchmail...FOUND fetchmail-6.3.8-8ubuntu2
    libpcre3...FOUND libpcre3-7.4-0ubuntu0.7.10.1
    libgmp3c2...FOUND libgmp3c2-2:4.2.1+dfsg-5ubuntu4
    libexpat1...FOUND libexpat1-1.95.8-4ubuntu1
    libxml2...FOUND libxml2-2.6.30.dfsg-2ubuntu1
    libstdc++6...FOUND libstdc++6-4.2.1-5ubuntu4
    libstdc++5...FOUND libstdc++5-1:3.3.6-15ubuntu2
    openssl...FOUND openssl-0.9.8e-5ubuntu3.1
    libltdl3...FOUND libltdl3-1.5.24-1ubuntu1

Checking for installable packages

Found zimbra-core
Found zimbra-ldap
Found zimbra-logger
Found zimbra-mta
Found zimbra-snmp
Found zimbra-store
Found zimbra-apache
Found zimbra-spell
Found zimbra-proxy


Select the packages to install

Install zimbra-ldap [Y] y

Install zimbra-logger [Y] y

Install zimbra-mta [Y] y

Install zimbra-snmp [Y] y

Install zimbra-store [Y] y

Install zimbra-spell [Y] y

Install zimbra-proxy [N] n
Checking required space for zimbra-core
checking space for zimbra-store

Installing:
    zimbra-core
    zimbra-ldap
    zimbra-logger
    zimbra-mta
    zimbra-snmp
    zimbra-store
    zimbra-apache
    zimbra-spell

The system will be modified.  Continue? [N] y

Removing /opt/zimbra
Installing packages

    zimbra-core......zimbra-core_5.0.0_RC2_1745.UBUNTU6_i386.deb...FAILED
###ERROR###

zimbra-core_5.0.0_RC2_1745.UBUNTU6_i386.deb installation failed

Installation cancelled

```

Does anyone know what needs to be changed?

THANKS!

---

### Post by lexarrow on 2007-12-11
I solved it by editing /etc/lsb-release setting version to 6 and
```
mv /etc/debian_version /etc/debian_version.zimbra
```

---

### Post by Shikha Sood on 2008-07-15
I am facing the same problem, tried the above trick.But it didn't work for me.Can anybody help?

---

