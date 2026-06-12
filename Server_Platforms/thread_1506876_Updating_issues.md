---
title: "Updating issues"
date: 2010-06-10
forum: Server Platforms
---

### Post by guessswh0 on 2010-06-10
Hey guys, any time that I try to do an apt-get upgrade on my server, it keeps failing.  This time, this is what I am getting:

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libmysqlclient15off: Depends: mysql-common (>= 5.1.30really5.0.75-0ubuntu10.5) but 5.1.30really5.0.75-0ubuntu10.3 is installed
  mysql-client-5.0: Depends: mysql-common (>= 5.1.30really5.0.75-0ubuntu10.5) but 5.1.30really5.0.75-0ubuntu10.3 is installed
E: Unmet dependencies. Try using -f.


This is what I am recently getting, however, it all goes back to me having an issue install libkrb53.

An error I get is this:  dpkg: serious warning: files list file for package `libkrb53' missing, assuming package has no files currently installed.



I believe this to be the root cause (the libkrb53).  This has been going on for a while, and I've just been unable to figure it out.  Any ideas?

Thanks

---

### Post by Ryan Dwyer on 2010-06-11
So what happens when you try apt-get install -f?

---

### Post by guessswh0 on 2010-06-12
It keeps erroring out.  This is the message I get currently:

error processing /var/cache/apt/archives/mysql-common_5.1.30really5.0.75-0ubuntu10.5_all.deb (--unpack):
 unable to install new version of `./usr/share/mysql-common': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-common_5.1.30really5.0.75-0ubuntu10.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


But the reason for that is because of the lib file above.  So basically, I can't install any updates.... ideas?

---

### Post by terry_gardener on 2010-06-12
i have had this problem before but for another package on the desktop version but should be the same.
the only i could find to solve it is remove the bad package. sudo apt-get remove libmysqlclient15off and then do sudo apt-get update and see if you get the same message with a different package, and repeat the process until update goes through and then reinstall the packages. 

hope this helps

---

### Post by guessswh0 on 2010-06-15
sorry, I wish it did, but nothing happens.  I can't apt-get remove the libkrb53 files.  And I can't install anything.

This is turning into some bigger issues.  I cannot update anything.  Can anyone please help?

---

### Post by terry_gardener on 2010-06-16
this is a long shot but does apt-get purge <packagename> work 

also try: sudo aptitude -f 

again another long but never know your luck.

---

