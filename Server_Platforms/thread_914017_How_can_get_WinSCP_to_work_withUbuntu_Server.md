---
title: "How can get WinSCP to work withUbuntu Server?"
date: 2008-09-08
forum: Server Platforms
---

### Post by grs on 2008-09-08
I'm trying to setup WinSCP to work with my Ubuntu Server from a Windows PC.
I am able to get it connect and look at all the files/folders on the server, but because when using commands like making files/folders, editing files, moving files and deleting files all need to have sudo before them in the termnial, they don't seem to work in WinSCP. Also I can't transfer files from my Windows PC to the server trough WinSCP. I can do all this with other Linux distros.

Is there a way around this?

---

### Post by hyper_ch on 2008-09-08
```

sudo apt-get install openssh-server

```

---

### Post by grs on 2008-09-08
Have that, like I said I can connect WinSCP and browser the files I just can't get it carry out commands.

---

### Post by hyper_ch on 2008-09-08
never had such a problem... are you sure you have the according permissions on your user?

---

### Post by grs on 2008-09-08
Ther is only one user setup on my SERVER system. Below is the error message I got when I tried to delte a file:-

```

Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 13

```

I take files off the system ok because that doesn't actually affect the files that are on it. WinSCP is sending a command like:-

```

rmdir (filename)

```

When it should be sending :-

```

sudo rmdir (filename)

```

---

### Post by hyper_ch on 2008-09-08
I guess the problem is that winscp can't prompt you for the password when using sudo.

---

### Post by grs on 2008-09-08
Yes, thats what I've worked out, i'm looking for a work around. How did you do it.

---

### Post by mrsteveman1 on 2008-09-08
The difference is, this is actually the SFTP protocol you are using and not a shell. Sudo is a shell command that changes the UID of the process you are executing so that it has permissions of the super user (or any user really).

What you have to do with winscp is ensure that the user you are connecting with, either has permissions (7, meaning rwx) for any files you want to actually change. Or alternatively you could add this user to an admin group that already has those permissions, i believe there is one setup by default on ubuntu but i don't have mine sitting here at the moment.

Basically, sftp (and scp too) put you back into a situation where the actual user must have permissions for the files you want to change.

I used to get so annoyed doing this that i just set a password for root and logged in using that account for winscp, because it just works :D Of course then you have a root password and a larger attack surface.

---

### Post by grs on 2008-09-08
So, I can do it if I log in as GRS but change my user permissions for ever folder/folder I may want to edit.
I don't know much about user groups and permissions.

Or I can log in as root and edit with having to change permissions or use sudo.

I heave read something before that using root is not advisable. How do I set a password for root?
I don't have the server setup as a web-server, does this still leave it prone to attack?

---

### Post by lazyart on 2008-09-08
Now that you have openssh installed, use putty on Windows to SSH to your box and do your business that way.

---

### Post by grs on 2008-09-08
I have got Putty on Windows already, I'm just used to graphic interface which WinSCP gives so I would really like to get it running.

---

### Post by jerome1232 on 2008-09-08
WinSCP has the ability to execute commands you can add custom commands, it can grep fiels and some other stuff, but it doesn't seem to support sudo, I tried entering sudo cp filename fileName and it asked me if I wanted to open a putty session to execute commands.

I don't think there's a graphical way to do this. But I'm slightly interested so I'll keep messing with winscp

edit: I found this, it's possible, but you have to tweak sudo a bit, I wouldn't have a user that can be ssh'd to and has sudo access with no password though. I don't even allow admin accounts to be ssh'd to. I ssh in to a limited account and switch users.

[http://winscp.net/eng/docs/faq_su](http://winscp.net/eng/docs/faq_su)

---

### Post by grs on 2008-09-08
I tried the custom commands too, they must not be programmed to handle the follow up request for the password. That could be something the people at WinSCP might have a look at(?)
I've found how to set a password for root but I would like to know how to un-set the password for root before changing it, if in-case WinSCP is able to handle sudo in the future I can set root back to the original setting.

---

### Post by jerome1232 on 2008-09-08
> **grs said:**
> I tried the custom commands too, they must not be programmed to handle the follow up request for the password. That could be something the people at WinSCP might have a look at(?)
I've found how to set a password for root but I would like to know how to un-set the password for root before changing it, if in-case WinSCP is able to handle sudo in the future I can set root back to the original setting.

I might have edited my post after you looked follow that faq I linked you can allow winscp sudo access, but the user has to have passwordless sudo along with a few other tweaks that are outlined in the faq.

---

### Post by mrsteveman1 on 2008-09-08
To set password for root, use an account that already has sudo access (your main account should) and do this:

sudo passwd root

you will be asked for a new password twice, at which point root should be able to login normally with winscp.

As far as SSH and SFTP are concerned, having a password for root is not really less secure than a sudo-enabled account if it's a good password. 

Basically, when sudo is enabled, your username + your password = root, its just not as easy to guess random usernames, and attackers always try root before moving on to dictionary lists of usernames.

---

### Post by grs on 2008-09-08
I think I've got enough options to look into now. Thanks for the help.

---

