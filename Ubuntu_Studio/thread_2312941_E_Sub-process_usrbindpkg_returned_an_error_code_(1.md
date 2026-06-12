---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1) for Pd-extended"
date: 2016-02-08
forum: Ubuntu Studio
---

### Post by chris420 on 2016-02-08
Hi all,

Firstly, I'm a new Ubuntu Studio (and Linux user). It's amazing my PC is so fast again! However, when trying to install pd-extended from PPA ppa:eighthave/pd-extended, but I've got this error E: Sub-process /usr/bin/dpkg returned an error code (1) for Pd-extended.

My terminal output is below:

```
me@me-R520-R522-R620:~$ sudo add-apt-repository ppa:eighthave/pd-extended
 Test builds of the Pd-extended package
 More info: [https://launchpad.net/~eighthave/+archive/ubuntu/pd-extended](https://launchpad.net/~eighthave/+archive/ubuntu/pd-extended)
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpfmdf_t25/secring.gpg' created
gpg: keyring `/tmp/tmpfmdf_t25/pubring.gpg' created
gpg: requesting key C39F5EEB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpfmdf_t25/trustdb.gpg: trustdb created
gpg: key C39F5EEB: public key "Launchpad Pure Data" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
me@me-R520-R522-R620:~$ ^C
me@me-R520-R522-R620:~$ sudo apt-get install pd-extended
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  compiz-core compiz-plugins-default dkms fftw-dev fftw2 libavifile-0.7-common
  libavifile-0.7c2 libcompizconfig0 libcr0 libdecoration0 libglew-dev
  libgmerlin-common libgmerlin0 libgsoap4 libhwloc-plugins libhwloc5
  libibverbs1 libjpeg62 libopenmpi1.6 libprotobuf8 libqaccessibilityclient0
  libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-uitools
  libqtscript4-xml libsmpeg0 libsndobj-dev libsndobj2c2 libtorque2
  libvncserver0 musescore-soundfont-gm puredata-doc puredata-extra
  python-compizconfig tclxapian tkpng
Use 'apt-get autoremove' to remove them.
Recommended packages:
  x-ttcidfont-conf
The following NEW packages will be installed
  pd-extended
0 to upgrade, 1 to newly install, 0 to remove and 15 not to upgrade.
Need to get 0 B/35.5 MB of archives.
After this operation, 85.2 MB of additional disk space will be used.
(Reading database ... 272073 files and directories currently installed.)
Preparing to unpack .../pd-extended_0.43.4-1~trusty1_i386.deb ...
Unpacking pd-extended (0.43.4-1~trusty1) ...
dpkg: error processing archive /var/cache/apt/archives/pd-extended_0.43.4-1~trusty1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/pkgconfig/Gem.pc', which is also in package gem-dev 1:0.93.3-5ubuntu4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/pd-extended_0.43.4-1~trusty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```


Any help would be greatly appreciated

Chris :)

---

### Post by howefield on 2016-02-08
You could try the --force-overwrite command

```
sudo dpkg -i --force-overwrite path-to-deb-package
```

substituting the actual deb package path in the above command which is probably /var/cache/apt/archives/pd.extended.deb *but not before first taking a copy of the file first..*

```
sudo cp /usr/lib/pkgconfig/Gem.pc ~/Documents
```

---

### Post by chris420 on 2016-02-10
Ah thanks this seems to work now :) :) :) :)

---

### Post by howefield on 2016-02-10
> **chris420 said:**
> Ah thanks this seems to work now :) :) :) :)

Cool, glad you got it, perhaps you can mark the thread as Solved if you are happy that it is.

The backed up copy of the Gem.pc file can now be deleted. Or left, it won't cause you any grief.

---

