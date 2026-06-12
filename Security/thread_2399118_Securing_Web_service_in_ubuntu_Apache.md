---
title: "Securing Web service in ubuntu Apache"
date: 2018-08-22
forum: Security
---

### Post by heartlyforjesus on 2018-08-22
I am using Apache web server in ubuntu, Linux. I am writing Web Application using CGI. There are the paths of my works.
> WWW Dir -> /var/myproj/www/
Data Dir -> /var/myproj/data/
App Dir -> /usr/lib/cgi-bin/

Proj Dir -> /home/$USER/myproj/www/
Sometimes I will copy a file from Data Dir to WWW Dir through my CGI application. I will read, write and update data located in Data Dir from my CGI Application. My query is, I should read and write files located in WWW Dir and Data Dir only by CGI Application. Even an any of local user shouldn't read and write those file located in Data and WWW directories.
But I use grunt application to update my WWW Directory from my Proj Directory. Only My CGI application and Grunt Application can update the WWW and Data Directories.
To do this, What Ownership and access mode should I give?

[LIST=1]
[*]Creating Dedicated User and Group.
[/LIST]
> $ sudo groupadd apache
$ sudo useradd apache -g apache -d /dev/null/ -s /sbin/nologin

2.Modified Apache Configuration as below.
> $ sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak
$ sudo nano /etc/apache2/apache2.conf
    User apache
    Group apache
> $ sudo /etc/init.d/apache2 restart

3. make "data" be owned by the "CGI app user" and set it to "700" for directories and "600" for files.
> $ sudo adduser serverdata
$ sudo usermod -a -G apache serverdata 
$ sudo chown -R serverdata:apache /var/myproj/data/
$ sudo find /var/myproj/data/ -type d -exec chmod 700 {} \;
$ sudo find /var/myproj/data/ -type f -exec chmod 600 {} \;

4.Added 'www' ownership to group.
> $ sudo chown -R apache:apache /var/myproj/www/
$ sudo chmod -R 775 /var/myproj/www/
After this, I wrote a cgi call to copy a file from /var/myproj/data/ to /var/myproj/www/. But It didn't work.
What I missed in this settings? Why It couldn't get copy of that file from my Data directory to wwwdirectory which are all in the same group apache.
Test.cgi located in /usr/lib/cgi-bin/ just read this file '/var/myproj/data/test.html' and copies into '/var/myproj/www/'. But that Test.cgi doesn't read anything from '/var/myproj/data/' location.

---

### Post by QIII on 2018-08-22
Hello!

Please use the default and color unless you have a compelling reason to draw attention to a particularly important part of your post.

Thanks.

---

