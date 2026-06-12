---
title: "Problem Changing User Password"
date: 2010-03-15
forum: Security
---

### Post by chiques on 2010-03-15
Hello Everyone,
I've searched the forums and there are a few posts which describe how to change log in passwords. They all basically recommend to use **passwd**. I've tried to use this command in my log  and in recovery mode but I keep getting this error message.


> 
user@user-desktop:~$ sudo passwd user
[sudo] password for user: 
passwd: Authentication token manipulation error
passwd: password unchanged
user@user-desktop:~$ 


What am I doing wrong? What is "token manipulation error"?

---

### Post by wojox on 2010-03-15
Try it without sudo.

---

### Post by sisco311 on 2010-03-15
First of all, password is setuid root, you don't have use sudo to run it:
```
passwd username
```

What's the output of:
```
ls -al /usr/bin/passwd
```
and
```
ls -al /etc/{passwd,shadow}
```
?

---

### Post by chiques on 2010-03-15
> **wojox said:**
> Try it without sudo.

Same thing.

> 
user@user-desktop:~$ passwd
Changing password for user.
(current) UNIX password: 
passwd: Authentication token manipulation error
passwd: password unchanged
user@user-desktop:~$ 


---

### Post by nitstorm on 2010-03-15
> 
Quote:
 	 	 		 			 				user@user-desktop:~$ passwd
Changing password for user.
(current) UNIX password: 
passwd: Authentication token manipulation error
passwd: password unchanged
user@user-desktop:~$  			 		


Just tried it on my comp and I get the same error....

---

### Post by chiques on 2010-03-15
> **sisco311 said:**
> First of all, password is setuid root, you don't have use sudo to run it:
```
passwd username
```

What's the output of:
```
ls -al /usr/bin/passwd
```
and
```
ls -al /etc/{passwd,shadow}
```
?



I tried **passwd user** but I still receive:

> 

user@user-desktop:~$ passwd user
Changing password for user.
(current) UNIX password: 
passwd: Authentication token manipulation error
passwd: password unchanged
user@user-desktop:~$ 





Output of **ls -al /usr/bin/passwd**

> 
user@user-desktop:~$ ls -al /usr/bin/passwd
-rwsr-xr-x 1 root root 41292 2009-07-31 06:55 /usr/bin/passwd
user@user-desktop:~$ 




The output of **ls -al /etc/{passwd,shadow}** is :
> 
user@user-desktop:~$ ls -al /etc/{passwd,shadow}
-rw-r--r-- 1 root root   1708 2010-02-16 09:12 /etc/passwd
-rw-r----- 1 root shadow 1178 2010-02-16 09:12 /etc/shadow
user@user-desktop:~$ 


---

### Post by cdenley on 2010-03-15
Post this output
```

getent passwd $USER
sudo getent shadow $USER|cut -d : -f 1,3-

```

---

### Post by nitstorm on 2010-03-15
> **chiques said:**
> I tried **passwd user** but I still receive:




Output of **ls -al /usr/bin/passwd**






The output of **ls -al /etc/{passwd,shadow}** is :


When it asks for the Unix password put in your login password, not the super-user password ( i mean not the password that u give wen u type *su* in the terminal) . Worked for me that way just now...

---

### Post by cdenley on 2010-03-15
> **nitstorm said:**
> When it asks for the Unix password put in your login password, not the super-user password ( i mean not the password that u give wen u type *su* in the terminal) . Worked for me that way just now...

Yes, apparently you get that error when you enter the wrong password. However, you do not get the token manipulation error when running passwd with sudo or as root due to an incorrect password, so you do not have the same problem as chiques.

---

### Post by nitstorm on 2010-03-15
<deleted>
Sorry was making no sense there.

---

### Post by chiques on 2010-03-16
> **cdenley said:**
> Post this output
```

getent passwd $USER
sudo getent shadow $USER|cut -d : -f 1,3-

```



**user@user-desktop:~$ getent passwd $user**

```

user@user-desktop:~$ getent passwd $user
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:111:Gnome Display Manager:/var/lib/gdm:/bin/false
saned:x:106:113::/home/saned:/bin/false
pulse:x:107:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
messagebus:x:108:117::/var/run/dbus:/bin/false
polkituser:x:109:118:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:119:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:120:Hardware abstraction layer,,,:/var/run/hald:/bin/false
speech-dispatcher:x:112:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
couchdb:x:113:116:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
kernoops:x:114:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
ntp:x:115:124::/home/ntp:/bin/false
user:x:1000:1000:user,,,:/home/user:/bin/bash
user@user-desktop:~$ 

```




**sudo getent shadow $USER|cut -d : -f 1,3-**

```

user@user-desktop:~$ sudo getent shadow $user|cut -d : -f 1,3-
[sudo] password for user: 
root:14656:0:99999:7:::
daemon:14354:0:99999:7:::
bin:14354:0:99999:7:::
sys:14354:0:99999:7:::
sync:14354:0:99999:7:::
games:14354:0:99999:7:::
man:14354:0:99999:7:::
lp:14354:0:99999:7:::
mail:14354:0:99999:7:::
news:14354:0:99999:7:::
uucp:14354:0:99999:7:::
proxy:14354:0:99999:7:::
www-data:14354:0:99999:7:::
backup:14354:0:99999:7:::
list:14354:0:99999:7:::
irc:14354:0:99999:7:::
gnats:14354:0:99999:7:::
nobody:14354:0:99999:7:::
libuuid:14354:0:99999:7:::
syslog:14354:0:99999:7:::
klog:14354:0:99999:7:::
hplip:14354:0:99999:7:::
avahi-autoipd:14354:0:99999:7:::
gdm:14354:0:99999:7:::
saned:14354:0:99999:7:::
pulse:14354:0:99999:7:::
messagebus:14354:0:99999:7:::
polkituser:14354:0:99999:7:::
avahi:14354:0:99999:7:::
haldaemon:14354:0:99999:7:::
speech-dispatcher:14644:0:99999:7:::
couchdb:14644:0:99999:7:::
kernoops:14644:0:99999:7:::
ntp:14644:0:99999:7:::
user:14644:0:99999:7:::
user@user-desktop:~$ 




```


Not sure what this means.

---

### Post by cdenley on 2010-03-16
In linux, commands are case-sensitive. That output seems correct, though.

---

### Post by cariboo on 2010-03-16
When you see $USER or $user, you are supposed to use your user name.

---

### Post by cdenley on 2010-03-17
> **cariboo907 said:**
> When you see $USER or $user, you are supposed to use your user name.

Actually, using $USER would've been fine since the shell uses the "USER" variable, which is the current user's username. There is no "user" variable, though.

---

### Post by chiques on 2010-03-26
> **cdenley said:**
> Actually, using $USER would've been fine since the shell uses the "USER" variable, which is the current user's username. There is no "user" variable, though.



I guess using 'user' as a username was not very wise. How can I wipe all of this out? Reinstall all of Ubuntu?

---

