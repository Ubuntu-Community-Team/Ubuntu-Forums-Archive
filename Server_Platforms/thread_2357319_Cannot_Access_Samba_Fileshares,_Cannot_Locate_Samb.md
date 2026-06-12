---
title: "Cannot Access Samba Fileshares, Cannot Locate Samba Log Files"
date: 2017-03-31
forum: Server Platforms
---

### Post by stricklettk on 2017-03-31
Here is where I'm at in a nutshell.

-The server has a static IP
-I can SSH into the server
-I can ping the Fileserver server from other locations
-The server is able to ping and even see drives on other machines
-The server can download from the outside world and ping google
-Either I don't know how to open and view log files, or they aren't there
-Log level is set to 3
-Please assume that all the folders are created appropriately according to the specified filepath and that all machines are in the specified workgroup

I'll post my smb.conf file below. I am rather green and may require some explanation on the syntax as I had been babied on Windows up until recently. All help is immensely appreciated as this is my home fileserver and I am still very much learning.



```
smb.conf:





[global]


   workgroup = STRICKLETTS
   log level = 3
   username map = /etc/samba/smbusers
   encrypt passwords = yes
   security = user
   netbios name = Fileserver




        server string = %h server (Samba, Ubuntu)


   wins support = yes


   dns proxy = no


   max log size = 1000
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


   server role = standalone server


   security = user


   passdb backend = tdbsam


   obey pam restrictions = yes


  unix password sync = yes
 passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


   pam password change = yes


   map to guest = bad user


   usershare allow guests = yes




[All Users]
   comment = Directory accessible to all users
   path = /home/samba/allusers
   read only = no
   browseable = yes
   create mask = 0777
   directory mask = 0777


# Windows clients look for this share name as a source
[Backup]
 comment = Backup
 path = /files/backup
 browseable = yes
 read only = no
 valid users = Kyle kyle
 writable = yes


[Media]
 comment = Media
 path = /files/media
 browseable = yes
 read only = no
 valid users = Kyle kyle
 writable = yes


[Tools]
 comment = Tools
 path = /files/tools
 browseable = yes
 read only = no
 valid users = Kyle kyle
 writable = yes





[Share]
   comment = Guest Share
   path = /srv/samba/share
   browseable = yes
   guest ok = yes
   read only = no
   create mask = 0755
```

---

### Post by wildmanne39 on 2017-03-31
*Thread moved to **Server Platforms**.*

---

### Post by wildmanne39 on 2017-03-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by CharlesA on 2017-03-31
Log files for Samba should be in /var/log/samba

How are you trying to access Samba? From Windows? If so, which version?

---

### Post by stricklettk on 2017-04-01
> **CharlesA said:**
> Log files for Samba should be in /var/log/samba

How are you trying to access Samba? From Windows? If so, which version?

I tried looking in that directory and got the response that there was no such file. I am using Windows 10 and Windows 7, neither device can see the server or shares in the network. How does one go about opening and reading those files? As in are you supposed to use vim or less? Apologies, I am pretty new with Ubuntu and I want to learn. Though the GUI would probably be much much more helpful about now. Anyways, if you could include syntax and try to dumb down explanations to me, I would greatly appreciate it. Thank you again!

---

### Post by stricklettk on 2017-04-01
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.


I'm pretty new, but I'll try my best. I love your profile picture.

---

### Post by CharlesA on 2017-04-01
> **stricklettk said:**
> I tried looking in that directory and got the response that there was no such file. I am using Windows 10 and Windows 7, neither device can see the server or shares in the network. How does one go about opening and reading those files? As in are you supposed to use vim or less? Apologies, I am pretty new with Ubuntu and I want to learn. Though the GUI would probably be much much more helpful about now. Anyways, if you could include syntax and try to dumb down explanations to me, I would greatly appreciate it. Thank you again!

You can use vim, nano, less or even cat to look at the logs. I usually prefer using tail, myself:

```
tail -n 25 /path/to/log
```

What version of ubuntu are you using? Are you using a firewall?

You can try running this on the server and see if it returns anything.

```
smbtree
```

---

### Post by stricklettk on 2017-04-02
> **CharlesA said:**
> You can use vim, nano, less or even cat to look at the logs. I usually prefer using tail, myself:

```

tail -n 25 /path/to/log

```

What version of ubuntu are you using? Are you using a firewall?

You can try running this on the server and see if it returns anything.

```
smbtree
```

I'm using version 16.04.2 LTS.  I'll try the code you posted above. I have turned off all firewalls on my computers. I'll look around in my router settings and see if there is a network firewall, if there is I'll add the static IP to the whitelist and let you know if that fixes it. And please excuse my naivety, but would I enter
```

tail -n 25 /path/to/log

``` 
Exactly into the keyboard or something more along the lines of
```
 
tail -n 25 /var/log/samba/smbd.log

```

---

### Post by cariboo on 2017-04-02
On my systems, the logs are located in /var/log/samba, and the two logs to look at are:

[LIST]
[*]log.nmbd
[*]log.smbd
[/LIST]

---

### Post by Morbius1 on 2017-04-02
> The server has a static IP
> I am using Windows 10 and Windows 7, neither device can see the server or shares in the network. 

On both Windows machines open Run and enter:
```
\\192.168.0.100
```
[COLOR=#0000cd]*Replace with the static ip address of the Ubuntu machine.*[/COLOR]

Do you gain access or not. If not what are the error messages?

BTW, You might want to check to see if the Linux permissions on the folders being shared match the autorization allowed in the share definitions.
```
ls -dl /home/samba/allusers
ls -al /files
ls -al /srv/samba
```

---

