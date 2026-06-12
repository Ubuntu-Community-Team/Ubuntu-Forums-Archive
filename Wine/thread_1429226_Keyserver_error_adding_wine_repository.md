---
title: "Keyserver error adding wine repository"
date: 2010-03-13
forum: Wine
---

### Post by Linux_Zoo on 2010-03-13
Hi,

I'm trying to upgrade to the latest version of wine on Ubuntu 9.10.

When I run the command:

sudo add-apt-repository ppa:ubuntu-wine/ppa

I get:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

If I proceed without the trust certificate I get dire warnings about the dangers of upgrading from untrusted repositories. The entry at:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

...seems to think it's not required for 9.10. Can anyone help?

---

