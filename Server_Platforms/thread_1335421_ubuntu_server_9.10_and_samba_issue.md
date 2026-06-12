---
title: "ubuntu server 9.10 and samba issue"
date: 2009-11-23
forum: Server Platforms
---

### Post by mjfroggy on 2009-11-23
Hello,

I have been having issues for a few weeks with setting up Samba which I thought maybe if I stop and then comeback to it I would be able to figure out but I am still at a loss.

I have samba and smbfs installed and I edited the smb.conf file what I thought was the correct why but guess not. The server is on an intranet network so it is reachable by hostname I am attaching screenshots hoping this will help someone with looking at it and seeing what I maybe am missing.

The goal is to map to perminentaly map my xp desktop machine to the var/www folder on the server

I have also setup a username and password which is the same as my ssh login.

now when I try to map to the server on my windows xp desktop I get a error saying the network path \\lidevbox\tadmin could not be found.
Yes I can open up a browser on any desktop in the building and get to the website at [http://lidevbox](http://lidevbox)

???
any suggestions
thanks

---

### Post by Charlietje on 2009-11-23
Hi,

a /etc/samba/smb.conf could be something like that

```
[global] 
  workgroup = CARL 
  server string = %h server (Samba, Ubuntu) 
  dns proxy = no 
  log file = /var/log/samba/log.%m 
  max log size = 1000 
  syslog = 0 
  panic action = /usr/share/samba/panic-action %d 
  security = user 
  encrypt passwords = true 
  passdb backend = tdbsam 
  obey pam restrictions = yes 
  unix password sync = yes 
  passwd program = /usr/bin/passwd %u 
  passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdate\ssuccessfully* . 
  pam password change = yes 
  map to guest = bad user 
  usershare allow guests = yes

[homes] 
  comment = Home Directories 
  browseable = yes 
  writable = yes 
**[data] **
  comment = Data Share 
  path = /data/ 
  browsable = yes 
  valid users = carl 
  read users = carl 
  write users = carl writable = yes 
  writable = yes 

```

After that you should restart the samba service

Then you need to add a samba user like that

```
smbpasswd -a carl
```

on your XP machine you should be able to reach your server by

\\servername\**data**

---

### Post by mjfroggy on 2009-11-23
thanks that helped a lot!!

but now I want to map to the home/var/www/ directory which is where the internal website I need to build will love. so what do I change the path = /data/ line to?? I tried changing it to 

path = /var/www/

which does not work ??

thanks for all your help

---

### Post by Denbert on 2009-11-23
> **mjfroggy said:**
> thanks that helped a lot!!

but now I want to map to the home/var/www/ directory which is where the internal website I need to build will love. so what do I change the path = /data/ line to?? I tried changing it to 

path = /var/www/

which does not work ??

thanks for all your help

```
chown -R user /var/www/
```

Should do the trick - user being webmaster e.g. www-data

---

### Post by mjfroggy on 2009-11-24
thanks for the help so far

so on the command line I entered

```

chown -R tadmin /var/www/

```

tadmin being the username I use to ssh into the server and the username I plan on using to samba into the server with.

now when I try to map to the server it does not bring me to the www folder like I need it to. I know its not the www fol,der because in my www folder I have the apache2 default index.html file.

Anyway in my smb.conf file I have what was outlined in the post by Charlietje however I replaiced all instances of "carl" with tadmin and where it says path = /data/  I replaced that with path = /var/www/  

so I must be missing a step some where?

thanks again all

---

### Post by Charlietje on 2009-11-24
In the config file you replace
```
**[data]** with **[www]**    and
**path = /data/**  with **path = /var/www/**
``` 


after that you execute the command
```
smbpasswd -a tadmin
```


you restart the samba server 
```
sudo /etc/init.d/samba restart
```


on your XP machine, you can map the share like that

```
net use w: /user:tadmin \\servername_or_ip\www /persisten:yes
```

---

### Post by mjfroggy on 2009-11-24
thanks!!

---

