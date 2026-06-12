---
title: "SSH :  /bin/sh: Permission denied"
date: 2012-08-01
forum: Server Platforms
---

### Post by albertdiones on 2012-08-01
Hi, I created a new user on my VPS and but when trying login on SSH (using putty) it immediately closes and putty's log reads:
```
login as: xxxxxx
xxxxxx@yyyyyy.zz's password: 
Welcome to Ubuntu 12.04 LTS (GNU/Linux 2.6.32-042stab056.8 x86_64)

 * Documentation:  https://help.ubuntu.com/
Last login: Wed Aug  1 22:06:58 2012 from 120.28.84.122

/bin/sh: Permission denied

```Can you please suggest what we should do? My own sudoer, non-root  user works but this new user doesn't.

Here's the ls of the sh files on /bin
```
/bin$ ls -ld *sh*
-rwxr-xr-x 1 root root 955024 Apr  3 19:58 bash
lrwxrwxrwx 1 root root     21 Jul 20 01:23 csh -> /etc/alternatives/csh
-rwxr-xr-x 1 root root 109768 Mar 29 22:53 dash
lrwxrwxrwx 1 root root      4 Apr  3 19:58 rbash -> bash
lrwxrwxrwx 1 root root      4 Mar 29 22:53 sh -> dash
lrwxrwxrwx 1 root root     13 Oct 14  2011 tcsh -> /usr/bin/tcsh
```Thanks in advance

---

### Post by Loki57701 on 2012-08-01
It's possible that the wrong shell was assigned to the user, or permissions may be wrong for the .basrc file in that users home dir. 


Please post the output of this command:

```

cat /etc/passwd | grep user

```

Or 

```

cat /etc/passwd | awk -F: '/user/ {print $7}'

```

Obviously replace 'user' with the username of the user you are having issues with.


Also, check the permissions of the .bashrc file in the users home directory.

```

ls -al /home/username | grep .bashrc

```

---

### Post by albertdiones on 2012-08-02
Hi! Thank you for the reply,

the output of `cat /etc/passwd | grep xxxxxx`is

```
xxxxxx:x:1004:1004::/home/xxxxxx:/bin/sh
```

and `cat /etc/passwd | awk -F: '/xxxxxx/ {print $7}'`

```
/bin/sh
```

and the out put of ls -al /home/xxxxxx | grep .bashrc

is blank


what do you think?

---

### Post by Loki57701 on 2012-08-02
Try the following only if you are using the server version of Ubuntu. If you are using the desktop version just use the admin tools to do everything. 

**Option 1:**
The easiest way to fix this is by re-creating the user.

(as root or with sudo)

First remove the user:
```

userdel -r username

```
 
Again, replace 'username' with the user you are troubleshooting.


Create a new user:
```

useradd -m -s /bin/bash -c "add a comment about the user" -g groupname username

```

Replace 'groupname' and 'username' as appropriate.

I think I covered just about all the option you need above. Not every OS behaves the same way.

-m creates a home directory for the user
-s sets the shell type (In this case bash)
-c adds an optional comment for the user - name, role, ect..
-g name of the primary group

Make sure to set the password or the account will be locked:
```

passwd username

```


----------------------------------------------------------

**Option 2:**

If you cannot delete the user for whatever reason, or you just want to, go this route:

(as root or with sudo)

Set the shell:
```

usermod -s /bin/bash username

```

Copy default profiles:
```

cp /etc/skel/.bashrc /home/user/.bashrc
cp /etc/skel/.profile /home/user/.profile

```

You don't necessarily need .profile, but just in case.  

Set the correct permissions:
```

chown username:groupname /home/user/.bashrc
chown username:groupname /home/user/.profile
chmod 644 /home/user/.bashrc
chmod 644 /home/user/.profile

```

I think that should fix everything. Either log out and login with the new user, or use su.

---

### Post by albertdiones on 2012-08-07
sorry for the late reply

I tried the 2nd one and here's what I got:

> =~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2012.08.08 06:29:04 =~=~=~=~=~=~=~=~=~=~=~=
login as: xxx xxx
[email]xxxxxx@yyy.yy[/email]'s password: 
Access denied
[email]xxxxxx@yyy.yy[/email]'s password: 
Welcome to Ubuntu 12.04 LTS (GNU/Linux 2.6.32-042stab056.8 x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Wed Aug  8 02:25:37 2012 from 124.107.191.62

/bin/bash: Permission denied


which appears to be the same thing?

Here's the output of `ls -l /bin/*sh*`
```

-rwxr-xr-x 1 root root 955024 Apr  3 19:58 /bin/bash
lrwxrwxrwx 1 root root     21 Jul 20 01:23 /bin/csh -> /etc/alternatives/csh
-rwxr-xr-x 1 root root 109768 Mar 29 22:53 /bin/dash
lrwxrwxrwx 1 root root      4 Apr  3 19:58 /bin/rbash -> bash
lrwxrwxrwx 1 root root      4 Mar 29 22:53 /bin/sh -> dash
lrwxrwxrwx 1 root root     13 Oct 14  2011 /bin/tcsh -> /usr/bin/tcsh
```

---

### Post by spjackson on 2012-08-07
What about permissions on / and /bin ?
```

ls -ld / /bin

```
Does this work?
```

sudo su name_of_problem_user /bin/sh -c "/bin/echo hello"

```

---

### Post by albertdiones on 2012-08-08
Here are the results:

```
drwxr-xr-x 24 root root 4096 Jun 30 12:11 /
drwxr-xr-x  2 root root 4096 Jun 30 13:13 /bin
```

while for: `sudo su name_of_problem_user /bin/sh -c "/bin/echo hello"`
```
su: User not known to the underlying authentication module
```Thanks :)

---

### Post by hawkmage on 2012-08-08
I have that error if the /etc/shadow file is missing, empth or doesn't have an entry for the user.

Do you get an error for the user if you run:
```
sudo pwck
sudo grpck
```
You will likely have a bunch of errors for daemon users but you can ignore them.  
 
If you do get errors on accounts other than the daemon usersthen run:
```
sudo pwconv
sudo grpconv
```

---

### Post by albertdiones on 2012-08-10
`sudo pwck` gives me this:

```
user 'lp': directory '/var/spool/lpd' does not exist
user 'news': directory '/var/spool/news' does not exist
user 'uucp': directory '/var/spool/uucp' does not exist
user 'list': directory '/var/list' does not exist
user 'irc': directory '/var/run/ircd' does not exist
user 'gnats': directory '/var/lib/gnats' does not exist
user 'nobody': directory '/nonexistent' does not exist
user 'bind': directory '/var/cache/bind' does not exist
user 'klog': directory '/home/klog' does not exist
user 'syslog': directory '/home/syslog' does not exist
user 'mysql': directory '/nonexistent' does not exist
pwck: no changes
```

while `sudo grpck` gives me nothing


I ran both
```
sudo pwconv
sudo grpconv
```

but it results to:

> =~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2012.08.11 08:27:58 =~=~=~=~=~=~=~=~=~=~=~=
login as: xxxxxx
[email]xxxxxx@yyyyyy.yy[/email]'s password: 
Access denied
[email]xxxxxx@yyyyyy.yy[/email]'s password: 
Welcome to Ubuntu 12.04 LTS (GNU/Linux 2.6.32-042stab056.8 x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Sat Aug 11 04:26:10 2012 from 124.107.191.62

/bin/bash: Permission denied

which is pretty much the same thing... any other ideas? :(

---

### Post by hawkmage on 2012-08-10
Annother thing that can cause an error like that is a corrupt or bad pam configuration.  Can you check yours the files are under /etc/pam.d.

On one of my Ubuntu 12.04 systems I have the following (I used the grep to eliminate the commented/blank lines):
```
hawkmage@ubuntu:~$ grep '^[^#]' /etc/pam.d/sshd 
auth       required     pam_env.so # [1]
auth       required     pam_env.so envfile=/etc/default/locale
@include common-auth
account    required     pam_nologin.so
@include common-account
@include common-session
session    optional     pam_motd.so # [1]
session    optional     pam_mail.so standard noenv # [1]
session    required     pam_limits.so
@include common-password

hawkmage@ubuntu:~$ grep '^[^#]' /etc/pam.d/su
auth       sufficient pam_rootok.so
session       required   pam_env.so readenv=1
session       required   pam_env.so readenv=1 envfile=/etc/default/locale
session    optional   pam_mail.so nopen
@include common-auth
@include common-account
@include common-session

hawkmage@ubuntu:~$ grep '^[^#]' /etc/pam.d/common-auth 
auth    [success=1 default=ignore]    pam_unix.so nullok_secure
auth    requisite            pam_deny.so
auth    required            pam_permit.so
auth    optional    pam_ecryptfs.so unwrap
auth    optional            pam_cap.so 

hawkmage@ubuntu:~$ grep '^[^#]' /etc/pam.d/common-account 
account    [success=1 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    requisite            pam_deny.so
account    required            pam_permit.so
hawkmage@ubuntu:~$ grep '^[^#]' /etc/pam.d/common-session
common-session                 common-session-noninteractive  

hawkmage@ubuntu:~$ grep '^[^#]' /etc/pam.d/common-session
session    [default=1]            pam_permit.so
session    requisite            pam_deny.so
session    required            pam_permit.so
session optional            pam_umask.so
session    required    pam_unix.so 
session    optional    pam_ecryptfs.so unwrap
session    optional            pam_ck_connector.so nox11

hawkmage@ubuntu:~$ grep '^[^#]' /etc/pam.d/passwd 
@include common-password

hawkmage@ubuntu:~$ grep '^[^#]' /etc/pam.d/common-password 
password    [success=1 default=ignore]    pam_unix.so obscure sha512
password    requisite            pam_deny.so
password    required            pam_permit.so
password    optional    pam_gnome_keyring.so 
password    optional    pam_ecryptfs.so
```

---

### Post by albertdiones on 2012-08-13
Hi! thanks for the reply, here's the result of those commands:

> aaaaaa@bbbbbb:/etc/pam.d$ grep '^[^#]' /etc/pam.d/common-auth
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
auth    requisite                       pam_deny.so
auth    required                        pam_permit.so
aaaaaa@bbbbbb:/etc/pam.d$ grep '^[^#]' /etc/pam.d/common-account
account [success=1 new_authtok_reqd=done default=ignore]        pam_unix.so
account requisite                       pam_deny.so
account required                        pam_permit.so
aaaaaa@bbbbbb:/etc/pam.d$ grep '^[^#]' /etc/pam.d/common-session
session [default=1]                     pam_permit.so
session requisite                       pam_deny.so
session required                        pam_permit.so
session optional                        pam_umask.so
session required        pam_unix.so
aaaaaa@bbbbbb:/etc/pam.d$ grep '^[^#]' /etc/pam.d/passwd
@include common-password
aaaaaa@bbbbbb:/etc/pam.d$ grep '^[^#]' /etc/pam.d/common-password
password        [success=1 default=ignore]      pam_unix.so obscure sha512
password        requisite                       pam_deny.so
password        required                        pam_permit.so

---

### Post by hawkmage on 2012-08-13
The ones you posted look OK but what about the /etc/pam.d/su and /etc/pam.d/sshd files?

The pam files for su and sshd are the ones I was primarily interested in.  I included the common-auth, common-account, common-session, passwd and common-password since they are referanced by the other two.

---

### Post by albertdiones on 2012-08-16
Sorry for the late reply, here it is:

> xxxxxx@yyyyyy:~$ grep '^[^#]' /etc/pam.d/sshd
auth       required     pam_env.so # [1]
auth       required     pam_env.so envfile=/etc/default/locale
@include common-auth
account    required     pam_nologin.so
@include common-account
@include common-session
session    optional     pam_motd.so # [1]
session    optional     pam_mail.so standard noenv # [1]
session    required     pam_limits.so
@include common-password
xxxxxx@yyyyyy:~$ grep '^[^#]' /etc/pam.d/su
auth       sufficient pam_rootok.so
session       required   pam_env.so readenv=1
session       required   pam_env.so readenv=1 envfile=/etc/default/locale
session    optional   pam_mail.so nopen
@include common-auth
@include common-account
@include common-session

---

### Post by hawkmage on 2012-08-16
OK, you pam files look OK.  I even changed mine to have what you posted and they worked normily.  

This is a very odd issue.  If this doesn't work I am out of ideas.  I noticed that the size of the dash on the system is about 9Kb larger than what I have and the dash binary on recent versions of Ubuntu has not changed so I wonder if it have been corupted some how.  You can reinstall dash by running:
```
sudo apt-get install --reinstall dash
```

---

### Post by spjackson on 2012-08-17
> **hawkmage said:**
>   I noticed that the size of the dash on the system is about 9Kb larger than what I have and the dash binary on recent versions of Ubuntu has not changed so I wonder if it have been corupted some how.
OP's size is the same as I have. We are on 64-bit, and I guess you are not.

---

### Post by hawkmage on 2012-08-17
You are correct, the system I looked at is an old one that is 32 bit.  

OK, I am out of ideas.  Everything I can think of with has been checked or only fits one of tests.

---

### Post by albertdiones on 2012-08-19
:(

I once had made a terrible mistake of chmod -R the root but I recovered from it, I wonder if it has something to do with that, but the weird thing is why wouldn't it also happen on my sudoer user?

---

### Post by hawkmage on 2012-08-21
If you think is may be an issue with changed permissions the only way I can think of to really "fix" this is to reinstall the packages that contain the files that were screwed up.

If you take a look at the following page it will give you an idea of what is involved:
[http://hyperlogos.org/Restoring-Permissions-Debian-System](http://hyperlogos.org/Restoring-Permissions-Debian-System)

If you had debsums installed and initialised prior to the issue you may have been able to use it to list any discrepancies but I am not sure how it will work after the fact.

---

### Post by albertdiones on 2012-09-03
Hi HawkMage, Sorry for late reply;

Do you have idea which package should I reinstall? I am afraid it would reset my settings, would it?

---

### Post by hawkmage on 2012-09-03
It shouldn't change your settings but I can't make any guarantees.  I would start with openssh-server and openssl-client then possibly bash.

---

### Post by albertdiones on 2012-09-11
I tried it, got wild and I think I killed my server. LOL :lolflag:

I'll ask support to reinstall my OS.

I guess chmod`ing was really a very very serious mistake.

But thank you for all of you who took your time to help! ):P

---

### Post by albertdiones on 2012-09-11
Hi Hawkmage,

 I somehow made it work again after commenting some sysctl stuffs [http://ubuntuforums.org/showthread.php?t=1505356](http://ubuntuforums.org/showthread.php?t=1505356)

 And it's back.

Then I reinstalled the packages

and saw bind9 startup errors

 Then I saw this (your thread):
 [http://ubuntuforums.org/showthread.php?t=1698211](http://ubuntuforums.org/showthread.php?t=1698211)

 This is exactly my problem with the same syslog output (ie. no error)

 the $HOME thing didn't worked for me

 I've temporarily fixed it by using my own username as the -u

  Do you think this might be a clue to anything (regarding the SSH problem)?

  Or (off the topic) can you suggest other ways to fix it?

  Thanks in advance! :D

---

