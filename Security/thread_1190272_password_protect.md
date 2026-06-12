---
title: "password protect"
date: 2009-06-17
forum: Security
---

### Post by tcp91420 on 2009-06-17
very new to ubuntu. i want to password protect my web browsers firefox and opera. i also want to protect some folders. any ideas?

---

### Post by tcp91420 on 2009-06-17
very new to ubuntu. i want to password protect my web browsers firefox and opera. i also want to protect some folders. any ideas?

---

### Post by The Cog on 2009-06-17
For encrypted folders, google for ecryptfs and encfs. I use encfs, mainly because I heard of that one first. Others prefer ecryptfs. 

To also protect your browsers, maybe encrypting your entire home directory might be the best solution, for which ecryptfs is probably best. Your browser settings are stored in hidden folders such as .mozilla in your home folder.

---

### Post by bodhi.zazen on 2009-06-17
This is a recurring question. This is not windows.

In Linux, a user authenticates by logging into the system and access is governed by permissions.

You could "password protect" applications by giving each user a user name and password to log in with.

You then  change permissions on the binary to be owned by a group, say net , and add users to the net group if you wish them to use firefox.

sudo chown root.net firefox
sudo chmod 750 firefox

now users not in the net group can not run firefox.

QED

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by ManiacDan on 2009-06-17
Just set a password for your user account, and leave it at that.

Unless you want to have someone else also use the computer, in which case you should make them their own user account also, so they cannot see what goes on in your user account.  Once you do this, set your firefox configuration files to a folder in your home directly, and make them unreadable by anyone but you.

-Dan

---

### Post by akakingess on 2009-06-17
> **tcp91420 said:**
> very new to ubuntu. i want to password protect my web browsers firefox and opera. i also want to protect some folders. any ideas?
We may need some more details, like do you have multiple people logging in as you?, or do you want to keep other users from using said apps?, or trying to protect your home directory?  Let me know what exactly you are trying to do and I will see if I can be of assistance (I am fairly new to Ubuntu myself). Also, what version are you running? If you are running 9.04 (Jaunty Jackalope) then your home directory I believe is protected be default from other users unless they know your password.

akakingess

Looks like while I was typing a couple of others beat me to it, but let us know if those reponses answered your particular issue.

---

### Post by bodhi.zazen on 2009-06-17
Threads merged.

---

