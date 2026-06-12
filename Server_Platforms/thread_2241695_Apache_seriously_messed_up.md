---
title: "Apache seriously messed up"
date: 2014-08-27
forum: Server Platforms
---

### Post by jrop on 2014-08-27
Hi guys,

Apache on my server is really messed up.  Right, now, I don't have apache2 installed, and when I try to install it, I get this:

```
$ sudo apt-get install apache2Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libical0 libjs-scriptaculous gamin db4.6-util libcitadel2 libgamin0 wwwconfig-common citadel-client expect tcl8.5
  citadel-common libdb4.6 javascript-common citadel-webcit libjs-prototype libsieve2-1 tinymce
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-worker apache2.2-common
Suggested packages:
  apache2-suexec apache2-suexec-custom ufw
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2.2-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/304kB of archives.
After this operation, 2,286kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 64733 files and directories currently installed.)
Unpacking apache2.2-common (from .../apache2.2-common_2.2.14-5ubuntu8.14_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2.2-common_2.2.14-5ubuntu8.14_i386.deb (--unpack):
 unable to install new version of `./usr/share/doc/apache2.2-common/examples': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.14-5ubuntu8.14_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-mpm-worker_2.2.14-5ubuntu8.14_i386.deb (--unpack):
 unable to install new version of `./usr/lib/debug': No such file or directory
Unpacking apache2 (from .../apache2_2.2.14-5ubuntu8.14_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2_2.2.14-5ubuntu8.14_i386.deb (--unpack):
 unable to install new version of `./usr/share/doc/apache2': No such file or directory
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/apache2.2-common_2.2.14-5ubuntu8.14_i386.deb
 /var/cache/apt/archives/apache2-mpm-worker_2.2.14-5ubuntu8.14_i386.deb
 /var/cache/apt/archives/apache2_2.2.14-5ubuntu8.14_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anybody know what's going on?  I thought I had purged the packages mentioned, but it just won't let me reinstall apache.

---

### Post by jrop on 2014-08-27
Oh, and I'm running Ubuntu 10.04.4 LTS server

---

### Post by cariboo on 2014-08-28
I know 10.04 is supported for another year, but I'd consider updating to 14.04. Have you tried:

```
apt-get -f install
```

---

### Post by jrop on 2014-08-28
Yep, tried that:

```
apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libical0 libjs-scriptaculous gamin db4.6-util libcitadel2 libgamin0 wwwconfig-common citadel-client expect tcl8.5 citadel-common libdb4.6
  javascript-common citadel-webcit libjs-prototype libsieve2-1 tinymce
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Still no dice.  At this point the server really needs to be up and running...I'm thinking of just creating a new droplet with 14.04 like you suggested and moving the DB/files over.

---

### Post by Hugo_Serrano on 2014-08-28
Hi!

You can try
apt-cache clean
apt-get update
apt-get install apache2


Cheers,
Hugo.

---

### Post by jrop on 2014-08-28
I get the following when trying to clean
```
$apt-cache cleanE: Invalid operation clean

```

---

### Post by jrop on 2014-08-28
Whelp...I just created a new droplet, running 14.04 and transferred everything over to that...not sure what in the world went wrong with the other, but whatever I guess.

---

### Post by Hugo_Serrano on 2014-08-29
Ups... sorry, it's:
apt-get clean

---

