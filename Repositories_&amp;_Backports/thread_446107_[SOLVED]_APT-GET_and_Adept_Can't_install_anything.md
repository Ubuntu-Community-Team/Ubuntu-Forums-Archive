---
title: "[SOLVED] APT-GET and Adept: Can't install anything"
date: 2007-05-16
forum: Repositories &amp; Backports
---

### Post by trumpeteersman on 2007-05-16
NOTE: This is NOT a problem with the sources.list file.

I had this same exact problem for about 6 months now and I can't install anything(short of command line).  And even then, I can't install packages, and source installs(command line) only work if the software has very few dependencies that I need to install.
I posted about my problem a while ago and nobody answered... :confused: 

This is my original post:
[http://ubuntuforums.org/showthread.php?t=299790]("http://ubuntuforums.org/showthread.php?t=299790")

I still have the same problem:

```

The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 144 not upgraded.
Need to get 0B/8785kB of archives.
After unpacking 41.4MB of additional disk space will be used.
(Reading database ...
dpkg: serious warning: files list file for package `java-common' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/wine_0.9.9-0ubuntu2_i386.deb (--unpack):
 unable to open files list file for package `jfsutils': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/wine_0.9.9-0ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I found a possible solution to my problem if the problem were netbase instead of jfsutils and java-common:
[http://ubuntuforums.org/showthread.php?t=160126]("http://ubuntuforums.org/showthread.php?t=160126")
But I am not sure and there is no way to test it being that netbase is not the problem....

I hope I am not ignored yet again...

Thanks in advance and THANK YOU for even reading my problem.

---

### Post by gitfiddler on 2007-05-16
Trumpeteersman,

I'm sorry if you feel ignored. This community has been so helpful, I can only surmise that your problem is unusual or unique. Doesn't that make you feel special?!?

Seriously, in your first post you said "I cannot upgrade, install, or remove any package at all, it gives me the same error in adept and apt-get:", but you don't mention "update". What kind of error do you get when you try that.

Further questions:
1 - What version of Ubuntu are you using?
2 -  Do you have Automatix installed (or have you ever had it installed in the past)?
3 - Have you EVER been able to install packages, and if so, what might have been installed before this problem began?

I'm not a super geek, but I have Ubuntu installed on several machines, have been using them for almost 2 years. I'll do my best to help.

---

### Post by trumpeteersman on 2007-05-16
AWESOME!! Thanks for the reply!  I Really do believe that the Ubuntu community is excellent.  I think what happened is that because I replied to myself, the forums thought that I solved my problem.

Update works fine.

```

$ sudo apt-get update
Password:
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:4 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:6 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:7 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:8 http://archive.canonical.com dapper-commercial Release [4886B]
Hit http://security.ubuntu.com dapper-security Release
Get:9 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:10 http://us.archive.ubuntu.com dapper-backports Release.gpg [191B]$ sudo apt-get update
Password:
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:4 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:6 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:7 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:8 http://archive.canonical.com dapper-commercial Release [4886B]
Hit http://security.ubuntu.com dapper-security Release
Get:9 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:10 http://us.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper Release
Get:11 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper/multiverse Sources
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/universe Packages
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Sources
Hit http://us.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/universe Sources
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 5086B in 2s (2048B/s)
Reading package lists... Done

Hit http://us.archive.ubuntu.com dapper Release
Get:11 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper/multiverse Sources
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/universe Packages
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Sources
Hit http://us.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/universe Sources
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 5086B in 2s (2048B/s)
Reading package lists... Done


```

And as you can see, I do currently have automatix installed(extremely helpful).  I think my original problem was because Skype locked up my computer and I had to do a hard reset.  Ext3 and hard resets are evil.  The result was some corrupt files. I happened to be gleefully installing some stuff through Adept, so the files lists got hammered and I have not been able to fix it.  

I run Kubuntu 6.06 and running kernel version 2.6.15-27-386

I have a feeling that if I can just fix the files list for java-common and jfsutils, my problem would just go away.

Aside:You know, my Kubuntu reminds me of my old Toyota pickup.  Even with a bent axil, messed up side, broken gear box, and a giant exhaust leak, it still runs excellently no matter what. (and even passes smog)

---

### Post by gitfiddler on 2007-05-16
OK, I'm at work now. I'll be in front of my Ubuntu box in a few hours, I'll get a look at those files then. Sit tight.
In the meantime, maybe someone else will notice the activity of these posts and offer a suggestion.

---

### Post by kelvin spratt on 2007-05-16
i had this problem today downloadig Java 6 so went into synpatic manager pressed custom filters,
in the left hand pane BROKEN PACKAGES clicked on removed the package back to normal, nowt to do with automatix i use it all the time, its a purist thing like doing every thing from the command line, I have to find ways around as much as i can i did the same with DOS most things have a simple answer if you look hard enough

---

### Post by trumpeteersman on 2007-05-16
I use Kubuntu's package manager called Adept (Similar to Synaptic).  I can get into Adept, however any changes I make while in there results in the same error as above.  Whether it be install, remove, reinstall, or purge.  Thanks for the reply though.

---

### Post by gitfiddler on 2007-05-16
I don't find "jfsutils" on my system. java-common.list definitely should not be blank. What about java-common.md5sums? Does it look like it may have been corrupted? java-common.conffiles has just one line...
/etc/jvm

Do you think it would help if I PM'd you those files?

Other than that, I'm afraid I just don't know. Sorry.

---

### Post by trumpeteersman on 2007-05-16
```

$ locate java-common
/var/cache/apt/archives/java-common_0.24ubuntu2_all.deb
/var/lib/dpkg/info/java-common.prerm
/var/lib/dpkg/info/openoffice.org-java-common.list
/var/lib/dpkg/info/openoffice.org-java-common.md5sums
/var/lib/dpkg/info/openoffice.org-java-common.postinst
/usr/share/doc/java-common
/usr/share/doc/java-common/debian-java-faq
/usr/share/doc/java-common/debian-java-faq/.dhelp
/usr/share/doc/java-common/debian-java-faq/apA.html
/usr/share/doc/java-common/debian-java-faq/ch-browser-java.html
/usr/share/doc/java-common/debian-java-faq/ch-debian-java-sarge.html
/usr/share/doc/java-common/debian-java-faq/ch-debian-java-woody.html
/usr/share/doc/java-common/debian-java-faq/ch1.html
/usr/share/doc/java-common/debian-java-faq/ch10.html
/usr/share/doc/java-common/debian-java-faq/ch11.html
/usr/share/doc/java-common/debian-java-faq/ch2.html
/usr/share/doc/java-common/debian-java-faq/ch5.html
/usr/share/doc/java-common/debian-java-faq/ch6.html
/usr/share/doc/java-common/debian-java-faq/ch7.html
/usr/share/doc/java-common/debian-java-faq/ch9.html
/usr/share/doc/java-common/debian-java-faq/footnotes.html
/usr/share/doc/java-common/debian-java-faq/index.html
/usr/share/doc/java-common/debian-java-policy
/usr/share/doc/java-common/debian-java-policy/.dhelp
/usr/share/doc/java-common/debian-java-policy/c149.html
/usr/share/doc/java-common/debian-java-policy/c173.html
/usr/share/doc/java-common/debian-java-policy/c28.html
/usr/share/doc/java-common/debian-java-policy/c36.html
/usr/share/doc/java-common/debian-java-policy/index.html
/usr/share/doc/java-common/debian-java-policy/x105.html
/usr/share/doc/java-common/debian-java-policy/x138.html
/usr/share/doc/java-common/debian-java-policy/x73.html
/usr/share/doc/java-common/debian-java-policy/x86.html
/usr/share/doc/java-common/dummy-packages
/usr/share/doc/java-common/dummy-packages/README
/usr/share/doc/java-common/dummy-packages/java-compiler-dummy.control
/usr/share/doc/java-common/dummy-packages/java-virtual-machine-dummy.control
/usr/share/doc/java-common/dummy-packages/java1-runtime-dummy.control
/usr/share/doc/java-common/dummy-packages/java2-compiler-dummy.control
/usr/share/doc/java-common/dummy-packages/java2-runtime-dummy.control
/usr/share/doc/java-common/examples
/usr/share/doc/java-common/examples/classpath-from-jars-1
/usr/share/doc/java-common/html
/usr/share/doc/java-common/README.Debian
/usr/share/doc/java-common/changelog.gz
/usr/share/doc/java-common/copyright
/usr/share/doc/java-common/policy.ps.gz
/usr/share/doc/java-common/policy.txt.gz
/usr/share/doc/java-common/policy.xml.gz
/usr/share/doc/openoffice.org-java-common
/usr/share/java-common
/usr/share/java-common/java-common.sh
/usr/share/java-common/jvm-find.sh

```

I can't seem to find the non-OOo java-common .list and .md5sum files.  Where are they supposed to be?

---

### Post by trumpeteersman on 2007-05-16
I think I found where those files are supposed to be and I also found a java-common.prerm:

```

/var/lib/dpkg/info$ ls | grep java
backupjavacommon
java-common.prerm
java-gcj-compat.conffiles
java-gcj-compat-dev.list
java-gcj-compat-dev.md5sums
java-gcj-compat-dev.postinst
java-gcj-compat-dev.prerm
java-gcj-compat.list
java-gcj-compat.md5sums
java-gcj-compat.postinst
java-gcj-compat.prerm
kdebindings-java.list
libbcprov-java.list
libbcprov-java.md5sums
libcairo-java.list
libcairo-java.md5sums
libcairo-java.postinst
libcairo-java.postrm
libcairo-java.shlibs
libcommons-cli-java.list
libcommons-cli-java.md5sums
libdcop3-java.list
libdcop3-java.md5sums
libglib-java.list
libglib-java.md5sums
libglib-java.postinst
libglib-java.postrm
libglib-java.shlibs
libgnucrypto-java.list
libgnucrypto-java.md5sums
libgtk-java.list
libgtk-java.md5sums
libhsqldb-java.list
libhsqldb-java.md5sums
libhsqldb-java.postinst
libhsqldb-java.postrm
libjaxp1.2-java.list
libjaxp1.2-java.md5sums
libjessie-java.list
libjessie-java.md5sums
libjline-java.list
libjline-java.md5sums
libkde3-java.list
libkde3-java.md5sums
liblog4j1.2-java.list
liblog4j1.2-java.md5sums
libqt3-java.list
libqt3-java.md5sums
libseda-java.list
libseda-java.md5sums
libservlet2.3-java.list
libservlet2.3-java.md5sums
libswt3.1-gtk-java.list
libswt3.1-gtk-java.md5sums
libxalan2-java.list
libxalan2-java.md5sums
libxerces2-java.list
libxerces2-java.md5sums
libxt-java.list
libxt-java.md5sums
openoffice.org-java-common.list
openoffice.org-java-common.md5sums
openoffice.org-java-common.postinst

```

---

### Post by trumpeteersman on 2007-05-16
Is there a was for me to recreate those missing files?  What do you mean by PM'd?  Since they look to be plain text files, Could I just run "touch" to create the needed files and write the necessary info in them?  If so, could you post the info I need for those files?

---

### Post by gitfiddler on 2007-05-17
Here's the contents of my java-common.list:

/.
/usr
/usr/share
/usr/share/java
/usr/share/java-common
/usr/share/java-common/java-common.sh
/usr/share/java-common/jvm-find.sh
/usr/share/doc
/usr/share/doc/java-common
/usr/share/doc/java-common/README.Debian
/usr/share/doc/java-common/copyright
/usr/share/doc/java-common/policy.ps.gz
/usr/share/doc/java-common/changelog.gz
/usr/share/doc/java-common/debian-java-policy
/usr/share/doc/java-common/debian-java-policy/index.html
/usr/share/doc/java-common/debian-java-policy/c28.html
/usr/share/doc/java-common/debian-java-policy/c36.html
/usr/share/doc/java-common/debian-java-policy/x73.html
/usr/share/doc/java-common/debian-java-policy/x86.html
/usr/share/doc/java-common/debian-java-policy/x105.html
/usr/share/doc/java-common/debian-java-policy/x138.html
/usr/share/doc/java-common/debian-java-policy/c149.html
/usr/share/doc/java-common/debian-java-policy/c173.html
/usr/share/doc/java-common/debian-java-faq
/usr/share/doc/java-common/debian-java-faq/apA.html
/usr/share/doc/java-common/debian-java-faq/ch-browser-java.html
/usr/share/doc/java-common/debian-java-faq/ch-debian-java-sarge.html
/usr/share/doc/java-common/debian-java-faq/ch-debian-java-woody.html
/usr/share/doc/java-common/debian-java-faq/ch1.html
/usr/share/doc/java-common/debian-java-faq/ch10.html
/usr/share/doc/java-common/debian-java-faq/ch11.html
/usr/share/doc/java-common/debian-java-faq/ch2.html
/usr/share/doc/java-common/debian-java-faq/ch5.html
/usr/share/doc/java-common/debian-java-faq/ch6.html
/usr/share/doc/java-common/debian-java-faq/ch7.html
/usr/share/doc/java-common/debian-java-faq/ch9.html
/usr/share/doc/java-common/debian-java-faq/footnotes.html
/usr/share/doc/java-common/debian-java-faq/index.html
/usr/share/doc/java-common/dummy-packages
/usr/share/doc/java-common/dummy-packages/README
/usr/share/doc/java-common/dummy-packages/java-compiler-dummy.control
/usr/share/doc/java-common/dummy-packages/java-virtual-machine-dummy.control
/usr/share/doc/java-common/dummy-packages/java1-runtime-dummy.control
/usr/share/doc/java-common/dummy-packages/java2-compiler-dummy.control
/usr/share/doc/java-common/dummy-packages/java2-runtime-dummy.control
/usr/share/doc/java-common/examples
/usr/share/doc/java-common/examples/classpath-from-jars-1
/usr/share/doc/java-common/policy.txt.gz
/usr/share/doc/java-common/policy.xml.gz
/usr/share/doc-base
/usr/share/doc-base/java-policy
/usr/share/doc-base/debian-java-faq
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/update-java-alternatives.8.gz
/usr/sbin
/usr/sbin/update-java-alternatives
/etc
/etc/jvm.d
/etc/jvm
/usr/share/doc/java-common/html

jfsutils.list looks like this:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/jfsutils
/usr/share/doc/jfsutils/README
/usr/share/doc/jfsutils/AUTHORS
/usr/share/doc/jfsutils/README.Debian
/usr/share/doc/jfsutils/copyright
/usr/share/doc/jfsutils/changelog.gz
/usr/share/doc/jfsutils/NEWS.gz
/usr/share/doc/jfsutils/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/jfs_fsck.8.gz
/usr/share/man/man8/jfs_fscklog.8.gz
/usr/share/man/man8/jfs_logdump.8.gz
/usr/share/man/man8/jfs_mkfs.8.gz
/usr/share/man/man8/jfs_tune.8.gz
/usr/share/man/man8/mkfs.jfs.8.gz
/usr/share/man/man8/fsck.jfs.8.gz
/usr/share/man/man8/jfs_debugfs.8.gz
/sbin
/sbin/jfs_fsck
/sbin/fsck.jfs
/sbin/jfs_fscklog
/sbin/jfs_logdump
/sbin/jfs_mkfs
/sbin/mkfs.jfs
/sbin/jfs_tune
/sbin/jfs_debugfs

...and jfsutils.md5sums looks like this:

8e2d84235a894b479fb77b0c72da5d3d  usr/share/doc/jfsutils/README
5ca7cb02a9d8836222ac428cdb25be10  usr/share/doc/jfsutils/AUTHORS
ad22a5f4cfec52ed2c181fb64d5469ae  usr/share/doc/jfsutils/README.Debian
a197cba657c8e1abc3eabbe10413fa44  usr/share/doc/jfsutils/copyright
cecbd3030adeaf4d9ebdad1094080a96  usr/share/doc/jfsutils/changelog.gz
adbbb06f21c784a0228634e56f1b569c  usr/share/doc/jfsutils/NEWS.gz
05af7c7098c36c26448615b51b1cc772  usr/share/doc/jfsutils/changelog.Debian.gz
68dbcb56a3be3bea7a311610193fd523  usr/share/man/man8/jfs_fsck.8.gz
cd99dd1ac0570f853d7d668d3390c63a  usr/share/man/man8/jfs_fscklog.8.gz
78f5c18760980b2101e566ae2c609513  usr/share/man/man8/jfs_logdump.8.gz
e3d53b0f67b0a799de9b0dc56754885a  usr/share/man/man8/jfs_mkfs.8.gz
8e0ed54d30d18ebc152a8dfd0b6b0a07  usr/share/man/man8/jfs_tune.8.gz
9d7e89295b62556cbe2b3e7a43029c6c  usr/share/man/man8/mkfs.jfs.8.gz
e97ab6f34726d8ac9ec3edecfe3d93c8  usr/share/man/man8/fsck.jfs.8.gz
84576732bcac026853910134439f9134  usr/share/man/man8/jfs_debugfs.8.gz
5d7dd523ead964bae6d510f8829284e6  sbin/jfs_fsck
5d7dd523ead964bae6d510f8829284e6  sbin/fsck.jfs
e538849b50cc08f1c9760fb986589993  sbin/jfs_fscklog
701deeeee318868b72260b575e4c75ef  sbin/jfs_logdump
d7599660c616144f6b0cd6b9ca9efabb  sbin/jfs_mkfs
d7599660c616144f6b0cd6b9ca9efabb  sbin/mkfs.jfs
fac9f7c1108110acb5ceb7d424efac1e  sbin/jfs_tune
cce5cd807322e19ef0fe573767c48e39  sbin/jfs_debugfs

and PM means "Private Message", like a personal email.

We've got to get this fixed, because the alternative is to reinstall, and that's just not the 'buntu way!

---

### Post by trumpeteersman on 2007-05-17
This is awesome, I think our idea is working, although it looks like I need the kaffeine.list and kaddressbook.list.  The Java-common.list and jfsutils.list error are gone.  I did not get the kaffeine and kaddressbook error before, must be because it stops at the first errors.  It looks like it could be in alphabetical order so letters we could possible have left: KLMNOPQRSTUVWXYZ

It looks like I found the error: the permissions, ownership, and group settings on the files are all messed up.

```

& ls -l | grep 1969
brw-r--r-- 1 root       root       102, 192 1969-07-26 11:34 java-common.prerm
brwx--S-wT 1 1757609776 4281362370 104, 194 1969-07-27 05:51 java-gcj-compat.conffiles
b-ws----w- 1 1774452528 4281428163 104, 195 1969-07-27 05:55 java-gcj-compat.list
brws----wx 1 1774518065 4281428419 105, 195 1969-07-28 00:12 java-gcj-compat.md5sums
brws---r-- 1 1791360817 4281493956 105, 196 1969-07-28 00:12 java-gcj-compat.postinst
b-ws---r-t 1 1791360818 4281494213 106, 197 1969-07-28 18:28 java-gcj-compat.prerm
b-ws---r-t 1 1808203570 4281494214 107, 198 1969-07-28 18:28 jfsutils.list.corrupt
brws---rwT 1 1808269106 4281560006 107, 198 1969-07-28 18:32 jfsutils.md5sums
b-ws--s-wT 1 1858797364 4281626314 110, 202 1969-07-30 07:10 kaddressbook.list
b-ws--s-wT 1 1875640116 4281691850 110, 203 1969-07-30 07:10 kaddressbook.md5sums
brws--s-wt 1 1875705653 4281692107 111, 203 1969-07-31 01:26 kaddressbook.postinst
brws--sr-T 1 1892482869 4281692108 111, 204 1969-07-31 01:26 kaddressbook.postrm
-rw-r--r-- 1 root       root          19694 2006-08-05 17:05 openoffice.org-l10n-en-za.list

```

Instead of deleting the corrupt jfsutils.list file, I appended .corrupt to it. I did the search on 1969 because I saw that common string in the messed up files dates.  So it looks like I need the above files.  And hopefully they are the only ones left.

---

### Post by heimo on 2007-05-17
There was similar problem in another thread day or couple ago. There the problem was solved by booting from Live-CD and running fsck.ext3 on the partition that contains /var. Not saying that this is the same problem, but something to keep in mind and try if other tricks eventually fail. My usual approach to similar problems is to move /var/lib/dpkg/info/[package].* files away, then using apt-get or aptitude --purge remove package that has these problems and then reinstall it - that also installs these list/preinst/postinst/md5sums files.

Edit: Link to the thread:
[http://ubuntuforums.org/showthread.php?t=440890](http://ubuntuforums.org/showthread.php?t=440890)

---

### Post by trumpeteersman on 2007-05-17
I think that I only need the .list files.  The md5sums are for checking purposes only and re downloaded when the package is updated right?  I am not sure about the conffiles, postinst, or the prerm files though...

---

### Post by heimo on 2007-05-17
> **trumpeteersman said:**
> I think that I only need the .list files.  The md5sums are for checking purposes only and re downloaded when the package is updated right?  I am not sure about the conffiles, postinst, or the prerm files though...

Perhaps. :) I don't know - I'm just adding here what I know so that if the way you're now fixing it fails, you (or someone else reading this and having same problem) have some ideas what to try.

---

### Post by trumpeteersman on 2007-05-17
I think I did run a fsck-ext3 a while back.  From a SuSE 9.3 disk I think.  Although, I can't remember what that did. As for purging after removing the corrupt files in the ~dpkg/info/ directory,  I think I tried that with java-common which is why there was not a java-common.list file in that directory, corrupt or otherwise.  Well, if this does not work, I will try that again.  The fsck option is my last being that I have had VERY bad experience with fsck on ext3.  Thanks for the input.

---

### Post by gitfiddler on 2007-05-17
I'm afraid I won't be much help with the "k" files, as I'm running Ubuntu, not Kubuntu.

Examining the live CD might not be a bad idea, though.

---

### Post by trumpeteersman on 2007-05-17
I don't know why I did not think of that before...
I will try that in about 3 hours as I have class...

---

### Post by trumpeteersman on 2007-05-17
Just one problem... The Kubuntu live disk does not have the files I need.  Since SuSE uses KDE, I will try the 10.1 disk, hopefully that has it.

---

### Post by trumpeteersman on 2007-05-17
I can't seem to mount the image on the SuSE 10.1 disk.
```

$ sudo mount -t iso9660 -o loop,user cloop.img /home/****/Desktop/suse/

```

It says wrong fs type. Is there a way to find the image type so I can mount it?

---

### Post by trumpeteersman on 2007-05-17
Or maybe someone could point me toward the .list files are on the net.  Like where Ubuntu goes to get the files for installation. FTP?  I am alright with the command line, however, someone looking for help and came to this post might not be so comfortable with the command line...

---

### Post by trumpeteersman on 2007-05-18
!!!!!!FIXED!!!!!!!!

This is for those who have similar problems and need a fix:
Note: When you come from Windows, try not to be [RESET] button happy, else you may get my problem.  [RESET] and reinstall every 6 months is how you fix Windows, not Linux.

I found where I can get the contents of those .list files:
[http://packages.debian.org/stable/allpackages]("http://packages.debian.org/stable/allpackages")

Since these are KDE packages and Debian(Ubuntu's Daddy), they should be the same as Kubuntu.
Search for the packages with the messed up .list files in the above link then scrolled down to where it says:

```

Download PACKAGENAME
Download for all available architectures Architecture	Files	Package Size	Installed Size

```
 and selected the architecture of my proc(which is i386).

To find out what architecture you are running, run the command:  "uname -r"

For my specific example, I needed i"java-gcj-compat": [http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=java-gcj-compat&version=stable&arch=i386]("http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=java-gcj-compat&version=stable&arch=i386")

Copy that list of files to a temp file and edit out all of the links "interpreters/java-gcj-compat" (from my example, will change depending on package) and also edit out all of the spaces and tabs for good measure(To make this process faster, use CTRL-R{replace} if using Kate or something similar). Make sure there is no empty newlines at the bottom or top also, else the package manager will yell at you with:
```

files list file for package `PACKAGENAME' contains empty filename
Errors were encountered while processing:
 PACKAGENAME

```

Using the command line, I want to move the old corrupt .list file to a .corrupt extention so I have it if I ever needed it again. And also create a new file with the exact same name as the old corrupt one(In my case it was "java-gcj-compat.list" or "kaffeine.list" or "kaddressbook.list"):

```

cd /var/lib/dpkg/info
sudo mv PACKAGE_NAME.list PACKAGE_NAME.list.corrupt 
sudo nano PACKAGE_NAME.list

```

Copy and past the edited list and add a "/." at the top (all other .list files do this)
Then CTRL-X, 'Y', and ENTER.

Repeat for multiple packages if necessary.


YAY!!!, I can gleefully and ignorantly install butt loads of random software again!  o_O

---

