---
title: "Accidentally unticked all permissions of user..."
date: 2010-01-20
forum: Security
---

### Post by Geweten on 2010-01-20
Hi all, checked the internet and this site and couldn't find a clear solution for ubuntu 9.04.

I allready reinstalled 9.04 instead of 9.10 because of bugs...

Now in 9.04 a user can make files, but somehow looses permission to delete or write...

I figured it had to do something with the user/ group permissions and tried so many things, that I finally accidentally "unticked" all permissions of my "superuser"...:(

How can I give my user permissions again via comandline ?
Because login with root seems to be impossible in 9.04...

It would be so easy to log in as root, go-to system->admin->Usr&grps...

But nope... Could any one ease my pain ? ;)

THX!

---

### Post by sisco311 on 2010-01-20
If you have enabled the root account, then run:
```
su -c "gpasswd -a $USER admin"
```
If not, then boot in the Recovery Mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by Geweten on 2010-01-21
Thx for helping me finding the path "sisco311" !!:KS

I first tried your code and this didn't work...

I got some error message " not in sudoers list"
and later "sudo not allowed as user"

Then I read your link and :

- went to recovery mode
- picked root shell
-  sudo cp /etc/sudoers /etc/sudoers.backup
- sudo nano /etc/sudoers

and modified line : "Defaults **       !lecture,tty_tickets,!fqdn**"
(I even believe that this line arranges permission issues with files/ disks I had ?! At first sight...)

- then did : "adduser *myusername* admin"
- exit

Rebooted and tahdah !! 
Maybe the adduser command would have been enough, but I went for the full option !
THX SISCO311, think I can use my braincells for an other queste now !:popcorn:

Now I hold my breath, because the update mgr just has another update ready...:confused:

Cheers !

---

