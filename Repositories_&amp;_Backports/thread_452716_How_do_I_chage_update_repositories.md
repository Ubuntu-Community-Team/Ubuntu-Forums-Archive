---
title: "How do I chage update repositories?"
date: 2007-05-23
forum: Repositories &amp; Backports
---

### Post by slacker9876 on 2007-05-23
I am currently unable to access the default repos from /etc/apt/sources.list, I would like to try a local mirror but I am unsure of the syntax. I am hoping someone could help me out with sample. I would like to use [http://mirror.mcs.anl.gov](http://mirror.mcs.anl.gov) but I do not know how to format an entry in sources.list, or even if mirrors host the updates. Any help would be appreciated.

---

### Post by ahaslam on 2007-05-23
[source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/") ;)

---

### Post by eentonig on 2007-05-23
Why would you go for some unknwon repo.

Ubuntu has mirrors all around the world.

Using the GUI, 

System\Administration\Synaptic...
Settings\Software Sources

And there you have the option "Download from"
Choose your country as you like.

---

### Post by slacker9876 on 2007-05-23
Thanks for the tips, I really feel stupid after seeing the "Other" option in there. Here is the problem though, they are all failing on download.

[http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:](http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:) Error reading from server - read (104 Connection reset by peer)
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Error reading from server - read (104 Connection reset by peer)
[http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/main/source/Sources.gz:](http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/main/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Error reading from server - read (104 Connection reset by peer)
[http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/universe/source/Sources.gz:](http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/universe/source/Sources.gz:) Error reading from server - read (104 Connection reset by peer)
[http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://ubuntu.cs.utah.edu/ubuntu/dists/feisty/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://ubuntu.cs.utah.edu/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://ubuntu.cs.utah.edu/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)


I cannot seem to get the index or files from any of them.

---

