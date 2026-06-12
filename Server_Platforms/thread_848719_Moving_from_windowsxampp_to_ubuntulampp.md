---
title: "Moving from windows/xampp to ubuntu/lampp"
date: 2008-07-03
forum: Server Platforms
---

### Post by kumo99 on 2008-07-03
I have xampp installed in both ubuntu and windows under the same box. Now because I can no longer log into windows as a result of a system failure, I tried to move my website which is under development from windows to my newly installed ubuntu xampp. 

I did the following:
I copied the folder /xampp/htdocs/<my-website-folder> to /opt/lampp/htdocs under ubuntu, and xampp/mysql/data/<my-database-name> to /opt/lampp/var/mysql under ubuntu.

However, when I checked http://localhost/<my-website> I get the following:

You don't have permission to access /<my-website> on this server.

any help..? thanks

---

### Post by hai2lp on 2009-07-27
You can move your xampp/htdocs diretory by accessing to httpd.conf on lampp
that you don't need to copied the the folder and the file but i don't now either how to move the sql data never try it before 
```
su 
```
```
enter password if you have 
```
```
sudo gedit /opt/lampp/etc/httpd.conf
```
And change
DocumentRoot "/opt/lampp/htdocs"
And
<Directory "/opt/lampp/htdocs">
into
DocumentRoot "/media/sda1/your_path_to_xampp/htdocs"
And
<Directory "/media/sda1/your_path_to_xampp/htdocs">
and still in terminal
```
cd /opt/lampp/ 
```
```
./lampp restart 
```
And that i can only try if you want to access xampp htdocs 
I need to know also how to access the older Xampp MySQl
Please i need a help also 
Already find anywhere in google but still no result

---

