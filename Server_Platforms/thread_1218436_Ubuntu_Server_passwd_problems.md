---
title: "Ubuntu Server passwd problems"
date: 2009-07-20
forum: Server Platforms
---

### Post by arkainus on 2009-07-20
Hi All,
 
Question here from someone who is new to Ubuntu. I decided to give this OS a try and have installed Ubuntu 9.04 server edition. After reading several forums I decided to keep it at the command line interface and no gui. I read several sites and used the instructions located at this site to get my box joined up to my windows domain environment:
[http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html](http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html)
 
using likewise. Even though the instructions stated it was for 8.04, it worked without a hitch on 9.04. 
 
I have since tried adding new users to the box and the creation of the user account works fine, but it does not create a password (that I know of at least) nor will the system allow me to use the passwd command.
 
I have tried both adduser and useradd --password and it will not report an error but when I try the password I specified in --password it fails to login as invalid password. When i go to use the passwd command I get the following message:
 
passwd: Authentication token manipulation error
passwd: password unchanged
 
This message persists no matter if I am trying to change MY password logged in as myself, logged in as root, etc. Browsing around to several sites people seem to think it was a problem with shadowing and recommended creating a backup of /etc/shadow, deleting the original and running the pwconv command. I have done this and I continue to get this error. 
 
Does anyone at all have any familiarity with this issue?? Any help whatsoever would be HUGELY appreciated as I cannot seem to get past this point. 
 
permissions for shadow are:
-r--rw---- 1 root root 1153 2009-07-20 11:31 shadow
 
permissions for passwd are:
-rw-r--r-- 1 root root 1742 2009-07-20 11:31 passwd
 
Thank you in advance for any help you may be able to provide.

---

### Post by wojox on 2009-07-20
I just use:

```
sudo adduser <whoever>
```

replace <whoever> with user like wojox.
And it goes from there.

---

### Post by arkainus on 2009-07-20
> **wojox said:**
> I just use:
 
```
sudo adduser <whoever>
```
 
replace <whoever> with user like wojox.
And it goes from there.
 
 
I run through that and I get Adding user 'test'...
Adding new group 'test' (1003) ...
Adding new user 'test' (1002) with group test...
Creating home directory '/home/test' ...
copying files from '/etc/skel'....
passwd: Authentication token manipulation error
passwd: password unchanged
Try again? [y/N]
 
:frown:

---

### Post by grantemsley on 2009-07-21
Check the file permissions for /usr/bin/passwd

It should have the user and group root.

Another possibility is that /etc/password and/or /etc/shadow is corrupt, invalid or has bad permissions.



BTW - googling the error message helps... plenty of info for "authentication token manipulation error"

---

### Post by arkainus on 2009-07-21
> **grantemsley said:**
> Check the file permissions for /usr/bin/passwd
 
It should have the user and group root.
 
Another possibility is that /etc/password and/or /etc/shadow is corrupt, invalid or has bad permissions.
 
 
 
BTW - googling the error message helps... plenty of info for "authentication token manipulation error"
 
/usr/bin/passwd has the following permissions:
 
-rwsr-x-r-x 1 root root 37084 2009-04-03 22:45 passwd (highlighted in red)
 
As per the explanation of the openning post I did perform a google search of that error message and out of 10 to 15 different sites browsed everyone was suggesting that /etc/shadow was corrupt and to make a backup of it and then delete it and then run the command pwconv, all steps that I did. After doing that I was unable to log back into the machine, and had to do the restore trick where you edit the kernel line to be ro init=\bin\bash to be thrown into the root (as regular restore mode kept asking me for a password and nothing I had worked). Trying the passwd command with this new shadow file created by pwconv still gave me the authentication token error as above so I just restored the old shadow file as that didn't seem to be the problem. And as you can see, the permissions seem to be correct for the files, so I do not think it is that.

---

### Post by grantemsley on 2009-07-21
Ok, my fault for not seeing that you had tried google...I'm sorry.

My permissions for the shadow file are:
-rw-r----- 1 root shadow 2166 2009-07-06 18:11 shadow

Perhaps that is part of your problem?

---

### Post by arkainus on 2009-07-21
> **grantemsley said:**
> Ok, my fault for not seeing that you had tried google...I'm sorry.
 
My permissions for the shadow file are:
-rw-r----- 1 root shadow 2166 2009-07-06 18:11 shadow
 
Perhaps that is part of your problem?
 
 
I did a chmod 640 for the /etc/shadow file to match the above permissions and changed the group ownership to shadow and I still get the 
 
passwd: Authentication token manipulation error
passwd: password unchanged 
 
error

---

