---
title: "SystemImager Prepareclient not working: here's the err. syntax"
date: 2006-09-06
forum: Server Platforms
---

### Post by kenquad on 2006-09-06
Hi all:

I'm trying to use SystemImager on an OpenSuSE 10.0 box to moderate between 2 Ubuntu Dapper boxes, making one a duplicate of the other.  But when I try to run prepareclient on the primary Ubuntu box, here's what I get:

```

kenquad@UMD1:~$ sudo si_prepareclient
Password:
si_prepareclient (part of SystemImager) v3.6.2

Copyright (C) 1999-2005 Brian Elliott Finley

This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Usage: si_prepareclient --server IMAGESERVER [OPTION]...

Options:
 --version
    Display version and copyright information.

 --help
    Display this output.

 --server IMAGESERVER
    Where IMAGESERVER is either the IP address or host name of your
    SystemImager server.  Prepareclient makes your golden client's root
    filesystem readable to other rsync capable machines.  While this
    access is read only, it may expose sensitive information.  This
    option limits access so that only your SystemImager server can read
    your golden client's root filesystem.

 --no-rsyncd
    Do not start the rsync daemon.

 --yes
    Answer yes to all yes/no questions.

 --exclude, -e DISK [-e DISK...]
    Do not gather partition information for DISK(s).  The result of
    using this option, is that DISK(s) will not be partitioned during
    the auto-install process.

    You may prefix DISK with "/dev/", but it is not necessary, and a
    base directory of /dev/ will be assumed.

    Example: -e /dev/sdb -e sdc -e /dev/ida/c0d0 -e ida/c0d1

 --quiet
    Run silently.  Return an exit status of 0 for success or a non-zero
    exit status for failure.

 --rpm-install
    This is only used when building an RPM.

Download, report bugs, and make suggestions at:
http://systemimager.org/

Try the --server option.

jason@UMD1:~$ sudo si_prepareclient --server
Option server requires an argument
si_prepareclient (part of SystemImager) v3.6.2

Copyright (C) 1999-2005 Brian Elliott Finley

This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Usage: si_prepareclient --server IMAGESERVER [OPTION]...

Options:
 --version
    Display version and copyright information.

 --help
    Display this output.

 --server IMAGESERVER
    Where IMAGESERVER is either the IP address or host name of your
    SystemImager server.  Prepareclient makes your golden client's root
    filesystem readable to other rsync capable machines.  While this
    access is read only, it may expose sensitive information.  This
    option limits access so that only your SystemImager server can read
    your golden client's root filesystem.

 --no-rsyncd
    Do not start the rsync daemon.

 --yes
    Answer yes to all yes/no questions.

 --exclude, -e DISK [-e DISK...]
    Do not gather partition information for DISK(s).  The result of
    using this option, is that DISK(s) will not be partitioned during
    the auto-install process.

    You may prefix DISK with "/dev/", but it is not necessary, and a
    base directory of /dev/ will be assumed.

    Example: -e /dev/sdb -e sdc -e /dev/ida/c0d0 -e ida/c0d1

 --quiet
    Run silently.  Return an exit status of 0 for success or a non-zero
    exit status for failure.

 --rpm-install
    This is only used when building an RPM.

Download, report bugs, and make suggestions at:
http://systemimager.org/

jason@UMD1:~$ sudo si_prepareclient --server 192.168.2.170
Welcome to the SystemImager si_prepareclient command.  This command may modify
the following files to prepare your golden client for having it's image
retrieved by the imageserver.  It will also create the /etc/systemimager
directory and fill it with information about your golden client.  All modified
files will be backed up with the .before_systemimager-3.6.2 extension.

 /etc/services:
   This file defines the port numbers used by certain software on your system.
   Entries for rsync will be added if necessary.

 /tmp/rsyncd.conf.5785:
   This is a temporary configuration file that rsync needs on your golden client
   in order to make your filesystem available to your SystemImager server.

 inetd configuration:
   SystemImager needs to run rsync as a standalone daemon on your golden client
   until it's image is retrieved by your SystemImager server.  If rsyncd is
   configured to run as a service started by inetd, it will be temporarily
   disabled, and any running rsync daemons or commands will be stopped.  Then,
   an rsync daemon will be started using the temporary configuration file
   mentioned above.

See "si_prepareclient --help" for command line options.

Continue? (y/[n]): y

*********************************** WARNING ***********************************
This utility starts an rsync daemon that makes all of your files accessible
by anyone who can connect to the rsync port of this machine.  This is the
case until you reboot, or kill the 'rsync --daemon' process by hand.  By
default, once you use si_getimage to retrieve this image on your imageserver,
these contents will become accessible to anyone who can connect to the rsync
port on your imageserver.  See rsyncd.conf(5) for details on restricting
access to these files on the imageserver.  See the systemimager-ssh package
for a more secure method of making images available to clients.
*********************************** WARNING ***********************************

Continue? (y/[n]): y

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Using "sfdisk" to gather information about disk:
    /dev/hda

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 39560/16/63).
For this listing I'll assume that geometry.
rsync: link_stat "/usr/share/systemimager/boot/i386/standard/initrd_template/." failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(791)
Couldn't rsync -a /usr/share/systemimager/boot/i386/standard/initrd_template/ /tmp/.systemimager.1/. at /usr/lib/systemimager/perl/SystemImager/UseYourOwnKernel.pm line 58.
kenquad@UMD1:~$ sudo si_prepareclient --server 192.168.2.170

```

With whitespace removed.  Any help would be greatly appreciated, if someone out there has a little experience with SystemImager - because I don't....

---

