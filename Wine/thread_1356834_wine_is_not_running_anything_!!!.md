---
title: "wine is not running anything !!!"
date: 2009-12-16
forum: Wine
---

### Post by chuina on 2009-12-16
in my Karmic,

the same software run well in RHEL5/Fedora6.

but due this message:

```
Component 'msdxm.ocx' or one of its dependencies not correctly
registered: a file is missing
```it doen't run.....

no help, no thanks 

Give help, Get thanks.

---

### Post by HighCommander540 on 2009-12-17
> **chuina said:**
> :(, in my Karmic,

the same software run well in RHEL5/Fedora6.

but due this message:

```
Component 'msdxm.ocx' or one of its dependencies not correctly
registered: a file is missing
```

it doen't run.....

no help, no thanks 

Give help, Get thanks.

Just uninstall and reinstall wine.

```
 sudo apt-get remove --purge wine
```

```
 sudo apt-get install wine
```

---

### Post by chuina on 2009-12-17
(This thread is big)

The result is same.
During install the following messages given (i'm posting the complete msg): 

```

chuina@desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract samba-common smbclient ttf-liberation ttf-mscorefonts-installer winbind
Suggested packages:
  smbfs
The following NEW packages will be installed:
  cabextract ttf-liberation ttf-mscorefonts-installer winbind wine
The following packages will be upgraded:
  samba-common smbclient
2 upgraded, 5 newly installed, 0 to remove and 154 not upgraded.
Need to get 0B/24.9MB of archives.
After this operation, 67.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package wine.
(Reading database ... 126087 files and directories currently installed.)
Unpacking wine (from .../wine_1.0.1-0ubuntu8_i386.deb) ...
Selecting previously deselected package cabextract.
Unpacking cabextract (from .../cabextract_1.2-3_i386.deb) ...
Preparing to replace smbclient 2:3.4.0-3ubuntu5 (using .../smbclient_2%3a3.4.0-3ubuntu5.1_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 2:3.4.0-3ubuntu5 (using .../samba-common_2%3a3.4.0-3ubuntu5.1_all.deb) ...
Unpacking replacement samba-common ...
Selecting previously deselected package ttf-liberation.
Unpacking ttf-liberation (from .../ttf-liberation_1.05.1.20090721-0ubuntu1_all.deb) ...
Selecting previously deselected package ttf-mscorefonts-installer.
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.0_all.deb) ...
Selecting previously deselected package winbind.
Unpacking winbind (from .../winbind_2%3a3.4.0-3ubuntu5.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for sreadahead ...
Setting up wine (1.0.1-0ubuntu8) ...
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
vm.mmap_min_addr = 0

Setting up cabextract (1.2-3) ...
Setting up samba-common (2:3.4.0-3ubuntu5.1) ...

Setting up smbclient (2:3.4.0-3ubuntu5.1) ...
Setting up ttf-liberation (1.05.1.20090721-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.

Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-17 20:34:54--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-17 20:34:54--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `switch.dl.sourceforge.net'
--2009-12-17 20:34:55--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-17 20:34:55--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-12-17 20:34:55--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2009-12-17 20:34:55--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-17 20:34:55--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2009-12-17 20:34:55--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2009-12-17 20:34:55--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2009-12-17 20:34:56--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2009-12-17 20:34:56--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-12-17 20:34:56--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up winbind (2:3.4.0-3ubuntu5.1) ...
 * Starting the Winbind daemon winbind                                                                                [ OK ] 

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

:confused:And also after this each time i use apt-get/aptitude it tryes to connect  ....sourceforge...... 
and failed. Also slowing other fetching process.

waiting for more steps ...
Thanks ...!

---

### Post by beastrace91 on 2009-12-17
Are you using the default Ubuntu repos or did you add the ones form WineHQ.org? Its not unheard of for repos to hang up every now and then, give it a try again in a few hours.

Regards,
~Jeff

---

### Post by chuina on 2009-12-17
Hey, Senior,

here is my repos :

```
deb http://ubuntu.stu.edu.tw/ubuntu/ karmic main restricted
deb-src http://ubuntu.stu.edu.tw/ubuntu/ karmic main restricted
```

there are a few more lines above and below of these two lines.
all of them are related to **ubuntu.stu.edu.tw**.

this repo is selected by ......Select Best Repo option.......(from my location)

i have just tried again and .......it installed many things of ...andale32.exe....stopped with two 
error lines :
```

dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
```

is it possible to download andale32.exe manually & install.

Thanks

---

### Post by chuina on 2009-12-23
It is my ISP , which is not allowing me to download from sourceforge.net.
Cause i tried to download other softs from sourceforge but failed.
Not Ubuntu or Wine is responsible for this.

Is there any alternet  way to download those fonts ?
Or, should i try to copy fonts from other windows machine ?

thanks.

---

