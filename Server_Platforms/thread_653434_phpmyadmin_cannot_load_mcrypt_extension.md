---
title: "phpmyadmin: cannot load mcrypt extension"
date: 2007-12-29
forum: Server Platforms
---

### Post by Chake99 on 2007-12-29
Trying to set up a server on top of my already existing kubuntu partition. Installed phpmyadmin to simplify website development (fooling around with website creation/hosting during holiday school-break) but whenever I log in I get a "cannot load mcrypt extension" error. How do I enable it/install it?

Googling turned up that it is encryption stuff, and I surmised windows users who it happens have to just edit some lines in their php.ini file (which for some reason I couldn't find, the lines I mean, I found php.ini through php.info()).

A pointer would be appreciated.

---

### Post by andol on 2007-12-29
```
sudo apt-get install php5-mcrypt
```
(Assuming you run php5.)

---

### Post by Chake99 on 2007-12-29
woah, ty. That was embarrassingly easy.

---

### Post by jcolo on 2008-01-02
sudo apt-get install php5-mcrypt

gives me 

E: Couldn't find package php5-mcrypt

any hints ???

---

### Post by andol on 2008-01-02
Do you have *Universe* (repository) enabled?

What version of Ubuntu are you running?

---

### Post by jcolo on 2008-01-02
Hi Andol,

I am on edgy and I do have universe enabled.

I have download the mcrypt library, compiled and run successfuly

I have downloaded php5-mcrypt and got 

joomlaserver: sudo aptitude install php5-mcrypt
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for php5-mcrypt
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


however 

aptitude search php

posts among other things

c   php5-mcrypt                                                            - MCrypt module for php5

I can't find the mcrypt library as a package... there seems to be a dependency...

Any help appreciated.

Thanks.

JCG

---

### Post by andol on 2008-01-02
Done an *apt-get update* recently?

---

### Post by jcolo on 2008-01-02
Hi Many thanks for your comments.

I did followed manually all the depencies  via dpkg.

I first installed limcrypt4, them mcrypt and finally php5-mcrypt

at least it shows as installed......

let's see if it works  :-)

JCG

---

