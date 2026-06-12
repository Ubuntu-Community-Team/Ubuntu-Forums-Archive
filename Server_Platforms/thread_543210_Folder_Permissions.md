---
title: "Folder Permissions"
date: 2007-09-04
forum: Server Platforms
---

### Post by turtle02 on 2007-09-04
I am using ubuntu lamp server. the /var/www directory will not allow me to edit anything unless i am root. how to i add another user to full read write access.

---

### Post by inphektion on 2007-09-04
You can chown the folder to the user leaving the group to whatever it is now.  so if group and owner are both root now and perms are 744 then chown user:root www and make perms 774

---

### Post by turtle02 on 2007-09-05
Sounds good my friend but i am new to linux and i have no idea what chown mean or the command to do what you talked about. can you help me please.

---

### Post by p_quarles on 2007-09-05
You'll need to type the following commands in the terminal:
```
sudo chown (username):root /var/www
```
and then
```
sudo chmod 744 /var/www
```

---

### Post by turtle02 on 2007-09-06
Thanks for the help i will try these tonite. Can you explain to me what each command is actually doing?

---

### Post by turtle02 on 2007-09-06
After running those commands this is what i get when trying to browse to my web server.

Forbidden

You don't have permission to access / on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.0.55 (Ubuntu) Server at 192.168.1.106 Port 80

---

### Post by p_quarles on 2007-09-06
chown and chmod change the owner and permissions levels, respectively, of a file/directory. "744" is a numeric representation of a permission level that says "everyone can read, only owner can write and execute."

The only reason I can think of for those commands to fail is that you don't actually have administrative access to this server. Is it yours, or is it an external host? 

Anyway, I don't really think that changing ownership is the right way of going about this. The safest way to transfer files to a web server's document root directory is to use sftp (part of the OpenSSH-server package) and connect to it either through the command line or with an sftp compatible client like GFTP or FileZilla.

---

### Post by turtle02 on 2007-09-06
i am working locally on the server. why is it giving me that error now.

---

### Post by p_quarles on 2007-09-06
I honestly don't know. It could be that you are trying to run those commands from a user who doesn't have full sudo privileges, but it could be a number of other things as well. 

That said: it's really much better, in terms of security, to use the root account or sudo to manage the web server's doc root.

---

### Post by turtle02 on 2007-09-07
now my site is down. can anyone help? I give me the error posted above.

---

