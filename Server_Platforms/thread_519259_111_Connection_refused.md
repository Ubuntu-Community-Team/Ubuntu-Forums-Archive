---
title: "111 Connection refused"
date: 2007-08-06
forum: Server Platforms
---

### Post by jaakan on 2007-08-06
I just got this after I upgraded from 6.06.1 to 6.10 to 7.04 server.



PING [www.l.google.com](www.l.google.com) (64.233.169.147) 56(84) bytes of data.

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2002ms

jaakan@MD-DMZ-WEBTEST-02:~$

jaakan@MD-DMZ-WEBTEST-02:~$ nslookup [www.google.com](www.google.com)
Server:         192.168.50.10
Address:        192.168.50.10#53

Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.169.104
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.169.103
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.169.99
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.169.147

jaakan@MD-DMZ-WEBTEST-02:~$


jaakan@MD-DMZ-WEBTEST-02:~$ sudo aptitude update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Reading package lists... Done
jaakan@MD-DMZ-WEBTEST-02:~$


jaakan@MD-DMZ-WEBTEST-02:~$ cat /etc/resolv.conf
search isky.com
nameserver 192.168.50.10
jaakan@MD-DMZ-WEBTEST-02:~$

jaakan@MD-DMZ-WEBTEST-02:/etc$ cat nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns mdns
networks:       files dns

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
jaakan@MD-DMZ-WEBTEST-02:/etc$

---

### Post by bmathis on 2007-08-07
this was posted on answers.launchpad.net 

[https://answers.launchpad.net/ubuntu/+question/10408]("https://answers.launchpad.net/ubuntu/+question/10408")

go to System > Administration > Software Sources, choose the main servers and try again. It should work after that.

---

### Post by jaakan on 2007-08-07
there has to be something broken or missing, I upgraded 2 other servers and they don't have this issue and they are the same hardware, dell PE 2450 with 2 HDs ( raid 1 )

that won't help since I can't ping by name and I'm not running Xorg.

[edit]

jaakan@MD-DMZ-WEBTEST-02:/etc/dhcp3$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  console-setup gnupg libsasl2-2 python2.5 tasksel-data update-manager-core
The following packages will be REMOVED:
  ca-certificates grub laptop-detect libcurl3-gnutls libdb4.2 libidn11 libsqlite3-0 ntp openssh-server openssl perl
  perl-modules python-apt python-gnupginterface ssh x11-common
0 packages upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.8MB will be freed.
The following packages have unmet dependencies:
  update-manager-core: Depends: python-apt (>= 0.6.16.2) but it is not installable
                       Depends: python-gnupginterface but it is not installable
  python2.5: Depends: libsqlite3-0 (>= 3.3.13) but it is not installable
  tasksel-data: Depends: laptop-detect but it is not installable
  console-setup: Depends: perl but it is not installable
  libsasl2-2: Depends: libdb4.2 but it is not installable
  gnupg: Depends: libcurl3-gnutls (>= 7.15.5-1) but it is not installable
         Depends: libidn11 (>= 0.5.18) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
ca-certificates [20061027 (now)]
grub [0.97-20ubuntu6 (now)]
laptop-detect [0.12.1-ubuntu4 (now)]
libcurl3-gnutls [7.15.5-1ubuntu2.1 (feisty-security, now)]
libdb4.2 [4.2.52+dfsg-1build1 (now)]
libidn11 [0.6.5-1build1 (now)]
libsqlite3-0 [3.3.13-0ubuntu1 (now)]
openssl [0.9.8c-4build1 (now)]
perl [5.8.8-7build1 (now)]
perl-modules [5.8.8-7build1 (now)]
python-apt [0.6.20ubuntu16 (now)]
python-gnupginterface [0.3.2-9 (now)]

Score is -530

Accept this solution? [Y/n/q/?]

---

### Post by jaakan on 2007-08-07
when I moved the server back to the inside LAN from the DMZ and changed it to DHCP. I don't get the "111 Connection refused" error.



I can't boot this server with the 7.04 server or LIVE CD.
6.06 server CD works.  I need to try 6.10 server CD.

Is there anyway I can sync whats install and configured from one server to another, basicly mirror the working server?

---

### Post by bmathis on 2007-08-08
if you arent using a GUI you can edit the sources file in /etc/apt/sources.list and remove the country code from each repository (i.e. [http://us.repository.com/](http://us.repository.com/) to [http://repository.com/](http://repository.com/))

I believe you can use rsync to "mirror" another machine.

---

### Post by jaakan on 2007-08-16
the add-in NIC was eth0
the internal NIC was eth1

eth0 and eth1 have gone missing

ifconfig shows 

lo...
eth2 ...

eth2 seems to now be the internal NIC.

seems like the network sub system is trashed

---

