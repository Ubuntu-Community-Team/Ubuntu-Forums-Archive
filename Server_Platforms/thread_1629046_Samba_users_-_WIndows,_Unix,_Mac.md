---
title: "Samba users - WIndows, Unix, Mac"
date: 2010-11-23
forum: Server Platforms
---

### Post by molinus on 2010-11-23
If I want to add Windows & Mac users as Samba users, must I first add them all as Ubuntu users?

If so, since none of the other users will actually be working on the Ubuntu Server, how do I disable the other non-admin users on the Ubuntu Server login screen.

I am using Webmin to administer some server settings, and command line for others.

Thanks in advance for any help.

---

### Post by yettiman2208 on 2010-11-23
Is it possible to create a generic Logon that all of your windows users can use?
for example. John Doe logs onto his XP machine as John Doe. Then connects to the samba server. It asks for his credentials and he logs on as Samba User (the one you created).

This is how my mac connects to the samba.

My mac Username is John Doe (example), but I have a ubuntu user called John. When I connect to the server from my mac, I connect as John with a password.

however, if you need specific limitations for different users/machines, then I am not sure you can avoid creating users. But I do not know this.

good luck.

-a large yetti

---

### Post by molinus on 2010-11-23
Thanks!

I went ahead and added individual Ubuntu users, but first used Webmin to automatically add new Unix users as Samba users.
Worked beautifully.
Then I used gconf-editor to not show any users names at login (under /apps/gdm/simple-greeter).

---

### Post by redmk2 on 2010-11-23
> **molinus said:**
> Thanks!

I went ahead and added individual Ubuntu users, but first used Webmin to automatically add new Unix users as Samba users.
Worked beautifully.
Then I used gconf-editor to not show any users names at login (under /apps/gdm/simple-greeter).

You can create a ***system user*** that has no login shell.  The user **[COLOR="DarkRed"]nobody [/COLOR]**is an example.  This provides you with the ability to restrict the user to Samba shares only.  They can't login to the Samba server as regular users.  In addition there is no /home directory for you to manage.  Just because there is no name at the login doesn't mean they can't login.

Look for ***System User ***in this man page```
man adduser
``` 

See the first 2 posts on this [**_thread_**]("http://ubuntuforums.org/archive/index.php/t-516518.html").

---

