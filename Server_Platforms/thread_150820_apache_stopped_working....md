---
title: "apache stopped working..."
date: 2006-03-26
forum: Server Platforms
---

### Post by grim918 on 2006-03-26
I had my apache server working with php5 and I wanted to use php4 so I uninstalled php5 and installed php4. I restarted the apache server to update the new settings, but when I did that the server is no longer working. When I try to open up any file in the browser it prompts me if I want to download it. I got tired of messing with it so I uninstalled everything and reinstalled apache,php but I still get the same problem. I don't get any errors. It tells me that everything is up to date and no files have been updated. Has anyone had this kind of problem, I would appreciate any help.

---

### Post by wsanders on 2006-03-26
Do you have anything new (since you updated) in /var/log/apache in either your error.log file or your access.log ? This can give you an idea of whether the server is doing anything.

---

### Post by grim918 on 2006-03-26
ok my bad, apache is working. I tried to load a test.php page and the server said that it could no find it. I think that the path got mixed up somehow. I have my test.php file in /var/www/ but the server says that it can't find it. Do you know how to check where the servers document root is at.

---

### Post by wsanders on 2006-03-26
You can go into /etc/apache2/sites-enabled/000-default
the DocumentRoot directive at the top should be it.(I think)
If you're using Apache 1.3, it's under /etc/apache/httpd.conf ; search for DocumentRoot

---

### Post by grim918 on 2006-03-27
ok, apache is now working. I don't know what happened I just left to go work, when I came back it was working like before. I have another problem though. PHP is not installed. I tried to reinstall PHP using

> sudo apt-get install php4 

when it installs it says that I already have the most recent files and that no files were updated. I don't get any errors with the installation. When I try to view any files with my browser it doesn't display them. I just get a prompt to download the file. It does this with php files. If I load an html file it works. I think that php is not working with apache but im not sure. Does anyone know how to fix this.

---

