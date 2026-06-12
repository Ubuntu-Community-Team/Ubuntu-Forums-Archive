---
title: "[SOLVED] Samba sharing, linux permissions and best practice"
date: 2008-06-26
forum: Server Platforms
---

### Post by batfastad on 2008-06-26
Hi everyone

I've got a RAID 6 array successfully formatted and mounted in Ubuntu Server 8.04. I'm now looking to share this device out to the network as a series of Samba shares. I'm not worrying about printers yet, I'll wait until I've got basic shares working until I get my printers on there.
I'm using a rather excellent 3ware hardware RAID controller which is automatically picked up by Ubuntu.
There's a few things I need some advice on though.

The RAID device is mounted at /media/raid so within that device I've created a few folders which will be the root of some shares.

I want all of these shares to be complete anonymous access - anyone on our local network can read/write to the files on these shares (once I've got our mail transferred to Zimbra I'll set up LDAP auth)

1) Do the Linux permissions of the root share folders within /mount/raid matter to Windows/Mac clients?
Or is that all down to the Samba/Netatalk conf files?

2) Should I set the permissions of /mount/raid to that of my main user account on this server box?

3) Do the Linux permissions of any files/folders created on this device through Samba, get inherited from the partitions of the /mount/raid mountpoint or anywhere else?

Or will I have to run a shell script every so often to reset all the file permissions on the NAS to ensure my server admin account retains ownership?
Does my server admin user account need to retain ownership of the files/folders?

4) Here's my smb.conf so far (modified the default but have stripped most of the cruft/comments out)

```
[global]
workgroup = domain.com
netbios name = files
server string = %h server (Samba, Ubuntu Server 8.04)
encrypt passwords = yes

dns proxy = no
;name resolve order = lmhosts host wins bcast
interfaces = eth0
bind interfaces only = true

log file = /var/log/samba/log.%m
max log size = 10000
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = share

;map to guest = bad user

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

[testshare1]
path = /media/raid/shared
comment = comment
browseable = yes
public = yes
writeable = yes
read only = no
guest only = yes
guest ok = yes
create mask = 0777
directory mask = 0777
```

The last thing I want with these anonymous/guest shares is for people to be getting permission errors on certain files/folders

Any comments/suggestions/answers are most appreciated ;)

Thanks, B

---

### Post by Cadmus on 2008-06-26
I'm tagging this thread as I'm also tying myself in knots trying to get the permissions right on a Samba share, I can never quite get it how I want it.

---

### Post by weryl on 2008-06-26
Hi

I myself am quite a beginner with samba but ill try to help. I have a home server with /data setup as a samba share. Users from other machines access it occasionnally but connect as a user "data" which owns the directory so they have write/read rights. However, if they were to try loggin in with another user, say "mike" they wouldnt be able to write on /data. So yes, ownership and access rights do work because you have to connect as a user.

I dont think "data" can even see the rest of the tree (/, /home, etc) because only /data is shared, so there's no problem there.

Now concerning your questions, I really dont know if that's the right thing to do but I would do exactly the same. Its easy to set permissions for a single user (data) and you can configure the other machines so that connecting to the share remains transparent.

Hope this helps a bit.

Mike

---

### Post by cdenley on 2008-06-26
As with windows, the filesystem permissions are used as well as the share permissions. Guest users are assigned a local user account such as nobody. Opening or writing files are done as this user, so that user needs the required filesystem permissions. Permissions are not inherited. I think the global umask is used, unless you set the masks for the samba share (as you have). The group ownership will be the user's primary group. You can force all user's on a share to access files as a different user/group...
```

[myshare]
force user = myuser
force group = mygroup

```
This will make all new files or directories owned by myuser:mygroup. This won't matter much with your 0777 masks, though.
```

man smb.conf

```

---

### Post by batfastad on 2008-06-26
Ah ok, I think I understand.

So on my samba server, I have an account that I use for administration called: administrator
I notice at the moment when I create files over Samba that the permissions get created as nobody.

Is it a better idea to use force user=administrator up in the global section?
This would make sure that my administrator user never has any problems with accessing files that users have created on the shares?

And also makes sure that all users connecting through Samba, who are automatically 'administrator' can do everything with those files?

Also should I move those mask bits I've got into the global section?
To cut a few lines out of smb.conf

Thanks for your help so far, B

---

### Post by cdenley on 2008-06-26
> **batfastad said:**
> 
Is it a better idea to use force user=administrator up in the global section?
This would make sure that my administrator user never has any problems with accessing files that users have created on the shares?

And also makes sure that all users connecting through Samba, who are automatically 'administrator' can do everything with those files?

Also should I move those mask bits I've got into the global section?
To cut a few lines out of smb.conf

I don't think those options can be used in the global section, but I never tried. A more secure approach would be to create a new group specifically for this share. Then anyone belonging to the group can have permissions. Generally, you don't want to give network users any more permissions than you have to.

```

sudo groupadd share
sudo usermod -G share -a administrator
sudo chown -R root:share /media/raid/shared
sudo chmod -R 770 /media/raid/shared

```

```

[testshare1]
path = /media/raid/shared
comment = comment
browseable = yes
public = yes
writeable = yes
read only = no
guest only = yes
guest ok = yes
[B]create mask = 0660
directory mask = 0770
force group = share[/B]

```

---

### Post by Cadmus on 2008-06-26
Ah, it's starting to make a bit more sense to me. One problem I have found though is when I try to connect to a samba share from Linux.

If I do something like
```
sudo mount -t cifs //bigserver/music /media/music
```
then the /media/music permissions change from root (who owns the folder when not mounted) to whichever user on my machine has the same uid as user I forced it to in the smb.conf.

What is the proper way to mount a samba share so it's like a floppy in a drive or a USB key i.e. any user on the system can read or write with the same priveleges as any other, do I need to play with the mounting options or the samba config.

---

### Post by cdenley on 2008-06-26
> **Cadmus said:**
> Ah, it's starting to make a bit more sense to me. One problem I have found though is when I try to connect to a samba share from Linux.

If I do something like
```
sudo mount -t cifs //bigserver/music /media/music
```
then the /media/music permissions change from root (who owns the folder when not mounted) to whichever user on my machine has the same uid as user I forced it to in the smb.conf.

What is the proper way to mount a samba share so it's like a floppy in a drive or a USB key i.e. any user on the system can read or write with the same priveleges as any other, do I need to play with the mounting options or the samba config.

Places>Connect to Server...

---

### Post by batfastad on 2008-06-26
> **cdenley said:**
> I don't think those options can be used in the global section, but I never tried. A more secure approach would be to create a new group specifically for this share. Then anyone belonging to the group can have permissions. Generally, you don't want to give network users any more permissions than you have to.

Ok that makes sense.
So I create a group... but then I guess I can just re-use that group for all these guest all-access shares
Adding force group = whatever to each share
Is that acceptable?

Also why the change of masks from 0777 to:
create mask = 0660
directory mask = 0770

Thanks for your help so far! :D

---

### Post by Cadmus on 2008-06-26
> **cdenley said:**
> Places>Connect to Server...

Tempting, but if memory serves this isn't persistent across reboots, also if I recall correctly it doesn't put it under the local file system, rendering it invisible to certain apps.

---

### Post by cdenley on 2008-06-26
> **batfastad said:**
> Ok that makes sense.
So I create a group... but then I guess I can just re-use that group for all these guest all-access shares
Adding force group = whatever to each share
Is that acceptable?

Also why the change of masks from 0777 to:
create mask = 0660
directory mask = 0770

Thanks for your help so far! :D

Yes, that is probably what I would do if I needed to use a guest account.
```

create mask = 0660
directory mask = 0770

```
The 6's instead of 7's prevent the files from being executed. Not really helpful since they can't execute files on the server, but couldn't hurt. Making the last digit a zero makes sure that anyone outside the share can't read/write anything. You can't access the share as a different user through samba, but it is always possible for a local account to be compromised. In fact you could probably make it 0060 and 0070, in case the nobody user gets hacked.

It's not really necessary, maybe a little paranoid, but probably the most secure way of doing it.

---

### Post by cdenley on 2008-06-26
> **Cadmus said:**
> Tempting, but if memory serves this isn't persistent across reboots, also if I recall correctly it doesn't put it under the local file system, rendering it invisible to certain apps.

It isn't persistent across reboots, but you can create a bookmark and tell it to remember your password. It can be accessed through the filesystem at ~/.gvfs if you use ctrl+h to view hidden directories. You can also create a link which isn't hidden.
```

sudo ln -s .gvfs network

```
I've also been annoyed by how mounting as cifs uses your local unix permissions instead of the samba server's. I think smbfs works a little differently, but I usually let gnome mount it.

---

### Post by Cadmus on 2008-06-26
> **cdenley said:**
> It isn't persistent across reboots, but you can create a bookmark and tell it to remember your password. It can be accessed through the filesystem at ~/.gvfs if you use ctrl+h to view hidden directories. You can also create a link which isn't hidden.
```

sudo ln -s .gvfs network

```
I've also been annoyed by how mounting as cifs uses your local unix permissions instead of the samba server's. I think smbfs works a little differently, but I usually let gnome mount it.

Nice, I'll have to remember that one (as soon as I figure out the xubuntu equivalent).

In the mean time I appear to have taken one step forward two steps back :(

I've got a share with the following definition, and I can't access unless I comment out the force user/group stanzas, and if i do that I can't write into the share. I've check that the foler and all files in the share are owned by 'vault'.

[music]
path = /home/vault/music
available = yes
read only = no
guest ok = yes
force user = vault
force group = vault

---

### Post by cdenley on 2008-06-26
> **Cadmus said:**
> Nice, I'll have to remember that one (as soon as I figure out the xubuntu equivalent).

In the mean time I appear to have taken one step forward two steps back :(

I've got a share with the following definition, and I can't access unless I comment out the force user/group stanzas, and if i do that I can't write into the share. I've check that the foler and all files in the share are owned by 'vault'.

[music]
path = /home/vault/music
available = yes
read only = no
guest ok = yes
force user = vault
force group = vault

```

sudo ls -ld /home
sudo ls -ld /home/vault
sudo ls -ld /home/vault/music

```

```
[music]
path = /home/vault/music
available = yes
read only = no
guest ok = yes
**writeable = yes**
force user = vault
force group = vault
```

---

### Post by batfastad on 2008-06-26
It's not working entirely as expected.

I've created the group called sambaaccess and added the force group = sambaaccess to each share
And changed the create/directory masks to 0660 and 0770 respectively

And I've added the user administrator to the sambaaccess group

But when I create new files/folders in one of the shares, from a remote machine through samba... I look at the properties in Gnome File Browser and owner is set as nobody, and group is sambaaccess
So me, administrator, logged in to the console and viewing the shares in Gnome, can't do anything to files created by users. They all have a small padlock shown.

Surely because administrator is part of the sambaaccess group, I should be able to create/edit/delete any files where group is set to sambaaccess?

Also files/directories that administrator (my local Linux user account) creates are viewable over Samba, but Samba guests can't copy/move files into them.

Any suggestions?
Thanks, B

---

### Post by Cadmus on 2008-06-26
I'm having to copy this by eye as I'm sshing from a WinXP box... so I'm skipping a couple of details like terminal prompts

```
ls -ld /home
drwxr-xr-x 5 root root 4096 2008-06-24 14:01 /home

ls -ld /home/vault
drwxr-xr-x 4 vault vault 4096 2008-06-24 13:51 /home/vault

ls -ld /home/vault/music
drwxr-xr-x 2 vault vault 54 2008-06-24 13:46 /home/vault/music

```

Just to clarify something, with the force user/group stanzas in I can see the folder for the share, but I can't go into it, access is denied.

---

### Post by cdenley on 2008-06-26
> **batfastad said:**
> It's not working entirely as expected.

I've created the group called sambaaccess and added the force group = sambaaccess to each share
And changed the create/directory masks to 0660 and 0770 respectively

And I've added the user administrator to the sambaaccess group

But when I create new files/folders in one of the shares, from a remote machine through samba... I look at the properties in Gnome File Browser and owner is set as nobody, and group is sambaaccess
So me, administrator, logged in to the console and viewing the shares in Gnome, can't do anything to files created by users. They all have a small padlock shown.

Surely because administrator is part of the sambaaccess group, I should be able to create/edit/delete any files where group is set to sambaaccess?

Any suggestions?
Thanks, B
```

groups

```
Log out, log back in.

---

### Post by batfastad on 2008-06-26
> **cdenley said:**
> ```

groups

```
Log out, log back in.

Perfect, works!!!:D

Final thing... if my local Linux user 'administrator' creates files/folders in the Samba shares, then Samba clients (guests) can't edit/create inside those files/folders

Thanks, B

---

### Post by cdenley on 2008-06-26
> **batfastad said:**
> Perfect, works!!!:D

Final thing... if my local Linux user 'administrator' creates files/folders in the Samba shares, then Samba clients (guests) can't edit/create inside those files/folders

Thanks, B

There's not much you can do about that. You can either change the permissions every time you create a file locally, change your local umask for all new files, or use "force user = administrator". Privilege separation is important for security, but not always convenient.

---

### Post by cdenley on 2008-06-26
> **Cadmus said:**
> I'm having to copy this by eye as I'm sshing from a WinXP box... so I'm skipping a couple of details like terminal prompts

```
ls -ld /home
drwxr-xr-x 5 root root 4096 2008-06-24 14:01 /home

ls -ld /home/vault
drwxr-xr-x 4 vault vault 4096 2008-06-24 13:51 /home/vault

ls -ld /home/vault/music
drwxr-xr-x 2 vault vault 54 2008-06-24 13:46 /home/vault/music

```

Just to clarify something, with the force user/group stanzas in I can see the folder for the share, but I can't go into it, access is denied.

```

sudo grep -i security /etc/samba/smb.conf

```

---

### Post by batfastad on 2008-06-26
> **cdenley said:**
> There's not much you can do about that. You can either change the permissions every time you create a file locally, change your local umask for all new files, or use "force user = administrator". Privilege separation is important for security, but not always convenient.

Ah ok, fair enough then.
It will be rare that I'll be adding files/folders through the console anyway. If necessary I just need to run the chown/chmod commands from the previous page and they should recurse through the files/folders in the shares.

Well it's up and running now, so thanks for all your help! :D
Ben

---

### Post by Cadmus on 2008-06-27
> **cdenley said:**
> ```

sudo grep -i security /etc/samba/smb.conf

```

```
# "security = user" is always a good idea, this will require a Unix account
security = share
# File creation mask is set to 0700 for security reasons. If you want to
# Directory creation mask is set to 0700 for security reasons. If you want to

```

EDIT: Took a bit more of a look, it works if I have the force user line but not if I have force group. What happened I used a different explorer to get to the share and it returned an error about not being able to find the group name. I'm pretty damn sure the group exists and vault is a member of the vault group.

EDIT 2: It's working now with vault in, what may have happened is a control charater of other non-printing char was in the gorup name, or WinXP may have simply cahed the succesful attempt.

---

### Post by Cadmus on 2008-06-27
Looks like the success was simply WinXP caching the successful logon, for some reason adding the 'force group = vault' causes the share to complain that the share cannot be found, which is frustrating.

---

### Post by cdenley on 2008-06-27
There must be something wrong with your smb.conf file. This works fine for me.
```

[music]
path = /home/share/music
available = yes
read only = no
guest ok = yes
force user = share
force group = share

```

```

cdenley@ubuntu:~$ ls -ld /home
drwxr-xr-x 5 root root 4096 2008-06-26 09:03 /home
cdenley@ubuntu:~$ ls -ld /home/share
drwxr-xr-x 3 share share 4096 2008-06-26 11:29 /home/share
cdenley@ubuntu:~$ ls -ld /home/share/music
drwxr-xr-x 2 share share 4096 2008-06-27 09:23 /home/share/music

```

---

### Post by Cadmus on 2008-06-27
Yeah, I have a feeling I've messed something up with regards to users and group membership as this is now almost a direct version of the smb.conf I use at home.

All I can think is that I must have added/removed someone important from the 'vault' group. The fact I can't force the group to vault is going to cause problems when people start writing to it as (presumably) anything that gets added will belong to their local group.

EDIT: Gah! I keep saying the wrong thing, this is what comes from attending an event the previous evening... what I meant to say earlier is not that the share cannot be found, but rather that the error is about the *group* not being found.

---

### Post by Cadmus on 2008-06-27
Hmm... reading man smb.conf it seems using force user implies force group of the primary group of the user, so I might be ok.

---

### Post by prostar on 2008-06-27
I would strongly recommend "webmin" for this task.  I first found it when I had samba issues, and now I use it for several config tasks that can be "stupid" when just looking at .cfg files.

As a side note, there is a "default" setting for user,group, etc.. for files added to each share, so you don't have to go back and fix it up later.

---

### Post by batfastad on 2008-06-27
Does webmin support the editing of the Netatalk configurations?

Thanks, B

---

