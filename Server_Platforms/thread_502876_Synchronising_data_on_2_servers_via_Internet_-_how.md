---
title: "Synchronising data on 2 servers via Internet - how?"
date: 2007-07-17
forum: Server Platforms
---

### Post by feenster on 2007-07-17
Hi all,
I've got two data servers (seperated by quite a few miles ;)) that i'd like to synchronise the data on, via the Internet. I've tried using Rsync, which is great, but can lead to a lot more data transfer than is necessary. 

For example, if both Servers have a 200GB folder called "Data", and it gets renamed to "data1" on the main server, the whole 200GB of data will be re-transferred. I know this is obviously correct, as Rsync thinks the data is new. However, I was wondering if there were any more intelligent bits of software out there that could determine when data is simply moved around the filestructure (or renamed). Any recommendations?

Matt

---

### Post by koenn on 2007-07-17
I'm not 100% sure about this, but I think you need to give rsync a closer look.

- I think it would be possible to tell rsync to compare the_ contents _of /srv1/data1/ with the _contents_ of /srv2/Data, so the change of dir name on srv1 wouldn't cause a complete transfer - if you correct you rsync statement to reflect the name change. 

- rsync has a couple of options that might help, such as
```
     
      --size-only             skip files that match in size
 -T, --temp-dir=DIR          create temporary files in directory DIR
 -y, --fuzzy                 find similar file for basis if no dest file
     --compare-dest=DIR      also compare received files relative to DIR
     --checksum                    skip files based on checksum

```

a combination of the above might do the trick, (I haven't tried)

---

### Post by dbott67 on 2007-07-17
You may also want to look at unison:
[http://www.linuxjournal.com/article/7712](http://www.linuxjournal.com/article/7712)

```
dbott@feisty:~$ sudo apt-cache show unison
Package: unison
Priority: optional
Section: universe/net
Installed-Size: 1128
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Sylvain Le Gall <gildor@debian.org>
Architecture: i386
Version: 2.13.16-6ubuntu1
Depends: libc6 (>= 2.5-0ubuntu1)
Recommends: ssh-client | openssh-client
Conflicts: unison (<< 2.9.1-3)
Filename: pool/universe/u/unison/unison_2.13.16-6ubuntu1_i386.deb
Size: 480874
MD5sum: 994dbfa4796f832c2adaae2e189897f2
SHA1: cf93eabbf0dda3956102bf4e1c6ed015eed2a775
SHA256: da308a0573610b7d74a5030b5af35ee13cf9aad554267cfcf3a1d3f338be3dec
Description: A file-synchronization tool for Unix and Windows
 Unison is a file-synchronization tool for Unix and Windows, written
 in OCaml. It allows two replicas of a collection of files and
 directories to be stored on different hosts (or different disks
 on the same host), modified separately, and then brought up to
 date by propagating the changes in each replica to the other.
 .
 Unison offers several advantages over various synchronization methods
 such as CVS, Coda, rsync, Intellisync, etc. Unison can run on and
 synchronize between Windows and many UNIX platforms. Unison requires
 no root privileges, system access or kernel changes to function. Unison
 can synchronize changes to files and directories in both directions,
 on the same machine, or across a network using ssh or a direct
 socket connection.
 .
 Transfers are optimised using a version of the rsync protocol,
 making it ideal for slower links. Unison has a clear and precise
 specification, and is resilient to failure due to its careful
 handling of the replicas and its private structures.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

-Dave

---

### Post by feenster on 2007-07-17
Thanks for the replies. I'll have a look at the Rsync fuzzy command, but it looks like Unison may do the job :)

Matt

---

