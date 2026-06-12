---
title: "Samba problems"
date: 2023-07-19
forum: Server Platforms
---

### Post by lokkete2 on 2023-07-19
Hello, I have a problem with Samba and I would like to know if someone can help... Thank you.


Samba is not creating files with the desired group:


I had "force group = arq" configured, and it was working perfectly. Suddenly, without any server updates, Windows clients lost access to the 'arq' resource. When I removed that line, access was restored, but now I have trouble maintaining the group. Samba saves the files with the user's primary group instead of the 'arq' group. Is there another way to force saving files under the 'arq' group, which the user already belongs to?


I don't have access from users in the 'arq' group:


For example, I have a user named 'xxx' who belongs to the 'arq' group (when checked). With file permissions set to 770, the user doesn't even have read access. It seems like Samba is using the 'others' permissions. Currently, I have to set the permissions to 774 (minimum for read and edit) so that Samba can save the file. It's worth mentioning that I don't have any issues when accessing files through Bash, which leads me to believe it's related to Samba. In fact, if I use the configuration line 'writer list = @arq', users belonging to the 'arq' group cannot save files.

Conclusion: When I set "force group," I am unable to log in. I didn't find anything useful in the logs, and when I log in from Windows, it says "group not found."

```
smb.conf


[global]
browseable = no
panic action = /usr/share/samba/panic-action %d
usershare allow guests = yes
passwd chat = Enter\snew\s\spassword:* %n\n Retype\snew\s\spassword:* %n\n password\supdated\ssuccessfully .
pam password change = yes
logging = file
read raw = no
log file = /var/log/samba/log.%m
server role = standalone server
workgroup = xxx
obey pam restrictions = yes
max log size = 1000
write raw = no
unix password sync = yes
map to guest = bad user
passwd program = /usr/bin/password %u


[homes]
comment = Home Directories
browseable = no
read only = yes
create mask = 0770
directory mask = 0770
valid users = %S


[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = no
read only = yes
create mask = 0700


[arq]
comment = arq
path = /smb/arq
read only = no
writable = yes
browsable = yes
valid users= @arq
force create mode = 0664
create mask = 0664
force directory mode = 0774
directory mask = 0774
```

---

### Post by Morbius1 on 2023-07-19
I am confused by your post.

> I had "force group = arq" configured, and it was working perfectly. Suddenly, without any server updates, Windows clients lost access to the 'arq' resource.
It's the "suddenly" part that is confusing unless the permissions of /smb/arq itself have changed. What are those permissions:
```
ls -dl /smb/arq
```

> Samba saves the files with the user's primary group instead of the 'plan' group. Is there another way to force saving files under the 'plan' group, which the user already belongs to?
Where did @plan come from and why were you using "force group = arq" if you wanted the files to save with group = plan?

And if you want members of the "plan" group to have acess to the share why isn't @plan part of the valid users line? Unless members @plan are also members of @arq?

---

### Post by lokkete2 on 2023-07-20
> **Morbius1 said:**
> I am confused by your post.


It's the "suddenly" part that is confusing unless the permissions of /smb/arq itself have changed. What are those permissions:
```
ls -dl /smb/arq
```


Where did @plan come from and why were you using "force group = arq" if you wanted the files to save with group = plan?

And if you want members of the "plan" group to have acess to the share why isn't @plan part of the valid users line? Unless members @plan are also members of @arq?

First of all, thank you for the response.

Sorry, I meant to say 'arq.' 'plan' is another shared resource with the same issue. To simplify the post, I used only one.
I going to correct that

Here are the permissions from 'arq' folder:
```

xxx@xxxxx:/smb$ ls -dl arq
drwxrwxrwx 16 root arq 4096 Jul 19 00:51 arq

```

and here you have de ACL permissions
```

xxx@xxxxx:/smb$ getfacl arq/
# file: arq/
# owner: root
# group: arq
user::rwx
group::rwx
other::rwx


xxx@xxxxx:/smb$

```

With this configuration, if I add 'force group = arq' , the windows 10 can't access. The user can access from the Linux console, but not through Samba.

---

### Post by Morbius1 on 2023-07-20
More confusion,

What is the relationship between the standard linux group of "arquitectura" and the ACL specified group of "arq" ?

Why are they different?

And what happens if you specify "force group = arquitectura" in smb.conf?

---

### Post by lokkete2 on 2023-07-20
> **Morbius1 said:**
> More confusion,

What is the relationship between the standard linux group of "arquitectura" and the ACL specified group of "arq" ?

Why are they different?

And what happens if you specify "force group = arquitectura" in smb.conf?

Yes, you are right. I replied to the post while I was running some tests. When I finished these tests, I left it with ''arq'. Sorry for the confusion.

Now I have...
```
berto@UBUNTU:~$ ls -dl /smb/arq
drwxrwxrwx 16 root arq 4096 Jul 19 00:51 /smb/arq
xxx@xxxxx:~$

```


```

smb.conf


[global]
browseable = no
panic action = /usr/share/samba/panic-action %d
usershare allow guests = yes
passwd chat = Enter\snew\s\spassword:* %n\n Retype\snew\s\spassword:* %n\n password\supdated\ssuccessfully .
pam password change = yes
logging = file
read raw = no
log file = /var/log/samba/log.%m
server role = standalone server
workgroup = xxx
obey pam restrictions = yes
max log size = 1000
write raw = no
unix password sync = yes
map to guest = bad user
passwd program = /usr/bin/password %u


[homes]
comment = Home Directories
browseable = no
read only = yes
create mask = 0770
directory mask = 0770
valid users = %S


[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = no
read only = yes
create mask = 0700


[arq]
comment = arq
path = /smb/arq
read only = no
writable = yes
browsable = yes
valid users= @arq
force create mode = 0664
create mask = 0664
force directory mode = 0774
directory mask = 0774

```

---

### Post by Morbius1 on 2023-07-20
When I can't see anything wrong with a setup I try to reproduce the error.

I made 2 changes in trying to reproduce your error: I used my own user ( tester ) and the group I used was plugdev since it already exists and I am already a member.

```
sudo mkdir -p /smb/arq
sudo chown :plugdev /smb/arq
sudo chmod 770 /smb/arq
```

Then I created the share definition per your setting but adding the force group directive:
```
[arq]
comment = arq
path = /smb/arq
read only = no
writable = yes
browsable = yes
valid users= @plugdev
force group = plugdev
force create mode = 0664
create mask = 0664
force directory mode = 0774
directory mask = 0774
```

I logged into the server from Win10 with the tester user name and added a file. Works fine for me:
> tester@vubsrv2204:~$ ls -al /smb/arq
total 8
drwxrwx--- 2 root   plugdev 4096 Jul 20 17:37 .
drwxr-xr-x 3 root   root    4096 Jul 20 16:35 ..
-rw-rw-r-- 1 tester plugdev    0 Jul 20 17:37 new-file-from-Win10.txt

I can't reproduce your error.

Mind you I would have done this a bit differently just to avoid the following scenario:

Say I want to add a file to the /smb/arq folder from within the server itself:
> tester@vubsrv2204:~$ touch /smb/arq/new-file-server-side.txt
tester@vubsrv2204:~$ ls -al /smb/arq
total 8
drwxrwx--- 2 root   plugdev 4096 Jul 20 17:38 .
drwxr-xr-x 3 root   root    4096 Jul 20 16:35 ..
-rw-rw-r-- 1 tester plugdev    0 Jul 20 17:37 new-file-from-Win10.txt
-rw-rw-r-- 1 tester tester     0 Jul 20 17:38 new-file-server-side.txt

The file saved server-side will have the primary group of the user not plugdev.

So a more classic(?) way of doing this would be:

Add the setgid bit to the shared folder so that all new files will inherit the group of the parent:
```
sudo chmod 2770 /smb/arq
```
And add the setgid bit to the share definition:
```
[arq]
comment = arq
path = /smb/arq
read only = no
writable = yes
browsable = yes
valid users= @plugdev
force group = plugdev
create mask = 0664
force directory mode = 2775
```

From the client nothing has changed except that all new folder will have the setgid bit set but on the server side when I add a new file it will save with the plugdev group:
> tester@vubsrv2204:~$ touch /smb/arq/new-file-server-side-2.txt
tester@vubsrv2204:~$ ls -al /smb/arq
total 8
drwxrwx--- 2 root   plugdev 4096 Jul 20 17:38 .
drwxr-xr-x 3 root   root    4096 Jul 20 16:35 ..
-rw-rw-r-- 1 tester plugdev    0 Jul 20 17:37 new-file-from-Win10.txt
-rw-rw-r-- 1 tester tester     0 Jul 20 17:38 new-file-server-side.txt
-rw-rw-r-- 1 tester plugdev     0 Jul 20 18:38 new-file-server-side-2.txt

---

### Post by lokkete2 on 2023-07-25
I found a solution; I don't have the same issue with the new groups. For some reason, Samba has a synchronization problem with the 'arq' unix group. My concern is to know the origin of the problem to prevent it from happening again. Thank you for your help....

Any idea about the cause?

---

