---
title: "How to use AES-GCM encryption for IPsec / racoon on Ubuntu 15.10"
date: 2016-02-16
forum: Security
---

### Post by gijs007 on 2016-02-16
I'm using racoon to create an IPsec tunnel between a Windows machine and Linux.
I'm currently using the following configuration for phase 2:

```
sainfo anonymous{
        encryption_algorithm aes_256;
        authentication_algorithm hmac_sha1;
        compression_algorithm deflate;
        lifetime time 12 hour;
}

```
The above configuration results in using AES-CBC which is less secure than AES-GCM according to this cloudflare blog: [https://blog.cloudflare.com/padding-oracles-and-the-decline-of-cbc-mode-ciphersuites/](https://blog.cloudflare.com/padding-oracles-and-the-decline-of-cbc-mode-ciphersuites/)
I can't find any documentation on how to use AES-GCM, I'm not sure what the proper value for it is. I've tried a few obvious ones like aes_gcm_256 but that didn't work (resulted in racoon not starting up).

I'd also like to use AES-GMAC or AES-GCM as authentication algorithm, but couldn't find out how to do this either.

---

