---
title: "Web Server Folder Permissions!"
date: 2007-08-12
forum: Server Platforms
---

### Post by kevin11951 on 2007-08-12
i have a lamp server installed on ubuntu fiesty, and no matter what the folder permissions are set to on my computer (i used "sudo chmod -R 777 /home/ksoviero/www"), the web server just wont let anyone in, it says:

Forbidden

You don't have permission to access / on this server.
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at 71.70.131.6 Port 80

---

### Post by shearn89 on 2007-08-12
> **kevin11951 said:**
> i have a lamp server installed on ubuntu fiesty, and no matter what the folder permissions are set to on my computer (i used "sudo chmod -R 777 /home/ksoviero/www"), the web server just wont let anyone in, it says:

Forbidden

You don't have permission to access / on this server.
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at 71.70.131.6 Port 80

Try ```
sudo chmod a+R
```

I don't know that much about web servers, but i think thats what the command should be. In your command, the "-R" takes away read permissions... [i think]

---

### Post by kevin11951 on 2007-08-12
that didnt help :(

---

### Post by schorsch on 2007-08-12
First of all what is the content of "DocumentRoot" in the file "/etc/apache2/sites-available/default":

```
grep DocumentRoot /etc/apache2/sites-available/default
```

After a standard installation of apache(2) this is set to /var/www. Did you change it to "/home/ksoviero/www"?

Second the folder should be owned by the user who is running the apache daemon and this is normally www-data in group www-data. This is important as ....

Third you should NEVER make the DocumentRoot folder world-writeable!! It should be 755 and nothing more! Every directory in this DocumentRoot should then have 755 as permissions and every plain file should have 644 as permissions.

---

### Post by kevin11951 on 2007-08-12
[LIST=1]
[*]i changed the default document root
[*]i want it to be world avalable
[/LIST]

---

### Post by schorsch on 2007-08-12
Have you restarted the webserver after changing DocumentRoot?

```
/etc/init.d/apache2 restart
```

---

### Post by kevin11951 on 2007-08-12
i restarted the whole computer

---

### Post by Brunellus on 2007-08-12
post moved to the server area.

---

### Post by heimo on 2007-08-12
Who, which user and which group, owns the files and directories? Check owner and permissions of root directory itself. Try accessing subdirectory and a specific file.

---

### Post by kevin11951 on 2007-08-13
i did, it didnt work, and the folder permissions are set to me...

---

