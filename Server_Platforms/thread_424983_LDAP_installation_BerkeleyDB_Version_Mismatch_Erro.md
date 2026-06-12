---
title: "LDAP installation BerkeleyDB Version Mismatch Error"
date: 2007-04-27
forum: Server Platforms
---

### Post by daveynet on 2007-04-27
Hi,

  I'm trying to install OpenLDAP from source, and when I run the configure command I get this errors:

  1    checking db.h usability... yes
  2    checking bd.h prescence... yes
  3    checking for db.h... yes
  4    checking for Berkeley DB major version... 4
  5    checking for Berkeley DB minor version... 2
  6    checking for Berkeley DB link (-ldb42)... no
  7    checking for Berkeley DB link (-ldb-42)... no
  8    checking for Berkeley DB link (-ldb-4.2)... yes
  9    checking for Berkeley version match... no
  10  configure: error Berkeley DB version mismatch
  11  checking for Berkely DB

  I've tried linking the db.h header as advised from an [older thread]("http://ubuntuforums.org/showthread.php?p=2395353") and I think I solved that problem. On line 3 i think that's what it means, but I still get the error. I also tried installing the relevant libdb{version}-dev package and I'm still stumped?

  Any help would be greatly appreciated. Also if anyone has an alternative method to install OpenLDAP I'd appreciate any of your ideas. I'm running Ubuntu 6 from a VMWare image and we cannot seem to get the OpenLDAP packages to install because of various "clamav" dependency issues, so have to resort to building and installing it from scratch. 

  Anyone can help? 

  Thanks in advance

daVe =P

---

