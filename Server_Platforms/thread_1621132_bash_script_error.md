---
title: "bash script error"
date: 2010-11-13
forum: Server Platforms
---

### Post by pehden on 2010-11-13
```

#!/bin/sh
chown -Rc steven:users "/home/steven"


```
I have more lines in the script but each line does the same error.
this is run in a cron job but it always returns 

```

chown: cannot access `/home/steven\r': No such file or directory

```

But it is a valid directory i have even tried adding an / and even a space on the end and still same error.

---

### Post by wongo888 on 2010-11-13
Why is there a \r after your file name?

Are there errant control characters in your scripts?

---

### Post by SeijiSensei on 2010-11-14
Just a guess but you wrote this script on a Windows machine perhaps?  DOS and Windows use both a "new line" and a "carriage return" to denote the end of a line; Unix uses just a new line.

Either you can rewrite the file in an editor in Linux (nano or gedit are good for beginners), or you can install the program called dos2unix from the repositories and run your file through it like this:

```
$sudo apt-get install dos2unix
stuff happens
dos2unix < oldfile > newfile

```

newfile will look identical to oldfile but will have all the returns stripped off.  Use "man dos2unix" to get more information.

---

### Post by pehden on 2010-11-14
> **SeijiSensei said:**
> Just a guess but you wrote this script on a Windows machine perhaps?  DOS and Windows use both a "new line" and a "carriage return" to denote the end of a line; Unix uses just a new line.

Either you can rewrite the file in an editor in Linux (nano or gedit are good for beginners), or you can install the program called dos2unix from the repositories and run your file through it like this:

```
$sudo apt-get install dos2unix
stuff happens
dos2unix < oldfile > newfile

```

newfile will look identical to oldfile but will have all the returns stripped off.  Use "man dos2unix" to get more information.

I thought i would get this answer but i was at work when i posted the question, thing is i am using webmin text editor and a weeble ftp php thing to edit the files so its all in linux.



I tried to just now install this and it says not found.

---

### Post by wongo888 on 2010-11-14
```
$ apt-cache show tofrodos
Package: tofrodos
Priority: optional
Section: utils
Installed-Size: 84
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Alexander Reichle-Schmehl <tolimar@debian.org>
Architecture: i386
Version: 1.7.8.debian.1-2
Depends: libc6 (>= 2.4)
Conflicts: sysutils (<= 2.0.0-1)
Filename: pool/main/t/tofrodos/tofrodos_1.7.8.debian.1-2_i386.deb
Size: 20392
MD5sum: 23ccf67eb371b1b07bb0941919b48e7d
SHA1: 662e7437ba62ecf39ba718ac2722b238ebca6178
SHA256: 0449e95e9f1fdd439f4425ce80c1267f0c85df862cee146e03ead9c22eeb1ab1
Description: Converts DOS <-> Unix text files, alias tofromdos
 DOS text files traditionally have CR/LF (carriage return/line feed) pairs
 as their new line delimiters while Unix text files traditionally have
 LFs (line feeds) to terminate each line.
 .
 Tofrodos comprises one program, "fromdos" alias "todos", which converts
 text files to and from these formats. Use "fromdos" to convert DOS
 text files to the Unix format, and "todos" to convert Unix text files
 to the DOS format.
Homepage: http://www.thefreecountry.com/tofrodos/index.shtml
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m

```

---

### Post by pehden on 2010-11-14
> **wongo888 said:**
> ```
$ apt-cache show tofrodos
Package: tofrodos
Priority: optional
Section: utils
Installed-Size: 84
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Alexander Reichle-Schmehl <tolimar@debian.org>
Architecture: i386
Version: 1.7.8.debian.1-2
Depends: libc6 (>= 2.4)
Conflicts: sysutils (<= 2.0.0-1)
Filename: pool/main/t/tofrodos/tofrodos_1.7.8.debian.1-2_i386.deb
Size: 20392
MD5sum: 23ccf67eb371b1b07bb0941919b48e7d
SHA1: 662e7437ba62ecf39ba718ac2722b238ebca6178
SHA256: 0449e95e9f1fdd439f4425ce80c1267f0c85df862cee146e03ead9c22eeb1ab1
Description: Converts DOS <-> Unix text files, alias tofromdos
 DOS text files traditionally have CR/LF (carriage return/line feed) pairs
 as their new line delimiters while Unix text files traditionally have
 LFs (line feeds) to terminate each line.
 .
 Tofrodos comprises one program, "fromdos" alias "todos", which converts
 text files to and from these formats. Use "fromdos" to convert DOS
 text files to the Unix format, and "todos" to convert Unix text files
 to the DOS format.
Homepage: http://www.thefreecountry.com/tofrodos/index.shtml
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m

```

Ok sudo apt-get install tofrodos

installed.

---

### Post by SeijiSensei on 2010-11-14
> **pehden said:**
> I tried to just now install [dos2unix] and it says not found.

Hmm.  I checked to see if I could install it on Maverick before I posted this suggestion, and I found it in the repositories.  After installing, dpkg reports:

$ dpkg -s dos2unix
Package: dos2unix
Status: install ok installed
Priority: extra
Section: text
Installed-Size: 184
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 5.0-2
Depends: libc6 (>= 2.4)
Conflicts: tofrodos (<< 1.7.8.debian.1-2)
Description: convert text file line endings between CRLF and LF
[...]

---

### Post by pehden on 2010-11-14
> **SeijiSensei said:**
> Hmm.  I checked to see if I could install it on Maverick before I posted this suggestion, and I found it in the repositories.  After installing, dpkg reports:

$ dpkg -s dos2unix
Package: dos2unix
Status: install ok installed
Priority: extra
Section: text
Installed-Size: 184
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 5.0-2
Depends: libc6 (>= 2.4)
Conflicts: tofrodos (<< 1.7.8.debian.1-2)
Description: convert text file line endings between CRLF and LF
[...]


I got it installed and it looks like you have to use fromdos <file> <file>   so I think this is working.

---

