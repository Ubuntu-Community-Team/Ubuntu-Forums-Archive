---
title: "Webserver problem after upgrade to 11.10 ==&gt; sqlite2 missing"
date: 2011-10-16
forum: Server Platforms
---

### Post by Bram Snip on 2011-10-16
I upgraded from UBUBTU 11.04 to UBUNTU 11.10. 

After the update my webserver (apache,php5,sqlite2) no longer is functioning. sqlite2 seems to have dissapeared. sqlite3 is available but my code relies on sqlite2!

Phpinfo reports:
ext_dir: usr/lib/php5/20090626

this directory contains sqlite3.so but no sqlite.so or sqlite2.so.

My configuration file is located in /etx/php5/apache.

Any help would be greatly appreaciated!

---

### Post by BilboTav on 2011-10-16
Hi, I had a same problem - it is because the file sqlite.so (shared object library for sqlite2) is missing in a new .deb package (for 11.10 distribution) - don't know, if it is a bug or some sort of security issue.

It may not be 100% optimal solution, but here is, how I made it work:
Download an older .deb package for 11.04 distr. - [http://pkgs.org/ubuntu-11.04/ubuntu-main-amd64/php5-sqlite_5.3.5-1ubuntu7_amd64.deb.html](http://pkgs.org/ubuntu-11.04/ubuntu-main-amd64/php5-sqlite_5.3.5-1ubuntu7_amd64.deb.html) (choose the right package - if you have 64-bit or 32-bit system), then don't install it through package manager, but unpack it via ark - then you should get a data.tar.gz archive, where our file sqlite.so is located. Unpack it and then just copy it to a folder '/usr/lib/php5/20090626/'.
Then restart Apache and sqlite2 should be loaded properly.

GL! ;)

---

### Post by memilanuk on 2011-10-16
Not any kind of solution... but I am honestly curious as to why you'd be using sqlite2 instead of sqlite3 - I thought it was more or less the standard version for a few years now?

---

### Post by Bram Snip on 2011-10-17
Hello Bilbotav,

Thank you so much! I tried it and it works now. Initially i downloaded the i386 file since i have an Intel I5 processor but that did not work. Tried the AMD version of the download and it immediately worked after restarting apache.

Again, thanks for the good support.

Bram.

---

### Post by Bram Snip on 2011-10-17
Hello Memolanuk,

Reason 1 for this is that i have a lot of existing sqlite2 database files. These files cannot be read using sqlite3 (incompatible).

Reason 2: In order to use sqlite3 i need to rewrite (and more importantly re-test!!) existing code. A redesign of this code to support both sqlite2 as well as sqlite3 databases is planned but at this moment i am very happy to have working source code that supports sqlite2.

Regards,

Bram

---

### Post by omniuni on 2011-10-18
What a strange problem, but thank you so much for the solution! I figure this is some sort of odd bug. Any idea if it should be reported?

---

### Post by yukonhenry on 2011-10-21
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/875262](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/875262)

I believe this is a bug that tracks a similar issue.

---

### Post by omniuni on 2011-10-22
Hey all,

In an effort to make this problem easier to resolve, I have prepared a package to provide SQLite2 support. Right now, it is just the x86 version. If you would like an AMD64 version, please let me know. Also, if it works (or doesn't) I would appreciate the feedback.

Download: [http://omniimpact.com/packages/php5-sqlite2_5.3.5-1dm1_i386.deb](http://omniimpact.com/packages/php5-sqlite2_5.3.5-1dm1_i386.deb)

If you use dpkg to install, you may need to run "sudo apt-get -f install" to resolve unmet dependencies.

After installing, you will need to restart Apache using "sudo service apache2 restart".

Good Luck,
OmniUni

---

