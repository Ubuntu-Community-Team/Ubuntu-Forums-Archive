---
title: "Joomla &amp; pure_ftpd"
date: 2008-11-29
forum: Server Platforms
---

### Post by joakim.hove on 2008-11-29
Hello,

I might be in a bit over my neck here - hopefully I can manage to sort this out with some help. What I am trying to do is to install the CMS Joomla on a Ubuntu 8.04 server. During the installation process Joomla requires that I have a valid ftp account on the server where Joomla is running. So I set about and installed the pure-ftpd server - that was not so easy.

My questions:

1. What exactly is jooml using this ftp account for - seemed a bit unnecessary to me?

2. I have (at least) two problems with the pure-ftpd installation:

2.1 I want to log in as user www-data; but that seems to be impossible. I have set the MINUid parameter to 33, manually set a password for the www-data user, and confirmed with ssh from an external box that I can log in as user www-data. I have configured pure-fptd to use unix style authentification. However the www-data user never succeeds in logging in with ftp - ordinary users go straight in.

2.2 [Disclaimer: I am really quite unknowledgeable about networking]. The server has an IP number a.b.c.d which I use to log on from a remote site. However on the inside (behind firewall/router ??) the server is known with IP 192.168.c.d - and the ftp server only seems to answer request on that IP (i.e. I can only ftp in from other computers on the inside of the firewall/router). I have tried to the -S [Bind] option to pure-ftpd to bind to IP a.b.c.d - but it does not work.


Thank you for any help - Joakim

---

### Post by Nepherte on 2008-11-29
1. For preserving the correct owner of the directories and files.

---

### Post by joakim.hove on 2008-11-29
> **Nepherte said:**
> 1. For preserving the correct owner of the directories and files.

Thank you for answering - I should have phrased my question clearer: Does Jomla use the ftp login during normal operation, or is this _only_ something needed during installation? 

Joakim

---

