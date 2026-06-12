---
title: "make_chroot_jail"
date: 2008-08-06
forum: Security
---

### Post by 0perator on 2008-08-06
hi, i am trying to jail someone on my ssh, and i have, /jail/make_chroot_jail.sh

so i cd /jail

and do this

./make_chroot_jail.sh coke (for the user called coke)

and it comes out with this.

```
Release: 2007-10-19

Am I root?  
  OK
Checking distribution... 
  Supported Distribution found
  System is running Debian Linux
Checking for which... 
  OK
Checking for chroot...
  OK
Checking for sudo...
  OK
Checking for dirname...
  OK
Checking for awk...
  OK

Subsystem sftp /usr/lib/openssh/sftp-server

-----------------------------
User coke exists. 

Are you sure you want to modify the users home directory and lock him into the
chroot directory?
Are you REALLY sure?
Say only yes if you absolutely know what you are doing!
(yes/no) -> yes

-----------------------------
The file /bin/chroot-shell exists. 
Probably it was created by this script.

Are you sure you want to overwrite it?
(you want to say yes for example if you are running the script for the second
time when adding more than one account to the jail)
(yes/no) -> yes

Modifying /etc/sudoers

Not creating new User account
Modifying User "coke" 
Copying files in coke's $HOME to "/home/jail/home/coke"

Adding User coke to jail
Copying necessary library-files to jail (may take some time)
mv: missing destination file operand after `.bak'
Try `mv --help' for more information.
mv: missing destination file operand after `.bak'
Try `mv --help' for more information.
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent



```

help much appreciated thanks.

EDIT: forgot to mention that the script doesnt actually end, it just hangs there....

---

### Post by Mordac85 on 2008-08-07
Dumb question, but have you checked perms on /jail to make sure you can create the destination objects?

---

### Post by kevdog on 2008-08-07
A little off topic but I use the package named jailkit to make my jail since someone else with much more time and thought has previously figured out how to do this and troubleshoots this with much more expertise:

[http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

---

### Post by hyper_ch on 2008-08-07
I like mysecureshell quite a lot :)

---

### Post by Schgoddy on 2008-08-13
Hello Mr. Operator

I had the same problem with the error messages:
> mv: missing destination file operand after `.bak'
Try `mv --help' for more information.
mv: missing destination file operand after `.bak'
Try `mv --help' for more information.
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent

the main cause were the lines
```
TMPFILE1=`mktemp` &> /dev/null ||  TMPFILE1="${HOME}/ldlist"; if [ -x ${TMPFILE1} ]; then mv ${TMPFILE1} ${TMPFILE1}.bak;fi
TMPFILE2=`mktemp` &> /dev/null ||  TMPFILE2="${HOME}/ldlist2"; if [ -x ${TMPFILE2} ]; then mv ${TMPFILE2} ${TMPFILE2}.bak;fi
```

because the return of the mktemp command is not set to TMPFILE1/2 and therefore the mv and the ldd command fail.
The clue is:
delete the beginning of the 2 lines, the result should look like this:
```
TMPFILE1="${HOME}/ldlist"; if [ -x ${TMPFILE1} ]; then mv ${TMPFILE1} ${TMPFILE1}.bak;fi
TMPFILE2="${HOME}/ldlist2"; if [ -x ${TMPFILE2} ]; then mv ${TMPFILE2} ${TMPFILE2}.bak;fi
```
...and it works.

Greetz, Robert

BTW, @ Mordac85:
> have you checked perms on /jail to make sure you can create the destination objects?
the make_chroot_jail script should be executed with root permissions so you should have the proper rights to copy the files.

---

### Post by unleadedblues on 2009-03-26
None of the solutions above worked for me at all.  

I simply changed the first line of the script 

from:
#!/bin/sh
to:
#!/bin/bash

I think it will work for you.

---

### Post by hvollebregt on 2009-05-26
Awesome! Thanks a lot, the combination of the last two suggestions made things work for me.

---

### Post by max404s on 2011-08-25
For any people reading this: only the change mentioned by **unleadedblues** is needed (changing the hashbang from sh to bash).

I *think *this may be because Debian/Ubuntu uses dash as its system shell, which has different syntax to bash.

---

