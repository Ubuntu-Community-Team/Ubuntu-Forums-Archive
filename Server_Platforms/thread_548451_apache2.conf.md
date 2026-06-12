---
title: "apache2.conf"
date: 2007-09-11
forum: Server Platforms
---

### Post by u_kraze on 2007-09-11
hi 

First off i installed ubuntu 7 and then i installed the server since im not so  verse in the command line as others but am trying to.

Anyway ive set up php, mysql and apache2 on it and well it works fine. Now i wanted to lock down the server well security wise. So ive been search for my httpd.conf file when i did find it i found out it has nothing inside so i check some more and googled some more and checked the forums and BOOM!! i saw the config for the server was in the apache2.conf so i opened that up and i have the default configs. 

What i would like to know is that i want to turn the directory index off because everytime i go to [http://www.my.site.com/](http://www.my.site.com/) it lists the directory files because i have no index.html file there instead i just want the listing to be turned off for now. 

All ive seen in this file is the Fancy Indexing thing and ive tried turning that off then they have a listing above that but i didnt trouble that. ive searched the whole file the the <directory> where it says allow or deny and theres none there for my /var/www  directory.

Can someone give me some advice.

thanks in advance

---

### Post by eggdeng on 2007-09-11
The appropriate configuration file is /etc/apache2/sites-available/default
Find the section

DocumentRoot /var/www
	<Directory />
		Options Indexes FollowSymLinks
		AllowOverride None
	</Directory>
	
Remove the word Indexes and restart apache.

---

### Post by u_kraze on 2007-09-11
thanks you so much:lolflag:

---

### Post by southernman on 2007-09-11
You could easily have just put a - sign in front like this:

DocumentRoot /var/www
<Directory />
Options -Indexes FollowSymLinks
AllowOverride None
</Directory>

---

