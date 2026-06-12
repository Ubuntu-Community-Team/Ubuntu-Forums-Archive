---
title: "Share Ubuntu repositories via nfs -&gt; How?"
date: 2005-07-03
forum: Repositories &amp; Backports
---

### Post by wantilles on 2005-07-03
I have 3 PCs at home connected via ethernet TCP-IP LAN.

PC-3 is a x86 machine running 24/7 as a file server with nfs & samba exports (it runs Gentoo Linux & the /usr/portage directory is placed in a separate partition and shared via nfs).

The other two are running Ubuntu (and one of them is running Gentoo also).

I would like to do the same for the package lists & the packages themselves for Ubuntu in order to be able to update both of the other two PCs by downloading only once lists & packages.

Questions:

1. Where does Synaptic / apt-get store the package list files?

2. Where does Synaptic / apt-get store the packages themselves;

3. Is there a configuration file present to instruct them where to find package lists & packages?

4. The other two PCs are of different architectures (PC-1 -> amd64, PC-2 -> x86). Since Ubuntu is a binary distro (and not a source one like Gentoo), I assume that I will need separate package lists & packages for each architecture?

---

### Post by mtron on 2005-07-03
hi wantilles

ad1: the repositories sources.list file is stored in /etc/apt
ad2: downloaded packages are stored in /var/cache/apt/archives
ad3: create a new sources.list file with your local or lan repository
ad4: yes, you will need 2 versions of each package

to create your own repository see the debian repository howto
[http://www.debian.org/doc/manuals/repository-howto/repository-howto.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html)

cheers

---

