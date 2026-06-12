---
title: "samba is making me go crazy"
date: 2008-12-22
forum: Server Platforms
---

### Post by Underpants on 2008-12-22
I'm really pulling my hair out on this. I've searched around and can't find anything....

I need a samba server in a windows environment. I've done this before and can't do it today. I don't know what I'm doing wrong. 

I need to be able to browse to the server \\servername and get prompted, immediately, for username and password. 

as it stands now, my config allows a windows client to browse to \\servername and list the shares. When you click on the shares it's a big ACCESS DENIED.

can anyone tell me what I'm doing wrong? I'm using Ubuntu 8.10



```
[global]
   workgroup = WORKGROUP
   server string = LNXCORP
   dns proxy = no

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######
   security = user

   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

   map to guest = bad user


[backup-corp]
path = /home/gwik/backup-corp
available = yes
browseable = yes
writable = yes
valid users = gwik



```

---

### Post by DrZoidy on 2008-12-22
yup it will do that lol. i had exactly the same problem. it took me around 4 days on and off to get a shared directory to work in windows as i dont have a cdrom on the server or a floppy drive i need to use networking to get files onto the server.

try this link [http://samba.netfirms.com/](http://samba.netfirms.com/) it help me and it worked, i am not an expert i have been working with ubuntu server 8.04 for all of five minutes but this definitely worked. 

i started by reading the first page and checking i had all the right bits in place like the matching workgroup names and setup of a samba password these are very important, also check you can ping the server. then i edited my smb.conf file i backed up the original renaming it to smb.conforg and then the actual smb.conf file that samba looks for i emptyed all of it and typed in what the tutorial told me to and it worked.

note i didnt type any of the [music], [everyone] or [apps] perams only the global and home.

NOW i have told you to do this and it worked for me i cannot vouch for its stability or security strength maybe some one who knows samba can do that for the both of us.....good luck.

---

### Post by albinootje on 2008-12-22
> **Underpants said:**
> 
I need to be able to browse to the server \\servername and get prompted, immediately, for username and password. 

as it stands now, my config allows a windows client to browse to \\servername and list the shares. When you click on the shares it's a big ACCESS DENIED.

I'm using Ubuntu 8.10



```

[backup-corp]
path = /home/gwik/backup-corp
available = yes
browseable = yes
writable = yes
valid users = gwik

```

Did you create the samba user with smbpasswd ?
Or are you using swat or webmin samba module ?

On the Linux-box you can check whether you can login with the smbclient command to possible see more error-messages.
```

smbclient //localhost/backup-corp -Ugwik

```
Check also the samba logfiles in /var/log/samba/ and put the log level in the samba config higher when needed.

---

### Post by CarolinaGuy on 2008-12-22
Temporarily COMMENT OUT this line in your smb.conf file
valid users = gwik

Either restart SAMBA or re-boot

You might try chmod 777 /home/gwik/backup-corp

CarolinaGuy

---

### Post by CarolinaGuy on 2008-12-22
Also run:

```
# testparm /etc/samba/smb.conf
```


The testparm program checks that the file is logically correct. I pretty certain I tried the user line and it LOCKED me out.

CarolinaGuy

---

### Post by albinootje on 2008-12-22
> **CarolinaGuy said:**
> Also run:

```
# testparm /etc/smb.conf
```


The testparm program checks that the file is logically correct. I pretty certain I tried the user line and it LOCKED me out.

If you don't use the ```
valid users =
``` line, then you give everyone else access.
That might not be what the OP wants.

---

### Post by CarolinaGuy on 2008-12-22
Yes, I agree that's true. When he determine what keeping him locked out of the share, he then needs to determine how to resolve the problem to maintain the desired security level for the share.


CarolinaGuy

---

