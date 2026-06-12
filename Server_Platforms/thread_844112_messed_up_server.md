---
title: "messed up server"
date: 2008-06-29
forum: Server Platforms
---

### Post by leewilson78 on 2008-06-29
hi all, 

i am waiting back for a response from my host, but basically, i have done something majorily stupid.

i wanted to change the owner and group for files i had transferred from another server, it looks like i changed the details for all files and folder on the server, and now i cannot login to my server via ssh.

here is what i used to try and changed the details:

chown -R sml *

chgrp -R psacln *

is there any option for me, when i try to login to my server, i get the folowing:

ssh_exchange_identification: Connection closed by remote host

appreciate any help.

thanks

---

### Post by windependence on 2008-06-29
Nope, you're gonna have to have someone boot into single user mode to fix this I'm afraid or log on as root at the con if they can.

-Tim

---

### Post by leewilson78 on 2008-06-29
thanks for the reply, i have sent several emails to support, can't blame them for not replying, sunday and all.

i guess there is nothing at i can do, just wait till tomorrow, holding of the angry clients.

thanks for the advice.

---

### Post by promodus on 2008-06-29
> **leewilson78 said:**
> 

chown -R sml *

chgrp -R psacln *



What directory where you in when you typed those commands?

---

### Post by leewilson78 on 2008-06-29
I cannot be too sure, I have noticed that not all sites have gone down though, and I can still login to some sites via ftp.

My main site that is associated with the server has gone down though.

---

### Post by leewilson78 on 2008-06-29
actually, I stand corrected, I can access the main site. When I look at the owner and group in ftp, I see they are all set to the new owner and group.

---

### Post by promodus on 2008-06-29
I'm wondering that since you're able to log in by FTP, maybe you can chown the specific files back to normal to repair SSH?

/var/run/ssh 
and possibly /var/log

A couple log files that I'd check.
```

root@server:/var/log# ls -l
total 4708
drwxr-x--- 2 root   adm        4096 2008-06-23 06:25 apache2
drwxr-xr-x 2 root   root       4096 2007-10-13 18:32 apparmor
drwxr-xr-x 2 root   root       4096 2008-06-01 06:25 apt
drwxr-xr-x 4 root   root       4096 2008-02-28 13:43 asterisk
-rw-r----- 1 syslog adm      124286 2008-06-29 03:28 auth.log
-rw-r----- 1 root   adm          31 2007-11-06 07:41 boot
-rw-rw-r-- 1 root   utmp          0 2008-06-01 06:25 btmp
-rw-r----- 1 syslog adm       15156 2008-06-29 02:04 daemon.log
-rw-r----- 1 syslog adm      168410 2008-06-25 14:49 debug
drwxr-xr-x 2 root   root       4096 2007-10-13 18:09 dist-upgrade
-rw-r----- 1 root   adm       30822 2008-06-25 10:56 dmesg
-rw-r----- 1 root   adm       14199 2008-06-19 02:08 dpkg.log
-rw-r--r-- 1 root   root      32032 2008-05-08 13:44 faillog
drwxr-xr-x 2 root   root       4096 2007-11-06 07:41 fsck
drwxr-xr-x 3 root   root       4096 2007-11-06 08:09 installer
-rw-r----- 1 syslog adm      207238 2008-06-25 14:49 kern.log
-rw-rw-r-- 1 root   utmp     292292 2008-06-29 03:28 lastlog
-rw-r----- 1 syslog adm       56358 2008-06-29 03:19 messages
-rw-r----- 1 syslog adm       11683 2008-06-29 03:17 syslog
-rw-r--r-- 1 root   root     328527 2008-06-25 10:56 udev
-rw-r----- 1 syslog adm           0 2007-11-06 07:42 user.log
-rw-rw-r-- 1 root   utmp      65280 2008-06-29 03:28 wtmp

```

Also check permissions in /etc

---

### Post by leewilson78 on 2008-06-29
I can login via ftp to specific accounts only, I cannot login via root (SFTP), when I try to, my FTP program gives the following error:

I/O Error: Connection failed. There was a problem connecting

There is no option in my FTP program to change the owner of a folder also.

Thanks

---

### Post by promodus on 2008-06-29
I'm thinking if you're able to ftp to this machine with the user you chown'd the files to *sml* possibly chown back.

Most daemons will not let you log in via root, as root is common with every Unix. Not to mention the privilege associated. Also, when traversing logs it's easier to see that user sml became root, rather than someone logged in as root and not knowing who.

What FTP Daemon are you using?

Any other services on this box?

Maybe you could use PHP to run a system command.
i.e. have PHP chown the files, or have php run another instance of SSH from a different configuration file... A temporary backdoor.

---

### Post by leewilson78 on 2008-06-29
I have managed to login to the server via a remote console that my hosting co. provides. 

I guess there is no command to 'roll back' the system, should I manually change the owner and group of all files?

---

### Post by leewilson78 on 2008-06-29
seems like I am getting somewhere, where did I go wrong with the commands I first used, i.e:

chown -R sml *

chgrp -R psacln *

should i run this command only from the correct directory, for example, I want to change the owner to lee, do I navigate to the account I setup called lee and change from there?

---

### Post by leewilson78 on 2008-06-29
Sorry for multiple replies, but no I can login via their remote console, is there anything I can do to reset my login, so that I can safely login via SSH or SFTP?

Thanks

---

### Post by mrpeenut24 on 2008-06-29
chown/chgrp -R are recursive.  This means it will go into every directory inside the current directory and change the privileges there too.  Depending on how high up you were (how close to /), it could be very bad.  Do you have any idea what directory you were in when you issued that command?  Or how high up you were (how many directories in)?

---

### Post by leewilson78 on 2008-06-29
I have tried to find this out, but its proving to be a little difficult, I had assumed that I had carried it out from the root directory, everything seemed to go down, I had plesk running and that messed up.

I used to be able to login via SSH with root access, however, I can only do this via their remote console, so I am guessing that the server blocked my IP or something.

Is there anything I can do on the remote console to allow me to login again va SSH or SFTP?

Thanks

---

### Post by windependence on 2008-06-30
You shouldn't be logging in externally as root anyway. This is a big security risk. Log in as a regular user and su to root. Og course that means you must enable the root account but it appears you already have.

Pleskk is a funny animal. It installs it's own stuff and you shouldn't mess with it unless you wanna break things. I support several Plesk servers.

-Tim

---

### Post by Keith Hedger on 2008-08-03
This wont be of help now but I have done similar things so I created a small app to record/repair permissions so checkout: [http://code.google.com/p/perms/](http://code.google.com/p/perms/) for future use.

---

### Post by Vishal Agarwal on 2008-08-03
just logon with the ssh -v and post the screen shot.

This can be a problem with hosts.allow, or /etc/ssh/sshd_config file.

---

