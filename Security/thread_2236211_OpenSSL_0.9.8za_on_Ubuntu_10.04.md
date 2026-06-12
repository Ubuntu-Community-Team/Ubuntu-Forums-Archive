---
title: "OpenSSL 0.9.8za on Ubuntu 10.04"
date: 2014-07-25
forum: Security
---

### Post by leigh.hicks on 2014-07-25
Hi Guys,

Have been scouring the forums but can't seem to find any info... I have a server running Ubuntu 10.04 and currently has OpenSSL 0.9.8k. Due to vulnerabilities my manager has asked me to upgrade this to OpenSSL 0.9.8za. Can somebody please advise me on the best way to do this? The basics (apt-get update && apt-get upgrade) do not update it past 0.9.8k. 

OpenSSL 0.9.8k 25 Mar 2009
built on: Fri Jun 20 19:17:57 UTC 2014
platform: debian-amd64
options:  bn(64,64) md2(int) rc4(ptr,char) des(idx,cisc,16,int) blowfish(ptr2)
compiler: cc -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -m64 -DL_ENDIAN -DTERMIO -O3 -Wa,--noexecstack -g -Wall -DMD32_REG_T=int -DOPENSSL_BN_ASM_MONT -DSHA1_ASM -DSHA256_ASM -DSHA512_ASM -DMD5_ASM -DAES_ASM
OPENSSLDIR: "/usr/lib/ssl"

I've noticed the build date of Fri Jun 20 19:17:57 UTC 2014 which would indicate that it should be ok? But if there is a way I can upgrade I would love to hear it, please.

Sorry if this sounds like a rubbish question, I've spent a good few hours going insane - it may be that I can't see the wood for the trees! Any more info please let me know...

Cheers

---

### Post by leigh.hicks on 2014-07-25
... Have also tried an apt-get dist-upgrade.

Of course there's compiling from source:

wget [http://www.openssl.org/source/openssl-1.0.1h.tar.gz](http://www.openssl.org/source/openssl-1.0.1h.tar.gz)


wget [http://www.openssl.org/source/openssl-1.0.1h.tar.gz.md5](http://www.openssl.org/source/openssl-1.0.1h.tar.gz.md5)


md5sum openssl-1.0.1h.tar.gz


cat openssl-1.0.1h.tar.gz.md5


tar -xvzf openssl-1.0.1h.tar.gz


cd openssl-1.0.1h


./config --prefix=/usr/local/openssl --openssldir=/usr/local/openssl


make


make install

But would prefer an apt-get :)

Cheers

---

### Post by SeijiSensei on 2014-07-25
You should read the [Changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.19/changelog).  Any vulnerabilities you are concerned about that are not on that list?

0.9.8 is not vulnerable to the "Heartbleed" bug.

---

### Post by leigh.hicks on 2014-07-28
Thanks for the reply, it was the CVE-2014-0224 I was concerned about, I was aware that 0.9.8 was not vulnerable to Heartbleed.

When posting I thought it might have been a total noob question, which has been the case. I didn't realise that Ubuntu has it's own way of updating OpenSSL and that simply by running an apt-get upgrade patches OpenSSL and the vulnerability! Panic over :)

---

### Post by SeijiSensei on 2014-07-28
No, it's not a noob question at all.  On systems with long-term support, security patches will often be "backported" to an existing release version without a change in the version number.  This can be really confusing even for seasoned veterans.

It's not just a Debian/Ubuntu thing; RedHat does this as well.

---

