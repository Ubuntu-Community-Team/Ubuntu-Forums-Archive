---
title: "Can't install APC on Ubuntu Server 10.04"
date: 2010-08-03
forum: Server Platforms
---

### Post by HittingSmoke on 2010-08-03
I'm trying to install Alternative PHP Cache on my web server and am running into an error with pecl.

```
checking whether apc needs to get compiler flags from apxs...

Sorry, I was not able to successfully run APXS.  Possible reasons:

1.  Perl is not installed;
2.  Apache was not compiled with DSO support (--enable-module=so);
3.  'apxs' is not in your path.  Try to use --with-apxs=/path/to/apxs
The output of /var/tmp/pear-build-root/APC-3.0.19/y follows
/tmp/pear/temp/APC/configure: line 4113: /var/tmp/pear-build-root/APC-3.0.19/y: No such file or directory
configure: error: Aborting
ERROR: `/tmp/pear/temp/APC/configure --with-apxs=y' failed

```

I have apache2-threaded-dev installed but don't know where to go from here. Apache was installed using LAMP during the OS install.

The full output when trying to install it is:

```
chris@webserver:~$ sudo pecl install apc
[sudo] password for chris:
downloading APC-3.0.19.tgz ...
Starting to download APC-3.0.19.tgz (115,735 bytes)
......................done: 115,735 bytes
47 source files, building
running: phpize
Configuring for:
PHP Api Version:         20090626
Zend Module Api No:      20090626
Zend Extension Api No:   220090626
Use apxs to set compile flags (if using APC with Apache)? [yes] : y
building in /var/tmp/pear-build-root/APC-3.0.19
running: /tmp/pear/temp/APC/configure --with-apxs=y
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20090626+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking whether apc needs to get compiler flags from apxs...

Sorry, I was not able to successfully run APXS.  Possible reasons:

1.  Perl is not installed;
2.  Apache was not compiled with DSO support (--enable-module=so);
3.  'apxs' is not in your path.  Try to use --with-apxs=/path/to/apxs
The output of /var/tmp/pear-build-root/APC-3.0.19/y follows
/tmp/pear/temp/APC/configure: line 4113: /var/tmp/pear-build-root/APC-3.0.19/y: No such file or directory
configure: error: Aborting
ERROR: `/tmp/pear/temp/APC/configure --with-apxs=y' failed
chris@webserver:~$ checking whether apc needs to get compiler flags from apxs...
Sorry, I was not able to successfully run APXS.  Possible reasons:

1.  Perl is not installed;
2.  Apache was not compiled with DSO support (--enable-module=so);
3.  'apxs' is not in your path.  Try to use --with-apxs=/path/to/apxs
The output of /var/tmp/pear-build-root/APC-3.0.19/y follows
/tmp/pear/temp/APC/configure: line 4113: /var/tmp/pear-build-root/APC-3.0.19/y: No such file or directory
configure: error: Aborting
ERROR: `/tmp/pear/temp/APC/configure --with-apxs=y' failed
No command 'checking' found, did you mean:
 Command 'checkint' from package 'netdiag' (universe)
checking: command not found

```

Anyone have any ideas? There doesn't seem to be a lot of perl related guides around for Debain based systems. The ones I've found are for much older versions and aren't helping.

---

### Post by JPorter on 2010-08-05
APC is packaged on Ubuntu 10.04, have you tried the packaged PHP module version?

Package: [FONT="Courier New"][php-apc]("apt:php-apc")[/FONT]
Current Version: 3.1.3p1-2
Dependencies: [FONT="Courier New"]libc6 phpapi-20090626+lfs[/FONT]
Suggests: [FONT="Courier New"]php5-gd[/FONT]

---

### Post by HittingSmoke on 2010-08-05
> **JPorter said:**
> APC is packaged on Ubuntu 10.04, have you tried the packaged PHP module version?

Package: [FONT="Courier New"][php-apc]("apt:php-apc")[/FONT]
Current Version: 3.1.3p1-2
Dependencies: [FONT="Courier New"]libc6 phpapi-20090626+lfs[/FONT]
Suggests: [FONT="Courier New"]php5-gd[/FONT]

Thank you! Worked great.

---

### Post by JPorter on 2010-08-06
No problem!  

A good rule of thumb is to always check for packaged versions of software in Synaptic before you try to download and compile anything.  Generally speaking, if any significant number of people use a particular piece of software on a regular basis, it's almost certainly going to be available pre-packaged, either through the primary Ubuntu repositories (main, universe, restricted, multiverse, partner) or through a PPA repo on Launchpad.

---

### Post by Sprintweb on 2010-08-13
I am getting: [I]Couldn't find package php-apc  :(

[/I]Any suggestions?
Using ubuntu server 10.04

---

### Post by bopomofo on 2010-08-14
Running a 10.04 server and it looks like apxs is actually:

/usr/bin/apsx2

---

### Post by JPorter on 2010-09-07
> **Sprintweb said:**
> I am getting: [I]Couldn't find package php-apc  :(

[/I]Any suggestions?
Using ubuntu server 10.04

It's in the "universe" repository. Make sure you have universe turned on in /etc/apt/sources.list and it should become available after you get updates.

---

