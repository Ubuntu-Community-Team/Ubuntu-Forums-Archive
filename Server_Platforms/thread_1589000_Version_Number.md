---
title: "Version Number"
date: 2010-10-05
forum: Server Platforms
---

### Post by Mr.O on 2010-10-05
Hi, 
I am having problems with a printer driver because it says that the libcupsys2 library is not up to date. I know that it is not true because I am using a copy of the 10.01version of the operating system. I was wondering where the version numbers of the software are stored so I can convince the server to cooperate. 
Mr. O

---

### Post by PapaNerd on 2010-10-05
Files:
/etc/issue
/etc/issue.net
/etc/lsb-release

(and perhaps a few others)

---

### Post by Mr.O on 2010-10-05
I dont mean to say this in a bad way, but I was wanting to get the version numbers off the packages and not the system. I need to change the package numbers to convince the driver to install, not the os.

---

### Post by drs305 on 2010-10-05
```
apt-cache show <packagename>
```
will give you the version number plus a lot more. 

If you want only the version:
```
apt-cache show <packagename> | head -8
```

although libcupsys2 specifically generates a message saying it is "purely virtual".

There is also (which also won't work for libcupsys2):
```
dpkg-query -l <packagename>
```

---

### Post by Mr.O on 2010-10-05
What I mean by convince is to change the version number that the package requires, even if that is not the real version number. In other words hack the system to get it to do what I want.

---

### Post by PapaNerd on 2010-10-05
Or if you don't want to sift through the output: ```
 apt-cache show <packagename> | grep Version 
```

---

### Post by Mr.O on 2010-10-05
Change, as in rename, overwrite, delete and replace, etc...

---

### Post by PapaNerd on 2010-10-05
I am not convinced that approach will work.  However, what you might try is ```
 find / | grep <package-name> 
``` and then cd to the subdirectory and create a symbolic link with the version you think is current pointing to the installed version.

Alternately, have you tried updating the libcupsys2 library?

---

