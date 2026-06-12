---
title: "Deny Local Logon"
date: 2010-09-17
forum: Server Platforms
---

### Post by roystreet on 2010-09-17
Hello,
....I am using 10.04 & Samba is working wonderfully with my windows machines.  I perform most of my admin type of work via webmin.  I have a user in which I would like to only be able to use Samba & not logon in locally to the server.  Which of course, means they can't logon via the terminal.  I use puTTY quite a bit also & I thought there was a way to deny users from logging in to that.
.
Can anyone help me out here?
~Thanks, roystreet

---

### Post by e79 on 2010-09-17
As puTTY use SSH, then restrict SSH login to specific users:
taken from [https://help.ubuntu.com/10.04/serverguide/C/user-management.html](https://help.ubuntu.com/10.04/serverguide/C/user-management.html)
 
Restrict SSH access to only user accounts that should have it.  For  example, you may create a group called "sshlogin" and add the group name  as the value associated with the AllowGroups variable located in the file /etc/ssh/sshd_config.
```
**AllowGroups sshlogin**
```Then add your permitted SSH users to the group "sshlogin", and restart the SSH service. ```
**sudo adduser username sshlogin**[B]
sudo /etc/init.d/ssh restart[/B]
```Unfortunately, I don't know how to achieve this for the local console login, I hope someone else will be able to help you on that.

Regards

---

### Post by Fraaik on 2010-09-18
Hello,

you can also do

```

sudo adduser --disable-login --no-create-home --gecos "<username>" username

```cheers, fraaik

---

### Post by kevinthecomputerguy on 2010-09-18
Roystreet-
Samba users and local users are not the same thing. For example if you had a local account named "kevin" this is not kevins samba account. It isnt until you run "smbpasswd -a kevin" that your actually making a samba account.
 
So just never make user "kevin" a local account, and only make him a samba account, and your all set. Think of a local account as am ssh \ ftp \ putty \ terminal account, and think of a samba account as a share users account, and that will help paint a picture of what is happening.
 
*Unless your using webmin, and have checked that really cool option that makes a samba account everytime you make a local account, in that case, just un-check it when making accounts you wish to not have both, then check it back when done.
 
-KevinTheComputerGuy

---

### Post by roystreet on 2010-09-18
Hi kevinthecomputerguy,
...Thank you for responding.  Don't you need a user account on the server before you can give them Samba access?  Isn't that also how you can even more directly give them certain read/write rights to different areas on the server?  I'm just trying to get the right understanding here.

Thanks,
~roystreet

---

### Post by kevinthecomputerguy on 2010-09-18
Roystreet-
 
[FONT=Calibri][SIZE=3]It really depends on your needs.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Your immediate fix \ answer is no, they are not the same list of users, so just don&#8217;t create them on the local system and your set. If they only have a samba account, then all they can do is samba.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I choose to use the i-will-punch-you-in-the-throat-if-you-touch-my-computer approach when worrying about local threats within my own house \ network. So if you&#8217;re worried about a family member or roommate logging in locally, try punching them in the throat. Or using the security role=share in your smb.conf, so your samba users don&#8217;t need a local account.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Or you can take a more standard approach and make your server bullet-proof, controlling who can sudo and local file permissions to where it doesn&#8217;t matter if they login locally, because they won&#8217;t have rights to do anything. But still punch them in the throat if they touch your computer.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Linux is fully customizable. You could change that users shell, you could take away device rights for that user, it&#8217;s really limitless. But for your scenario, just make it to where their local login is mostly useless, and they will get bored and never login again. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*Keep in mind, in the security world, if they have local physical access to your computer, then you&#8217;re done, your hacked, they can boot off a cd, take out your hard-drive, etc&#8230; so really control who has local physical access to your computer. But in practice, just lock it down and you will be ok. Take away ssh and sudo rights, and your 90% the way there.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Kev[/SIZE][/FONT]

---

### Post by e79 on 2010-09-19
> **kevinthecomputerguy said:**
> 
*Unless your using webmin, and have checked that really cool option that  makes a samba account everytime you make a local account, in that case,  just un-check it when making accounts you wish to not have both, then  check it back when done.

I decided to play with '**webmin**' ([http://www.webmin.com/](http://www.webmin.com/)) and the Samba modules in a virtual machine and here some screens of few interesting things :

1) You can specify whether you want a home or not for the users you create (see no-homes.png - at the bottom)  but it will not have the same effect than '**Fraaik**' command line, and will not prevent from login on locally.

2) You can also configure an  'automatic synchronization' as '**KevinTheComputerGuy**' stated  (see unix-samba-users.png - at the bottom),between the Unix and Samba user's database, then, each time you create a Unix user on the system it creates the same user in Samba as well.

And there's a lot more you can do with this nice tool !

Just wanted to share  :)

---

### Post by Bachstelze on 2010-09-20
> **e79 said:**
> 
1) You can specify whether you want a home or not for the users you create (see no-homes.png - at the bottom) thus, preventing them to log on locally. It has probably the same effect as 'Fraaik' command line.

Uh, no. The lack of a home directory does not prevent a user from logging in.

---

### Post by e79 on 2010-09-20
> **Bachstelze said:**
> Uh, no. The lack of a home directory does not prevent a user from logging in.

Thanks for pointing my noob mistake, I stand corrected as is my post.

---

### Post by roystreet on 2010-09-20
Please excuse my confusion...
...How you do you create Samba user that don't have an account on the server?  How am I to assign permissions?  The servers permissions supersede Samba permissions (As far as I've seen)
.
Sorry about the confusion...I've just never created a Samba user that doesn't have a local account on the server, even if the user never planned on logging into the machine.  In fact, I didn't know you could.
.
Thanks,
~roystreet

---

### Post by kevinthecomputerguy on 2010-09-20
Roystreet-
 
Just change the role
-Edit smb.conf
 
#security=user
security=share
 
-save
-exit
-reboot
 
Then use Samba to control the read \ write rights. (super easy in webmin)
 
-Kevinthecomputerguy

---

### Post by roystreet on 2010-09-24
Thanks everyone for your thoughts. I haven't entirely tested the last thing you sugessted kevin.  I'm still a little slow to try that because I don't want to possibly lose total Samba access.  Maybe I'm a little too worried :)

---

### Post by kevinthecomputerguy on 2010-09-24
Roystreet-
Your smart to not dive into that setting, good job.
 
But if you can't punch people that are touching your keyboard, atleast you have some other options.
 
: - )
 
-Kevin

---

