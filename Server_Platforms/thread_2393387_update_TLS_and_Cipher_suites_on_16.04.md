---
title: "update TLS and Cipher suites on 16.04"
date: 2018-06-02
forum: Server Platforms
---

### Post by Heeter on 2018-06-02
Hi all,

Running a test on ssllabs.com of my server tells me that I have quite a few outdated and weak cipher suites.

Also, My server is currently using TLS 1.0 & 1.1, would like to change that to TLS1.2 & 1.3

I have never done these types of tasks in Ubuntu Server, before. Hopefully someone who has can assist me.

Regards

---

### Post by CharlesA on 2018-06-02
I'm assuming you are testing an HTTP server, but the way you configure strong SSL ciphers and whatnot varies based on which web server you are using.

This should be a good start, though: [https://cipherli.st/](https://cipherli.st/)

---

