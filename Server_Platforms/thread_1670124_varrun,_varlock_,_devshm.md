---
title: "/var/run, /var/lock , /dev/shm"
date: 2011-01-18
forum: Server Platforms
---

### Post by cormu7 on 2011-01-18
Hello,

I just recently started using ubuntu. I recently installed ubuntu and did the partitioning. However, when i type in the "df" command, i get this:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19222656    386168  17859952   3% /
none                  12358348       296  12358052   1% /dev
none                  12363188       332  12362856   1% /dev/shm
none                  12363188       412  12362776   1% /var/run
none                  12363188         0  12363188   0% /var/lock
none                  12363188         0  12363188   0% /lib/init/rw
/dev/mapper/vg03-usr  96118540   2907748  88328156   4% /usr
/dev/sda7              4804736    165176   4395492   4% /tmp
/dev/sda8              9611492    995480   8127772  11% /var
/dev/mapper/vg01-data
                     2685654296    206864 2549024008   1% /data
/dev/mapper/vg02-home
                      19219156    274940  17967936   2% /home

Under the Filesystem header, i'm not quite sure what "none" indicates, and what exactly do the /dev/shm, /dev/, /var/run/, /var/lock, /lib/init/rw, partitions indicate? Is there something that i did wrong with the partitioning during installation?

your help would greatly be appreciated.

thanks,

cor

---

### Post by koenn on 2011-01-18
those "none" directories  are parts of the filesystem that are not present on a physical medium (s.a. a hard disk). They point to RAM, or to a fusion of a ram drive and a physical partition, so that files that are stored there don't occupy disk space and are wiped when the system reboots.
 
Unix-like systems like to represent everything as a file, and traditionally some of those locations (like /var/lock, ...)  did actually point to locations on a disk, so the directory three shows them as directories (and therefore your mount table has them too). Mapping this to RAM (or even swap) is convenient for small temp files that don't need to survive a reboot. 

So you did not do anything wrong, it's how the system is set up

I don't know the meaning or purpose of all of them, but mostly they'll contain volatile, temporary, or system-generated data, eg

/dev  : (file-like representations of) I/O devices such as disks and serial ports; populated during boot by udev (or whatever the current hardware detection thingy is)

/var/lock : location for lock files - files that signal that a given shared resource is in use by an application

/var/run  : place for files with the process ID of running applications

shm : shared memory, memory used to pass information  from application to another

/lib/init/rw : read write location for init, to be used during system start, when / is  (temporarily) read-only

more here : [http://www.pathname.com/fhs/2.2/](http://www.pathname.com/fhs/2.2/) , or google

---

### Post by cormu7 on 2011-01-18
koenn,

thanks for your response. that clears some things up for me.

much appreciated.

cor

---

### Post by koenn on 2011-01-19
no problem.

---

