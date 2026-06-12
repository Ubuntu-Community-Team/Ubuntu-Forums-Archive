---
title: "Firebird? WTF!?!?!!?"
date: 2009-08-27
forum: Server Platforms
---

### Post by zkriesse on 2009-08-27
Trying to get firebird running on Ubuntu Jaunty Desktop. But I can't....HELP!

---

### Post by zkriesse on 2009-08-27
udo apt-get install firebird2-super-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firebird2-super-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  firebird2.0-server-common
E: Package firebird2-super-server has no installation candidate
root@zach-laptop:~# sudo apt-get install firebird2.0-server-common
Reading package lists... Done

that's what i get....but i can't run it cause i don't know where it is!

---

### Post by lovinglinux on 2009-08-27
```
sudo apt-get install firebird2.0-server-common firebird2.0-common
```

---

### Post by zkriesse on 2009-08-27
Ok....did that...now what? It ends in terminal without doing anything but installing the packages....should it start what? Cause it doesn't.

---

### Post by wojox on 2009-08-27
Here's the pdf:

[www.firebirdsql.org/pdfmanual/Firebird-2-QuickStart.pdf](www.firebirdsql.org/pdfmanual/Firebird-2-QuickStart.pdf)

---

### Post by zkriesse on 2009-08-27
Ok...I installed Firebird(I think) but I don't know how to start, much less run it.

---

### Post by lovinglinux on 2009-08-27
> **Zachk18 said:**
> Ok...I installed Firebird(I think) but I don't know how to start, much less run it.

I never used it, so I can't help you, but the link provided by wojox should get you started.

---

### Post by zkriesse on 2009-08-27
It kinda did...thanks for the help guys.

---

### Post by zkriesse on 2009-08-29
> **lovinglinux said:**
> ```
sudo apt-get install firebird2.0-server-common firebird2.0-common
```

Tried that...here's what I get.  sudo apt-get install firebird2.0-server-common firebird2.0-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.8-0 libwxbase2.8-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firebird2.1-classic firebird2.1-common firebird2.1-dev flamerobin
  libfbclient2 libfbembed2.1
The following NEW packages will be installed:
  firebird2.0-common firebird2.0-server-common
0 upgraded, 2 newly installed, 6 to remove and 5 not upgraded.
Need to get 0B/1295kB of archives.
After this operation, 12.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109029 files and directories currently installed.)
Removing firebird2.1-classic ...
Removing libfbembed2.1 ...
Removing flamerobin ...
Removing firebird2.1-dev ...
Removing libfbclient2 ...
Removing firebird2.1-common ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Selecting previously deselected package firebird2.0-common.
(Reading database ... 108914 files and directories currently installed.)
Unpacking firebird2.0-common (from .../firebird2.0-common_2.0.4.13130-1.ds1-5ubuntu1_i386.deb) ...
Selecting previously deselected package firebird2.0-server-common.
Unpacking firebird2.0-server-common (from .../firebird2.0-server-common_2.0.4.13130-1.ds1-5ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firebird2.0-server-common_2.0.4.13130-1.ds1-5ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/gdef.1.gz', which is also in package firebird2.1-server-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/firebird2.0-server-common_2.0.4.13130-1.ds1-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Oh...and I get this in FlameRobin

*** IBPP::SQLException ***
Context: Service::Connect
Message: isc_service_attach failed

SQL Message : -902
Unsuccessful execution caused by a system error that precludes
successful execution of subsequent statements

Engine Code    : 335544721
Engine Message :
Unable to complete network request to host "localhost".
Failed to establish a connection.
Connection refused

---

