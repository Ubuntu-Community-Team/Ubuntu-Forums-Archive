---
title: "shared directory between 2 users with Samba/cifs"
date: 2021-06-11
forum: Server Platforms
---

### Post by jfaberna on 2021-06-11
I have 2 user account on a desktop and I want them both to have access to a smb share on a server. Currently I can't seem to get the share mounted so the permissions are right.

Both my users are a member of group 'users'
I uses smbpasswd -a for both users
My smb.conf for the share is:

[Anonymous]
path = /mnt/md0/samba/anonymous
browsable =yes
writable = yes
guest ok = yes
read only = no
force group = users
force user = jim
create mask = 0774
force directory mode = 2775

However, the other user (not jim) can't write on the share.

The desktop with the problem for the second user has a fstab as follow:
//192.168.0.250/public /mnt/public cifs defaults,user=jim,password=123456,uid=jim,gid=users
//192.168.0.250/anonymous /mnt/anonymous cifs defaults,user=jim,password=123456,uid=jim,gid=users

What am I missing?

---

### Post by MAFoElffen on 2021-06-11
Answering this... but have lots to type... Will add it as an edit to another post.

---

### Post by MAFoElffen on 2021-06-11
You have it configured it locked down to just the one user... When you said, force user = Jim, then it limited to just Jim. 

Let me walk you through that as summarized...
```

# Creating the share called "anonymous".


sudo mkdir -p /mnt/md0/samba/anonymous

# Create the group users
sudo groupadd users


# Change the group ownership and permissions of the directory
sudo chgrp users /mnt/md0/samba/anonymous
&#8203;sudo chmod -R 770 /mnt/md0/samba/anonymous


# Add users to the group in the system
sudo usermod -a -G users Jim
sudo usermod -a -G users Jane


# Add the users to Samba
sudo smbpasswd -a Jim
&#8203;sudo smbpasswd -e Jane


```
If Samba security is set to allow verified users who used system credentials, then you don't need that last part... But you did say you locked it down to two users...

The in the Samba Config:
```

[global}
&#8203;workgroup = WORKGROUP
&#8203;server string = Name_Of_Server
&#8203;netbios name = Ubuntu
&#8203;security = user
&#8203;map to guest = bad user
&#8203;dns proxy = no


#### SHARES ####
[anonymous]
&#8203;path = /mnt/md0/samba/anonymous
&#8203;browsable = yes
&#8203;writable = yes
&#8203;guest ok = yes
&#8203;read only = no
&#8203;valid users = @users

```
At least, that is "one way" to set up groups to a Samba Share.

Personally, I would use a group name that is not as close to a system type of name. "users" is, well... LOL

---

### Post by jfaberna on 2021-06-12
I seem to have made it worse.  I made some changes to my smb.conf based on you response and now even the owner 'jim' can't list the directory.  I commented out the force and added the valid users. Then restarted smbd and nmbd . Here's the conf file:
```

[Anonymous]
path = /mnt/md0/samba/anonymous
browsable =yes
writable = yes
guest ok = yes
read only = no
#force group = users
#force user = jim
#create mask = 0774
#force directory mode = 2775
valid users = @users


```

I tried unmounting the share and when I tried to remount it I see this error in dmesg:

[35166.414246] CIFS: Attempting to mount //192.168.0.250/anonymous
[35166.425319] CIFS: VFS: cifs_mount failed w/return code = -13

---

### Post by jfaberna on 2021-06-12
Let me add that the goal here is to allow any users (of which there are only 2) to read and write to a smb share on a ubuntu server. If I need to create a complete new share pointing to the same directory on the server that is fine as well.

---

### Post by Morbius1 on 2021-06-12
Just so I understand: This is how your share was created originally:
> [Anonymous]
path = /mnt/md0/samba/anonymous
browsable =yes
writable = yes
guest ok = yes
read only = no
force group = users
force user = jim
create mask = 0774
force directory mode = 2775
And you are connecting to the share with this mount declaration on the client - can't seem to get rid of that space between user and s in the quote for some reason:
>  //192.168.0.250/anonymous /mnt/anonymous cifs defaults,user=jim,password=123456,uid=jim,gid=users
That mount declaration will create a mount of that share with permissions that look like this **[COLOR=#ff0000]on the client[/COLOR]**:
> drwxr-xr-x 2 jim users
That mounted share is owned and writeable only to jim - on the client.

This will make it so every user - [COLOR=#ff0000]at least every user who is a member of the "users" group **on the client**[/COLOR] - can write to the share:
```
 //192.168.0.250/anonymous /mnt/anonymous cifs defaults,user=jim,password=123456,uid=jim,gid=users,dir_mode=0775,file_mode=0664 0 0
```
Now your mount will have permissions that look look this:
> drwxrwxr-x 2 jim users 

---

### Post by jfaberna on 2021-06-12
Thank you, that worked. but I'm not sure I understand why I need to read up on samba/cifs.  So many of the references I found are either too complicated or too simple.

---

### Post by Morbius1 on 2021-06-12
I think the issue for some users is a conceptual one.

Samba uses a Client-Server model to do its thing.

A server never ever exposes the internal permissions of it's assets to the client. And the client never never never ever has any control over the permissions on the server.  But each one is free to do whatever it wants on it's own end.

When you do a cifs mount of a share you are creating on the client a "view" of that share with ownership and permissions that pertain to that client. For your particular mount expression you are passing to the server a username ( jim ) and password. From that moment on "jim" is the only user the server sees. It doesn't even know the other users on the client exist. 

But on the client you can have this share accessible by as many as you want: Only to jim the way it was before, To all members of the "users" group which is what you have now, or to every user on the client ( dir_mode=0777,file_mode=0666 ). To the server they are all "jim".

---

