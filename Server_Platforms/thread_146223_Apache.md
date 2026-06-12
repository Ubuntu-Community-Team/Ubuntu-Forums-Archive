---
title: "Apache"
date: 2006-03-17
forum: Server Platforms
---

### Post by ice.man on 2006-03-17
i installed apache lastnight but i don't seem to have permissions is there an easy what to give myself permissions so i can put my website in there..



Also how do u setup vncserver?

---

### Post by tkiesel on 2006-03-17
See if this works.  Replace the word username in Line 1 with your user name.

```
sudo adduser username www-data
sudo chown -R www-data:www-data /var/www
sudo chmod -R 664 /var/www
```

You might want to change that 664 to something else depending on the directories, files and intended uses that you've got in mind for your website.  But that should do a basic "let me add files to the website without slamming my head against the wall" setup.

For educational purposes:  Line by line

Line 1: Adds your username to the group that Apache is in.
Line 2: Makes the web directory owned by the Apache user and the Apache group (which you're now in!)
Line 3: Sets the website file space as readable and writeable by the user and group mentioned in Line 2. Also sets the file space as readable but NOT writeable by "everyone else" (i.e. your website visitors)

---

### Post by ice.man on 2006-03-18
it says i don't have permissions to write to /var/www

---

### Post by tkiesel on 2006-03-18
Even after executing the three lines above?  Those lines should very explicitly give you write access to /var/www

---

### Post by ice.man on 2006-03-18
yes even after i did those three line that u said to try

---

### Post by ice.man on 2006-03-18
***@lanstats:~$ sudo adduser *** www-data
Password:
The user `***' is already a member of `www-data'.
***@***stats:~$ sudo chown -R www-data:www-data /var/www
***@***stats:~$ sudo chmod -R 664 /var/www
***@***stats:~$


And it still says i don't have permissioms

---

### Post by kmi on 2006-03-19
Hello what are the actual permissions and owner of /var/www ?

---

### Post by d-x on 2006-03-19
Root is the user permissions if you right click on the folder and goto permissions you'll see that you don't have actual permssions until you make it 777 which is read write etc.

---

### Post by kmi on 2006-03-19
[QUOTE=d-x]Root is the user permissions if you right click on the folder and goto permissions you'll see that you don't have actual permssions until you make it 777 which is read write etc.[/QUOTE]
Oops, I meant : "Hello ice.man, what are the actual permissions and owner of YOUR /var/www ?" : 
```
ls -la /var
```
d-x : if I were you I would NEVER chmod 777 /var/www... [-( but follow tkiesel advice in post#2.

---

### Post by LordHunter317 on 2006-03-19
You shouldn't make the user a member of the www-data group.  That's for Apache and Apache only.

What you should do, is simply give the user ownership of /var/www.  There's no reason for Apache to own it, nor should it.  The person editing the files should own it.  

You just have to make sure to give Apache read access to all the files in there.   The simpliest way to do that is to ensure they're world readable.

So, to sum up:***NEVER EVER EVER EVER EVER SET PERMISSIONS ON ANYTHING TO 777.***  I can't stress that enough.  It's never a solution.

To control /var/www, do the following:```
sudo chown me.me -R /var/www
sudo chmod -R o=rX /var/www
```

In your specific case, take yourself out of the www-data group:```
sudo deluser me www-data
```

Logout and in to make the membership changes work.  This is likely the reason why it didn't work before.

---

### Post by kmi on 2006-03-19
:-# 

Does it mean I was wrong if I had ? :
```
sudo chown me:www-data -R /var/www
```
Nevertheless, I changed it to :
```
sudo chown me:me -R /var/www
```

I've noticed the symlink /var/www/phpmyadmin belongs to root will this affect phpmyadmin if I change it to belong to me ?

---

### Post by ice.man on 2006-03-19
thanks alot guys it seems to be working all fine now but never the less i might run into more problems and i'll just post a new thread :KS \\:D/

---

