---
title: "Ubuntu www-data group &amp; userad problem"
date: 2010-07-18
forum: Server Platforms
---

### Post by Stoneface on 2010-07-18
I just tried to added myself to group www-date using ```
sudo usermod -a -G www-data user
```. When I checked if I was added I did not see the group listed. ```
~$ groups
me adm dialout cdrom plugdev lpadmin admin sambashare
``` 

www-data a standard group in the Ubuntu desktop edition so what went wrong here?

PS LAMP server added using ```
sudo tasksel install lamp-server
```

---

### Post by Stoneface on 2010-07-18
Still not worked yet. I cannot put files into var/www wthout using sudo or changin the owner to root. I wanted to stick to owner root and www-data group with my own user in www-data, but somehow this is not working yet..

---

### Post by richardjh on 2010-07-19
You probably don't want to do this really.

If you add yourself to group www-data to allow you to write to /var/www/ that implies you are giving the group www-data write access to /var/www/

That means apache can write to /var/www.

Which means your web site has write access to your code.
This is insecure and will likely get your server owned. 

If you are the only developer, why not just make the owner of /var/www/ you?

```
$ sudo chown richardjh /var/www/
```and set permissions to 755 for directories and 644 for files. 

If you really want to add yourself to group www-data, you can do this directly without any issue by editing the line in /etc/group which looks like this:

```
www-data:x:33:
```to look like this 

```
www-data:x:33:richardjh
```Obviously using your user name where required.

The usermod command to do this is 

```
$ sudo usermod -aG www-data richardjh
```Which is what you did. 

**You will only see the change when you log out and back in again.** 

You can manually check it has worked by using 

```
$ grep www-data /etc/group
```And you should see your name on the end of the line.

---

### Post by Stoneface on 2010-07-20
Thanks richardjh for the information. Will make myself owner of the /var/www/ . Will work as well and will be more secure. This so I will do this in the future when I work with a VPS or dedicated server open to the internet.

---

### Post by Bemathis on 2010-08-26
the www-data group is usually reserved for directories that you want accessible to EVERYONE who visits your server. Only assign a dir to the www-data group if you want to give the world read and write privileges and do so with caution.

---

### Post by Vishal Agarwal on 2010-08-26
I am adding myself to the desired group using. 
sudo adduser Vishal_0010203  www-data

---

### Post by Stoneface on 2010-09-03
> **Bemathis said:**
> the www-data group is usually reserved for directories that you want accessible to EVERYONE who visits your server. Only assign a dir to the www-data group if you want to give the world read and write privileges and do so with caution.

Thanks for this tip. So let's say I have a WordPress installation, should I add most files and folder to a separate group? Maybe to the same group as the FTP group that has access to that site?

---

