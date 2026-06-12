---
title: "Hylafax and Sendmail"
date: 2006-10-27
forum: Server Platforms
---

### Post by mattwilsonmcp on 2006-10-27
I am trying to setup a Hylafax server on Dapper. I did a server install and installed Hylafax using the following: ```
sudo aptitude install hylafax-server hylafax-client hylafax-doc
``` This works just fine. I can send faxes using the Winprint Hylafax or WHFC Windows clients. The problem is, I don't get email confirmations like I'm supposed to. I believe the problem is with sendmail. I have a dns server and mail server on site. I would like to relay SMTP from the Hylafax server to my existing mail server. Can someone help?

---

### Post by danbar on 2007-03-10
Can anyone help?  I'm sending the fax.  It says that I'm successful but no fax was sent!!

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libtiff-tools mailx metamail sharutils 
The following NEW packages will be installed:
  hylafax-client hylafax-doc hylafax-server libtiff-tools mailx metamail 
  sharutils 
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2132kB of archives. After unpacking 6435kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) edgy/universe hylafax-client 2:4.3.0-5 [348kB]
Get:2 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) edgy/main libtiff-tools 3.8.2-6 [171kB]
Get:3 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) edgy/main mailx 1:8.1.2-0.20050715cvs-1ubuntu1 [153kB]
Get:4 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) edgy/universe metamail 2.7-51 [150kB]
Get:5 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) edgy/main sharutils 1:4.2.1-15 [111kB]
Get:6 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) edgy/universe hylafax-doc 2:4.3.0-5 [379kB]
Get:7 [http://mt.archive.ubuntu.com](http://mt.archive.ubuntu.com) edgy/universe hylafax-server 2:4.3.0-5 [820kB]
Fetched 2132kB in 10s (196kB/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package hylafax-client.
(Reading database ... 154994 files and directories currently installed.)
Unpacking hylafax-client (from .../hylafax-client_2%3a4.3.0-5_i386.deb) ...
Selecting previously deselected package libtiff-tools.
Unpacking libtiff-tools (from .../libtiff-tools_3.8.2-6_i386.deb) ...
Selecting previously deselected package mailx.
Unpacking mailx (from .../mailx_1%3a8.1.2-0.20050715cvs-1ubuntu1_i386.deb) ...
Selecting previously deselected package metamail.
Unpacking metamail (from .../metamail_2.7-51_i386.deb) ...
Selecting previously deselected package sharutils.
Unpacking sharutils (from .../sharutils_1%3a4.2.1-15_i386.deb) ...
Selecting previously deselected package hylafax-doc.
Unpacking hylafax-doc (from .../hylafax-doc_2%3a4.3.0-5_all.deb) ...
Selecting previously deselected package hylafax-server.
Unpacking hylafax-server (from .../hylafax-server_2%3a4.3.0-5_i386.deb) ...
Setting up hylafax-client (4.3.0-5) ...

Creating config file /etc/hylafax/pagesizes with new version

Setting up libtiff-tools (3.8.2-6) ...
Setting up mailx (8.1.2-0.20050715cvs-1ubuntu1) ...

Setting up metamail (2.7-51) ...

Setting up sharutils (4.2.1-15) ...

Setting up hylafax-doc (4.3.0-5) ...

Setting up hylafax-server (4.3.0-5) ...
Adding system user `faxmaster' with uid 111...
Adding new group `faxmaster' (120).
Adding new user `faxmaster' (111) with group `faxmaster'.
Not creating home directory `/var/spool/hylafax'.

Setup program for HylaFAX (tm) 4.3.0.

Created for i686-pc-linux-gnu on Wed Jun 21 11:14:57 UTC 2006.

Found encoder: /usr/bin/mimencode
Found encoder: /usr/bin/uuencode
Looks like /usr/bin/mimencode supports base64 encoding.
Checking system for proper server configuration.


Warning: /etc/hylafax/getty-link does not exist or is not an executable program!

The file:

    /etc/hylafax/getty-link

does not exist or this file is not an executable program.  The
HylaFAX software optionally uses this program and the fact that
it does not exist on the system is not a fatal error.  If the
program resides in a different location and you do not want to
install a symbolic link for /etc/hylafax/getty-link that points to your program
then you must reconfigure and rebuild HylaFAX from source code.


Warning: /etc/hylafax/vgetty-link does not exist or is not an executable program!

The file:

    /etc/hylafax/vgetty-link

does not exist or this file is not an executable program.  The
HylaFAX software optionally uses this program and the fact that
it does not exist on the system is not a fatal error.  If the
program resides in a different location and you do not want to
install a symbolic link for /etc/hylafax/vgetty-link that points to your program
then you must reconfigure and rebuild HylaFAX from source code.


Warning: /etc/hylafax/egetty-link does not exist or is not an executable program!

The file:

    /etc/hylafax/egetty-link

does not exist or this file is not an executable program.  The
HylaFAX software optionally uses this program and the fact that
it does not exist on the system is not a fatal error.  If the
program resides in a different location and you do not want to
install a symbolic link for /etc/hylafax/egetty-link that points to your program
then you must reconfigure and rebuild HylaFAX from source code.

Make /var/spool/hylafax/bin/ps2fax a link to /var/spool/hylafax/bin/ps2fax.gs.


Make /var/spool/hylafax/bin/pdf2fax a link to /var/spool/hylafax/bin/pdf2fax.gs.

Update /var/spool/hylafax/status/any.info.

        HylaFAX configuration parameters are:

        [1] Init script starts faxq:            yes
        [2] Init script starts hfaxd            yes
        [3] Start old protocol:                 no
        [4] Start paging protocol:              no
Are these ok [yes]? 
Modem support functions written to /var/spool/hylafax/etc/setup.modem.
Configuration parameters written to /var/spool/hylafax/etc/setup.cache.

Restarting HylaFAX server processes.

You do not appear to have any modems configured for use.  Modems are
configured for use with HylaFAX with the faxaddmodem(8) command.
Do you want to run faxaddmodem to configure a modem [yes]? 
Done verifying system setup.
Creating /etc/hylafax/setup.cache from /var/spool/hylafax/etc/setup.cache.
Creating /etc/hylafax/setup.modem from /var/spool/hylafax/etc/setup.modem.
/var/spool/hylafax
Stopping HylaFAX daemons: faxq(not running) hfaxd(not running) faxgetty.
+ /bin/cp -p "/etc/hylafax/setup.cache" "/var/spool/hylafax/etc/setup.cache"
Starting HylaFAX daemons: faxq hfaxd faxgetty.

---

