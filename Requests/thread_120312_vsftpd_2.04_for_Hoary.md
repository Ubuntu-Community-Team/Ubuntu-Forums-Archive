---
title: "vsftpd 2.04 for Hoary"
date: 2006-01-21
forum: Requests
---

### Post by Daicogra on 2006-01-21
Hello,

I like to request vsftpd as a backport for Hoary.
I have Hoary as a server with some modifications. I can't upgrade to Breezy. Next upgrade will be to Ubuntu 6.10 (after dapper). :)

Version at Hoary: 2.0.1
Newest version: 2.0.4
Changelog: [ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.4/Changelog](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.4/Changelog)

New Features:
* Files being uploaded are now locked; downloads wait until the upload is complete.
* Support to DNS resolve pasv_address was added.
* New settings rsa_private_key_file and dsa_private_key_file to allow
separate files for the certificates and private keys.
* Load per-IP config files earlier; allows more settings to be tuned on a
per-IP level.
* ...

Bugfixes:
* Bug with FlashFXP who will truncate files.
* Fix error with IPv4 connections to IPv6 listeners and PORT type data
connections when connect_from_port_20 is set.
* ...


Thanks

---

