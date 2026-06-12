---
title: "serious sudo problem"
date: 2008-04-29
forum: Server Platforms
---

### Post by dave103 on 2008-04-29
I'm a new linux user but I installed Ubuntu 8.04 server which went very easily as did installation of phpmyadmin but now have run into serious trouble with permissions because of the root user issue.  Not sure what I did but now when I use sudo it comes back with "dave is not in the sudoers file.  This incident will be reported" (a bit harsh!).  It may have been because in trying to upload some MySQL files from my PC I thought I would add myself to the mysql group which I thought I did, but I still didn't get access to the mysql folder and probably screwed up my "sudoer's" status in the process.


Can someone help me here - is there any way (short of re-installation) I can recover?

Dave


PS I've been a windows programmer for some years and am very happy with linux except for two things - (1) I can't understand the logic of the file system and I can never find anything because files seem to be sprinkled around everywhere in var, etc, usr, bin, sbin, lib and so on and so on and each location depends on the particular version or flavour of the installation (2) permissions can cause difficulty as in this case.  I mention this because what I was trying to do was amend the apache configuration which first required me to find it and then I ran into the permission problem. I tried to change owner but I assumed I needed first to stop apache which is when I realised I was locked out.

---

### Post by adamitj on 2008-04-29
Hello dave!

Maybe your user "dave" was removed from /etc/sudoers file. This file controls who (users and/or groups) can execute commands as root.

First of all, you will need access with some user wich one have rights as root (that means, user inside /etc/sudoers, or log in with root itself). Then you have to execute these commands:

*** NOTICE: Execute this step only if you have logged in with a different user than root, wich one have rights on sudo ***
```
sudo su
```

[COLOR="Red"]With this one, you become root on console. This command is not recommended by security reasons.[/COLOR]


1) Change /etc/sudoers file permission to be writeable
```
chmod 777 /etc/sudoers
```

2) Verify if your users have sudoers permissions.
```
vim /etc/sudoers
```

The file must be like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
dave    ALL=(ALL) ALL
# *** This line above grants you permissions on sudo ***

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

3) Change the file permission to readonly (as it was before)
```
chmod 440 /etc/sudoers
```

And finish! After set your file to readonly, you be able to use sudo with your user "dave". There is no need to re-install the OS.

---

### Post by Monicker on 2008-04-29
If you were changing groups for your acocunt, you may have inadvertently removed yourself from the admin group, which is how Ubuntu grants you sudo access by default.

You can select the Recovery Mode option from the boot menu to get to a root shell.  Then you will be able to examine /etc/group and /etc/sudoers.


For /etc/group you should have a line similar to the following:

```
admin:x:115:dave
```

---

### Post by dave103 on 2008-04-29
Thanks for the responses.  Unfortunately I was too hasty and tried visudo (I had run into vi years ago on a Unix system and vowed never to go near it again).  I managed to do this by entering recovery mode and getting root access.  However, I did something wrong then I got a /etc/.sudoers.tmp.swp file which I could not recover.

NEXT TIME I will put myself in the admin group and/or edit the sudoers file correctly.

Dave

---

