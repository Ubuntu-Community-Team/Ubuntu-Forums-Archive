---
title: "How to setup folder share through the terminal"
date: 2009-07-09
forum: Server Platforms
---

### Post by greavette on 2009-07-09
Hello,

I would like to use Ubuntu Server (Hardy 8.04) as a place for our office to store files and documents.  We have a web portal our users can login too and through this portal I will setup a network file share to this ubuntu server.  This portal will give our users a nice Gui interface with which to upload and download files.  I don't want this server to have a desktop Gui since this Server will be in a VM and I want to keep the Ram down to a minimum and not waste resources on the Desktop.

My problem is I can't find documentation on setting up a shared folder purely through the terminal.  I know how to setup shared folders when there is a Gnome desktop on Ubuntu but my searches on this forum and Google haven't come up with instructions on how to do this purely through terminal commands.

Once the share is setup I also need help with the following:

[LIST]
[*]Each user will have their own folder to store files in. There will also be one common folder for all users to share files in.  Would I use useradd or adduser on this server to add our users?  Each user will never be logging directly into the server with their Id. Only I will be logging in to administer the server. 
[*]How do I add permissions to these folders for each user again purely through  terminal commands?
[*]I plan on using Hardy since it's supported to 2013, but are there advantages to using Jaunty server instead that I'm not aware off?
[/LIST]

If someone can point me in the right direction on where I can find the information to set this up, it would be greatly appreciated.

Thanks in advance for your help!

---

### Post by renzokuken on 2009-07-09
if you are using a ubuntu server and accessing it through windows workstations, you can simply install SAMBA, and then edit the smb.conf (the configuration file) through the terminal to set up file shares and permissions etc.

as for users, you can simply create samba users and passwords (which could match your xp logins for simplicity)

---

### Post by ptn107 on 2009-07-09
> **renzokuken said:**
> if you are using a ubuntu server and accessing it through windows workstations, you can simply install SAMBA, and then edit the smb.conf (the configuration file) through the terminal to set up file shares and permissions etc.

as for users, you can simply create samba users and passwords (which could match your xp logins for simplicity)

Samba is definitely your friend here.  Learn it and it will serve you well.
[http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by greavette on 2009-07-09
Hello renzokuken..thanks for the quick response!

So I could just install my server and setup my user id so I can login and administer the server.  I don't need to setup userid's for each employee on the server.  Instead I create samba users (which could be the userid of their windows PC's). I didn't know you could do this?  I thought each user who used the share needed to have an Ubuntu login id? 

So, it would seem I would need to do the following to add a user to samba and setup these shares:

Install samba and smbfs:
```
sudo apt-get install smbfs samba
```

Run the smbpasswd utility to create a samba password for the user.

   ```
 sudo smbpasswd -a user1
```

Then I'll add that username to the smbusers file.

```
    sudo nano /etc/samba/smbusers

    user1 = “user1”
```

Then I'll create my shares:

```
sudo mkdir /mnt/user1
sudo mkdir /mnt/common
```

Then I'll edit the /etc/samba/smb.conf and define the share directory in it.

```
sudo nano /etc/samba/smb.conf
```

And add something like this for user files:

```
   [user1]
    comment = user1 Private Files
    path = /mnt/user1
    valid users = user1
    public = no
    writable = yes
```

And add this for a directory where everyone can share files:

```
[public]
   path = /mnt/common
   public = yes
   only guest = yes
   writable = yes
   printable = no
```

I would then restart samba on Ubuntu server:

```
sudo /etc/init.d/samba restart
```

Have a I missed anything?

Thanks!

---

### Post by capscrew on 2009-07-09
> **greavette said:**
> ...
Then I'll create my shares:

```
sudo mkdir /mnt/user1
sudo mkdir /mnt/common
```

A couple of things to note.  One is that Samba has a way to handle individual user (home dir) shares.  The share is called [homes] and it is for all users.  The second thing is where you are creating your mount point.  Although you can create the mount point anywhere in the file system, I find that it makes more sense to keep the Samba shares under its own mount point.  I use /smb[QUOTE]

---

### Post by greavette on 2009-07-09
Hi capsrew...thanks for the information.

Just wanted to clarify...Are these "individual user (home dir) shares" you mention home directories for a samba user or an ubuntu login user.  From the Samba reference guide (thanks ptn107!) it seems that each Samba user is automatically setup with a home folder share that would resemble this:

```
\\server\user1
```

This would mean I wouldn't need to use my mkdir code for each user...just create one directory for common files that will be accessed by all.

Although I guess I should add the following:

```
users = %S
```

option in the [homes] share definition to ensure each user does not have access other users directories.

Sorry if I've just rehashed what you've just said.  I just want to make sure I'm doing it right.

Thanks for you point on keeping Samba shares under it's own mount point.  This is a good idea (this way I won't make it so confusing for me and anyone who might manage this after me to figure out where everything is.)  I appreciate your help!

---

### Post by capscrew on 2009-07-09
> **greavette said:**
> ...
Just wanted to clarify...Are these "individual user (home dir) shares" you mention home directories for a samba user or an ubuntu login user.
From my point of view there is no difference between the remote user (via samba) and the local user (Ubuntu).  Both user databases are needed.  That being said the "Ubuntu" user does not need to have a Linux home directory or shell (as the user will never log in locally)> 


 From the Samba reference guide (thanks ptn107!) it seems that each Samba user is automatically setup with a home folder share that would resemble this:

```
\\server\user1
```

This would mean I wouldn't need to use my mkdir code for each user...just create one directory for common files that will be accessed by all. ...

See [_here_]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/") to start.  I would highly recommend you also read the Samba literature at [_here_ ]("http://us6.samba.org/samba/docs/man/Samba-Guide/") and [_here_]("http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/").

Edit: Here is my home directory section for samba users```
### Default home directory shares.  
#  This will share each user's home directory as \\server\username

[homes]
        comment = Home Directories
        path = /smb/home/%S
        browseable = no
        guest ok = no

```

---

### Post by smeerbartje on 2009-07-17
I managed to create a home directory for the 'primary' user of the Ubuntu 9.04 system, but now I need to add another user. How can I do this? I don't want to create a unix user, I just want to add another samba user. Is this possible? In the smb.conf file I have the following lines:

```

[homes]
comment = Home Directories
path = /smb/home/%S
browseable = yes
guest ok = no
writable = yes
read only = no
valid users = %S

```

Now when I try to add another user called 'eva', it says that there is no unix user found. But I only want another SAMBA user :confused:.

```

rogier@server-dev:/smb/home$ sudo smbpasswd -a eva
Cannot locate Unix account for 'eva'!

```

---

### Post by capscrew on 2009-07-17
> **smeerbartje said:**
> I managed to create a home directory for the 'primary' user of the Ubuntu 9.04 system, but now I need to add another user. How can I do this? I don't want to create a unix user, I just want to add another samba user. Is this possible? ...
Samba compares the "unix user" (the local user) to the smbpasswd database.  You have to have a local user account (unless you are using a domain wide system (DC).> 

Now when I try to add another user called 'eva', it says that there is no unix user found. But I only want another SAMBA user :confused:.

```

rogier@server-dev:/smb/home$ sudo smbpasswd -a eva
Cannot locate Unix account for 'eva'!

```

See the earlier posts in this thread. It is very common to add users without shell access or home directory for just this purpose.

Edit:  It might be helpful if you thought of "But I only want another SAMBA user" in a different way.  There are no "samba users", only users of samba services.  The local user and the remote user must be the same to use samba home directories.

---

