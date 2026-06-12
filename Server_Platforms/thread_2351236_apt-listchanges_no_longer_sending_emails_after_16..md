---
title: "apt-listchanges no longer sending emails after 16.04 LTS upgrade"
date: 2017-02-01
forum: Server Platforms
---

### Post by mdlueck on 2017-02-01
Greetings,

Our first server upgrade from 14.04 to 16.04, I observe we are no longer getting apt-listchanges emails when updating via:
```
/usr/bin/apt-get --assume-yes dist-upgrade
```

This 16.04 server showed the following output this morning applying an OpenSSL update:
```
$ sudo /opt/distrib/tools/ubuntu_autoupdate.sh 
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]       
Fetched 204 kB in 1s (123 kB/s)                              
Reading package lists... Done
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages will be upgraded:
  libssl1.0.0 openssl
Reading changelogs...
Preconfiguring packages ...
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
                                                              Need to get 0 B/1,415 kB of archives.
                                                                                                   After this operation, 0 B of additional disk space will be used.
(Reading database ... 52924 files and directories currently installed.)                                                                                            (Reading database ... 
Preparing to unpack .../libssl1.0.0_1.0.2g-1ubuntu4.6_i386.deb ...
Unpacking libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) over (1.0.2g-1ubuntu4.5) ...
Preparing to unpack .../openssl_1.0.2g-1ubuntu4.6_i386.deb ...
Unpacking openssl (1.0.2g-1ubuntu4.6) over (1.0.2g-1ubuntu4.5) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
Setting up openssl (1.0.2g-1ubuntu4.6) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
```

Where as a very similar server config still at 14.04 showed the following output for the same operation:
```
$ sudo /opt/distrib/tools/ubuntu_autoupdate.sh
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]
Get:2 http://security.ubuntu.com trusty-security InRelease [65.9 kB]
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [389 kB]
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,911 B]
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [173 kB]
Get:6 http://security.ubuntu.com trusty-security/main Sources [124 kB]       
Get:7 http://security.ubuntu.com trusty-security/restricted Sources [4,637 B]  
Get:8 http://security.ubuntu.com trusty-security/universe Sources [48.6 kB]    
Get:9 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [7,535 B] 
Get:10 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [898 kB] 
Get:11 http://security.ubuntu.com trusty-security/multiverse Sources [3,208 B] 
Get:12 http://security.ubuntu.com trusty-security/main i386 Packages [534 kB]  
Get:13 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.2 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [398 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.4 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/main Translation-en [461 kB]
Get:17 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,340 B]
Get:18 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,847 B]
Get:19 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [210 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Get:20 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.1 kB]
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Get:21 http://security.ubuntu.com trusty-security/universe i386 Packages [151 kB]
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Get:22 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,284 B]
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US  
Fetched 3,597 kB in 22s (160 kB/s)                                             
Reading package lists... Done
Reading package lists...
Building dependency tree...
Reading state information...
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
The following packages will be upgraded:
  libssl1.0.0 openssl
Reading changelogs...
Get:1 Changelog for libssl1.0.0 (http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_1.0.1f-1ubuntu2.22/changelog) [139 kB]
openssl (1.0.1f-1ubuntu2.22) trusty-security; urgency=medium

  * SECURITY UPDATE: Pointer arithmetic undefined behaviour
    - debian/patches/CVE-2016-2177-pre.patch: check for ClientHello message
      overruns in ssl/s3_srvr.c.
    - debian/patches/CVE-2016-2177-pre2.patch: validate ClientHello
      extension field length in ssl/t1_lib.c.
    - debian/patches/CVE-2016-2177-pre3.patch: pass in a limit rather than
      calculate it in ssl/s3_srvr.c, ssl/ssl_locl.h, ssl/t1_lib.c.
    - debian/patches/CVE-2016-2177.patch: avoid undefined pointer
      arithmetic in ssl/s3_srvr.c, ssl/t1_lib.c, 
    - CVE-2016-2177
  * SECURITY UPDATE: ECDSA P-256 timing attack key recovery
    - debian/patches/CVE-2016-7056.patch: use BN_mod_exp_mont_consttime in
      crypto/ec/ec.h, crypto/ec/ec_lcl.h, crypto/ec/ec_lib.c,
      crypto/ecdsa/ecs_ossl.c.
    - CVE-2016-7056
  * SECURITY UPDATE: DoS via warning alerts
    - debian/patches/CVE-2016-8610.patch: don't allow too many consecutive
      warning alerts in ssl/d1_pkt.c, ssl/s3_pkt.c, ssl/ssl.h,
      ssl/ssl_locl.h.
    - debian/patches/CVE-2016-8610-2.patch: fail if an unrecognised record
      type is received in ssl/s3_pkt.c.
    - CVE-2016-8610
  * SECURITY UPDATE: Truncated packet could crash via OOB read
    - debian/patches/CVE-2017-3731-pre.patch: sanity check
      EVP_CTRL_AEAD_TLS_AAD in crypto/evp/e_aes.c,
      crypto/evp/e_aes_cbc_hmac_sha1.c, crypto/evp/e_rc4_hmac_md5.c,
      crypto/evp/evp.h, ssl/t1_enc.c.
    - debian/patches/CVE-2017-3731.patch: harden RC4_MD5 cipher in
      crypto/evp/e_rc4_hmac_md5.c.
    - CVE-2017-3731

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Mon, 30 Jan 2017 11:38:06 -0500

apt-listchanges: Mailing root: apt-listchanges: changelogs for **serverhostnamehere**
Preconfiguring packages ...
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,262 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 48361 files and directories currently installed.)
Preparing to unpack .../libssl1.0.0_1.0.1f-1ubuntu2.22_i386.deb ...
Unpacking libssl1.0.0:i386 (1.0.1f-1ubuntu2.22) over (1.0.1f-1ubuntu2.21) ...
Preparing to unpack .../openssl_1.0.1f-1ubuntu2.22_i386.deb ...
Unpacking openssl (1.0.1f-1ubuntu2.22) over (1.0.1f-1ubuntu2.21) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libssl1.0.0:i386 (1.0.1f-1ubuntu2.22) ...
Setting up openssl (1.0.1f-1ubuntu2.22) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
```


I have checked the 16.04 machine and command apt-listchanges appears to still be installed. Why suddenly are apt commands no longer triggering apt-listchanges output emails?

I am thankful,

---

### Post by mdlueck on 2017-02-07
On the upgraded 16.04 server, I tried purging off the apt-listchanges and then reinstalling it. Some time later, package apticron notified me of pending updates, I applied them, and still no email from apt-listchanges. Opening a defect against apt-listchanges package.

Defect logged here:
"After LTS upgrade to 16.04, no more emails come from apt-listchanges"
[https://bugs.launchpad.net/bugs/1662550](https://bugs.launchpad.net/bugs/1662550)

---

