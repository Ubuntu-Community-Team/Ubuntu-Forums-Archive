---
title: "manually clean up defective dependencies."
date: 2013-05-19
forum: Server Platforms
---

### Post by mettavihari on 2013-05-19
I have installed the Ubuntu server 12.04 64bit and everything went OK 
till I gave a rather foolish command

I have on an other server installed sputnik and with it came some requirements for some dependencies
I have the following files in that server as dependencies
lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb
lib32stdc++6_4.6.3-1ubuntu5_amd64.deb
lib32z1_1%3a1.2.3.4.dfsg-3ubuntu4_amd64.deb
libc6_2.15-0ubuntu10_i386.deb
libc6-dbg_2.15-0ubuntu10_amd64.deb
libc6-i386_2.15-0ubuntu10.3_amd64.deb
To install the dependencies in this machine:
I gave the command dpkg -i * within the folder where these files where situated.
This caused several errors

dpkg:error processing "pkg" (--install):
dependency problems - leaving unconfigured
Errors where encountered while processing:
bad 
lib32gcc1
lib32stdc++6
lib32z1
libc6-dbg
libc6-i386

If I know where the files are then I presume I could go in and delete the info about these unconfigured files.
I had a look in 
/var/lib/dpkg/info/
and the files with the following extentions are there
.list    (modified with todays date)
.md5sum
.postinst
.postrm
.shlibs
.symbols

apt-get -f install    does not fix the problem
dpkg --configure -a    does also not fix the problem.

My question is:
Where are these unconfigured files laying on the system and
How do I remove these un-configured files from the system.
My apt-get system is not working

I shall be very greatful for your help in this

regards
Mettavihari

---

### Post by lykwydchykyn on 2013-05-20
Can you just do "apt-get purge" or "dpkg -r" on the packages that had problems?

---

### Post by tgalati4 on 2013-05-20
It looks like you have a mixture of 32-bit and 64-bit libaries.  Which is OK if that is your intent to run 32-bit code in a 64-bit environment.  You might be missing the "glue" that allows 32-bit code to run in a 64-bit environment:

ia32-libs - ia32 shared libraries - transitional package
ia32-libs-multiarch - Multi-arch versions of former ia32-libraries

Anything that says i386 or 32 is probably 32-bit code.  Anything AMD64 or i686 is probably 64-bit code.  Sputik is a wiki written in LUA and it looks like 32-bit:

tgalati4@Mint14-Extensa ~ $ apt-cache search sputnik
sputnik - Extensible wiki
tgalati4@Mint14-Extensa ~ $ apt-cache depends sputnik
sputnik
  Depends: <lua5.1-coxpcall>
    lua-coxpcall
  Depends: <lua5.1-wsapi>
    lua-wsapi
  Depends: <lua5.1-markdown>
    lua-markdown
  Depends: <lua5.1-cosmo>
    lua-cosmo
  Depends: <lua5.1-filesystem>
    lua-filesystem
  Depends: <lua5.1-md5>
    lua-md5
  Depends: <lua5.1-socket>
    lua-socket
  Depends: lua5.1
**    lua5.1:i386**
  Suggests: git
  Suggests: <lua5.1-sql-sqlite3>
    lua-sql-sqlite3
  Suggests: <lua5.1-sql-mysql>
    lua-sql-mysql
  Suggests: <lua5.1-logging>
    lua-logging
  Suggests: <lua5.1-zlib>
  Suggests: xavante
  Recommends: <lua5.1-posix>
    lua-posix
  Recommends: <lua5.1-iconv>
    lua-iconv

Does anyone know if LUA 5.1 runs natively in 64-bit?

---

### Post by mettavihari on 2013-05-21
Thank you for your suggestions.
The 2 suggestions did not work

I guess this is the trouble maker.

as Root# apt-get purge libc6

pages of errors

xz-utils : Depends: libc6 (>= 2.7) but it is not going to be installed
zlib1g : Depends: libc6 (>= 2.4) but it is not going to be installed
E: **Unmet dependencies. Try 'apt-get -f install'** with no packages (or specify a solution).
root@nenasa-live:/home/nenasa/download2/teradek/dependencies#

-------------
dpkg -r libc6

two pages of errors.

mysql-client-core-5.5 depends on libc6 (>= 2.14).
tcpd depends on libc6 (>= 2.4).
kpartx depends on libc6 (>= 2.4).
dpkg: error processing libc6 (--remove):
**dependency problems - not removing**
[B]Errors were encountered while processing:
** libc6**
[/B]root@nenasa-live:/home/nenasa/download2/teradek/dependencies#

--------------
root@nenasa-live:/home/nenasa/download2/teradek/dependencies# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gcc-4.6-base:i386 libc6:i386 libc6-dbg libc6-i386 libgcc1:i386
Suggested packages:
  glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  gcc-4.6-base:i386 libc6-i386 libgcc1:i386
The following packages will be upgraded:
  libc6:i386 libc6-dbg
2 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
7 not fully installed or removed.
Need to get 0 B/10.9 MB of archives.
After this operation, 10.1 MB of additional disk space will be used.
Do you want to continue [Y/n]?
**E: Internal Error, No file name for libc6**
root@nenasa-live:/home/nenasa/download2/teradek/dependencies#

---

### Post by mettavihari on 2013-05-21
Thank you for your comments

Sputnik is a program produces by Teradek.com
[http://www.teradek.com/pages/downloads](http://www.teradek.com/pages/downloads) ... select sputnik
It is asembleing several video streams into a single stream

I did the installation of this version with these dependencies in the other server.
but this time when installing the dependencies the problem came up.

Thank you for your help

---

### Post by schragge on 2013-05-21
> **mettavihari said:**
> **E: Internal Error, No file name for libc6**
To fix this, try
```
dpkg --configure -a
```
BTW, removing libc6 is a **very** bad idea as pretty much everything depends on this package.

---

### Post by tgalati4 on 2013-05-21
The commercial Sputnik package is packaged for Debian6/Squeeze, not Ubuntu 12.04.  So it is possible there are some dependency issues.  I would remove it.  Fix your system so that it is running correctly.  Then do some research on the Sputnik Debian package to determine what its exact dependencies are.

```
dpkg-deb -I sputnik*.deb
```

This will gather some information about the sputnik debian package.

---

### Post by mettavihari on 2013-05-26
Thank you all for the suggestions

The problem was solved in this way.

 $ sudo gedit /var/lib/dpkg/status (you can use vi or nano instead of gedit)

 Locate the corrupt package, and remove the whole block of information  about it and save the file.

Thank you to the community and to google

---

