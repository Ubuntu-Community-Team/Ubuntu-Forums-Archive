---
title: "Trouble getting the source code for a package."
date: 2016-08-31
forum: Ubuntu, Linux and OS Chat
---

### Post by denny4 on 2016-08-31
There is a particular Ubuntu package, arm-linux-gnueabihf, that I would like to get the source code for.  When I type the command ```
apt-get source arm-linux-gnueabihf
```  I get a __.tar.gz file.  When it is extracted there is a directory called 'gcc-defaults-armhf-cross-1.17' and under it a directory 'debian', and then under it are 5 files (apparently common Debian files) named 'changelog', 'compat', 'contol', 'copyright' and 'rules'.  I am new to these debian files, and I don't see any source code (*.c, *.cpp) files anywhere.  Can anyone help?

---

### Post by user1397 on 2016-09-02
Which version of Ubuntu are you on?  I just searched for that package on 16.04 and found 80 packages with that name included as part of the package name but not a single one just called "[COLOR=#000000][FONT=&quot]arm-linux-gnueabihf"


[/FONT][/COLOR]

---

### Post by denny4 on 2016-09-02
I am on 15.04.  Do you see any package named "gcc-arm-linux-gnueabihf"?  If so, are you able to get the source code (*.c, *.cpp) files for it?

---

### Post by ian-weisser on 2016-09-02
The source package is gcc-defaults. See [https://code.launchpad.net/ubuntu/+source/gcc-defaults](https://code.launchpad.net/ubuntu/+source/gcc-defaults)

---

