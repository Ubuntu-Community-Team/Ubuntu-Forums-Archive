---
title: "Installing Synaptic on Fresh Install does weird Scroll Keeper registration"
date: 2013-02-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-02-05
Just did a fresh install of the daily i386 and got these new scripts up and about:

```

ventrical@ventrical-P4M266A-8237:~$ sudo apt-get install synaptic
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docbook-xml libept1.4.12 librarian0 rarian-compat sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide perlsgml w3-recs opensp
  libxml2-utils dwww menu deborphan tasksel
The following NEW packages will be installed:
  docbook-xml libept1.4.12 librarian0 rarian-compat sgml-data synaptic
0 upgraded, 6 newly installed, 0 to remove and 12 not upgraded.
Need to get 3,338 kB of archives.
After this operation, 12.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ raring/main sgml-data all 2.0.8 [276 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ raring/main docbook-xml all 4.5-7.1 [336 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ raring/main libept1.4.12 i386 1.0.9 [136 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ raring/main librarian0 i386 0.8.1-5build1 [58.4 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ raring/main rarian-compat i386 0.8.1-5build1 [100 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ raring/universe synaptic i386 0.80~exp1 [2,430 kB]
Fetched 3,338 kB in 14s (226 kB/s)                                             
Selecting previously unselected package sgml-data.
(Reading database ... 156497 files and directories currently installed.)
Unpacking sgml-data (from .../sgml-data_2.0.8_all.deb) ...
Selecting previously unselected package docbook-xml.
Unpacking docbook-xml (from .../docbook-xml_4.5-7.1_all.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.9_i386.deb) ...
Selecting previously unselected package librarian0.
Unpacking librarian0 (from .../librarian0_0.8.1-5build1_i386.deb) ...
Selecting previously unselected package rarian-compat.
Unpacking rarian-compat (from .../rarian-compat_0.8.1-5build1_i386.deb) ...
Selecting previously unselected package synaptic.
Unpacking synaptic (from .../synaptic_0.80~exp1_i386.deb) ...
Processing triggers for sgml-base ...
Processing triggers for doc-base ...
Scrollkeeper was installed, forcing re-registration of all documents.
Unregistering 32 doc-base files, re-registering 32 doc-base files...
Registering documents with scrollkeeper...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up sgml-data (2.0.8) ...
Setting up libept1.4.12 (1.0.9) ...
Setting up librarian0 (0.8.1-5build1) ...
Setting up synaptic (0.80~exp1) ...
Processing triggers for sgml-base ...
Setting up docbook-xml (4.5-7.1) ...
Processing triggers for sgml-base ...
Setting up rarian-compat (0.8.1-5build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ventrical@ventrical-P4M266A-8237:~$ 

```

Haven't seen this 'scrollkeeper' before.

---

### Post by Harry33 on 2013-02-06
Ventrical, you are installing the recommended and suggested packages too.
Then, there is the recommended package rarian-compat (depends on librarian0).
Rarian is a documentation meta-data library, a replacement for Scrollkeeper.

---

### Post by ventrical on 2013-02-06
Ok.. thanks Harry33.  I install synaptic as I always do.  I just do not recall seeing the scrollkeeper lines of script in my previous installs of synaptic.

---

### Post by grahammechanical on 2013-02-06
It is those drives that you are using. They are so old the data is stored on parchment or papyrus. :)

---

### Post by ventrical on 2013-02-06
> **grahammechanical said:**
> It is those drives that you are using. They are so old the data is stored on parchment or papyrus. :)


Bwaaaahahahahaha!! ROTFLMAO!

---

