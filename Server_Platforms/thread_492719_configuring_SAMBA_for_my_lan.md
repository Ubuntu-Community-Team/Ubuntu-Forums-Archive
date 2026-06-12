---
title: "configuring SAMBA for my lan"
date: 2007-07-05
forum: Server Platforms
---

### Post by dfreer on 2007-07-05
Hi everyone,

  I'm looking at sharing some media files across my LAN (mixed Windows/Linux Clients). I'm reading up on how to configure samba correctly, but I thought I better check with you guys first :D
  So here's what I'm looking to do: I want to share a folder /home/media with everyone on the LAN with read only permissions (basically anonymous login, no username/password needed). However, I want to also have the choice to login with my username/password and access the same folder /home/media with read and write permissions.
  Any ideas on the best way to proceed with this?

---

### Post by vmikalinis on 2007-07-06
Hi everyone,

*I want to share a folder /home/media with everyone on the LAN with read only permissions (basically anonymous login, no username/password needed)*. 

well you'll need a share for this, your just making a regular share, then setting the admin user to be your login, something like this should work:

[media]
   comment = media folder
   path = /home/media
   guest ok = yes

*However, I want to also have the choice to login with my username/password and access the same folder /home/media with read and write permissions.*

for the admin user, you could just add:
admin users = "your username"


There is more to it than this.  Are you familiar with samba and editing the smb.conf file or did you need it from the ground up basically?  You'll also have to make sure the permissions of the folder your sharing are open to who you need them to be.  Just like windows, there is the share permissions, and the folder and file permissions.  I believe that "admin users=" overrides all permissions and gives full access to that user.  You may also have to add the username to smbusers.  Set up the share, restart samba, and see what kind of prompt you get.  Then we can take it from there.  There is also a tool called swat which I have never used, but some like it.

---

### Post by reckless2k2 on 2007-07-06
if you're looking for simple gui editing or usability, check out SWAT. i love the command line and editing conf files but some prefer a gui front end. it will not be as powerful as the command line but for your needs it'll do.

---

### Post by dfreer on 2007-07-06
> **vmikalinis said:**
> Hi everyone,

*I want to share a folder /home/media with everyone on the LAN with read only permissions (basically anonymous login, no username/password needed)*. 

well you'll need a share for this, your just making a regular share, then setting the admin user to be your login, something like this should work:

[media]
   comment = media folder
   path = /home/media
   guest ok = yes

*However, I want to also have the choice to login with my username/password and access the same folder /home/media with read and write permissions.*

for the admin user, you could just add:
admin users = "your username"


There is more to it than this.  Are you familiar with samba and editing the smb.conf file or did you need it from the ground up basically?  You'll also have to make sure the permissions of the folder your sharing are open to who you need them to be.  Just like windows, there is the share permissions, and the folder and file permissions.  I believe that "admin users=" overrides all permissions and gives full access to that user.  You may also have to add the username to smbusers.  Set up the share, restart samba, and see what kind of prompt you get.  Then we can take it from there.  There is also a tool called swat which I have never used, but some like it.

Yeah, I'm familiar with editing smb.conf, just wasn't sure on how to proceed. So if my username on the system is "joeblow", I can set my /home/media/ to be owned by "joeblow:joeblow", and then change the permissions to 755/644.
From there, I'd add "joeblow" to my smbusers, and add "joeblow" to the "admin users=" option under my /home/media/ share in smb.conf, along with "guest ok = yes". This should allow anonymous access with read only permissions, and read/write permissions if I log in with my "joeblow" account, correct?

I'll go ahead and give this a try, but one last question: would I need to do anything special on my windows client when logging in as "joeblow" (i.e. would I need a local user account named "joeblow" on my windows machine?) Thanks!

Thanks for the info about SWAT, I knew about it but I generally just use the smb.conf file myself.

---

### Post by dfreer on 2007-07-06
I did a google on "admin users" and came across this:
[http://www.oreilly.com/catalog/samba/chapter/book/ch06_02.html](http://www.oreilly.com/catalog/samba/chapter/book/ch06_02.html)
Specifically,
> If you wish to force read-only or read-write access to users who access a share, you can do so with the read list and write list options, respectively. These options can be used on a per-share basis to restrict a writable share or grant write access to specific users in a read-only share, respectively. For example:

[sales]
		path = /home/sales
		comment = Fiction Corp Sales Data
		read only = yes
		write list = tom dick

So now I'll test several shares out, with both admin users and the write list settings really quick.

---

### Post by dfreer on 2007-07-07
Ok, I'm still having some problems, specifically I can access the media from Windows/Linux without logging in, and read only. However, either I don't know how to login as admin or I don't have the share set up correctly. Here's the relevent parts of my /etc/samba/smb.conf file:

```

[global]
   security = user
   username map = /etc/samba/sbmusers
;   guest account = nobody
   invalid users = root

[media]
   path = /home/media/
   comment = Media
   guest ok = yes
   public = yes
   admin users = "joeblow"

```

I added the user with the following command:
```
sudo smbpasswd -a joeblow
```
And then added the following line to /etc/samba/smbusers
```
joeblow = "network joeblow"
```
Ownership of /home/media
drwxr-xr-x 3 joeblow joeblow 120 2007-07-04 23:00 media

Evidently I don't know smb.conf as well as I thought, although I've never needed guest access before, I've always just create user accounts and use username/password logins. Thanks for anyone who has some advice for me!

EDIT: It never asks for username/password when I log in, btw.

---

### Post by dfreer on 2007-08-23
Alright, so I had the day off today, and spent some time figuring out exactly what I *want* to do, and what is *possible* for me to do with samba. I've got it working fairly well now, although guest access still isn't possible:
First, I created 2 new Linux users, *admin* and *joeblow*, like so:
```
sudo groupadd admin
sudo useradd --gid admin --shell /bin/false admin --home /nonexistant
sudo smbpasswd -a admin
# I then repeated this procedure with joeblow
``` 
I create a seperate samba password for each user, and mapped their names to /etc/samba/smbusers:
```
# /etc/samba/smbusers
admin = "network admin"
joeblow = "network joeblow"
```
This is what my /etc/samba/smb.conf looks like, abbreviated:
```
# /etc/samba/smb.conf
[global]
   security = user
   encrypt passwords = true
   passdb backend = tbdsam
   username map = /etc/samba/smbusers

# Since all of my media files are not actually located in /home/media 
# (they are located across several hard drives, and I use symbolic 
# links to access them all at the one location /home/media), this is 
# needed in order for linux samba clients to be able to successfully 
# navigate the share)
   **unix extensions = no**


[share]
   path = /home/media/
   public = yes
   read only = yes

# The @admin refers to anyone part of the *admin* group, btw
   write list = admin, **@admin**

```

I modified all of the files in /home/media/ to be owned by admin, with 644 permissions, and all of the folders with 755 permissions (not sure if this was needed). I then restarted samba, and was able to login from windows machines either using by joeblow account (with read only access), or my admin account (with read/write access). 

I wish it were possible to anonymously access the share using read access, without needing to supply a username and password, but this seems to be a limitation in Samba (or I just haven't found a way to do so yet ;) ). This will work for now, thanks everyone for your help so far!

---

