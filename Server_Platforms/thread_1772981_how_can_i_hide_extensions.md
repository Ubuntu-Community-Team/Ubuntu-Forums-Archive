---
title: "how can i hide extensions?"
date: 2011-06-01
forum: Server Platforms
---

### Post by stigma-x11 on 2011-06-01
I installed Ubuntu 32 bit non server edition a while ago and set up mysql, phpmyadmin, apache2, php5 and also proftpd my site is up and running perfectly but one thing I want to do is to hide the file extensions like for example at the moment it shows [http://mydomain.com/index.php](http://mydomain.com/index.php) i just want [http://mydomain.com/](http://mydomain.com/) on all pages.

---

### Post by arrrghhh on 2011-06-01
> **stigma-x11 said:**
> I installed Ubuntu 32 bit non server edition a while ago and set up mysql, phpmyadmin, apache2, php5 and also proftpd my site is up and running perfectly but one thing I want to do is to hide the file extensions like for example at the moment it shows [http://mydomain.com/index.php](http://mydomain.com/index.php) i just want [http://mydomain.com/](http://mydomain.com/) on all pages.

Isn't that how php works...?

I'm not an expert on the matter, but I think that's just how it works...  Is it causing a problem?

Also, you posted in the Server section yet you said you're running the non-server edition...

---

### Post by ruffEdgz on 2011-06-01
You have to make sure the apache option "DirectoryIndex" has what you need to make your request happen.

You should be able to find this by executing the following command:
```

grep -i "DirectoryIndex" /etc/apache2/sites-available/dir.conf

```
This config file should also be sym-linked to another directory called /etc/apache2/sites-enabled/.

Read more about "DirectoryIndex" at this link: [http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex](http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex)

---

### Post by SeijiSensei on 2011-06-01
You can create a link to [http://www.example.com/](http://www.example.com/), but the browser will always show the actual file being displayed in the address bar like [http://www.example.com/index.php](http://www.example.com/index.php).  There's no way you can control this, nor would I want you to have the ability to do so.  Users should be able to see the exact address of every file they display.

If you're asking how to make sure [http://www.example.com/](http://www.example.com/) results in [http://www.example.com/index.php](http://www.example.com/index.php) being sent to the browser, ruffEdgz already answered that question.

---

### Post by ruffEdgz on 2011-06-01
> **SeijiSensei said:**
> You can create a link to [http://www.example.com/](http://www.example.com/), but the browser will always show the actual file being displayed in the address bar like [http://www.example.com/index.php](http://www.example.com/index.php).  There's no way you can control this, nor would I want you to have the ability to do so.  Users should be able to see the exact address of every file they display.

I would have to challenge this claim since sites like [www.google.com](www.google.com) and [www.ubuntu.com](www.ubuntu.com) don't display their indexed pages in the web browser (attachment shows what I mean). Granted, I could probably look at the source to find out what the name of the index page is if I cared but ... sometimes I don't ;)

I did miss two more things about getting this to work which is :
[LIST=1]
[*]Make sure **autoindex.conf** and **autoindex.load** are in the /etc/apache2/mod-enabled/ directory
[*] Find any <Directory> variable that you want the indexing to work on and add **Options +Indexes** to it. Example below
[/LIST]
```

<Directory /var/www/>
   Options +Indexes FollowSymLinks MultiViews
   AllowOverride None
   Order allow,deny
   allow from all
</Directory>

```

---

### Post by stigma-x11 on 2011-06-01
I dont want to start any arguments as you guys know a lot more about this then me, but it is possible on a website my friend hosted for me in the cpanel he had an option to change whether you can view the extensions or not.

It doesnt really make a difference whether they are hidden or not but it looks cleaner to me.

---

### Post by SeijiSensei on 2011-06-01
> **ruffEdgz said:**
> I would have to challenge this claim since sites like [www.google.com](www.google.com) and [www.ubuntu.com](www.ubuntu.com) don't display their indexed pages in the web browser (attachment shows what I mean).

I'm going to guess that, for Google, there's no actual "page" being displayed like "index.html" or "index.php".  Rather it's probably an application that generates the HTML code and sends it to the browser with the appropriate HTTP headers.  I doubt Google is running a normal web server like Apache to handle requests.  Try this:

```

$ telnet www.google.com 80
[server replies]
GET / HTTP/1.1


```

Note that you have to type two returns to get the site to send you the appropriate page.  

I don't know about ubuntu.com.

---

### Post by ashwinrao on 2011-06-01
I think, you can hide file extensions by simple .htaccess file with below codes. 

>  
RewriteEngine on 
RewriteCond %{REQUEST_fileNAME} !-d 
RewriteCond %{REQUEST_fileNAME}\.php -f 
RewriteRule ^(.*)$ $1.php 

Correct me if I'm wrong.

---

### Post by stigma-x11 on 2011-06-01
I think you might be right I remember seeing somewhere online before about .htaccess being able to change the extensions I will try it when I wake in the morning.

---

### Post by arvevans on 2011-06-02
It has been a while since I looked at this, but if my recollection is correct, you do not need extents on file names in any UNIX or UNIX derivative (i.e. Linux) operating system.  What to use for viewing, reading, or executing a file is carried in the hidden "sticky bits" that are not visible to the user.  Having file extents was only to make it clearer to the user what type of program to use with what type of file, and mostly came about because the then popular CPM file structure had file extents to show the operating system which program went with which file.

So, to better answer your question...try renaming a single file to something without the file name extension.  Then try using that file in the normal manner.  You should find that the original file association still works.  For new files with no extent you may have to set the file association data (i.e. the "sticky bits") to make things work right.  You can do this by setting the "Open With..." controls for individual files.

If this works for you, then you could really confuse things by renaming all your files, including data and executables, to not have any name extensions.  After doing this the only way you could readily determine what a file really is is by using the CLI "file" command to see how it interpreted the sticky-bit field.

---

