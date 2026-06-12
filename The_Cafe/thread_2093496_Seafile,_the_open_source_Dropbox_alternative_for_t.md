---
title: "Seafile, the open source Dropbox alternative for teams, released version 1.3"
date: 2012-12-10
forum: The Cafe
---

### Post by xjqkilling on 2012-12-10
Seafile ([http://seafile.com]("http://seafile.com")) is an open source file synchronization tool.
It comes with Dropbox-like file syncing, but is designed to be better suited to teamwork. 
You can build a file sharing and syncing service for your team on your servers.

It comes with many interesting features:
1) Users can create and join groups, then share files to the group. This makes it convenient for teamwork.
2) Files are organized into libraries, each be selectively synced to your computer. Libraries can be synced with any local folders.
3) Online file collaboration features, such as PDF and Office file preview and file commenting.

The project is hosted on Github ([https://github.com/haiwen/seafile]("https://github.com/haiwen/seafile")).

Compared to earlier open-source projects, such as SparkleShare and ownCloud, Seafile has several advantages:
1) Production quality file syncing algorithm.
2) Many team collaboration features.

The client-side software now runs on Windows, Mac OS X and Linux. And server-side runs on Linux.

The 1.3 release comes with many improvements:
* Encrypted data transfer
* Server-side garbage collection
* UI improvement for online markdown/text file editing

---

### Post by sandyd on 2012-12-10
**Moved to Community Cafe**

---

### Post by freeplant on 2013-01-25
Seafile version 1.4 is released,  introduced two major improvements:

* REST API to support mobile clients 
* Allow setting the length of history to keep on the server. Now you may choose not to keep any history or only keep a few months of history.

On the client side, it fixes bugs found in 1.3 release. The most important update is that Seafile now has an Android client!
Seafile can also run on ARM-based Raspberry pi, as long as you compile the server from source code :)

---

### Post by areteichi on 2013-02-01
Sorry to be asking such a basic question, but could anyone tell me if it is possible to install Seafile on a shared hosting? I would like to try it out if it is as easy to install as ownCloud (i.e. upload via FTP and done).

---

### Post by freeplant on 2013-02-17
> **areteichi said:**
> Sorry to be asking such a basic question, but could anyone tell me if it is possible to install Seafile on a shared hosting? I would like to try it out if it is as easy to install as ownCloud (i.e. upload via FTP and done).

Seafile is best to be installed on a VPS.

---

### Post by xjqkilling on 2013-03-12
Seafile 1.5 is available now. Major feature update includes:
* supports LDAP and Active Directory for account management
* CLI client for Linux

More detail can be view on: [http://seafile.com/en/news/](http://seafile.com/en/news/)

---

