---
title: "rkhunter warning : /usr/bin/ldd"
date: 2010-06-10
forum: Security
---

### Post by dinw3 on 2010-06-10
[PHP][21:16:42] Warning: The file properties have changed:
[21:16:42]          File: /usr/bin/ldd
[21:16:42]          Current hash: 4f4d16384d6680d9d7ea5d03f8868e562335011a
[21:16:42]          Stored hash : e95c1115b79776bf1c2d6f0a561e458bd36ced57
[21:16:42]          Current inode: 4121    Stored inode: 2334
[21:16:42]          Current size: 5279    Stored size: 5277
[21:16:42]          Current file modification time: 1274438312 (21-May-2010 14:38:32)
[21:16:42]          Stored file modification time : 1271956432 (22-Apr-2010 21:13:52)
[/PHP]I am getting this warning what can i do to check my system ?


and this ?[PHP]fc2aee3e87d0b4d130d060a9cd80dee2  /bin/egrep
5035f2982d7651b496d27644a0ea4dfc  /bin/fgrep
e942f154ef9d9974366551d2d231d936  /bin/which
1c7dddbbf51da85d0e71122449c97096  /usr/bin/groups
469dfd3336363953b83056591ff60ef9  /usr/sbin/adduser
[/PHP]

---

### Post by bodhi.zazen on 2010-06-10
It is poor forum to run a security tool, rkhunter or otherwise, without doing your home work. If you do not understand how to use these tools, nothing replaces reading the documentation.

See :

[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

I know it may seem harsh, but this advice is not intended that way.

---

### Post by lovinglinux on 2010-06-10
I have written a simple script that will download the flagged file from the repositories and compare it with the installed one. 

When you launch the script , it will ask for the path of the file to be tested. This is the path shown in rkhunter report. For example /usr/bin/ldd

```
#!/bin/bash

PACKPATH=$(zenity --entry --text="Package Path")
PACKAGE=$(dpkg -S ${PACKPATH} | sed 's/\:.*//g')

mkdir $HOME/Desktop/packtest
cd $HOME/Desktop/packtest/
aptitude download ${PACKAGE}
dpkg -x ./${PACKAGE}*.deb ${PACKAGE}

TEST1D=$(sha1sum $HOME/Desktop/packtest/${PACKAGE}/${PACKPATH} | sed 's/\/.*//g')
TEST1P=$(sha1sum ${PACKPATH} | sed 's/\/.*//g')

TEST256D=$(sha256sum $HOME/Desktop/packtest/${PACKAGE}/${PACKPATH} | sed 's/\/.*//g')
TEST256P=$(sha256sum ${PACKPATH} | sed 's/\/.*//g')

if [ "${TEST1D}" = "${TEST1P}" ]
then
    zenity --info --text "SHA1 OK:\n\n${TEST1D}\n\n${TEST1P}"
else
    zenity --info --text "SHA1 Failed:\n\n${TEST1D}\n\n${TEST1P}"
fi

if [ "${TEST256D}" = "${TEST256P}" ]
then
    zenity --info --text "SHA256 OK:\n\n${TEST256D}\n\n${TEST256P}"
else
    zenity --info --text "SHA256 Failed:\n\n${TEST256D}\n\n${TEST256P}"
fi

rm -r $HOME/Desktop/packtest
```

---

### Post by bodhi.zazen on 2010-06-10
Honestly, read the man page and google search those warnings, you will then know how to use rkhunter.

If there is something in your reading you do not understand, feel free to ask for clarification, but honestly these issues are well documented.

---

### Post by dinw3 on 2010-06-15
i reinstalled the distribution

---

### Post by bodhi.zazen on 2010-06-15
> **dinw3 said:**
> i reinstalled the distribution

Then you have learned nothing and should probably not use rkhunter.

---

