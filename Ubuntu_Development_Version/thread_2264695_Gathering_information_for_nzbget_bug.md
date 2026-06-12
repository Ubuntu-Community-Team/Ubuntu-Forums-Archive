---
title: "Gathering information for nzbget bug"
date: 2015-02-09
forum: Ubuntu Development Version
---

### Post by raptir on 2015-02-09
I've never submitted a bug report before and I'm hoping to get some help with gathering more information to log the bug. In Vivid, nzbget does not cooperate with the current version of gnutls. From reading on the nzbget forum it seems to be an ongoing incompatibility with newer versions of gnutls. When trying to download any files, nzbget now returns:

```
TLS handshake failed: Error in the system's randomness device.
```

The same error occurs if I build nzbget-14.1 from source. I was able to resolve the issue by installing libssl-dev and configuring nzbget to use openssl instead of gnutls.

```
./configure --with-tlslib=OpenSSL
```

I understand the basic bug report process using the built-in error reporting tools, but I am not sure what the proper bug to file here would be. Is it a bug with nzbget, that it should instead be built to use OpenSSL? Or is it a bug with libgnutls that causes it to be incompatible with nzbget?

---

### Post by mc4man on 2015-02-09
I'd re-install the repo version of nzbget then file a bug on it
ubuntu-bug nzbget

---

### Post by raptir on 2015-03-16
[https://bugs.launchpad.net/ubuntu/+source/nzbget/+bug/1427486](https://bugs.launchpad.net/ubuntu/+source/nzbget/+bug/1427486)

I logged the bug a couple weeks ago. Did I leave anything necessary out?

---

