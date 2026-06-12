---
title: "Linux noob General server setup"
date: 2011-11-02
forum: Server Platforms
---

### Post by EPops on 2011-11-02
I am new to Linux and Ubuntu, and want to set up a home server.  I am quite familiar with Windows and advanced tweaking of it, so hopefully I can pick this material up quickly.

I read about setting different partitions, but I cannot find a definitive answer to some questions.

First off, could someone explain which partitions I will need if my main goals are:

1.) File share server for Windows-only users on the network

2.) Run software like bittorent client, but nothing very large.  Nothing like video editing or CAD, just maybe some basic applications.

Also, which partition sizes should I use if my hardware is thus:
(1) 80GB HDD
2GB RAM
Core 2 Duo processor

Lastly, which file system is best for having bittorent running?  I read XFS is good for large files but should I use ext4 as default?

Thanks if you can help with any of these questions.

---

### Post by HermanAB on 2011-11-02
Howdy,

The best tips I can give you if you haven't used a Linux server before, is to simply use ordinary Desktop Ubuntu for your server.  Do a default install and take it from there.  As a first timer, avoid the Ubuntu server version.

If you want to be more pro-active, install ordinary Ubuntu, install Virtualbox on it and make a VM using ordinary Ubuntu as a virtual server.

The advantage of using a VM is that it is enormously much easier to manage, make backups and move the server to new hardware when the old hardware fails, or when you need more powerful hardware, with minimal downtime.

---

### Post by snowpine on 2011-11-02
Welcome to the forums, we could assist you better if you tell us details like: how big is the hard drive, will the computer be Ubuntu-only or dual boot with Windows, etc.

In general I recommend the default partitioning scheme for the majority of users. This would be an ext4 / (root) partition and a swap partition calculated based on your RAM. If you are an advanced user with specific needs then you might choose a more complex partitioning scheme, but the default should work great 99% of the time.

It is completely irrelevant what filesystem you choose as regards torrent performance, because the speed of your hard drive read/write is thousands of times faster than your internet connection. :)

---

### Post by EPops on 2011-11-02
> **HermanAB said:**
> Howdy,

The best tips I can give you if you haven't used a Linux server before, is to simply use ordinary Desktop Ubuntu for your server.  Do a default install and take it from there.  As a first timer, avoid the Ubuntu server version.

If you want to be more pro-active, install ordinary Ubuntu, install Virtualbox on it and make a VM using ordinary Ubuntu as a virtual server.

The advantage of using a VM is that it is enormously much easier to manage, make backups and move the server to new hardware when the old hardware fails, or when you need more powerful hardware, with minimal downtime.

Thanks for that suggestion.  I am going to take this route until I learn more about Ubuntu and Linux, it seems much less intimidating than a pure command line.

---

