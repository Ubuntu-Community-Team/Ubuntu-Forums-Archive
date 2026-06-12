---
title: "[SOLVED] Samba Server on Hardy, Write access problem"
date: 2008-10-27
forum: Server Platforms
---

### Post by townclown on 2008-10-27
Hi, I am new to Ubuntu, and am running 8.04 Server using webmin 1.430. 

I have Apache installed and working fine, however the only way i can upload my files is via the webmin filemanager.. not ideal. I develop on a windows XP machine and as such have created a samba server and shared the WWW directory(Security is not an issue here)

I have tried everything to give write access to this share so that i can just ship files across from windows. First off, i cannot find out how to log onto the share as any user other than Guest - i set up a guest account and password on Hardy, but when i click the share from windows the option to change the user from guest is locked out. 

Even after enabling read/write access for everyone, i still cannot write to that share from windows. 

I admit being a linux noob, but as i have explored every option from the webmin side of things and have enable all that i can, no doubt making the share as unsecure as possible in the process!

Rather frustrated now, how the hell can i write to this share from windows?

Thanks in Advance,
Dazz

---

### Post by hyper_ch on 2008-10-27
install openssh-server on the server and then use WinSCP (or another sftp/scp program).

---

### Post by townclown on 2008-10-27
Thanks, but i really want a share that i can map to. As this is a testing machine i want to be able to edit the files on the server from Dreamweaver(on XP) to save time.

Are there issues with writing to such directories using Samba?

---

### Post by Sef on 2008-10-27
moved to server platforms.

---

### Post by cdenley on 2008-10-27
This is not a good idea as far as security is concerned. However, since this is a development server:
```

sudo chgrp -R admin /var/www
sudo chmod -R 775 /var/www

```
Then, assuming you have samba installed, configure a share like
```

[web]
    comment = my insecure development environment
    path = /var/www
    guest ok = no
    browseable = yes
    create mask = 0664
    directory mask = 0775
    read only = no
    valid users = @admin
    force group = admin

```
Make sure you set this in the global section of smb.conf
```

security = user

```
restart samba
```

sudo /etc/init.d/samba restart

```
Now any users in the admin group should be able to read/write to /var/www through samba.

---

### Post by townclown on 2008-10-27
Thanks for your help, i followed your instructions and can now at least specify a username and password, but it is denying me access completely now.

I have tried every login that is setup on the ubuntu side and everything gets denied. I checked the admin group and made sure all where a part of it - still nothing :(

The joys of learning linux i guess.

Dazz

---

### Post by cdenley on 2008-10-27
Maybe you have to set a samba password
```

smbpasswd

```

---

### Post by townclown on 2008-10-27
Thanks again for your help on this, 
The password was set, i gave it a new one to be a sure, still denying me. 

From the windows side, where you enter the name for the login to the share, it is just the linux username, ie: in my case just: dazz nothing like servername\username or anything like that?

---

### Post by cdenley on 2008-10-27
Post this output
```

smbclient -d 2 '\\localhost\web'

```
Are you logged in on windows as a user with the same name but different password? I think windows assumes if the username is the same, the password must be, too.

---

### Post by townclown on 2008-10-27
Output:


dazz@ubuntu:/etc/samba$ smbclient -d 2 '\\localhost\web'
params.c:Parameter() - Ignoring badly formed line in configuration file: directory mask 0775
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
added interface ip=192.168.0.100 bcast=192.168.0.255 nmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Password:
Domain=[UBUNTU.SERVER] OS=[Unix] Server=[Samba 3.0.28a]

---

### Post by townclown on 2008-10-27
windows login: Administrator, when i connect to ubuntu i dont get prompted for a uname, only when i try access the specific share do i get the prompt for username and password where i enter my linux username: dazz & corresponding password

---

### Post by alienprdkt on 2008-10-27
you can try the security = share

---

### Post by townclown on 2008-10-27
No change :(

---

### Post by cdenley on 2008-10-27
> **townclown said:**
> Output:


dazz@ubuntu:/etc/samba$ smbclient -d 2 '\\localhost\web'
params.c:Parameter() - Ignoring badly formed line in configuration file: directory mask 0775
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: C
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: D
params.c:Parameter() - Ignoring badly formed line in configuration file: A
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
params.c:Parameter() - Ignoring badly formed line in configuration file: B
added interface ip=192.168.0.100 bcast=192.168.0.255 nmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Password:
Domain=[UBUNTU.SERVER] OS=[Unix] Server=[Samba 3.0.28a]
Make sure you typed your share's configuration correctly. "directory mask 0775" is not valid. You seem to be able to connect successfully from ubuntu. Do you get a "smb: \>" shell? Can you run the "ls" command?

---

### Post by alienprdkt on 2008-10-27
[global]

# set YOURWORKGROUP to the name of your workgroup
 
workgroup = YOURWORKGROUP 
netbios name = server
server string = somethingthatmakessense
security = share 
encrypt passwords = yes 
guest account = guest 

path=/shared_directory
writeable=yes
browsable=yes
available = yes
valid users = USERNAME
read only = no
public = yes


don't forget to restart samba:
sudo /etc/init.d/samba restart

---

### Post by townclown on 2008-10-27
I believe all is correct; i get the smb shell and can run ls:



smb: \> ls
  .                                   D        0  Fri Oct 24 17:29:20 2008
  ..                                  D        0  Wed Oct 22 22:09:24 2008
  mysqltest.php                       A      923  Fri Oct 24 17:29:20 2008
  Dazz.Snippets                       D        0  Fri Oct 24 17:19:11 2008

---

### Post by townclown on 2008-10-27
WORKGROUP is correct.

Thanks for your help on this one guys, i appreciate it a lot, i am loathe to go back to WAMP for my testing environment.

This is proving seriously tricky.

Would installing a desktop version of ubuntu and setting it up to run the services i need via the GUI be any easier? - i don't exactly want to go that route in an attempt to do things properly - but i really know very little about linux.

---

### Post by alienprdkt on 2008-10-27
yes,
you can still run a LAMP configuration on the desktop version... i would definitely recommend the desktop version if you have no experience with Ubuntu or Linux.

Also Samba on desktop usually automatically will pick up windows shares on install.

---

### Post by cdenley on 2008-10-27
> **townclown said:**
> I believe all is correct; i get the smb shell and can run ls:



smb: \> ls
  .                                   D        0  Fri Oct 24 17:29:20 2008
  ..                                  D        0  Wed Oct 22 22:09:24 2008
  mysqltest.php                       A      923  Fri Oct 24 17:29:20 2008
  Dazz.Snippets                       D        0  Fri Oct 24 17:19:11 2008

As far as I can tell, samba is functioning correctly. You were able to connect to the share and list the files. I don't know why windows would be giving you problems, but it must be a windows problem.

---

### Post by townclown on 2008-10-27
Thanks, will try fiddling with windows and see what it could be, possibly all the fiddling has wrecked something that is cached.

---

### Post by townclown on 2008-10-28
Thanks that worked btw, windows had obviously cached previous data.

Thanks a million for your help.

---

