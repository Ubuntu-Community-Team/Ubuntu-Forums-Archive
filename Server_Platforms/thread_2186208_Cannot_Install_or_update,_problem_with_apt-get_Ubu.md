---
title: "Cannot Install or update, problem with apt-get Ubuntu 12.04.03 Server"
date: 2013-11-06
forum: Server Platforms
---

### Post by jasonlyle88 on 2013-11-06
I am unable to install anything on my Ubuntu server.  When I do, i get the suggestion to run `apt-get -f install`


When I try running `apt-get -f install` I get:


```

apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-gnupginterface python-zope.interface
The following NEW packages will be installed:
  python-gnupginterface python-zope.interface
0 upgraded, 2 newly installed, 0 to remove and 61 not upgraded.
2 not fully installed or removed.
Need to get 0 B/133 kB of archives.
After this operation, 692 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Global symbol "$bundling" requires explicit package name at /usr/share/perl/5.14/Getopt/Long.pm line 77.
Global symbol "$bundling" requires explicit package name at /usr/share/perl/5.14/Getopt/Long.p line 84.
BEGIN not safe after errors--compilation aborted at /usr/share/perl/5.14/Getopt/Long.pm line 208.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 173.
dpkg: error: parsing file '/var/lib/dpkg/status' near line 5912 package 'libboost-iostreams1.46.1':
 'Depends' field, reference to 'zlib1g': error in version: epoch in version is not number
E: Sub-process /usr/bin/dpkg returned an error code (2)

```


and if I try running `dpkg --configure -a` I get: 


```

dpkg --configure -a
Setting up gconf2 (3.2.5-0ubuntu2) ...
XXX lineno: 400, opcode: 0
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 68, in <module>
    import os
  File "/usr/lib/python2.7/os.py", line 49, in <module>
    import posixpath as path
  File "/usr/lib/python2.7/posixpath.py", line 17, in <module>
    import warnings
  File "/usr/lib/python2.7/warnings.py", line 400, in <module>
    del _warnings_defaults
SystemError: unknown opcode
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libcanberra-gtk-module:i386:
 libcanberra-gtk-module:i386 depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libcanberra-gtk-module:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 libcanberra-gtk-module:i386

```


I have no idea where to go from here and would greatly appreciate any help anyone has to offer.


Thanks!

---

### Post by ian-weisser on 2013-11-06
Look at the file /usr/share/perl/5.14/Getopt/Long.pm in a text editor (like gedit), NOT a word processor.
Lines 72-95 should look like below. Does yours look like that?

```
sub ConfigDefaults() {
    # Handle POSIX compliancy.
    if ( defined $ENV{"POSIXLY_CORRECT"} ) {
        $genprefix = "(--|-)";
        $autoabbrev = 0;                # no automatic abbrev of options
        $bundling = 0;                  # no bundling of single letter switches
        $getopt_compat = 0;             # disallow '+' to start options
        $order = $REQUIRE_ORDER;
    }
    else {
        $genprefix = "(--|-|\\+)";
        $autoabbrev = 1;                # automatic abbrev of options
        $bundling = 0;                  # bundling off by default
        $getopt_compat = 1;             # allow '+' to start options
    }
    # Other configurable settings.
    $debug = 0;                 # for debugging
    $error = 0;                 # error tally
    $ignorecase = 1;            # ignore case when matching options
    $passthrough = 0;           # leave unrecognized options alone
    $gnu_compat = 0;            # require --opt=val if value is optional
    $longprefix = "(--)";       # what does a long prefix look like
}

```

---

### Post by jasonlyle88 on 2013-11-06
It looks very close, with just one other variable being set in the else block: $order = $PERMUTE;

Full listing:
```
sub ConfigDefaults() {
    # Handle POSIX compliancy.
    if ( defined $ENV{"POSIXLY_CORRECT"} ) {
        $genprefix = "(--|-)";
        $autoabbrev = 0;                # no automatic abbrev of options
        $bundling = 0;                  # no bundling of single letter switches
        $getopt_compat = 0;             # disallow '+' to start options
        $order = $REQUIRE_ORDER;
    }
    else {
        $genprefix = "(--|-|\\+)";
        $autoabbrev = 1;                # automatic abbrev of options
        $bundling = 0;                  # bundling off by default
        $getopt_compat = 1;             # allow '+' to start options
        $order = $PERMUTE;
    }
    # Other configurable settings.
    $debug = 0;                 # for debugging
    $error = 0;                 # error tally
    $ignorecase = 1;            # ignore case when matching options
    $passthrough = 0;           # leave unrecognized options alone
    $gnu_compat = 0;            # require --opt=val if value is optional
    $longprefix = "(--)";       # what does a long prefix look like
}

```

---

### Post by ian-weisser on 2013-11-06
Okay, so you don't have a typo in the file.

What happens if you do an ordinary **sudo apt-get update && sudo apt-get upgrade** ?
Does the error occur for all package management actions, or just when attempting to install a specific package?

---

### Post by jasonlyle88 on 2013-11-07
apt-get update runs just fine.

apt-get upgrade won't let me move forward, same with apt-get install [package]:

```
apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 landscape-common : Depends: python-gnupginterface but it is not installed
 python-lazr.restfulclient : Depends: python-zope.interface but it is not installed
 python-software-properties : Depends: python-gnupginterface but it is not installed
 python-twisted-core : Depends: python-zope.interface (>= 3.5) but it is not installed
 update-manager-core : Depends: python-gnupginterface but it is not installed
E: Unmet dependencies. Try using -f.

```

I can try running apt-get upgrade -f

```
apt-get upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  python-gnupginterface python-zope.interface
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  apport apt apt-transport-https apt-utils dash dpkg-dev ffmpeg initramfs-tools initramfs-tools-bin
  libapache2-mod-php5 libapt-inst1.4 libav-tools libavcodec53 libavdevice53 libavfilter2 libavformat53 libavutil51
  libc-bin libc-dev-bin libc6 libc6:i386 libc6-dev libdbi-perl libdbus-1-3 libdpkg-perl libdrm-intel1
  libdrm-intel1:i386 libdrm-nouveau1a libdrm-nouveau1a:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
  libdvdread4 libedit2 libglib2.0-data liblockfile-bin liblockfile1 libmysqlclient18 libmysqlclient18:i386
  libpostproc52 libsdl1.2debian:i386 libswscale2 linux-firmware linux-libc-dev multiarch-support mysql-client-5.5
  mysql-client-core-5.5 mysql-server-5.5 mysql-server-core-5.5 php5 php5-cli php5-common php5-curl php5-gd php5-json
  php5-mcrypt php5-mysql php5-readline procps python-apport python-lazr.restfulclient python-minimal
  python-problem-report python-software-properties python-twisted-bin tzdata tzdata-java wpasupplicant
69 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 80.0 MB/80.1 MB of archives.
After this operation, 851 kB of additional disk space will be used.
Do you want to continue [Y/n]?

```

Should I try to continue with that?

---

### Post by ian-weisser on 2013-11-07
Any idea how you managed to install packages without the dependencies?

Try the following. If you hit an error message, stop. Post the sequence leading to the error.
```
sudo apt-get install python-gnupginterface
sudo apt-get install python-zope.interface
sudo apt-get update && sudo apt-get upgrade
```

If the third command tries to upgrade 80MB of packages, go ahead and let it try.
If all three commands complete without error, then your system should be fixed.

---

### Post by jasonlyle88 on 2013-11-08
It won't let me just install a single package:

```
apt-get install python-gnupginterface
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python-lazr.restfulclient : Depends: python-zope.interface but it is not going to be installed
 python-twisted-core : Depends: python-zope.interface (>= 3.5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Even if I specify the -f option

```
apt-get -f install python-gnupginterface
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python-lazr.restfulclient : Depends: python-zope.interface but it is not going to be installed
 python-twisted-core : Depends: python-zope.interface (>= 3.5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

The same thing happens if I try to do python-zope.interface before python-gnupginterface.

---

### Post by ian-weisser on 2013-11-08
Has the original $bundling error recurred at all?

Try:
```
sudo apt-get install python-gnupginterface python-zope.interface
```

---

### Post by jasonlyle88 on 2013-11-08
That allows me to install, but the install fails with an error:

```
apt-get install python-gnupginterface python-zope.interface
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  python-gnupginterface python-zope.interface
0 upgraded, 2 newly installed, 0 to remove and 72 not upgraded.
2 not fully installed or removed.
Need to get 0 B/133 kB of archives.
After this operation, 692 kB of additional disk space will be used.
dpkg: error: parsing file '/var/lib/dpkg/status' near line 4664 package 'libgdk-pixbuf2.0-0':
 `Breaks' field, reference to `libwmf0.2-7': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by ian-weisser on 2013-11-08
> **jasonlyle88 said:**
> dpkg: error: parsing file '/var/lib/dpkg/status' near line 4664 package 'libgdk-pixbuf2.0-0':
 `Breaks' field, reference to `libwmf0.2-7': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

This particular problem is explained (and fixed) at [http://askubuntu.com/questions/343616/dpkg-exit-with-error-parsing-file-var-lib-dpkg-status-what-to-do](http://askubuntu.com/questions/343616/dpkg-exit-with-error-parsing-file-var-lib-dpkg-status-what-to-do)
```
sudo rm /var/lib/dpkg/status
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
sudo apt-get update
sudo apt-get install python-gnupginterface python-zope.interface
sudo apt-get upgrade
```

As before, stop if you get an error message. Show us the sequence leading to the error.

---

### Post by jasonlyle88 on 2013-12-11
Sorry for the long absence, i never got a notification of the last post.  I tried what you said and when I tried to do the apt-get install python-gnupginterface python-zope.interface it told me that they were already at the latest version.  When I then tried to do the apt-get upgrade it went through and fetched everything and then gave me the following lines:

```
Fetched 82.8 MB in 25s (3,289 kB/s)
E: Tar checksum failed, archive corrupted
E: Prior errors apply to /var/cache/apt/archives/libc6_2.15-0ubuntu10.5_i386.deb
E: Prior errors apply to /var/cache/apt/archives/linux-libc-dev_3.2.0-57.87_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libapt-pkg4.12_0.8.16~exp12ubuntu10.16_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/apt_0.8.16~exp12ubuntu10.16_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libapt-inst1.4_0.8.16~exp12ubuntu10.16_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/liblockfile-bin_1.09-3ubuntu0.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/liblockfile1_1.09-3ubuntu0.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm2_2.4.43-0ubuntu0.0.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm2_2.4.43-0ubuntu0.0.3_i386.deb
EE Prior errors apply to /var/cache/apt/archives/libdrm-intel1_2.4.43-0ubuntu0.0.3_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-intel1_2.4.43-0ubuntu0.0.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-nouveau1a_2.4.43-0ubuntu0.0.3_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-nouveau1a_2.4.43-0ubuntu0.0.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-radeon1_2.4.43-0ubuntu0.0.3_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-radeon1_2.4.43-0ubuntu0.0.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libglib2.0-0_2.32.4-0ubuntu1_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libglib2.0-0_2.32.4-0ubuntu1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libcurl3-gnutls_7.22.0-3ubuntu4.5_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libedit2_2.11-20080614-6+debphp.org~precise+1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libav-tools_4%3a0.8.9-0ubuntu0.12.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libpostproc52_4%3a0.8.9-0ubuntu0.12.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libavfilter2_4%3a0.8.9-0ubuntu0.12.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libswscale2_4%3a0.8.9-0ubuntu0.12.04.1_amd64.deb
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 34%E: Syntax error /etc/apt/apt.conf.d/01autoremove-kernels:9: Malformed tag
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ...
debconf: warning: possible database corruption. Will attempt to repair by adding back missing question samba-common/workgroup.
samba-common template parse error: Template parse error near `Descripti n-sk.UTF-8: PouÅ¾iÅ¥ Å¡ifrovanie hesiel?', in stanza #5 of /tmp/samba-common.template.136472


dpkg: error: parsing file '/var/lib/dpkg/available' near line 14101 package 'groff-base':
 `Replaces' field, reference to `jgroff': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by ian-weisser on 2013-12-11
Hmm. 
That's real bad.
Last time I saw package status and list corruption like that was due to bad RAM.

Have you had any other symptoms? Freezes, crashes, unexpected logouts, failure to boot or resume from suspend? Or corrupted/damaged files?
Is your data backed up?

Try the followg commands once more and see if you get the same errors
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jasonlyle88 on 2013-12-11
I have not had any freezes, crashes or failed boots/resumes.  I've been logged out unexpectedly only over SSH and I figured that was due to some kind of problem with only half updated packages or whatever.  As for corrupted files/inaccessible, I haven't ran in to any that have not been related to my updating (see first upgrade attempt)

Update ran fine, but I got the following on upgrade:

```
apt-get upgrade
Reading package lists... Error!
E: Could not open file /var/lib/apt/lists/us.arclive.ubuntu.co%01_ubuntu_dists_precise_universe_binary-i386_Packages - open (2: No such file or directory)
E: Problem opening /var/lib/apt/lists/us.archive.ubuntu.co%01_ubuntu_dists_precise_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

I tried upgrade one more time out of curiosity and got back to this:

```
apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  accountsservice apport apt apt-transport-https apt-utils curl dpkg dpkg-dev ffmpeg initramfs-tools initramfs-tools-bin landscape-common libaccountsservice0 libapache2-mod-php5 libapt-inst1.4
  libapt-pkg4.12 libav-tools libavcodec53 libavdevice53 libavfilter2 libavformat53 libavutil51 libc-bin libc-dev-bin libc6 libc6:i386 libc6-dev libcurl3 libcurl3:i386 libcurl3-gnutls libdpkg-perl
  libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau1a libdrm-nouveau1a:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libdvdread4 libedit2 libglib2.0-0 libglib2.0-0:i386 libglib2.0-data
  liblockfile-bin liblockfile1 libmysqlclient18 libmysqlclient18:i386 libnss3 libnss3:i386 libnss3-1d libpixman-1-0 libpixman-1-0:i386 libpostproc52 libsmbclient libswscale2 libwbclient0
  linux-firmware linux-libc-dev multiarch-support mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5 php5 php5-cli php5-common php5-curl php5-gd
  php5-json php5-mcrypt php5-mysql php5-readline procps python-apport python-lazr.restfulclient python-problem-report python-software-properties rsyslog samba-common samba-common-bin tzdata
  tzdata-java unzip wpasupplicant
87 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/97.3 MB of archives.
After this operation, 201 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Tar checksum failed, archive corrupted
E: Prior errors apply to /var/cache/apt/archives/libc6_2.15-0ubuntu10.5_i386.deb
E: Prior errors apply to /var/cache/apt/archives/linux-libc-dev_3.2.0-57.87_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libapt-pkg4.12_0.8.16~exp12ubuntu10.16_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/apt_0.8.16~exp12ubuntu10.16_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libapt-inst1.4_0.8.16~exp12ubuntu10.16_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/liblockfile-bin_1.09-3ubuntu0.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/liblockfile1_1.09-3ubuntu0.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm2_2.4.43-0ubuntu0.0.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm2_2.4.43-0ubuntu0.0.3_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-intel1_2.4.43-0ubuntu0.0.3_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-intel1_2.4.43-0ubuntu0.0.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-nouveau1a_2.4.43-0ubuntu0.0.3_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-nouveau1a_2.4.43-0ubuntu0.0.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-radeon1_2.4.43-0ubuntu0.0.3_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libdrm-radeon1_2.4.43-0ubuntu0.0.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libglib2.0-0_2.32.4-0ubuntu1_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libglib2.0-0_2.32.4-0ubuntu1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libcurl3-gnutls_7.22.0-3ubuntu4.5_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libedit2_2.11-20080614-6+debphp.org~precise+1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libav-tools_4%3a0.8.9-0ubuntu0.12.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libpostproc52_4%3a0.8.9-0ubuntu0.12.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libavfilter2_4%3a0.8.9-0ubuntu0.12.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libswscale2_4%3a0.8.9-0ubuntu0.12.04.1_amd64.deb
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 34%E: Tar checksum failed, archive corrupted
E: Prior errors apply to /var/cache/apt/archives/php5-json_1.3.2-3+debphp.org~precise+1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libsmbclient_2%3a3.6.3-2ubuntu2.9_amd64.deb
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ...
samba-common template parse error: Template parse error near `Descripton-id.UTF-8: Nama Domain/Workgrop:', in stanza #4 of /tmp/samba-common.template.140412


dpkg: error: parsing file '/var/lib/dpkg/status' near line 20271 package 'qdbus':
 `Depends' field, reference to `libstdc++6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by jfolsom2 on 2013-12-11
So, when I look at your error messages, the first thing that sticks out, I have never seen/noticed before.  The strings in your error message appear to be incorrect.

```

E: Could not open file /var/lib/apt/lists/us.arclive.ubuntu.co%01_ubuntu_dists_precise_universe_binary-i386_Packages - open (2: No such file or directory)

```

First of all, us.arclive.ubuntu.co.......   is misspelled. Is it misspelled in your /etc/apt/sources.list or sources.d/*?
Second, the "%" character doesn't appear in any of my packages, nor is it used to truncate any of my updates/upgrades. I don't think this is normal.

Perhaps that will give you a place to start.

Good Luck.
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by ian-weisser on 2013-12-11
> **jasonlyle88 said:**
> 
```
apt-get upgrade
Reading package lists... Error!
E: Could not open file /var/lib/apt/lists/us.arclive.ubuntu.co%01_ubuntu_dists_precise_universe_binary-i386_Packages - open (2: No such file or directory)
E: Problem opening /var/lib/apt/lists/us.archive.ubuntu.co%01_ubuntu_dists_precise_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
...
Do you want to continue [Y/n]? Y
E: Tar checksum failed, archive corrupted
E: Prior errors apply to /var/cache/apt/archives/libc6_2.15-0ubuntu10.5_i386.deb
E: Prior errors apply to /var/cache/apt/archives/linux-libc-dev_3.2.0-57.87_amd64.deb
...
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 34%E: Tar checksum failed, archive corrupted
E: Prior errors apply to /var/cache/apt/archives/php5-json_1.3.2-3+debphp.org~precise+1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libsmbclient_2%3a3.6.3-2ubuntu2.9_amd64.deb
...
debconf: apt-extracttemplates failed: No such file or directory
...
Preconfiguring packages ...
samba-common template parse error: Template parse error near `Descripton-id.UTF-8: Nama Domain/Workgrop:', in stanza #4 of /tmp/samba-common.template.140412
...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 20271 package 'qdbus':
 `Depends' field, reference to `libstdc++6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

There seem to be a few issues here. Both filename and contents are corrupted. And it seems to be getting worse.
How much time are you willing to invest fixing these?
If you don't have a backup of all your data, do so right away.
I don't see an easy fix. A reinstall may the fastest way to get you running effectively again.
We can try to fix it file-by-file. That may take significant effort.

I don't see an obvious cause to corruption in both filenames and file contents that would be limited to only the package manager. There might be one, but I don't know it.

When I have seen corruption like this before (happily only twice), it was in hardware and slowly corrupted everything in the system. I'm not saying that's your problem - I'm saying we don't know what your problem is. We're only seeing the symptoms.

Before reinstalling, I recommend running diagnostics to check your ram (memtest) and hard drive (smartmontools).

---

