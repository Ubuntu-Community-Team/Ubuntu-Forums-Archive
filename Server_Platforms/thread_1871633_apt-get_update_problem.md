---
title: "apt-get update problem"
date: 2011-10-29
forum: Server Platforms
---

### Post by wmtabada on 2011-10-29
I have the same problem in Ubuntu 10.04 LTS. When I sudo apt-get update I got this error:

W: GPG error: [http://download.webmin.com](http://download.webmin.com) sarge Release: The following  signature couldn't be verified because the public key is not available: NO_PUBKEY D97A3AE9111F63C51

Please help me resolve this problem.

---

### Post by garvinrick4 on 2011-10-29
> W: GPG error: [http://download.webmin.com]("http://download.webmin.com/")  sarge Release: The following  signature couldn't be verified because  the public key is not available: NO_PUBKEY D97A3AE9111F63C51
What is it? webmin.

---

### Post by howefield on 2011-10-29
Posts spliced off to own thread.

---

### Post by Lars Noodén on 2011-10-29
To make that repository available you have to import the key for it using [gpg --recv-key](http://manpages.ubuntu.com/manpages/oneiric/en/man1/gpg.1.html)  Then you'll need to use [apt-key](http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-key.8.html) to put it where APT needs it to be.  

Here's my guess:
```

$ gpg --recv-keys 11F63C51

$ gpg -a --output /tmp/pub.asc --export 11F63C51

$ sudo apt-key add /tmp/pub.asc

$ sudo apt-get update

```

---

