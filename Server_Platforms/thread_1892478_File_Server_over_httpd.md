---
title: "File Server over httpd"
date: 2011-12-08
forum: Server Platforms
---

### Post by dheerajkabra on 2011-12-08
Hi,

I want to host few files on a web server and want my users to download it via Web. Basically, I am looking for similar tree structure like the one shown in attached screenshot.

So, I installed httpd and copied all the files/folders that I want users to download under /var/www/html.
however, when I visit the IP address of the my web server, I see the the index.html content and nothing else. My aim to get a "Index of /" structure as shown in the screenshot. 

Could you point me what I am missing here?

Thank you.
-Dheeraj.

---

### Post by Lars Noodén on 2011-12-08
To get a directory index like that you need to make sure that [font=Courier New]index.html[/font] has been removed from the directory and that configuration [Options](http://httpd.apache.org/docs/trunk/mod/core.html#options) for that directory (or hierarchy of directories) includes **Indexes**.

---

### Post by dheerajkabra on 2011-12-08
Ok. I removed the index.html and commented out lines in welcome.conf and See the directory structure. but now I am not able to see the files inside my directories. Here is some info:

```
# pwd
/var/www/html/pub

# ls -l
total 20
drwxr-xr-x 2 root root 4096 Dec  8 01:51 test1
drwxr-xr-x 2 root root 4096 Dec  8 01:38 test2
drwxr-xr-x 2 root root 4096 Dec  8 01:51 test3
drwxr-xr-x 2 root root 4096 Dec  8 01:51 test4
drwxr-xr-x 2 root root 4096 Dec  8 01:51 test5

# ls -R
.:
test1  test2  test3  test4  test5

./test1:
README

./test2:
README

./test3:
README

./test4:
README

./test5:
README
```

So i can see all the test* directories but when i click on any one of them, i do not see the "README" which is file...
Thnx

---

### Post by dheerajkabra on 2011-12-08
BTW, the "Indexes" option is already in place. Probably that's why i can see the folder structure as soon as I removed the index.html:


# grep -n -i options /etc/httpd/conf/httpd.conf
.
.
.
320:    Options Indexes FollowSymLinks


But i still can see only the directories, the files are still not visible.

---

### Post by Lars Noodén on 2011-12-08
I'm not able to duplicate your error.  Are you sure that all the directories and files are readable by Apache?

---

### Post by dheerajkabra on 2011-12-08
Yes. just to make sure that this not a permissions issue, I made everything "777" by running below command:
# chmod -R 777 /var/www/html/

But i still can not see the files. If i create child directories, i can see them, but files are still missing. I think this is not a permissions issue but something that I might have missed in httpd.conf.

Thanks for the reply.

---

### Post by Lars Noodén on 2011-12-08
777 is unsafe.  Better set it to 775 or 755.

What changes did you make to httpd.conf or other config files?  With the default settings, I am able to see the directory indexes on my computer.

---

### Post by dheerajkabra on 2011-12-08
The only changes i made are:

```
ServerAdmin root@localhost
ServerName <my_hostname>:80
```

and created following stanza at hte end:

```
<VirtualHost *:80>
    ServerAdmin root@localhost
    DocumentRoot /var/www/html
    ServerName <my_hostname>
    ErrorLog logs/<my_hostname>-error_log
    CustomLog logs/<my_hostname>-access_log common
</VirtualHost>
```

It's a very basic configuration with most of the default settings.

---

### Post by dheerajkabra on 2011-12-08
i mean, i can see the Directory indexes but i cannot see the "Files" Inside those Directories. If I create child directories, I can see them as well. the only the "files" are not visible.

---

### Post by dheerajkabra on 2011-12-08
Found it.

The problem was the files that I created for my testing purpose, I named them as "**README**". And apache will ingore files that are "**README**" by default.
this is aparent from below configuration in httpd.conf file:


```
# grep -i IndexIgnore /etc/httpd/conf/httpd.conf | grep -v ^#
IndexIgnore .??* *~ *# HEADER* README* RCS CVS *,v *,t
```
I created a file with different name and WHOA!!!! I can see it.

This is probably the worst coincident I have ever come accross.

Thanks for your quick responces.

---

### Post by Lars Noodén on 2011-12-08
Glad it's solved.  

Interestingly the default for Apache 2.2.20 on Precise Pangolin doesn't ignore README, just backup files and 'hidden' files.  What version are you using?

---

