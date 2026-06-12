---
title: "read/write priveleges to eclipse, gPHPEdit, etc"
date: 2008-07-26
forum: Server Platforms
---

### Post by lsag on 2008-07-26
hello everyone

I'm having trouble understanding how can i use php editors like **eclipse** or **gPHPEdit**, if when i try to save a .php file with one of them, i always have a message saying i don't have enough privileges. like many pelople on this forum, id like to edit the files directly, like in windows.  so far i found, these solutions:

1 - "sudo gedit index.html", edits the file with gedit. don't realy like it, because i'd like to use one of those editors. 

2 - "sudo chmod 777 /var/www", makes the www folder writable, by all users. probably not very safe.

3 - the least practical solution is to edit the file on the desktop, and "sudo cp file.php /var/www" afterwards. my save / test cycles are too frequent for this to be practical

i think the solution is probably in giving those applications read/write priveleges to those folders. but how? is there a plugin or a config file on any of them?

thanks for any answer. I'll keep looking for one too

btw, i use Ubuntu 8.04.1, with PHP Version 5.2.4-2. i have no trouble running the files in "http://localhost"

---

### Post by ad_267 on 2008-07-26
You can't give an application privileges to edit files, only users and groups. You should be able to use "gksudo eclipse file_name" to edit the file.

I have apache + php installed for testing and the way I have it set up I just create symbolic links in /var/www to somewhere in my home directory where I have write privileges for each project.

If /var/www is owned by www-data you could also add yourself to the www-data group and make sure all the directories have group write privileges so that you can edit anything.

---

### Post by lsag on 2008-07-27
i think i know how u did it:

make the alias:
 **ln** -s /var/www/ /home/user_name/Documents/


change the permisions on the alias, because they also have been cloned:
 sudo **chmod** 777 www

many thanks!! :popcorn:

---

### Post by ad_267 on 2008-07-28
Yeah that's sort of what I did. I kept /var/www how it was but did something like "mkdir /home/user/web/project1" "sudo ln -s /home/user/web/project1 /var/www/project1"

---

