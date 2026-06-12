---
title: "mysql apt"
date: 2005-10-07
forum: Server Platforms
---

### Post by sickdude on 2005-10-07
sickdude@teletran:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
 
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-client (>= 4.0.23-3ubuntu2.1)
                Depends: libdbi-perl but it is not installable
E: Broken packages
sickdude@teletran:~$

Hmm dont know whats wrong with this, maybe repo's list? cant be so what can it be?

---

### Post by heimo on 2005-10-07
libdbi-perl seems to be in main - bad mirror is my best guess, but can't verify without seeing your sources.list You can search the file somewhere under (/pool/main/libd/libdbi-perl/) on the repository mirror you're using. For example:
[http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/)

---

### Post by sickdude on 2005-10-07
[QUOTE=heimo]libdbi-perl seems to be in main - bad mirror is my best guess, but can't verify without seeing your sources.list You can search the file somewhere under (/pool/main/libd/libdbi-perl/) on the repository mirror you're using. For example:
[http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/)[/QUOTE]


my sources list
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
                                                                                                    
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
                                                                                                    
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
                                                                                                    
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
                                                                                                    
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
                                                                                                    
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
                                                                                                    
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```

---

### Post by sickdude on 2005-10-07
hmm still looking some stuff up but i cant seem to find out whats wrong. 

its so strange because with my older ubuntu install this wasnt a issiue at all :confused:

---

### Post by sickdude on 2005-10-10
Depends: libdbi-perl but it is not installable

tryed to install this manually but this had no effect, wel apt tells me its broken :S so this is very strange

any help would rule big time :D

---

### Post by sickdude on 2005-10-12
hmm i think this is wierd these packages are broken, dont know if this is a error in my server or in the sources list.

tried to install mysql-server-4.1 to but then i get more errors

sickdude@teletran:~$ sudo apt-get install mysql-server-4.1
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
 
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
  mysql-server-4.1: Depends: mysql-client-4.1 (>= 4.1.10a-2ubuntu0.1) but it is not going to be installed
                    Depends: libdbi-perl but it is not installable
                    Depends: gawk but it is not installable
E: Broken packages
sickdude@teletran:~$

---

