---
title: "Problem with backports repository when installing samba"
date: 2005-05-27
forum: Ubuntu Backports
---

### Post by SkyNet_ on 2005-05-27
I recently added the backports repositories in the sources.list and started updating and then upgrading.
I then was prompted to add WINS server to samba, i answered that i didn't want.
After that I get this error:

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libxvidcore4 mplayer-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
/bin/sh: line 1:  9863 Segmentation fault      /usr/sbin/dpkg-preconfigure --apt
Setting up samba (3.0.14a-1~5.04ubp1) ...
Starting Samba daemons: nmbd smbd.
dpkg: error processing samba (--configure):
 subprocess post-installation script killed by signal (Segmentation fault)
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried removing the *.deb files from /var/cache/apt/archives, removed backports repository but no go.

Please help me resolve this issue.. 

P.S. I dont know if this is the best place to post this I hope it is!

---

### Post by jdong on 2005-05-27
that is a very strange error, usually indicating a bug in dpkg, or more likely, defective RAM. Can you run a Memory test?

---

### Post by SkyNet_ on 2005-05-27
How can I do that?
I am rather a newbie with Linux..

By the way what I tought was that maybe this samba package that is about to be installed is corrput or something similar.
Is there a way to "clear" this cache and then try to reinstall the package?

---

### Post by jdong on 2005-05-27
[QUOTE=SkyNet_]How can I do that?
I am rather a newbie with Linux..

By the way what I tought was that maybe this samba package that is about to be installed is corrput or something similar.
Is there a way to "clear" this cache and then try to reinstall the package?[/QUOTE]

To clear, run **sudo apt-get clean**

To check your memory, choose Memory Test (last option) from the bootup menu. This takes around 30 minutes to do.

---

### Post by SkyNet_ on 2005-05-27
ok i resolved it..
removed everything, reinstalled and then I told the script that I want WINS support and everything works smooooth now..
strange but there must be something wrong.
btw memtest completed fine :-)

---

