---
title: "Samba Sharing Problems"
date: 2009-10-16
forum: Server Platforms
---

### Post by yehoshua on 2009-10-16
B"H

Hi

got XUbuntu installed with Samba plus Ubuntu Desktop, but I have problems. I originally created Users and Shares with the Shared Folder App. But then I also used Gadmin, Samba, and Webmin.
From some users I could connect to the Server and from some I could not.

I uninstalled Samba and deleted manually all Samba Files, reinstalled Samba.
I deleted all Users and Shares through Webmin and created all new except for the main user with which I log in. Same problem. Some users can connect and some cannot. There is no telling why, it seems to be random.
HELP!!!

---

### Post by yehoshua on 2009-10-16
B"H
 
I have XUbuntu and Ubuntu Desktop installed with Samba. First I started Sharing with the Shared Folder App, then with Samba and Gadmin, and then with Webmin.
 
Now some of my Users cannot connect to the server and some cannot. I uninstalled Samba, plus deleted all Samba files manually and reinstalled Samba and all users and shares except the one I am logging in with. Same problem.
 
HELP!!!

---

### Post by yehoshua on 2009-10-16
B"H
 
I have XUbuntu and Ubuntu Desktop installed with Samba. First I started Sharing with the Shared Folder App, then with Samba and Gadmin, and then with Webmin.
 
Now some of my Users cannot connect to the server and some cannot. I uninstalled Samba, plus deleted all Samba files manually and reinstalled Samba and all users and shares except the one I am logging in with. Same problem.
 
HELP!!!

---

### Post by justleen on 2009-10-16
I dont know about the sharing thingy, never used that to be honest.
I share several folders, with the following smb.conf, perhaps usefull

```

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
map to guest = bad user
   usershare allow guests = yes

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[detectives]
path=/media/media/detectives
browseable=yes
public=yes
writable=yes
guest ok=yes

[kids]
path=/media/media/kids
browseable=yes
public=yes
writable=yes
guest ok=yes

[films]
path=/media/media/films
browseable=yes
public=yes
writable=yes
guest ok=yes

[series]
path=/media/media/series
browseable=yes
public=yes
writable=yes
guest ok=yes
[docus]
path=/media/media/docus
browseable=yes
public=yes
writable=yes
guest ok=yes

[cooking]
path=/media/media/cooking
browseable=yes
public=yes
writable=yes
guest ok=yes


```

---

### Post by swerdna on 2009-10-16
Please dont double (or triple) post -- it drives us nuts.

Which thread woulds you like the answer in:

this one [http://ubuntuforums.org/showthread.php?p=8113150#post8113150](http://ubuntuforums.org/showthread.php?p=8113150#post8113150)
or this one [http://ubuntuforums.org/showthread.php?p=8113220#post8113220](http://ubuntuforums.org/showthread.php?p=8113220#post8113220)
or this one [http://ubuntuforums.org/showthread.php?p=8113112#post8113112](http://ubuntuforums.org/showthread.php?p=8113112#post8113112)

You can see how hard this makes it to decide anything.

---

### Post by swerdna on 2009-10-16
Please dont double (or triple) post -- it drives us nuts.

Which thread woulds you like the answer in:

this one [http://ubuntuforums.org/showthread.php?p=8113150#post8113150](http://ubuntuforums.org/showthread.php?p=8113150#post8113150)
or this one [http://ubuntuforums.org/showthread.php?p=8113220#post8113220](http://ubuntuforums.org/showthread.php?p=8113220#post8113220)
or this one [http://ubuntuforums.org/showthread.php?p=8113112#post8113112](http://ubuntuforums.org/showthread.php?p=8113112#post8113112)

You can see how hard this makes it to decide anything.

---

### Post by swerdna on 2009-10-16
Please dont double (or triple) post -- it drives us nuts.

Which thread woulds you like the answer in:

this one [http://ubuntuforums.org/showthread.php?p=8113150#post8113150](http://ubuntuforums.org/showthread.php?p=8113150#post8113150)
or this one [http://ubuntuforums.org/showthread.php?p=8113220#post8113220](http://ubuntuforums.org/showthread.php?p=8113220#post8113220)
or this one [http://ubuntuforums.org/showthread.php?p=8113112#post8113112](http://ubuntuforums.org/showthread.php?p=8113112#post8113112)

You can see how hard this makes it to decide anything.

---

### Post by cariboo on 2009-10-16
Please don't multi post on the same subject, I have merged your three threads.

---

