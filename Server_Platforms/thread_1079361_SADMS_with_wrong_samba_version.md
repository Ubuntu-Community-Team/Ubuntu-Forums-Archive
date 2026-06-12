---
title: "SADMS with wrong samba version"
date: 2009-02-24
forum: Server Platforms
---

### Post by pierrot-san on 2009-02-24
i&#7743; getting the error that mine version is to low. but i can't find any other version.

-------------------------------------------------------------------------------
S A D M S  2.0.12
Samba as Active Directory Member Server
[email]bbou@ac-toulouse.fr[/email]
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
install
-------------------------------------------------------------------------------
[BEGIN]
[1]
+fix bugs/incompatibilities
disable avahi-daemon automatic startup
disable fam automatic startup
[2]
+customize krb5.conf
install new krb5.conf to /etc
[3]
+get current samba version for smb.conf syntax
samba minor version is 2:3.2.3-1ubuntu3.5
+samba config switches
use wins server
include sample shares
+customize smb.conf
install new smb.conf to /etc/samba
+customize user.map
install new user.map to /etc/samba
+creating sample data folder in /data shared as data
[4]
+ping kdc windows-2003-t2
ok
[5]
+sync clocks with kdc
local time was: 2009-02-24 15:46.50
synchronizing with windows-2003-t2
net time is now:2009-02-24 15:46.50
local time is now:2009-02-24 15:46.50
[6]
+get Kerberos ticket-granting ticket for principal [email]test@SCHOOL.LOCAL[/email]
got ticket-granting ticket for principal krbtgt/SCHOOL.LOCAL@SCHOOL.LOCAL
[7]
+get current samba version for join domain syntax
samba minor version is 2:3.2.3-1ubuntu3.5
+join domain to Computers
join failed and returned 255
[7>] with error
log extract
vvvvv
Feb 24 15:46:49 ubuntu sadms: sadms start
Feb 24 15:46:51 ubuntu sadms: sadms finish error 7 join domain
^^^^^
[END]

./config-smbconf.sh: line 54: 2:3.2.3-1ubuntu3.5: syntax error in expression (error token is ":3.2.3-1ubuntu3.5")
./join-domain.sh: line 60: 2:3.2.3-1ubuntu3.5: syntax error in expression (error token is ":3.2.3-1ubuntu3.5")
[ERROR]
returned error code 7
command line was <./_install.sh   'SCHOOL.LOCAL' 'school.local' 'windows-2003-t2' 'school' 'ubuntu' 'Computers' '*****' '*****' 'Domain Users' '192.168.5.0/255.255.255.0' '192.168.5.5'>


how do i stop this error????

---

### Post by capscrew on 2009-02-24
> **pierrot-san said:**
> i&#7743; getting the error that mine version is to low. but i can't find any other version...
how do i stop this error????

It appears you are not alone.  
See the 3 post here:
[https://bugs.launchpad.net/ubuntu-doc/+bug/278548]("https://bugs.launchpad.net/ubuntu-doc/+bug/278548")

I would contact the folks at SADMS.

---

### Post by pierrot-san on 2009-02-25
with help from a other forum we cam up with the fellowing changes in the config-smbconf.sh and join-domain.sh

```

sambamajorversion=`echo "${sambaversion}" | sed 's/^\([0-9]\).*$/\1/g'`
sambaminorversion=`echo "${sambaversion}" | sed 's/^[0-9]*\.[0-9]*\.\([0-9]*\).*$/\1/g'`
**to**
sambamajorversion=`echo "$sambaversion" | sed 's/^[0-9]:\([0-9]\).*$/\1/g'`
sambaminorversion=`echo "${sambaversion}" | sed 's/^[0-9]:[0-9]*\.[0-9]*\.\([0-9]*\).*$/\1/g'`
------------------------------------------------
if (( $((sambaminorversion)) < 23 )); then
**to**
if (( $((sambaminorversion)) < 2 )); then

```

---

### Post by jokager on 2009-08-11
I am trying to install sadms by getting the error highlighted in red, at the bottom:
./START
OS=Linux
KERNEL=2.6.28-14-generic
ARCHITECTURE=i686
DISTRIBUTION=Ubuntu
DISTRIBUTIONTAG=jaunty
DISTRIBUTIONVERSION=9.04
+P A C K A G E    S E L E C T I O N
select package /home/administrator/Desktop/sadms-2.0.12/ubuntu/sadms_2.0.12-1_all.deb
+P R E I N S T A L L
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
apt has universe repository
+UBUNTU PACKAGES
+python OK
+python-gtk2 OK
+python-glade2 OK
+samba OK
+samba-common OK
+winbind OK
+smbclient OK
+smbfs OK
+nscd OK
+libpam-mount OK
+krb5-user OK
+expect OK
+gawk OK
+bsdutils OK
+bind9-host OK
+iproute OK
+acl OK
+C H E C K
+SAMBA PACKAGE
[COLOR=DarkRed]package=samba
version=2:3.3.2-1ubuntu3.1
majorversion=2
current version is 2 [FAIL] (samba 3 is needed)
samba is not properly configured
[/COLOR]


Any help please

Regards

---

