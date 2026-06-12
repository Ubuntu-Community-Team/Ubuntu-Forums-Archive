---
title: "Installing Desktop on Ubuntu Server"
date: 2008-03-01
forum: Server Platforms
---

### Post by murpg on 2008-03-01
Hi Guys, I am totally new to Linux.  I had a colleague put together a server for me running Ubuntu 7.10 PHP and MySQL.  Unfortunately, I was not able to watch him do this.  He is not available at the moment and I would like to first change my password because he gave me a password of changeme and I would like to install the gnome desktop.  He gave me this command to change the desktop but it does not seem to do anything. sudo apt-get install gnome-desktop

Thanks in advance for any help you could please give me in accomplishing these 2 things.

---

### Post by farruinn on 2008-03-01
To change your password use the 'passwd' command. Then, when you run the 'sudo apt-get install gnome-desktop' command enter that password when it asks for it.

---

### Post by Jose Catre-Vandis on 2008-03-01
As previous poster says, just enter```
passwd
```on the command line, once you have logged in and ubuntu will ask you to enter your current password and then your new one twice.

To install a desktop on a server, have a look here for some options and ideas
```
http://www.psychocats.net/ubuntu/minimal
```

---

### Post by kerry_s on 2008-03-01
> **murpg said:**
> Hi Guys, I am totally new to Linux.  I had a colleague put together a server for me running Ubuntu 7.10 PHP and MySQL.  Unfortunately, I was not able to watch him do this.  He is not available at the moment and I would like to first change my password because he gave me a password of changeme and I would like to install the gnome desktop.  He gave me this command to change the desktop but it does not seem to do anything. sudo apt-get install gnome-desktop

Thanks in advance for any help you could please give me in accomplishing these 2 things.


use " **sudo passwd yourname** "
replace "yourname" with the name you use to log in
use the "changeme" password then it will ask you for the new one.

then you should be able to use your new password for installing the desktop.
**sudo apt-get install gnome-desktop**
or
**sudo apt-get install ubuntu-desktop**

for the ubuntu setup.

---

### Post by murpg on 2008-03-03
Hi Guys, I was successfull changing my password.  I have not had any luck adding my desktop.  I have tried everything but not seems to work.

---

### Post by Brazen on 2008-03-03
you need to do
**sudo apt-get update && sudo apt-get install ubuntu-desktop**

if it still does not work, what is the output when you do 'sudo apt-get install ubuntu-desktop' ?

---

### Post by murpg on 2008-03-03
The only thing that happens is it goes to the next line.
george@somehost:~$

---

### Post by Iowan on 2008-03-03
Silly question, but:
Does it ask for a password after entering the **sudo ...** command?

---

### Post by murpg on 2008-03-05
Hi Guys, here was the problem.  The guy who set me up did not have me in the admin group.  I am downloading my desktop now.  I have another question.  How do I set my IP address?  I need to have a static IP Address.

---

