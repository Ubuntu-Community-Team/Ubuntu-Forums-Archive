---
title: "LAMP Help"
date: 2008-10-11
forum: Server Platforms
---

### Post by Zook on 2008-10-11
I'll just go in order of the commands I issued.

adduser zook
usermod -a -G admin zook
sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart
sudo apt-get install mysql-server
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
sudo /etc/init.d/apache2 restart
mkdir /home/zook/public_html
sudo ln -s /home/zook/public_html /var/www
nano /home/zook/public_html/index.html
Error reading /home/zook/.nano_history: Permission denied
Press Enter to continue starting nano.

I'm thinking I messed up on the ln -s command.  Am I suppose to link it to a directory like /var/www/WEBSITE ?

The reason I ask is when I go to the domain I own now that points to the server it shows "Index of /" and shows the public_html directory and the testphp.php file I made, but like I said its not going to public_html automatically.

Would appreciate some help please :)

---

### Post by cariboo on 2008-10-11
You got the ln -s command almost right:

> sudo ln -s /home/zook/public_html /var/www

It should be:

```
ln -s /home/zook/public_html /var/www/public_html
```

The way you had it /var/www = public_html.

Jim

---

### Post by volkswagner on 2008-10-11
> nano /home/zook/public_html/index.html
Error reading /home/zook/.nano_history: Permission denied
Press Enter to continue starting nano.

You got this error using nano due to permissions.  When you created the user directories, sudo was needed.  These files need to be chown to their owner, and the group you want.  You are not the owner so you need to use sudo to edit the file.  

```
sudo nano /home/zook/public_html/index.html
```

Or switch to user zook

```
su zook
```

This will tell you details about the files and sub-directories```

ls -alt /home/zook
```

This will set the owner and recursively all sub files and folders
```
sudo chown -R zook /home/zook
```

Or you can set the owner and group.  Depending on what goup you want

```
sudo chown -R zook:zook /home/zook
```
or
```
sudo chown -R zook:www-data /home/zook
```

You may also want to change the permissions for zooks files with chmod.  This may not be required since you are using links

---

### Post by lykwydchykyn on 2008-10-12
> **cariboo907 said:**
> You got the ln -s command almost right:

It should be:

```
ln -s /home/zook/public_html /var/www/public_html
```

The way you had it /var/www = public_html.

Jim

Actually, if /var/www already existed (and I'm guessing it did), the command he used would have created a symlink to public_html inside /var/www.  I think what the OP was trying to accomplish is to make /var/www = public_html.  

The command was correct, but you'd need to delete /var/www first.  Otherwise, it assumes you want to link inside the existing folder.

---

