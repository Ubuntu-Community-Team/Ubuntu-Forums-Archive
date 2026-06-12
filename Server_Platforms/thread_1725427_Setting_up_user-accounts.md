---
title: "Setting up user-accounts"
date: 2011-04-09
forum: Server Platforms
---

### Post by Dry Lips on 2011-04-09
Hi!

I've got an old computer running Ubuntu Server 8.04 for educational 
purposes... (LAMP) I'm trying to create a user locked to his home directory, 
and using the commandos below didn't give me any error messages, 
but I still cannon log into the account I've set up using FileZilla. 
(The shell /bin/false is to prevent the user from using telnet.) After 
creating the backup directory I tried:
 
 ```
sudo useradd backup -p myspasswordhere -d /var/www/backup -s /bin/false
``` and then
```
sudo chown -hR backup /var/www/backup
```What am I doing wrong?

---

### Post by Dry Lips on 2011-04-10
I've found out what the problem was. I thought doing *useradd -p *
and adding a password (see the code above) would set a password
 to the account I was setting up. According to *useradd --help*
 the *-p* option  sets &#8220; *encrypted password for the new user  account *&#8221;. 
Now, whatever the *-p* option does, you need to set a password for 
your account using *passwd* afterwords. *-p* isn't enough in this respect. 

Does any of you know why?

---

