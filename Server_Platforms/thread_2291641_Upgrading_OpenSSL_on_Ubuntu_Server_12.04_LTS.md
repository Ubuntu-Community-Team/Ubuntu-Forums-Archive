---
title: "Upgrading OpenSSL on Ubuntu Server 12.04 LTS?"
date: 2015-08-21
forum: Server Platforms
---

### Post by Marc-NJ on 2015-08-21
Hi,

Hoping someone can point me in the right direction.  I use ownCloud on my Ubuntu 12.04 LTS server and recently updated it to v8.1.1, and now am getting a warning about needing to update OpenSSL since cURL is using an outdated version of it.  However, I've updated my Ubuntu server fully at this point with all available updates/patches, and apparently am still on an older version of OpenSSL.  I am planning to eventually migrate to Ubuntu Server 14.04, but want to know if there's an easy way to get a newer version of OpenSSL on my 12.04 server that won't break anything but will fix this issue?

Any help is greatly appreciated!  Thanks!

---

### Post by CharlesA on 2015-08-23
I don't believe there is an easy way to do that. I will check to see if I get the same message on my Wheezy box when I get home.

---

### Post by CharlesA on 2015-08-23
> **CharlesA said:**
> I don't believe there is an easy way to do that. I will check to see if I get the same message on my Wheezy box when I get home.

I just checked my wheezy box and it is running  OpenSSL 1.0.1e 11 Feb 2013 (built on Jun 13 2015) with curl 7.26.0 (x86_64-pc-linux-gnu) libcurl/7.26.0 OpenSSL/1.0.1e zlib/1.2.7 libidn/1.25 libssh2/1.4.2 librtmp/2.3

I do not see any warnings in the admin section of owncloud 8.1.1. My system is up-to-date.

Which version of openssl are you using at the moment? Run this:
```
openssl version -a
```
```
curl -V
```

---

### Post by Marc-NJ on 2015-08-26
Thanks for the replies!  Here's the info you requested.  Let me know what next steps are if any.  Thanks again!

```
<USER>@<SERVER>:~$ openssl version -a
OpenSSL 1.0.1 14 Mar 2012
built on: Thu Jun 11 15:26:20 UTC 2015
platform: debian-amd64
options:  bn(64,64) rc4(16x,int) des(idx,cisc,16,int) blowfish(idx)
compiler: cc -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -m64 -DL_ENDIAN -DTERMIO -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro -Wa,--noexecstack -Wall -DOPENSSL_NO_TLS1_2_CLIENT -DMD32_REG_T=int -DOPENSSL_IA32_SSE2 -DOPENSSL_BN_ASM_MONT -DOPENSSL_BN_ASM_MONT5 -DOPENSSL_BN_ASM_GF2m -DSHA1_ASM -DSHA256_ASM -DSHA512_ASM -DMD5_ASM -DAES_ASM -DVPAES_ASM -DBSAES_ASM -DWHIRLPOOL_ASM -DGHASH_ASM
OPENSSLDIR: "/usr/lib/ssl"
```

```
<USER>@<SERVER>:~$ curl -V
curl 7.22.0 (x86_64-pc-linux-gnu) libcurl/7.22.0 OpenSSL/1.0.1 zlib/1.2.3.4 libidn/1.23 librtmp/2.3
Protocols: dict file ftp ftps gopher http https imap imaps ldap pop3 pop3s rtmp rtsp smtp smtps telnet tftp
Features: GSS-Negotiate IDN IPv6 Largefile NTLM NTLM_WB SSL libz TLS-SRP
```

---

### Post by CharlesA on 2015-08-26
Strange that the 12.04's version of OpenSSL is older than the one on my Wheezy box, which 12.04 was based off.

From what I can tell, the only way to upgrade OpenSSL is to compile it from scratch: [http://askubuntu.com/questions/429385/upgrade-openssl-on-ubuntu-12-04](http://askubuntu.com/questions/429385/upgrade-openssl-on-ubuntu-12-04)

I found this ([from here]("https://doc.owncloud.org/server/8.1/admin_manual/configuration_server/security_setup_warnings.html")):

> 
Outdated NSS / OpenSSL version

&#8220;cURL is using an outdated OpenSSL version (OpenSSL/$version). Please update your operating system or features such as installing and updating apps via the app store or Federated Cloud Sharing will not work reliably.&#8221;

&#8220;cURL is using an outdated NSS version (NSS/$version). Please update your operating system or features such as installing and updating apps via the app store or Federated Cloud Sharing will not work reliably.&#8221;

There are known bugs in older OpenSSL and NSS versions leading to misbehaviour in combination with remote hosts using SNI. A technology used by most of the HTTPS websites. To ensure that ownCloud will work properly you need to update OpenSSL to at least 1.0.2b or 1.0.1d. For NSS the patch version depends on your distribution and an heuristic is running the test which actually reproduces the bug. There are distributions such as RHEL/CentOS which have this backport still pending.


This was also confirmed from someone on the OwnCloud IRC on Freenode. They suggested upgraded the OS, and that would probably be the best route to go imho.

---

### Post by Marc-NJ on 2015-08-26
Got it - I do plan to eventually move to Ubuntu Server 14.04, and am slowly making headway into doing that, but just haven't found the time to fully move over to it yet.  I guess I'll live with the out-of-date OpenSSL on ownCloud until then, but thanks for the info and help!!

---

### Post by CharlesA on 2015-08-26
> **Marc_Bressman said:**
> Got it - I do plan to eventually move to Ubuntu Server 14.04, and am slowly making headway into doing that, but just haven't found the time to fully move over to it yet.  I guess I'll live with the out-of-date OpenSSL on ownCloud until then, but thanks for the info and help!!

The person I spoke to on IRC said it should be ok as long as you aren't using Federated Cloud Sharing. There could be bugs if you use it with an older version of OpenSSL.

---

### Post by Marc-NJ on 2015-08-30
> **CharlesA said:**
> The person I spoke to on IRC said it should be ok as long as you aren't using Federated Cloud Sharing. There could be bugs if you use it with an older version of OpenSSL.

Federated Cloud Sharing is just the ability to use multiple instances of ownCloud in different locations in some sort of combined/networked fashion, right?  If so, then I'm not using that, so hopefully I'll be OK using it in the current manner until I move to 14.04.  Thanks again for your help and the information!

---

### Post by CharlesA on 2015-08-30
> **Marc_Bressman said:**
> Federated Cloud Sharing is just the ability to use multiple instances of ownCloud in different locations in some sort of combined/networked fashion, right?  If so, then I'm not using that, so hopefully I'll be OK using it in the current manner until I move to 14.04.  Thanks again for your help and the information!

Seems like it. This is what it says in my admin panel:

> Federated Cloud Sharing

Allow users on this server to send shares to other servers

Allow users on this server to receive shares from other servers 

---

