---
title: "Samba configuration, getting confused"
date: 2006-07-20
forum: Server Platforms
---

### Post by ozstriker on 2006-07-20
I'm having a bit of trouble with configuring Samba, it's probably quite a simple solution, but I'm finding it hard to get my head around.
Basically, I have a spare rig running Server 6.06, with some spare drive space on it. Currently it has only my music, and a few videos. 
With the various computers I have, it's getting difficult to figure out which computer I was working on with a particular file, or where music is stored. So I figured I'd set up the server to have a central place to save everything. I have a main rig, which dual boots Ubuntu 6.06 and Windows XP, and a couple of laptops running 6.06. 
I figured I'd create a couple of shares, one for music, and one for general documents. I did that, and it works fine, but read/write access is proving a pain.
I want to be able to access the music, without having to provide a username and passwword, so I can stream it to whatever PC I'm on (this includes my parent's computers, one running OSX, one running XP). I'd like this to be read only, so that if somebody connects to the share, nothing can be modified or deleted. However, I'd also like to be able to add/edit files from a remote computer, probably the XP rig. So I need write access for only one account.

The next share is only for documents, so I would like that to need a password to access, which would then allow read/write. 

If anybody could point me in the right direction, or walk me through the steps, it would be greatly appreciated :)

Edit: Just had a thought of automatically synchronising the music on my Main rig (Xp/Ubuntu) with that of the server. Any ideas?

---

### Post by Braino on 2006-07-20
Permissions are going to be handled with chmod and the specific share's configuration in smb.conf 

For example, your music share could be setup like this (assuming /srv/music/ is the location of your music)

```

sudo chmod 744 /srv/music

```

and in smb.conf:
```

[music]
path = /srv/music
browseable = yes
read only=yes
guest ok = true
write list = yourWriteAccount

```

To be able to write to this share, you will need to login with 'yourWriteAccount'. You will also need to make /srv/music writeable for that account(you can give write access specifically to that account, or just make that account the owner).

 
A more in-depth look at chmod can be found here:
[http://www.corantodemo.net/doc/chmod-doc.shtml](http://www.corantodemo.net/doc/chmod-doc.shtml)
And a detailed description of smb.conf can be found here:
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

Hope this helps, post back with any problems you may have.

-Braino

---

### Post by ozstriker on 2006-07-20
OK after doing that, when I try to access the Music share through windows Xp, it says I do not have permission to access this resource, and then a reference to a bad username/password.

---

### Post by Braino on 2006-07-20
If you haven't already, you will need to add the samba user. 
```

sudo smbpasswd -a yourWriteAccount

```
If you make the username and password the same as the one you use in Windows, supposedly you won't be asked for a username/password when you try to view the share from the Windows computer.

However, it should let you login with no username and password, as a guest. Does it prompt you for a username and password? Make sure that 'security=' in smb.conf is set to 'security=user'

If this doesn't work, you may have to wait until I get home so I can refresh my memory on what I did. :)

-Braino

---

### Post by ozstriker on 2006-07-20
So how can I log in as a guest via windows? It prompts me for a login password, and won't let me leave it blank.
Logging in works fine though :)

---

### Post by Braino on 2006-07-20
You may have to enter 'Guest' in the username area, or maybe 'Anonymous'. I'm glad to see the login is working now!

-Braino

---

### Post by oly on 2006-07-20
you can also change the security model to share, i think it uses users by default.

security = share

not that secure but if its only for home computers its not to bad and you can bind the share to your network with.

interfaces = 192.168.0.

for example

---

### Post by ragdemai on 2006-07-21
> **oly said:**
> you can also change the security model to share, i think it uses users by default.

security = share

not that secure but if its only for home computers its not to bad and you can bind the share to your network with.

interfaces = 192.168.0.

for example

I having the some problem in my samba server as well. All kind of setting I tried but I only can get all user cannot be write or all user can be write into shared folder.

as below is setting in smb.conf i can't anything wrong, please help!! :
security = share
[Shared]
path = /home/MySharedFolder
browseable = yes
write list = @MyUserGroup, User
guest ok = yes
create mask = 0765
directory mask = 0765
================================================================
Thank you

---

### Post by oly on 2006-07-21
[test]
path = /home/admin/test
available = yes
browseable = yes
public = yes
writable = yes

that is all i needed to share a folder with read and write access just change the mode using chmod to 777 to allow everyone full controll or use the restriction commands to restrict to a specific user, however in share mode you do not have to login so not sure how that works might have to set a default user or something.

not got much experience with this mode only used it for quick easy and dirty setup :p

---

### Post by Braino on 2006-07-21
When in 'security=share' mode and 'guest only=on' for that specific service, there is no validation. The person accessing the share is automatically logged in as whoever you setup as the guest account in smb.conf

So, you could make it so that you have read access as the guest user, but are also able to log into a different account to get write access. You can do this by turning off guests only (I think it's off by default) and setting security=user. You might also be able to do this with security=share, although I am not sure if it would take a user name.

---

