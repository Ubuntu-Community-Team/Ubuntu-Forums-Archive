---
title: "Request: psyBNC"
date: 2005-05-28
forum: Ubuntu Backports
---

### Post by SkyNet_ on 2005-05-28
Hello I was wondering if this could be added in the backports package:

[http://www.psybnc.info/](http://www.psybnc.info/)

Unrotunately I couldn't compile it...

---

### Post by woofcat on 2006-08-23
That would be nice. I also could not get it to run, needed ncurses and no ammount of installing helped.

---

### Post by crackseller on 2006-08-23
Just install ncurses-dev and it should compile fine, just did it yesterday (on pure debian though).

---

### Post by woofcat on 2006-08-23
```
jim@jim-desktop:~/Desktop/psybnc$ sudo apt-get install ncurses-dev
Reading package lists... Done
Building dependency tree... Done
Note, selecting libncurses5-dev instead of ncurses-dev
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@jim-desktop:~/Desktop/psybnc$ make menuconfig
Initializing Menu-Configuration
[*] Running Conversion Tool for older psyBNC Data.
Using existent configuration File.
[*] Running Autoconfig.
System: Linux
Socket Libs: Internal.
Environment: Internal.
Time-Headers: in time.h and sys/time.h
Byte order: Big Endian.
IPv6-Support: Yes.
async-DNS-Support: No, using blocking DNS.
SSL-Support: No openssl found. Get openssl at www.openssl.org
Creating Makefile
[*] Creating Menu, please wait.
This needs the ncurses library. If it is not available, menuconf wont work. If you are using curses, use make menuconfig-curses instead.
make: *** [menuconfig] Error 1

```

For me it just dosn't work :(
opened new thread for my problem [here](http://www.ubuntuforums.org/showthread.php?p=1414133#post1414133) since this is off topic.

---

### Post by madmonk3y on 2007-06-12
I would also LOVE to see a properly-compiled PsyBNC in the repos.  See my post here regarding the glibc problem: [http://ubuntuforums.org/showthread.php?t=471811](http://ubuntuforums.org/showthread.php?t=471811)

That being said, this will probably allow you to use make menuconfig and compile it (with warning mentioned in post linked to above):

```

sudo apt-get install build-essential libssl-dev ncurses-base ncurses-bin ncurses-term libncurses5 libncurses5-dev 

```

---

