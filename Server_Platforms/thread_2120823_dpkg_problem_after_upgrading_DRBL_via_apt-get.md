---
title: "dpkg problem after upgrading DRBL via apt-get"
date: 2013-02-27
forum: Server Platforms
---

### Post by tixetsal on 2013-02-27
***EDIT***

So I think that the problem is that the version of dpkg that's included with Ubuntu 10.04 can't handle the xz compression. I am considering upgrading dpkg. Does anyone have any tips on upgrading? I found a PPA, but I want to do a little bit more research before I start hacking on things.


I am having a problem after upgrading DRBL (diskless remote boot linux) on 10.04 Server AMD64. Any pointers would be appreciated. 

I added "deb [http://drbl.sourceforge.net/drbl-core](http://drbl.sourceforge.net/drbl-core) drbl stable" to sources.list and installed drbl about a year ago. I have had no problems in upgrading until now. This AM, while trying to upgrade installed packages, I received this error:

```

root@wilson:/var/cache/apt/archives# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  mkpxeinitrd-net
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@wilson:/var/cache/apt/archives# apt-get install drbl
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libcrypt-passwdmd5-perl syslinux syslinux-common
The following NEW packages will be installed:
  drbl libcrypt-passwdmd5-perl syslinux syslinux-common
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 10.4kB/2,767kB of archives.
After this operation, 8,437kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe libcrypt-passwdmd5-perl 1.3-9 [10.4kB]
Fetched 10.4kB in 0s (109kB/s)
Selecting previously deselected package libcrypt-passwdmd5-perl.
(Reading database ... 81067 files and directories currently installed.)
Unpacking libcrypt-passwdmd5-perl (from .../libcrypt-passwdmd5-perl_1.3-9_all.deb) ...
Unpacking syslinux-common (from .../syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb) ...
dpkg-deb: file `/var/cache/apt/archives/syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb' contains ununderstood data member data.tar.xz     , giving up
dpkg: error processing /var/cache/apt/archives/syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Unpacking syslinux (from .../syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb) ...
dpkg-deb: file `/var/cache/apt/archives/syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb' contains ununderstood data member data.tar.xz     , giving up
dpkg: error processing /var/cache/apt/archives/syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Selecting previously deselected package drbl.
Unpacking drbl (from .../drbl_2.3.9-drbl1_all.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb
 /var/cache/apt/archives/syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried all manner of dpkg repairs and manually installing the .debs. 

```

root@wilson:/var/cache/apt/archives# dpkg -i 
drbl_2.3.9-drbl1_all.deb                       lock                                           syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb
libcrypt-passwdmd5-perl_1.3-9_all.deb          partial/                                       
libdbus-glib-1-2_0.84-1ubuntu0.3_amd64.deb     syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb       
root@wilson:/var/cache/apt/archives# dpkg -i syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb 
(Reading database ... 81527 files and directories currently installed.)
Unpacking syslinux (from syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb) ...
dpkg-deb: file `syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb' contains ununderstood data member data.tar.xz     , giving up
dpkg: error processing syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 syslinux_2%3a4.06+dfsg-1.drbl1_amd64.deb

root@wilson:/var/cache/apt/archives# dpkg -i syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb 
(Reading database ... 81527 files and directories currently installed.)
Unpacking syslinux-common (from syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb) ...
dpkg-deb: file `syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb' contains ununderstood data member data.tar.xz     , giving up
dpkg: error processing syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 syslinux-common_2%3a4.06+dfsg-1.drbl1_all.deb

```

Has anyone seen this before? My next move is to comment out the sourceforge repo in sources.list and try to see if the syslinux packages from the standard repos can be installed.

---

### Post by Timo_Riekko on 2013-09-12
HI.

Yes i have similar problem.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  syslinux syslinux-common
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,126kB of archives.
After this operation, 695kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://free.nchc.org.tw/drbl-core/](http://free.nchc.org.tw/drbl-core/) drbl/stable syslinux-common 2:5.10+drbl-1 [953kB]
Get:2 [http://free.nchc.org.tw/drbl-core/](http://free.nchc.org.tw/drbl-core/) drbl/stable syslinux 2:5.10+drbl-1 [173kB]
Fetched 1,126kB in 4s (280kB/s)
dpkg: considering deconfiguration of syslinux, which would be broken by installation of syslinux-common ...
dpkg: yes, will deconfigure syslinux (broken by syslinux-common).
(Reading database ... 757753 files and directories currently installed.)
Preparing to replace syslinux-common 2:4.06+dfsg-1.drbl2 (using .../syslinux-common_2%3a5.10+drbl-1_all.deb) ...
De-configuring syslinux ...
Unpacking replacement syslinux-common ...
dpkg-deb: file `/var/cache/apt/archives/syslinux-common_2%3a5.10+drbl-1_all.deb' contains ununderstood data member data.tar.xz     , giving up
dpkg: error processing /var/cache/apt/archives/syslinux-common_2%3a5.10+drbl-1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
dpkg: considering deconfiguration of syslinux-common, which would be broken by installation of syslinux ...
dpkg: yes, will deconfigure syslinux-common (broken by syslinux).
Preparing to replace syslinux 2:4.06+dfsg-1.drbl2 (using .../syslinux_2%3a5.10+drbl-1_amd64.deb) ...
De-configuring syslinux-common ...
Unpacking replacement syslinux ...
dpkg-deb: file `/var/cache/apt/archives/syslinux_2%3a5.10+drbl-1_amd64.deb' contains ununderstood data member data.tar.xz     , giving up
dpkg: error processing /var/cache/apt/archives/syslinux_2%3a5.10+drbl-1_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/syslinux-common_2%3a5.10+drbl-1_all.deb
 /var/cache/apt/archives/syslinux_2%3a5.10+drbl-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Tried some clean up but nothing helps.

---

### Post by tixetsal on 2013-09-12
Timo, see my bug report:  [http://sourceforge.net/p/drbl/bugs/5/](http://sourceforge.net/p/drbl/bugs/5/)

---

