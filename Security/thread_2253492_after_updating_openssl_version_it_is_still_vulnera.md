---
title: "after updating openssl version it is still vulnerable from OpenSSL CCS vulnerability"
date: 2014-11-20
forum: Security
---

### Post by srinet on 2014-11-20
Hi,

I have one ubunti server running on ubuntu 12.04 and the openssl version is 1.0.0e i upgrade it to 1.0.0o to prevent from [OpenSSL CCS vulnerability (CVE-2014-0224)]("https://community.qualys.com/blogs/securitylabs/2014/06/13/ssl-pulse-49-vulnerable-to-cve-2014-0224-14-exploitable") but it is still showing [B]"Experimental: This server is vulnerable to the [OpenSSL CCS vulnerability (CVE-2014-0224)]("https://community.qualys.com/blogs/securitylabs/2014/06/13/ssl-pulse-49-vulnerable-to-cve-2014-0224-14-exploitable") and exploitable.            Grade set to F." on the ssl testing site

my configurations are

[/B]#  cat /etc/issue
Ubuntu 12.04.4 LTS \n \l

# openssl version -a
OpenSSL 1.0.0o 15 Oct 2014
built on: Thu Nov 20 08:35:14 UTC 2014
platform: linux-x86_64
options:  bn(64,64) rc4(1x,char) des(idx,cisc,16,int) idea(int) blowfish(idx) 
compiler: gcc -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -Wa,--noexecstack -m64 -DL_ENDIAN -DTERMIO -O3 -Wall -DMD32_REG_T=int -DOPENSSL_IA32_SSE2 -DOPENSSL_BN_ASM_MONT -DSHA1_ASM -DSHA256_ASM -DSHA512_ASM -DMD5_ASM -DAES_ASM -DWHIRLPOOL_ASM
OPENSSLDIR: "/usr/ssl"


o# dpkg -l openssl
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
ii  openssl                         1.0.1g-1ppa1~precise1 




# /usr/local/nginx/sbin/nginx -V
nginx version: nginx/1.1.13
built by gcc 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
TLS SNI support enabled
configure arguments: --prefix=/usr/local/nginx --add-module=/usr/local/chunkin-nginx-module-0.23/ --with-http_ssl_module --with-pcre=/usr/local/pcre-8.32/


Can any one help me why it is still vulnerable from the  [B][OpenSSL CCS vulnerability (CVE-2014-0224)]("https://community.qualys.com/blogs/securitylabs/2014/06/13/ssl-pulse-49-vulnerable-to-cve-2014-0224-14-exploitable") 

Thank in advance.



[/B]

---

