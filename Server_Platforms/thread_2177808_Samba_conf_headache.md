---
title: "Samba conf headache"
date: 2013-09-30
forum: Server Platforms
---

### Post by PFb84MW on 2013-09-30
I intend to follow the guide at [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide) to setup a samba private share with password protection however I must confess I am a little lost at the smb.conf portion.

[global]
[FONT=inherit][/FONT]        security = user
[FONT=inherit][/FONT]        encrypt passwords = true
[FONT=inherit][/FONT]        map to guest = bad user
[FONT=inherit][/FONT]        guest account = nobody
[private]
[FONT=inherit][/FONT]        comment = Private Share
[FONT=inherit][/FONT]        path = /path/to/share/point
[FONT=inherit][/FONT]        browseable = no
[FONT=inherit][/FONT]        read only = no


1a.I don't want to allow guest access so should I remove map to guest = bad user or change it to map to guest = never?
1b.Is there another option for guest account = ? that disables guest?
2.How do I create a user for purely samba access ? using useradd or adduser?
3.Do I have to set the create mask and directory mask? What values should I set them if I want them to be fully writetable and readable? 755?

Thank you for reading!

---

### Post by bab1 on 2013-10-01
> **PFb84MW said:**
> I intend to follow the guide at [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide) to setup a samba private share with password protection however I must confess I am a little lost at the smb.conf portion.

```
[global]
       security = user
       encrypt passwords = true
       map to guest = bad user
       guest account = nobody
[private]
       comment = Private Share
        path = /path/to/share/point
        browseable = no
       read only = no

```

1a.I don't want to allow guest access so should I remove map to guest = bad user or change it to map to guest = never?
1b.Is there another option for guest account = ? that disables guest?
2.How do I create a user for purely samba access ? using useradd or adduser?
3.Do I have to set the create mask and directory mask? What values should I set them if I want them to be fully writetable and readable? 755?

Thank you for reading!
What version of Samba are you using.  It appears that you are using Samba v3.  I will comment under that assumption.

1a. No you do not need to remove "map to guest".  In reality this really means: Map to the user nobody if Samba sees an attempt to authenticate without a proper password.  Which is exactly what you would get if you tried to access a share but didn't know the password,  This will only allow access to an anonymous user if you have the *share parameter* "guest = ok".

1b. As I said it is the *[I]share parameter* "guest ok = yes".[/I].

2. the tool adduser is the Debian (Ubuntu) tool for adding users.  It's mindful of Ubuntu user structure (UID/GID, home directory, and skel files).  But this is only part of what you have to do.  The user **must be a local user on the server** ( it's not necessary for the user to be able to log in to the Ubuntu account however) and the user **must be a Samba user **that is added via *smbpasswd -a <username>*.  The login and pass should be the same on the client and the server for ease of use.  You can map differing user names, but it gets messy.

3.  This is a matter of taste.  Permissions are only part of the deal. How about ownership?  

If this is truly a private (to only one user) share then I would use the [homes] share.  You can define that share once and it will automagically create a private share for all users you add via adduser/smbpasswd.  If it is going to be restricted access for a group then you need to set up a common group (GID) and group inheritance for that share's directory and the files and subdirectories.  It is really fairly easy to set up the share for group usage if that is what you want.  On my Samba server this is what I have: private [homes] shares and restricted access group shares and one public share for all to access with or without password (depending upon how you want it).

Depending upon how you set up the share and the directory permissions you may need to insure that the underlying directory permissions and ownership are adhered to.  At that point you can use the force user/group directives and the permissions masks.  There is no absolute way that you should do this.  Samba is flexible enough to do whatever you want.

---

### Post by PFb84MW on 2013-10-01
Thank you, but I have some points I am still a little confused with,

for example, this [homes] section, I assume it shares everything under my home directory with my ubuntu user id and password as security?

I would very much rather share just one directory on the server, /srv/samba/share?

so I can just remove or comment out the [homes] section? and any other unneeded sections? 

also, about the smbuser, if I were to add a user using useradd -s /bin/false Ford, and add Ford to the smbpasswd, when I try to access the share from a Windows 7 machine,
do I have to have the exact same account name and password? Or would it prompt me to input the username and password?
can you give me an example of a minimalistic smb.conf for a private share pertaining to one directory on the server (/srv/samba/share) and 
non browseable with username and password secured, no guest allowed?

I presume it would be something along these lines?:


[global]
        security = user
        encrypt passwords = true
        map to guest = never
        guest account = nobody
[private] 
       path = /srv/samba/share 
       browseable = no 
       guest ok = no 
       read only = no
I realize map to guest = never, guest account = nobody, guest ok = no is actually not needed since they are the default?

---

### Post by bab1 on 2013-10-01
> **PFb84MW said:**
> Thank you, but I have some points I am still a little confused with,

for example, this [homes] section, I assume it shares everything under my home directory with my Ubuntu user id and password as security?
Yes.  Samba authenticated **you** to **your** data in **your** home directory.  If someone else has a local login and a smbpasswd entry they are authenticated to view their home directory  The share [homes] shares everything under the logged in users home directory (depending on configuration) with their user id and password as **authentication**.  Note;  this is not *authorization*.  Logins are authentication and ownership and permissions are authorization.  The [homes] directory can be directed to use **any directory ** as the [homes] share.  A [homes] share is not necessarily the /home/$USER directory.  It could, for example, use the base directory of /srv/samba/$USER.  > 


I would very much rather share just one directory on the server, /srv/samba/share?

One directory for just you or one directory for multiple users?
> 

so I can just remove or comment out the [homes] section? and any other unneeded sections?

I suppose you could.
> 

also, about the smbuser, if I were to add a user using useradd -s /bin/false Ford, and add Ford to the smbpasswd, when I try to access the share from a Windows 7 machine,
do I have to have the exact same account name and password? Or would it prompt me to input the username and password?
By default Windows passes the logged in Windows user name to the Samba server so it defaults to that user, but you can type in a user name and password that is different.  The problem would arise if you had a user on Linux with a different password than the same named user on Windows. > 
can you give me an example of a minimalistic smb.conf for a private share pertaining to one directory on the server (/srv/samba/share) and 
non browseable with username and password secured, no guest allowed?

I presume it would be something along these lines?:


[global]
        security = user
        encrypt passwords = true
        map to guest = never
        guest account = nobody
[private] 
       path = /srv/samba/share 
       browseable = no 
       guest ok = no 
       read only = no
I realize map to guest = never, guest account = nobody, guest ok = no is actually not needed since they are the default?
If you are asking me for what I would do; it would be this:
```
[global]
        security = user
        encrypt passwords = true
        map to guest = never
#       guest account = nobody  ## You don't need this at all if you don't allow any guests
[homes] 
       path = /srv/samba/share 
       browseable = no 
       guest ok = no 
       read only = no
```

This would allow each user you create a private share at: /srv/samba/share/$USER.  If you don't specify a path (path = ) in the share the default would be /home/$USER,  Or you could set the path to /srv/samba/home or /samba/home.  Anything you like.

Why create multiple private shares (one for each user) when you can create a single [homes] share for the system.  Each user will have a different share created by Samba on the fly.  You can of course also create manually create shares at /srv/etc/etc/etc or where ever you like.  The root directory of the share is set by you. For instance /data can be shared as something like this //SERVER/MOVIES.  The directory is not really obvious and the end user doesn't need to know what it is for the most part.  All of this is to say Samba can share secure shares at any directory in the Linux file system.  It's up to you to select the directory, then set authentication and authorization.

I think you should spend some time with the smb.conf man page```
man smb,conf
```...and maybe the official Samba documentation.  It helps if you understand how Samba actually works.

---

