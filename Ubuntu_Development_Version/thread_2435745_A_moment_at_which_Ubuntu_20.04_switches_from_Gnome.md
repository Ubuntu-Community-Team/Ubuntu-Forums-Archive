---
title: "A moment at which Ubuntu 20.04 switches from Gnome to Unity?"
date: 2020-01-25
forum: Ubuntu Development Version
---

### Post by zika on 2020-01-25
```
The following packages were automatically installed and are no longer required:
  gir1.2-gst-plugins-base-1.0 gir1.2-rb-3.0 hplip-data libcolord-gtk1 libdmapsharing-3.0-2 libgpod-common libgpod4 libgsound0 libgupnp-av-1.0-2 libgupnp-dlna-2.0-3 libimagequant0 libldb2 liblirc-client0 libmtp-common libmtp-runtime libmtp9 libnfs13 librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2
  librygel-server-2.6-2 libsane-hpaio libsgutils2-2 libtalloc2 libtevent0 libwbclient0 mobile-broadband-provider-info network-manager-gnome printer-driver-postscript-hp python3-mako python3-markupsafe python3-olefile python3-pil python3-renderpm python3-reportlab python3-reportlab-accel rygel
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  gnome-control-center gvfs-backends hplip libsmbclient python3-talloc python3-uno rhythmbox-plugins samba-libs ubuntu-desktop ubuntu-desktop-minimal
The following NEW packages will be installed:
  activity-log-manager libfcitx-config4 libgeonames-common libgeonames0 libpython3.8 libtimezonemap-data libtimezonemap1 libunity-control-center1 libunity-settings-daemon1 libzeitgeist-2.0-0 policykit-1-gnome unity-control-center unity-settings-daemon zeitgeist-core
The following packages will be upgraded:
  compizconfig-settings-manager libpython3-stdlib python3 python3-compizconfig python3-minimal
```

Update&#8321;: Digging a bit more, it looks like it is not, just waiting for some packages to catch on with python... Will see... ;)

Update&#8322;: Eppur si muove. Turned out to be a catchup with Python: ```
The following packages were automatically installed and are no longer required:
  hplip-data libimagequant0 libpython3.7 libsane-hpaio printer-driver-postscript-hp python3-olefile python3-pil python3-renderpm python3-reportlab python3-reportlab-accel
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  hplip python3-uno
The following packages will be upgraded:
  gir1.2-rb-3.0 libpython3-stdlib librhythmbox-core10 libtalloc2 python3 python3-minimal python3-talloc rhythmbox rhythmbox-plugins
9 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 1067 kB of archives.
After this operation, 1079 kB disk space will be freed.
```

Update&#8323;: Since my first assumption was wrong and it was Python-related, as i suspected later, I'm marking this as &#8222;Solved&#8220;... Only python3-uno is left and i hope it will get resolved with new edition of LibreOffice...

Update&#8324;: 
A bit buggy due to bad syntax... :)
```
Setting up python3 (3.8.0-3) ...
running python rtupdate hooks for python3.8...
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/share/hplip/base/utils.py:2063: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if weburl is "" or weburl is None:
/usr/share/hplip/check-plugin.py:116: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if log_level is 'debug':
/usr/share/hplip/check.py:685: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if 'getfacl' not in g and '' is not g and 'file' not in g:
/usr/share/hplip/installer/core_install.py:2037: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if home_dir is "":
/usr/share/hplip/ui5/devmgr_ext.py:15: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if self.latest_available_version is not "":
/usr/share/hplip/ui5/devmgr_ext.py:37: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if self.latest_available_version is not "":
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
running python post-rtupdate hooks for python3.8...
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
Setting up printer-driver-hpcups (3.19.12+dfsg0-3ubuntu1) ...
Setting up python3-talloc:amd64 (2.3.0-3ubuntu1) ...
Setting up rhythmbox-plugins (3.4.4-1ubuntu2) ...
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
Setting up hplip-data (3.19.12+dfsg0-3ubuntu1) ...
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
/usr/share/hplip/base/utils.py:2063: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if weburl is "" or weburl is None:
/usr/share/hplip/check-plugin.py:116: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if log_level is 'debug':
/usr/share/hplip/check.py:685: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if 'getfacl' not in g and '' is not g and 'file' not in g:
/usr/share/hplip/installer/core_install.py:2037: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if home_dir is "":
/usr/share/hplip/ui5/devmgr_ext.py:15: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if self.latest_available_version is not "":
/usr/share/hplip/ui5/devmgr_ext.py:37: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if self.latest_available_version is not "":

```

---

### Post by Doug S on 2020-01-30
I am having struggles with 20.04 and lingering python 2.X dependencies also.

---

### Post by zika on 2020-01-31
> **Doug S said:**
> I am having struggles with 20.04 and lingering python 2.X dependencies also.On several installs I do have with 20.04, after all except python3-uno stopped to show up in dist-upgrade offer, I have 2.7-free machines. Yes, I do use some stuff to clean cruft  but I think, in this case, installs cleaned themselves successfully...
3.8 is a bit buggy due to somewhat starters syntax errors in packages. And it kind of goes downstream... I've tried to file bug reports but it is so slow and hard to document I did give up... ;) First bug report from some time ago is now in triage stage being confirmed and...

---

### Post by Doug S on 2020-02-01
Do you know how to check the status of a package's migration away from python 2.X dependencies?
My particular example is the "kernel-package", which still wants to pull in a ton of python 2.x stuff:

```
doug@serv-ff:~$ sudo apt install kernel-package
...
The following additional packages will be installed:
  ...
    ... python2 python2-minimal python2.7 python2.7-minimal
0 upgraded, 373 newly installed, 0 to remove and 0 not upgraded.

```The server team pointed me to [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2019-November/040842.html"), which in turn pointed me to [here]("https://people.canonical.com/~ubuntu-archive/transitions/html/python2-rm.html"),  but I can not find it on that list.

I have one 20.04 server, where I have allowed this stuff to be installed, and another where I haven't.

---

### Post by zika on 2020-02-02
> **Doug S said:**
> Do you know how to check the status of a package's migration away from python 2.X dependencies?
My particular example is the "kernel-package", which still wants to pull in a ton of python 2.x stuff:

```
doug@serv-ff:~$ sudo apt install kernel-package
...
The following additional packages will be installed:
  ...
    ... python2 python2-minimal python2.7 python2.7-minimal
0 upgraded, 373 newly installed, 0 to remove and 0 not upgraded.

```The server team pointed me to [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2019-November/040842.html"), which in turn pointed me to [here]("https://people.canonical.com/~ubuntu-archive/transitions/html/python2-rm.html"),  but I can not find it on that list.

I have one 20.04 server, where I have allowed this stuff to be installed, and another where I haven't.```
:~$ apt-cache depends kernel-package
kernel-package
  Depends: build-essential
  Depends: po-debconf
  Depends: gettext
  Depends: file
  Depends: bc
  Depends: binutils
  Depends: kmod
  Depends: xz-utils
  Depends: xmlto
  Depends: lzma
    xz-utils
  Depends: bzip2
  Depends: dpkg-dev
  Recommends: docbook-utils
  Recommends: cpio
  Recommends: <uboot-mkimage>
  Recommends: kernel-common
  Suggests: linux-source
    linux-source-5.4.0
  Suggests: libncurses-dev
```Then go upstream and see which package does bring back 2.7...

---

