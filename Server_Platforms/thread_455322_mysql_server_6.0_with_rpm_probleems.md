---
title: "mysql server 6.0 with rpm probleems"
date: 2007-05-26
forum: Server Platforms
---

### Post by thijs on 2007-05-26
Hi there, i have installed rpm and download the rpm file of mysql server 6.0. here my probleem 

```

root@ubuntu:~# rpm -i MySQL-server-6.0.0-0.glibc23.i386.rpm 
error: Failed dependencies:
        /bin/sh is needed by MySQL-server-6.0.0-0.glibc23.i386
        /sbin/chkconfig is needed by MySQL-server-6.0.0-0.glibc23.i386
        /usr/bin/perl is needed by MySQL-server-6.0.0-0.glibc23.i386
        /usr/sbin/groupadd is needed by MySQL-server-6.0.0-0.glibc23.i386
        /usr/sbin/useradd is needed by MySQL-server-6.0.0-0.glibc23.i386
        coreutils is needed by MySQL-server-6.0.0-0.glibc23.i386
        grep is needed by MySQL-server-6.0.0-0.glibc23.i386
        libc.so.6 is needed by MySQL-server-6.0.0-0.glibc23.i386
        libc.so.6(GLIBC_2.0) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libc.so.6(GLIBC_2.1) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libc.so.6(GLIBC_2.1.2) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libc.so.6(GLIBC_2.1.3) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libc.so.6(GLIBC_2.2) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libc.so.6(GLIBC_2.2.4) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libc.so.6(GLIBC_2.3) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libcrypt.so.1 is needed by MySQL-server-6.0.0-0.glibc23.i386
        libcrypt.so.1(GLIBC_2.0) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libdl.so.2 is needed by MySQL-server-6.0.0-0.glibc23.i386
        libdl.so.2(GLIBC_2.0) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libdl.so.2(GLIBC_2.1) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libm.so.6 is needed by MySQL-server-6.0.0-0.glibc23.i386
        libm.so.6(GLIBC_2.0) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libnsl.so.1 is needed by MySQL-server-6.0.0-0.glibc23.i386
        libpthread.so.0 is needed by MySQL-server-6.0.0-0.glibc23.i386
        libpthread.so.0(GLIBC_2.0) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libpthread.so.0(GLIBC_2.1) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libpthread.so.0(GLIBC_2.2) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libpthread.so.0(GLIBC_2.3.2) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libstdc++.so.5 is needed by MySQL-server-6.0.0-0.glibc23.i386
        libstdc++.so.5(CXXABI_1.2) is needed by MySQL-server-6.0.0-0.glibc23.i386
        libstdc++.so.5(GLIBCPP_3.2) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(DBI) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(Data::Dumper) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(File::Basename) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(File::Copy) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(File::Path) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(File::Temp) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(Getopt::Long) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(POSIX) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(Sys::Hostname) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(strict) is needed by MySQL-server-6.0.0-0.glibc23.i386
        perl(vars) is needed by MySQL-server-6.0.0-0.glibc23.i386
        procps is needed by MySQL-server-6.0.0-0.glibc23.i386

```

how do install well ?

---

### Post by kalisto on 2007-05-31
you cannot expect ubuntu to handle rpm's. 

I would recommend installing mysql5.0 through apt OR build from source.

---

### Post by scawa on 2007-12-30
The problem with MySQL 5.0 is it doesn't support Tablespaces like 5.1 and 6.0 do.

I'm wondering why there is not an APT install for MySQL 6.0????

---

### Post by xdice on 2007-12-30
> **scawa said:**
> The problem with MySQL 5.0 is it doesn't support Tablespaces like 5.1 and 6.0 do.

I'm wondering why there is not an APT install for MySQL 6.0????

My guess is that it's not there because MySQL 6.0 is just into an Alpha release at this time.  I would expect it to not be stable enough to include in the supported repositories for a while. 5.1 is on a release candidate, and I don't see it in my package list in Synaptic, and I would expect to see 5.1 before 6.0.

All of that being said, you can build 5.1 (or 6.0) from source if you do need it. 

As a possible alternative, have you considered postgresql 8.1?  It's available in Synaptic, and seems to have the tablespace support you're looking for.. (just throwing it in as an option.).

---

### Post by thijs on 2007-12-31
> **xdice said:**
> My guess is that it's not there because MySQL 6.0 is just into an Alpha release at this time.  I would expect it to not be stable enough to include in the supported repositories for a while. 5.1 is on a release candidate, and I don't see it in my package list in Synaptic, and I would expect to see 5.1 before 6.0.

All of that being said, you can build 5.1 (or 6.0) from source if you do need it. 

As a possible alternative, have you considered postgresql 8.1?  It's available in Synaptic, and seems to have the tablespace support you're looking for.. (just throwing it in as an option.).

Tnx for help i build it from source with gcc.

---

### Post by The Cog on 2007-12-31
You can create .debs from .rpms using alien. That may possibly help.

---

