---
title: "web folder questions"
date: 2008-10-15
forum: Server Platforms
---

### Post by cje on 2008-10-15
Hi, 
I have a few questions concerning the structure of the web folders.

Questions 1:
Under var/www I'm having several sub folders. Each folder should only be accessible/viewable for selected groups. 
Do you have any idea how to hide the sub folders for people who's browsing the www root folder?

Questions 2:
I've read of lot of posts regarding password protecting folders in Ubuntu. I'm not satisfied with the information I've found. So, I'm wondering; is it possible to use the built-in "Ubuntu user authentication" system to protect browsing at selected areas of the web folders?
I.e. is it possible to re-direct a user from a selected web folder to a user authenticated area of the server?

Same question for a ftp server.

Thanks for any suggestions.

---

### Post by penguinpi.com on 2008-10-15
In your apache virtual host file you have sections for directory options:

Like This

	<Directory /var/www/>

If you want to deny browsing access to a directory add something like this:

<Directory /var/www/somedir>

		Options -Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	
</Directory>

The important thing here is the -Indexes this will prevent people from browsing folders through http.

If you want to give specific access to specific IPs or something like that you can make a .htaccess file and place in the directory you want to protect.



Or are you referring to browsing from within the filesystem and not through http?

---

### Post by cje on 2008-11-05
Thanks for your suggestion 
I did find some more info here [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

---

