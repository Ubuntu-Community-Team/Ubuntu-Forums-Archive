---
title: "GPG error: Public key 40976EAF437D05B5"
date: 2011-06-23
forum: Server Platforms
---

### Post by sentinelace on 2011-06-23
GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

Tried this with no luck:
 
sudo bash
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

---

### Post by sentinelace on 2011-06-23
Fixed it with:
 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D97A3AE911F63C51
```

---

### Post by evoweiss on 2011-09-20
Hi,

I tried this and just about every other posted solution (deleting and recreating directories, switching to main server, etc.) None of it is working. I am running lucid lynx. Any ideas?

Alex

---

### Post by Elfy on 2011-09-20
Run 

```
sudo apt-get update
```

Post output.

---

### Post by prithamreddy on 2011-11-29
> **sentinelace said:**
> Fixed it with:
 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D97A3AE911F63C51
```
Thanks a lot, it worked for me..

---

