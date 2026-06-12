---
title: "mysql server dependency error"
date: 2015-06-22
forum: Server Platforms
---

### Post by marcus33 on 2015-06-22
Hi. My name is Marcus.
I have a server with Ubuntu server 15.04 x64. I have a problem when i try to install bind9, but i recive this messsage:

```
sudo apt-get install bind9Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bind9 : Depends: bind9utils (= 1:9.9.5.dfsg-9) but it is not going to be installed
 mysql-server : Depends: mysql-server-5.6 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I've allready try to install mysql-server-5.6 but i get this:

```
If are sure you want to downgrade to 5.6, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.6_5.6.24-0ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.6_5.6.24-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can anyone help me with this please?
It's the only thing that stuck me. The apache, and the other services i've managed to fix them.
Thank you so much!

See ya!

---

### Post by darkod on 2015-06-23
First of all, before going deeper, is this a production machine? If yes, you decided to use 15.04 on it which has very short support life?

For prod servers the usual choice is only LTS releases, in this case the current lts is 14.04.

I don't know if the dependancy issues are related to that or not. In case you want to continue with 15.04, I assume you tried the apt-get -f as the message suggests? Did it manage to fix anything?

---

### Post by marcus33 on 2015-06-27
Already try to apt-get -f, but i gave the same error.
In fact, i want to install also inadyn(for afraid.org) and it gives me the same error.

```
~$ sudo apt-get install inadynReading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.6 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

The server is personal. Iam triying to host my personal page, so i belived that the last version will be the best choice. Do you recomend to install the 14.04 version?
Thank you so much for the answer, and iam sorry for the delayed response, but iam with some trouble in my work.

:)

---

### Post by darkod on 2015-06-28
Even for a home server, you usually want to depend on it especially once you tune it up to your needs. You do not plan to reinstall linux servers every 6 or 12 months. Non-LTS releases have quite short support life from that point of view. Earlier it was 18 months, I haven't searched recently if it changed. LTS releases have 5 years support life, as compared to that.

So yes, using 14.04 is recommended in the majority of cases.

The error you are getting is sometimes a pain to fix... But if you do decide to redo the setup with 14.04 is pointless to waste more time trying to fix it.

PS. As I thought, they have lowered the support life of regular releases to 9 months according to this: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

There is no point tuning up your 15.04 server that will stopped being supported next January.

---

### Post by marcus33 on 2015-07-09
Thank you so much for thw answer, it really help me so much. This weekend I will install ubuntu server 14.04

:)

> **darkod said:**
> Even for a home server, you usually want to depend on it especially once you tune it up to your needs. You do not plan to reinstall linux servers every 6 or 12 months. Non-LTS releases have quite short support life from that point of view. Earlier it was 18 months, I haven't searched recently if it changed. LTS releases have 5 years support life, as compared to that.

So yes, using 14.04 is recommended in the majority of cases.

The error you are getting is sometimes a pain to fix... But if you do decide to redo the setup with 14.04 is pointless to waste more time trying to fix it.

PS. As I thought, they have lowered the support life of regular releases to 9 months according to this: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

There is no point tuning up your 15.04 server that will stopped being supported next January.

---

