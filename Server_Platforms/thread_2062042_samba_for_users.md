---
title: "samba for users"
date: 2012-09-24
forum: Server Platforms
---

### Post by Rakeshvijayan on 2012-09-24
Hi friends

presently I configured samba for a user1 works fine for me .my wish is add an another 3 users in server and give their own share folder I don't know how to setup this ...is it possible to do so if so please help me to configure this 

thanks

---

### Post by Jorel on 2012-09-24
Hi,

you can do the basic:

adduser "username"

if it has a group then:

adduser "username" "groupname"

to add it to samba:

smbpasswd -a "username" (then add the password for that user)
smbpasswd -e "username" (to enable the user)

then configure the /etc/samba/smb.conf to create their share files..

---

### Post by Rakeshvijayan on 2012-09-24
> **Jorel said:**
> Hi,


then configure the /etc/samba/smb.conf to create their share files..
Hi friend  from this onwards is my doubt , which portion in smb.conf do I need to edit 
this portion 
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

need help

---

### Post by Jorel on 2012-09-24
Hi,

Most probably the settings of different users are the same except the path or if you wish for the different Shares to have different actions.

ex:

[User1]
 comment = User1 Files
 path = /home/samba/user1files
 guest ok = no
 browseable = yes
 valid users = user1, user2
 write list = user1
 read list = user2
 create mask = 0755

[User2]
 comment = User2 Files
 path = /home/samba/user2files
 guest ok = no
 browseable = yes
 valid users = user1, user2
 write list = user2
 read list = user1
 create mask = 0755

you can do some stuffs like that, because that settings worked for me, you can also check the "owner" and "group" of the file you wish to share, and you can add that at the very bottom of the page of the smb.conf, dont forget to mkdir the path for different folders of different users, you can change "/home" for the mount where your samba is located of path will be used.

---

### Post by Rakeshvijayan on 2012-09-25
is this is enough

---

### Post by Rakeshvijayan on 2012-09-25
> **Rakeshvijayan said:**
> [QUOTE=Jorel;12257694]Hi,

Most probably the settings of different users are the same except the path or if you wish for the different Shares to have different actions.

ex:

[User1]
 comment = User1 Files
 path = /home/samba/user1files
 guest ok = no
 browseable = yes
 valid users = user1, user2
 write list = user1
 read list = user2
 create mask = 0755

[User2]
 comment = User2 Files
 path = /home/samba/user2files
 guest ok = no
 browseable = yes
 valid users = user1, user2
 write list = user2
 read list = user1
 create mask = 0755

you can do some stuffs like that, because that settings worked for me, you can also check the "owner" and "group" of the file you wish to share, and you can add that at the very bottom of the page of the smb.conf, dont forget to mkdir the path for different folders of different users, you can change "/home" for the mount where your samba is located of path will be used.[/QUOT]
[reception]
comment = /home/reception
path = /home/reception/share
guest ok = no
browseable = yes
valid users = reception
write list = reception
read list = reception
create mask = 0755

I run chown -R  reception: /home/reception/share
reception is also a user in server
is this setting is enough

---

### Post by xdracco on 2012-09-25
Why not just use the [Homes] directive?

```
[homes]
  comment = H:\\%u (Home directory)
  path = /home/%u
  case sensitive = auto
  default case = lower
  preserve case = yes
  short preserve case = yes
  valid users = %S
  read list = %S
  write list = %S
  browseable = no
  public = no
  writeable = yes
  guest ok = no
  create mask = 0700
  directory mask = 0700
  veto files = /.apdisk/.Apple*/aquota.*/.bin/.DS_Store/lost+found/Network Trash Folder/*root*/Tempory Items/*.tmp/
  delete veto files = no
  hide dot files = yes
```This way you don't need to define each and every user in smb.conf. Once you add the user with smbpasswd, the user will instantly see his/her share once they authenticate.

---

### Post by Rakeshvijayan on 2012-09-26
ok friends I finally setup the samba for my firm I use you help THANKS is first replay for you all 
 This is my configuration 

1: I add user 

{useradd -m -s /bin/bash u1

2:make directory in home folder
 make dir /home/u1/share
sudo chmod 777 /home/u1/share
chown -R u1: /home/u1/share

3:editing smb.conf file /add this into share definition 
[u1]
comment = /home/u1
path = /home/u1/share
guest ok = no
browseable = u1
valid users = u1
write list = u1
read list = u1
create mask = 0777
save the smb.conf

4:sudo smbpasswd u1
service smbd restart

This configuration is working for me .

please give your advice to have do more option 

Thanks

---

### Post by critin on 2012-09-26
[Rakeshvijayan]("http://ubuntuforums.org/member.php?u=1187849"):

The bots and spammers are going to send you lots of junky spam with your email addy posted like this.

---

### Post by Rakeshvijayan on 2012-09-26
> **critin said:**
> [Rakeshvijayan]("http://ubuntuforums.org/member.php?u=1187849"):

The bots and spammers are going to send you lots of junky spam with your email addy posted like this.

Thanks friend .

---

### Post by critin on 2012-09-26
> **Rakeshvijayan said:**
> Thanks friend .

You're welcome.  I speak from experience.  lol

---

