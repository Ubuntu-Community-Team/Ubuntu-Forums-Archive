---
title: "Needsome help with Apache2 file/folder permissions"
date: 2008-02-15
forum: Server Platforms
---

### Post by sandyeggoboy on 2008-02-15
Hello, everyone. i am having some issues with an Apache2 installation on my server, running debian etch 4.0. 
We have an application running here that needs to be configured with access with Dreamweaver CS3. I have configured it so that a user account as the application living in its home dir, with a symbolic link to it from /var/www. 

When i copy files into the applications' data folder, i have to chmod 664 filename.jpg otherwise i get a "you do not have permission to access that file.
The other problem is that when i use FTP (or dreamweaver) to save edited files into the web folder, and i am logging in as the user that the web app lives in, i again get a "you do not have permission ...." or just an "access denied" error.

Could someone please help me to figure out what the correct setup needs to be? i used to be able to make all this work, but now for some reason .........maybe i am just getting old......
I dont have a problem with re-installing the server if thats what it takes, but i need to get this working. 

TIA - Deric Stowell

---

### Post by rickyjones on 2008-02-15
I'm not sure on how to properly configure what you have right now but I can tell you how I configured a similar web server here at my job.

The server is running Ubuntu server with Apache2, Webmin, MySQL. I created a new directory - /data/http/ - and shared this via SAMBA. I have a virtual host in Apache2 defined for /data/http/. In Dreamweaver I create the site so that it stores the files on the server via SAMBA.

I hope this helps you in some way. If not, I apologize.

Thanks,

-Richard

---

### Post by faulkes on 2008-02-15
> **sandyeggoboy said:**
>  I have configured it so that a user account as the application living in its home dir, with a symbolic link to it from /var/www. 


Is Options FollowSymlinks turned on?

> 
When i copy files into the applications' data folder, i have to chmod 664 filename.jpg otherwise i get a "you do not have permission to access that file.
The other problem is that when i use FTP (or dreamweaver) to save edited files into the web folder, and i am logging in as the user that the web app lives in, i again get a "you do not have permission ...." or just an "access denied" error.


This sounds like a default UMASK issue combined with an ownership issue.

UMASK sets the default permissions files are set with, so if you are having to constantly "chmod 644 file", you may wish to set a new or different UMASK

```

myserver$ UMASK=0664
myserver$ export UMASK

```

Both of those lines (removing the myserver$ portion) can be put into .bashrc and .profile so they will automatically be picked up when you login.

I would as well check ownership of the directories and files to ensure that the user you are logging in as owns the files and directories.

> 
Could someone please help me to figure out what the correct setup needs to be? i used to be able to make all this work, but now for some reason .........maybe i am just getting old......
I dont have a problem with re-installing the server if thats what it takes, but i need to get this working. 

TIA - Deric Stowell

I don't think you need to re-install, at least not yet.  As for getting old, careful there sonny, some us aged codgers might a get all grumpy and give you what for ;)

Keep posting additional information and we'll help as much as possible.

Faulkes

---

### Post by sandyeggoboy on 2008-02-15
hi and thanks for your reply. You solved my problem!! i went back and used smbpasswd -a and added my user into samba, then enabled them, and the edited the smb.conf file further to allow for directory writing.

Now the only problem is that Windows Vista is not allowing me to access the shared folder the same way as Windows Xp does.  Any ideas on that issue?

Thanks,

Deric Stowell

---

### Post by rickyjones on 2008-02-15
> **sandyeggoboy said:**
> hi and thanks for your reply. You solved my problem!! i went back and used smbpasswd -a and added my user into samba, then enabled them, and the edited the smb.conf file further to allow for directory writing.

Now the only problem is that Windows Vista is not allowing me to access the shared folder the same way as Windows Xp does.  Any ideas on that issue?

Thanks,

Deric Stowell

I would think that XP vs Vista for network writing would be the same. Is it throwing an error message?

-Richard

---

### Post by faulkes on 2008-02-15
> **sandyeggoboy said:**
> 
Now the only problem is that Windows Vista is not allowing me to access the shared folder the same way as Windows Xp does.  Any ideas on that issue?

Thanks,

Deric Stowell

IIRC there are known issues with Vista and Samba, I can't offhand recall exactly what they are however a forum search should turn up related postings.

Faulkes

---

