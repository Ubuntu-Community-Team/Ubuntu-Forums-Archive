---
title: "How to Create File in /etc/sudoers.d"
date: 2014-08-12
forum: Security
---

### Post by borgward on 2014-08-12
How do I create a file in /sudoers.d? I want to add new user. I need to know how to do it from the command line. I understand how to edit using visudo (barely), but need to know how to start a new file. and save it in the /etc/sudoers.d directory.

---

### Post by JetStorm on 2014-08-12
A new file in Linux can be created with the "touch" command.

Have you tried something like:

[B]sudo touch /etc/sudoers.d/newfile

[/B](where you replace "newfile" with the file name you want)

---

### Post by ajgreeny on 2014-08-12
However, you would not add a new user in that manner, in fact I have never even heard of doing so.

See [http://ss64.com/bash/useradd.html](http://ss64.com/bash/useradd.html) for the more usual way

---

### Post by borgward on 2014-08-12
See LinuxFoundationX: LFS101x Introduction to Linux.

---

### Post by steeldriver on 2014-08-12
What exactly are you trying to do?

[LIST]
[*]add a user to the system? 
[*]add an existing user to the sudoers group? 
[*]give a particular non-sudo user the ability to run certain programs with elevated privileges? 
[/LIST]

---

### Post by borgward on 2014-08-12
Add user to sudoers.d from command line

---

### Post by ajgreeny on 2014-08-12
> **borgward said:**
> Add user to sudoers.d from command line

What exactly for?

---

### Post by ian-weisser on 2014-08-12
mc4man's advice below is much better than what I wrote.

---

### Post by borgward on 2014-08-12
What for?

Lab assignment from edX LinuxFoundationX: LFS101x Introduction to Linux.

---

### Post by bab1 on 2014-08-12
> **borgward said:**
> What for?

Lab assignment from edX LinuxFoundationX: LFS101x Introduction to Linux.

Read the Ubuntu Forums's COG.  It expressly states "NO homework help".

[COLOR="#0000FF"]This is what the OP is referring to[/COLOR]```
#
# As of Debian version 1.7.2p1-1, the default /etc/sudoers file created on
# installation of the package now includes the directive:
# 
# 	#includedir /etc/sudoers.d
# 
# This will cause sudo to read and parse any files in the /etc/sudoers.d 
# directory that do not end in '~' or contain a '.' character.
# 
# Note that there must be at least one file in the sudoers.d directory (this
# one will do), and all files in this directory should be mode 0440.
# 
# Note also, that because sudoers contents can vary widely, no attempt is 
# made to add this directive to existing sudoers files on upgrade.  Feel free
# to add the above directive to the end of your /etc/sudoers file to enable 
# this functionality for existing installations if you wish!
#

```

---

### Post by QIII on 2014-08-12
Hello, all.

The OP is referring to a course offered on line by the Linux Foundation.  It's not homework in the traditional sense.

---

### Post by bab1 on 2014-08-12
> **QIII said:**
> Hello, all.

The OP is referring to a course offered on line by the Linux Foundation.  It's not homework in the traditional sense.

The best answer is the man pages.  ```
Man 5 sudoers
```

There is a very complete description  of sudoers include files at line 451 of this man page.

---

### Post by mc4man on 2014-08-12
> **borgward said:**
> How do I create a file in /sudoers.d? I want to add new user. I need to know how to do it from the command line. I understand how to edit using visudo (barely), but need to know how to start a new file. and save it in the /etc/sudoers.d directory.
Petty simple, just this with blue name as desired. (just no ~ or . in name
> sudo visudo -f /etc/sudoers.d/[COLOR="#0000FF"]filename[/COLOR]

Ex. 
```
sudo visudo -f /etc/sudoers.d/01_file
```

There are some advantages to using a file in /etc/sudoers.d rather than messing about in sudoers itself.

---

