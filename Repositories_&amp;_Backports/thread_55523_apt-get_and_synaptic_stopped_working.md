---
title: "apt-get and synaptic stopped working"
date: 2005-08-09
forum: Repositories &amp; Backports
---

### Post by mato on 2005-08-09
Hi all,

When I try to install anything with either synaptic or apt-get it doesn't work. Here is output of command line I get after trying to install gambas

mato@ubuntu:~$ sudo apt-get install gambas
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gambas-doc gambas-gb-compress gambas-gb-db gambas-gb-db-mysql
  gambas-gb-db-postgresql gambas-gb-db-sqlite gambas-gb-debug gambas-gb-eval
  gambas-gb-net gambas-gb-net-curl gambas-gb-qt gambas-gb-qt-editor
  gambas-gb-qt-ext gambas-gb-sdl gambas-gb-vb gambas-gb-xml gambas-runtime
  libsdl-mixer1.2
The following NEW packages will be installed:
  gambas gambas-doc gambas-gb-compress gambas-gb-db gambas-gb-db-mysql
  gambas-gb-db-postgresql gambas-gb-db-sqlite gambas-gb-debug gambas-gb-eval
  gambas-gb-net gambas-gb-net-curl gambas-gb-qt gambas-gb-qt-editor
  gambas-gb-qt-ext gambas-gb-sdl gambas-gb-vb gambas-gb-xml gambas-runtime
  libsdl-mixer1.2
0 upgraded, 19 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/4654kB of archives.
After unpacking 23.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
dpkg: failed to open statoverride file: Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


Any idea about what is going on?

Mato

---

### Post by heimo on 2005-08-09
Not quite sure. I'd run:

 ```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get upgrade

``` 

Any help?

---

### Post by mato on 2005-08-09
I Tried the sequence of commands

> 
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get upgrade


The first three executed without errors and the fourth one gave me the same error:

Preconfiguring packages ...
dpkg: failed to open statoverride file: Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by mato on 2005-08-09
I Tried the sequence of commands

> 
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get upgrade


The first three executed without errors and the fourth one gave me the same error:

Preconfiguring packages ...
dpkg: failed to open statoverride file: Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by blind0wl on 2005-08-09
Can you post your df information?
```
df -h
```
and then Id try doing a ```
sudo apt-get clean
``` to free up some more space...sounds like a space issue possibly...

---

### Post by mato on 2005-08-09
Here is the output of df -h:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             8.7G  2.8G  5.5G  34% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/hda7              23G  6.8G   16G  31% /home
/dev/hda1              24G   19G  4.9G  80% /home/win
/dev                  8.7G  2.8G  5.5G  34% /.dev
none                  5.0M  2.8M  2.3M  55% /dev
//192.168.0.95/public_samba
                       35G   29G  6.7G  82% /home/Y

```


command

```
sudo apt-get clean
```

didn't help

---

### Post by heimo on 2005-08-10
Let's see if you have this file:
```
ls -l  /usr/sbin/dpkg-statoverride
```

---

### Post by mato on 2005-08-10
The file /usr/sbin/dpkg-statoverride is there.

---

### Post by heimo on 2005-08-10
I can't give specific instructions at the moment, but if you can find out how to turn on debug information, verbose mode or anything that could give more information, that'd be very helpful. I'd probably try to install dpkg package ... that's a bit like chicken-egg problem you have there, because I suspect dpkg is somehow broken and to install dpkg using package management...

I would also check /var/log/messages and search for any other errors, hopefully it's not failing hard disk. Have you had unexpected power loss, hangup, freeze lately?

---

### Post by mato on 2005-08-10
The problem seems to be fixed now. I assume that some of  the commands described above helped to fix the problem. I didn't reboot computer after executing those commands yesterday and it seemed they didn't have effect. However this morning after I booted the computer the problem was gone.

Thanks everybody for help.

Mato

---

