---
title: "Can't access Subpages/No CSS or Javascript on Apache VHost"
date: 2008-05-25
forum: Server Platforms
---

### Post by Nodestar on 2008-05-25
OK so I just got Apache2 installed and have made 5 virtual hosted web sites. Their all in my home folder so I can work on them from there. They are named domain1, domain2. domain3, etc. When I type [http://domain1.com](http://domain1.com) I get my "This is Domain1 it works" simple HTML page I made to test them all. It all works.

My problem comes in when I copied a site I had to domain1. Within domain1 Apache is set to look for index.html. So I just copied the contents of my main site into the index.html file. Going to [http://domain1.com](http://domain1.com) now brings up the HTML page of my new site. But it has no CSS styling, no images, and no Javascript. Also when I click on any of the links to the subdomains I get a Permission Denied page.
My paths should all be correct. The layout of the folders is below.

/home/My User Name/public_html/domain1.com (domains 1-5 are all located in the public_html folder. 

Within domain1.com
/backup
/cgi-bin
/logs
/private
/public

Within the public Folder I just copy and pasted my entire site. 
So it contains 

/images ---------------// site images. None are displaying properly
/subpages -------------// site subpages. Permission Denied for all.
/jquery-1.2.5.js ------// Javascript Library
/main.js --------------// Javascript File
/screen.css -----------// CSS File
/variance.html --------// Was the Main Page. Now has it's contents 
-----------------------// copy/pasted into /index.html
/index.html -----------// New Main Page and the only page that 
-----------------------// works. But without any CSS, images, or
-----------------------// Javascript

Within my etc/apache2/sites-enabled/domain1

```
# Place any notes or comments you have here
# It will make any customisation easier to understand in the weeks to come

# domain: domain1.com
# public: /home/MY USER NAME/public_html/domain1.com/

<VirtualHost *:80>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin webmaster@domain1.com
  ServerName domain1.com
  ServerAlias www.domain1.com


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html
  DocumentRoot /home/MY USER NAME/public_html/domain1.com/public


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/MY USER NAME/public_html/domain1.com/logs/error.log
  CustomLog /home/MY USER NAME/public_html/domain1.com/logs/access.log combined

</VirtualHost>
```

I haven't changed the index.html just for simplicities sake. I also just put the whole site( css, Javascript, etc) all in the public folder for the same reasons. Modifying the paths as little as possible. Keeping it simple until it's all worked out.
I'm very new to Apache. And Linux. I've made it this far through guides.
I'm running Hardy Heron Desktop Version.
The Server is for local building and testing of web sites. Not to actually host anything.

If you need any other information please ask.
Thanks for any help.

**EDIT**

I thought it might be useful to post some error logs. Here are some when I load the main site. The page tries to retrieve the images but it can't because of permissions.

```

[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/images/closehollow.gif, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/images/closepaper.gif, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/images/comingsoonsaad.gif, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/kelly_thumb.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/red_thumb.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/michelle_thumb.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/soju_thumb.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/tony_thumb.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/branson_thumb.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/images/gobackpaper.gif, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/kelly.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/red.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/michelle.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/soju.jpg, referer: http://domain1.com/
[Sun May 25 04:32:21 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/tony.jpg, referer: http://domain1.com/
[Sun May 25 04:32:22 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/bio/branson.jpg, referer: http://domain1.com/
[Sun May 25 04:32:22 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/images/smalllogo.gif, referer: http://domain1.com/
[Sun May 25 04:32:22 2008] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/MY USER NAME/public_html/domain1.com/public/images/poteblack.gif, referer: http://domain1.com/
```**[B]**[/B]

---

### Post by windependence on 2008-05-25
Some or all of the files ownership probably got hosed when you copied them over. See if the files are owned by root and if they are, you need to change that to the same user that apache runs under, I believe it's www. Let me know what happens.

-Tim

---

### Post by Nodestar on 2008-05-25
When I go to the files Properties > Permissions it says the files are owned by my user name. The Index file. (the only one thats working) is also owned by my user name. All the files have read/write privileges for me. 

I left my apache2 user and group as defaults. 
Within the apache.conf file
```
# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
```

Within the envvars file
```
# export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

```

www-data. I'm not really sure how that works. I've never logged in as a [www.data](www.data) user. I don't really now anything about it. I thought by having the web page files within my home directory I avoided having to change apache files directly and avoided having to use their user name. I don't really know though. Have no idea how it works.

---

### Post by Nodestar on 2008-05-25
It was simple permission problems. I originally had: 
```

drwxr-xr-x 2 MY USER NAME MY USER NAME  4096 2008-05-25 02:09 bio
drwxr-xr-x 3 MY USER NAME MY USER NAME  4096 2008-05-25 02:09 images
-rw-r--r-- 1 MY USER NAME MY USER NAME 15680 2008-05-25 04:32 index.html
-rw-r--r-- 1 MY USER NAME MY USER NAME 15685 2008-05-25 04:32 index.html~
-rwx------ 1 MY USER NAME MY USER NAME 99997 2008-05-25 02:09 jquery-1.2.5.js
-rwx------ 1 MY USER NAME MY USER NAME  4175 2008-05-25 02:09 main.js
-rwx------ 1 MY USER NAME MY USER NAME  2629 2008-05-25 02:09 screen.css
drwxr-xr-x 2 MY USER NAME MY USER NAME  4096 2008-05-25 02:09 subpages
-rwx------ 1 MY USER NAME MY USER NAME 15680 2008-05-25 14:29 variance.html
-rw------- 1 MY USER NAME MY USER NAME 15687 2008-05-25 14:28 variance.html~
```

I tried giving group permissions to read. But that didn't do anything. I then gave Others permissions to read. And that solved it. I didn't relize when I viewed the web site I was considered a "other". It all works now. Thanks for the help.

---

