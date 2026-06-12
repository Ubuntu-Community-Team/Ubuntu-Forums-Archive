---
title: "How can I show only the shares that user have access to in SAMBA ?"
date: 2009-05-21
forum: Server Platforms
---

### Post by uge on 2009-05-21
Hi people

Here's my config :
Ubuntu 8.04 LTS, Server version, 64 bits

I've got SAMBA running, security = user

Now I made my set-up and everything is great except that when my users type in the IP of the server, it doesn't ask them a password, it simply displays all the possible share.
When they click on a share they have access to, since I made "home shares", their username appear as a new share, but still then can see all the other share anyway.

Is it possible to make it so when they type in the IP of the server, they get asked for their passwords, and then they only see the shares they have access to ?

Or any suggestions that could help me do something similar ?


THANKS ! 
:guitar:

---

### Post by toolfan2k4 on 2009-05-22
Are the end users using windows based PCs? If so you can login using an admin account and set permissions under the security tab of the folders properties screen.

IE:Right click the folder, choose properties. Next click the security tab and alter the permissions. Again, this will need to be done with an admin account, most likely root with your root password. Unless of course you have already made yourself an admin account with a different user name.

---

### Post by koenn on 2009-05-23
Samba can hide shares that users don't have access to, eg with
```

		hide dot files = yes
		hide unreadable = yes

```
more access control : 
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html)

Your server should prompt for passwords, though. 
Maybe you have some sort of guest access enabled ? or the clients pass a valid username and password automatically (I don't remember all the details of smb ...)

---

### Post by uge on 2009-05-23
> **koenn said:**
> Samba can hide shares that users don't have access to, eg with
```

        hide dot files = yes
        hide unreadable = yes

```more access control : 
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html)

Your server should prompt for passwords, though. 
Maybe you have some sort of guest access enabled ? or the clients pass a valid username and password automatically (I don't remember all the details of smb ...)

Well they do get prompted for their password, but only once they click on a share.

And about the code you posted, where should I put these lines ?
in smb.conf ?

Thanks !

---

### Post by koenn on 2009-05-23
yes, in smb.conf.

---

