---
title: "non-parallel &quot;make&quot;"
date: 2011-10-21
forum: Server Platforms
---

### Post by kuala on 2011-10-21
G'day! Long time reader, 1st time querier!

Current Setup
-----------------
Intel Core 2 Quad Q9450 (4 x 2.66GHz - 1333FSB - 12MB Cache)
Asus P5KPL-CM
RAID 1 Set as root (2 WD 500GB Caviar Blue SATA HDD)

Installed Ubuntu 11.04 Server
Upgraded to 11.10 by running the following commands:
"sudo apt-get install update"
"sudo apt-get install update-manager-core"
"sudo do-release upgrade"
------------------------------------------------

I'm trying to install the most recent version of bind9, since SAMBA4 versions 9.8.0 and later include "a set of patches from the Samba Team to make dynamic DNS updates much more robust and easier to configure"(Sama4 wiki).

I'm getting stuck at the bind9 installation, tho.

I unpackage the bind-9.9.0a3 archive, cd into the directory, and run "./configure".

Then when I try to run "make" I get the following error:

make: *** No targets specified and no makefile found.  Stop.

The bind9 faq instructs that "Using a parallel or distributed 'make' to build BIND 9 is not supported, and doesn't work. If you are using one of these, use normal make or gmake instead."

Tried running:
$ make -j 1

but I get the same error.

I'm looking for help to run make in non-parallel mode, and/or for anyone who has experience installing bind9 v9.8.0 or later from a tar package. Thanks so much. Good to be on the forum at last.

-kuala

---

### Post by vasile002 on 2011-10-22
I believe you get that because you are trying a beta version. Try the latest stable one:
[http://www.isc.org/software/bind/981/download/bind-981targz](http://www.isc.org/software/bind/981/download/bind-981targz)

---

### Post by kuala on 2011-10-30
Thanks for the reply, vasile002. Unfortunately, I'm having the same issue with bind version 9.8.1. I've even tried installing it on a natty minimal server install. Also, tried purging make, and re-installing GNU make from source. Still same issue.

Bind9 addresses this in the FAQ as follows:

> 1. Compilation and Installation Questions

Q: I'm trying to compile BIND 9, and "make" is failing due to files not
   being found. Why?

A: Using a parallel or distributed "make" to build BIND 9 is not
   supported, and doesn't work. If you are using one of these, use normal
   make or gmake instead.

I do not understand. Any help would be greatly appreciated.

-kuala

---

### Post by kuala on 2011-10-30
SOLVED!!! YAY!!!

I used commands from the following website:

[https://www.os3.nl/2011-2012/students/joris_soeurt/cia_lab_wk2](https://www.os3.nl/2011-2012/students/joris_soeurt/cia_lab_wk2)> 
**Compiling BIND**

     First, unpack the tarball.  
 tar -zxvf bind-9.8.1.tar.gz 
   Then, install tools needed to compile.  
 sudo apt-get install gcc libssl-dev
   Compile the code  
 cd bind-9.8.1
sudo ./configure --sysconfdir=/etc --localstatedir=/var/state 
make


Thanks for all the laughter!

-kuala

---

