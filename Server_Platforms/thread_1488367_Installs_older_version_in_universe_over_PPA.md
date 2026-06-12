---
title: "Installs older version in universe over PPA?"
date: 2010-05-20
forum: Server Platforms
---

### Post by victorhooi on 2010-05-20
heya,

I've having some weirdness trying to insta

The box is running Lucid 10.04.

I've added the repostitory with:

```
sudo add-apt-repository ppa:jdub/devel
```

There was some issue with the key, when I ran the apt-key command again, I got:

```
root@ip-XX-XX-XX-XX:/etc/apt# apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E9EEF4A1
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys E9EEF4A1
gpg: requesting key E9EEF4A1 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

Anyhow, either way, I ran apt-get update, then tried to install Nginx, and for some reason, each time it insists on installing "nginx_0.7.65-1ubuntu2_i386.deb" from Universe, even though the PPA([https://launchpad.net/~jdub/+archive/devel](https://launchpad.net/~jdub/+archive/devel)) has "0.8.37-0~ppa1".

Is there any reason that Ubuntu would be trying to install the older version? Anything I should check?

Thanks,
Victor

---

### Post by victorhooi on 2010-05-20
heya,

Hmm, turns out I found out the issue, for some reason, on jdub's PPA, he offers Nginx only for Hardy, not for Lucid.

I've managed to install it under Lucid, just by switching around my apt.sources line, but still not sure why he's done it this way?

Cheers,
Victor

---

