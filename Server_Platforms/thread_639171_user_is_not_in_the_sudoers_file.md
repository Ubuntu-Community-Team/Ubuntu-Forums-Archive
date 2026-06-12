---
title: "user is not in the sudoers file"
date: 2007-12-12
forum: Server Platforms
---

### Post by hobojjr on 2007-12-12
I just installed ubuntu 7.10 server with "user" as the root. But when I tried to do sudo it said that "user" is not in the sudoers file... 

I can't do anything now... any one knows wtf?

---

### Post by gaten on 2007-12-13
That's very odd. Can you access any other administrative funtions, like Synaptic Package Manager? If you can't something's messed up with your installation, and you might have to go into single user mode to fix it.

---

### Post by suyixiang on 2007-12-14
I have the same problem!!!  I just installed 7.10 server edition.

Did you ever find a solution?

---

### Post by ddb9587 on 2007-12-15
You might try booting into recovery mode and adding user to the file:
/etc/sudoers

---

### Post by HermanAB on 2007-12-15
Yup, I guess the install wizard got confused by your weird choice of user name.  Boot into single user mode, create a new user account with a proper name, read the sudoers man page and edit the file /etc/sudoers.  It is not difficult to understand.

Cheers,

Herman

---

### Post by Duroon on 2007-12-15
> **HermanAB said:**
> Yup, I guess the install wizard got confused by your weird choice of user name.  Boot into single user mode, create a new user account with a proper name, read the sudoers man page and edit the file /etc/sudoers.  It is not difficult to understand.

Cheers,

Herman

How do you boot into single user mode? I am having the same problem and I have a user account named jim.


Nevermind I figured it out already.

---

### Post by The Cog on 2007-12-17
But normally, there are no users in the sudoers file - just the group **admin**. Adding a user to sudoers is a departure from the standard install. Make sure that your user is a member of group admin, and that should be enough.

---

### Post by mstrickl on 2008-02-13
I have the same problem. Also I cannot see the admin group.

---

### Post by baixinhu on 2008-03-18
> **hobojjr said:**
> I just installed ubuntu 7.10 server with "user" as the root. But when I tried to do sudo it said that "user" is not in the sudoers file... 

I can't do anything now... any one knows wtf?

I have the same problem, installed ubuntu server 7.10 not only didnt get the Xdesktop but can't install it because when i run sudo "user" apt-get ubuntu-desktop it says "user" is not in the sudoers file

---

### Post by D!mon on 2008-03-18
It seems to be a bug in the 7.10 installation; anyway you can load in a single user mode (select the 'recovery' option from the grub boot menu). 
 and after that add the following line to your /etc/sudoers file:

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Also make sure that admin group exists and the user is in this group (or optionally you can use say the adm group instead of admin)

---

### Post by sambhav on 2008-07-18
In ubuntu, the default first user has sudo priviliges. how one can restrict sudo priviliges to root user only?

( i am newbir to ubuntu, please excuse if its wrong thread to post this query)

---

### Post by gaten on 2008-07-19
Yes you *can* remove the user from the **admin** user group, but I wouldn't recommend this, as you won't have a way to administer your system, as Ubuntu by default doesn't even have a root user. 

Would I would recommend, however, is to create a new user via System->Administration->Users and Groups and do *not* add them to the admin group (this is the default). This will create an unprivileged user account which sounds like what you need.

---

