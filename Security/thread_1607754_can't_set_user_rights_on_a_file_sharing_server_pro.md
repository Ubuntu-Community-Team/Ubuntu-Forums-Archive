---
title: "can't set user rights on a file sharing server propery"
date: 2010-10-28
forum: Security
---

### Post by ndefontenay on 2010-10-28
Hi,

I got a file sharing server on Debian. 
To do so, I've created a user "sharing" in which home I've created File-Sharing which is then shared on the local network.

That way with the name like File-Sharing it's pretty clear what this is doing on the network.

Currently, my File-Sharing folder looks like this:
(date removed for clarity)
```
drwxrwxrwx 2 sharing sambashare Applications
drwxrwxrwx 2 nicolas nicolas Backup
drwxrwxrwx 2 sharing sambashare Dev
drwxrwxrwx 2 nicolas nicolas Documentation
drwxrwxrwx 2 nicolas nicolas expat-blog.com Debug
drwxrwxrwx 4 julien  julien Guides
d---rwx--- 2 sharing infrastructure Infrastructure
drwxrwxrwx 2 julien  julien Photos Istock
drwxrwxrwx 4 julien  julien Protos
drwxrwxrwx 2 julien  julien Temp
```

As you can see pretty much anyone can access anything and that's mainly because I don't have a clear understanding of how the user rights work with samba.

I've been testing things up with the folder Infrastructure above.

I returned ownership to user sharing:
```
chown sharing /home/sharing/File-Sharing/Infrastructure
```

I created group infrastructure:
```
groupadd infrastructure
```

I then assigned my user and a colleague who should be the only one accessing this folder:
```

usermod -aG infrastructure nicolas
usermod -aG infrastructure julien
```

I assign the group infrastructure to the folder infrastructure:
```
chgrp infrastructure /home/sharing/File-Sharing/Infrastructure
```

I then modify the user rights as follow:
```
chmod 070 /home/sharing/File-Sharing/Infrastructure
```

Now, I go back to my windows machine I look for File-Sharing on the server, I find Infrastructure, click on it aaaand... Access Denied.

After toying around, I know that I can access the folder as nicolas only with chmod 007 Infrastructure.

Why does the user nicolas still belong to "Others"? Does he need to be assigned to some sort of samba group instead? Is there any best practice to prevent people from accessing everything?

Some of these folders will hold structure sensitive information.

thanks

Nico

---

### Post by SeijiSensei on 2010-10-28
Samba has its own mechanisms to enforce file security.  You need to look at "man smb.conf" and particularly directives like "create mask" and "force user".

---

