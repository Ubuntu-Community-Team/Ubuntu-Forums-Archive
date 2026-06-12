---
title: "SSL question"
date: 2014-04-19
forum: Security
---

### Post by WogBoy on 2014-04-19
Ok so I had a look at what SSL I have on my pc and it shows 2 dates.
```
OpenSSL 1.0.1 14 Mar 2012
built on: Mon Apr  7 20:33:29 UTC 2014
platform: debian-amd64
options:  bn(64,64) rc4(8x,int) des(idx,cisc,16,int) blowfish(idx) 
compiler: cc -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -m64 -DL_ENDIAN -DTERMIO -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -Wl,-z,relro -Wa,--noexecstack -Wall -DOPENSSL_NO_TLS1_2_CLIENT -DOPENSSL_MAX_TLS1_2_CIPHER_LENGTH=50 -DMD32_REG_T=int -DOPENSSL_IA32_SSE2 -DOPENSSL_BN_ASM_MONT -DOPENSSL_BN_ASM_MONT5 -DOPENSSL_BN_ASM_GF2m -DSHA1_ASM -DSHA256_ASM -DSHA512_ASM -DMD5_ASM -DAES_ASM -DVPAES_ASM -DBSAES_ASM -DWHIRLPOOL_ASM -DGHASH_ASM
OPENSSLDIR: "/usr/lib/ssl"

```

I see built on: Mon Apr  7 20:33:29 UTC 2014 and figure i am ok. Is this correct?

Thanks 
Wog

---

### Post by sammiev on 2014-04-19
Apr  7 is good.

---

### Post by WogBoy on 2014-04-23
Thank you.

---

