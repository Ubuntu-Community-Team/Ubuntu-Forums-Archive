---
title: "Permission Issue with SAMBA Share"
date: 2008-01-22
forum: Server Platforms
---

### Post by ej00 on 2008-01-22
Here is my background:

I am setting up a file server at home for general backup for my computer and my kids computers. I basically want two types of users: parents and kids. I also want to shares: Share and Private. I would like to have parents be able to access both shares and kids only access Share.

So I went into KControl and set up two shares but am having troubles accessing them from Windows. I keep getting a permission denied when trying to access the Share folder from either account. Just to make sure it was not a permission issue with the folder, I created a share for my home account (for the kids) which I can then navigate down into the Share folder (for the kids but not the parents). Here is a summary of my issue:

parent: can access private but cannot access home or share.
kid: can access home but cannot access private or share. Note I changed the owner of the private folder to parent so I am OK with kid not being able to access private.

kid and parent are in the same group.
home belongs to kid

Kubuntu 7.10



Here are my smb.conf entries:

[homes]
valid users = %S
create mask = 0600
directory mask = 0775
browseable = no
read only = no
veto files = /*.{*}/.*/mail/bin/

[PRIVATE]
path = /home/server/private/
guest ok = yes
case sensitive = no
strict locking = no
msdfs proxy = no
read only = no

[SHARE]
path = /home/server/Desktop/Share/
guest ok = yes
case sensitive = no
strict locking = no
msdfs proxy = no
read only = no
valid users = kid,parent
create mask = 0774
directory mask = 0775

---

### Post by smileypaul on 2008-01-22
probably permissions on the /home/server/Desktop/Share

post the output of

ls -al /home/server/Desktop | grep Share

---

### Post by ej00 on 2008-01-22
drwxrwxrwx  3 kid server 4096 2008-01-21 11:34 Share

---

### Post by ej00 on 2008-01-22
Here is some more information if this helps anyone give me some clue. I did a little more testing and found the following. SHARE is on sda1 and PRIVATE is on sdb1. I tried setting up a shared folder in several places on sda1 but could not get access to it. It seems that the only share located on sda1 that I can access is the HOME share. Does this give anyone a clue???

---

### Post by ej00 on 2008-01-22
I figured this out. I don't know why but when I configured the SHARED share as follows (I took all other entries out) it worked.

[SHARE]
path = /home/kid/Desktop/Share/
guest ok = yes
read only = no

---

