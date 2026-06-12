---
title: "Only Firefox can connect to local named virtualhost"
date: 2015-06-09
forum: Server Platforms
---

### Post by monkeybrain20122 on 2015-06-09
Hi, I am setting up a named virtualhost in my /home directory for development. Here is my configuration file test.conf
```


NameVirtualHost *:80

<VirtualHost *:80>
    ServerAdmin webmaster@test
    ServerName test.com
    ServerAlias www.test.com

    DocumentRoot /home/monkeybrain/www/webtest
    
    
   <Directory /home/monkeybrain/www/webtest/>
        Options Indexes FollowSymLinks
        AllowOverride all
        Allow from all
        Require all granted
    </Directory>


    ErrorLog ${APACHE_LOG_DIR}/webtest/error.log
    CustomLog ${APACHE_LOG_DIR}/webtest/error.log combined

```


My /etc/hosts
```

127.0.0.1    localhost
127.0.1.1    monkeybrain-localhost
127.0.0.1    test.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```

I saved test.conf in /etc/apache2/sites-available then ran 

```
sudo a2ensite test 
sudo service apache2 restart
```


In Firefox it works, typing localhost in the url shows the standard apache2 greetings  and typing test.com shows my index.html file. But in Chrome localhost gives the apache2 greetings and test.com produces an error

```
**Forbidden**

[COLOR=#000000][FONT=Times New Roman]You don't have permission to access / on this server.[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.[/FONT][/COLOR][HR][/HR]Apache/2.2.29 (Unix) mod_ssl/2.2.29 OpenSSL/1.0.1e-fips mod_bwlimited/1.4 Server at www.test.com Port 80

```

I tried with opera and got the same error as in Chrome.

What is going wrong? Thanks.


OS is Ubuntu 15.04 Desktop version.

Edited: I have not changed any permission on  /home/monkeybrain/www/webtest yet.

---

### Post by monkeybrain20122 on 2015-06-09
Now it works for Chrome as well after clearing the cache. But Opera is a new install just to test this and still does not work.

Additional questions:

I have read many tutorials on setting up virtualhosts on Ubuntu 14.04 and 14.10 but only two mentioned editing the hosts file and only in one stackoverflow thread I find the NameVirtualHost  directive and one mentioned disabling 000-default.conf (not needed here with the NameVirtualHost directive) All the other tutorials don't work. Am I doing something wrong?

---

### Post by volkswagner on 2015-06-09
Web browsers that allow searching in the address bar often need to type the full url, else it will search instead.

Try typing [http://test.com](http://test.com) I even add a space at the end, then hit enter.

---

### Post by nerdtron on 2015-06-09
A document root on /home? I think this won't work since your folder /home/monkeybrain is only readable by you.

Or if that permission is already world readable, then you have a bigger problem, like app-armor since you did not put the vhost document root on the standard folder /var/www/html folder.

Try to put the document root on /var/www/html folder first and be sure that all files are world readable, aka "chmod -R a+r /var/www/*"

---

### Post by monkeybrain20122 on 2015-06-09
> **volkswagner said:**
> Web browsers that allow searching in the address bar often need to type the full url, else it will search instead.

Try typing [http://test.com](http://test.com) I even add a space at the end, then hit enter.

But it works for Firefox and Chrome both of which allow searching in the address bar. Only doesn't work in Opera and it doesn't search but give a 403 error.

Edited: in view of my second post it actually only does not work in Opera, but I can't change the title of the thread.

---

### Post by monkeybrain20122 on 2015-06-09
> **nerdtron said:**
> A document root on /home? I think this won't work since your folder /home/monkeybrain is only readable by you.

Or if that permission is already world readable, then you have a bigger problem, like app-armor since you did not put the vhost document root on the standard folder /var/www/html folder.

Try to put the document root on /var/www/html folder first and be sure that all files are world readable, aka "chmod -R a+r /var/www/*"

Sorry, I am not following. What are the appamour problems? /home/monkeybrain is world readable, but not writeable I suppose I need to chmod o+w to the upload subfolder (like /home/monkeybrain/www/webtest/public) The point of not putting the document root in /var/www is because I don't want to change the default permissions and I don't want to have to sudo whenever I edit a script in it

---

### Post by nerdtron on 2015-06-09
> What are the appamour problems?

AppArmor, Ubuntu's version of SELinux. It basically strengthens security by limiting application access to their intended directories. In this case, apache is intended to access /var/www/html. If you point your document root to another directory, then you'll get "Access Forbidden" because apache is not allowed to access that directory. This can't be solved by making all files world readable.

One way I think to workaround is to keep the document root as /var/www/html. But instead of a folder, delete this and make it a symlink to your desired document root.
```
ln -s /home/monkeybrain/www/webtest /var/www/html
```

> 
I need to chmod o+w to the upload subfolder
Since your document root is on your home folder, you should be able to write/edit/create any files inside it and any subfolder inside it. Do not chmod o+w to any folder. You will be compromising your security. You'll be allowing anyone to write on your apache folder if you do that.

---

### Post by monkeybrain20122 on 2015-06-13
I checked that the NameVirtualHost directive (first line in test.conf) is a feature of Apache2.2 but there is no mention of it in Apache2.4 which is the version in 15.04. [http://httpd.apache.org/docs/2.4/vhosts/name-based.html](http://httpd.apache.org/docs/2.4/vhosts/name-based.html)

After commenting out the NameVirtualHost line in test.conf and restarting Apache all browsers (Firefox, Opera and Chrome) connect to test.com but Chrome can no longer connect to localhost (standard apache2 greeting) by typing "localhost" in the url bar, but have to type in 127.0.0.1 to access that page. But for Firefox and Opera typing 'localhost' in the url bar still works. 

What happens?

In summary, my configuration now is as my first post except the first line was commented out

```
NameVirtualHost *:80
```

P.S. It seems that test.com has worked all along but [www.test.com]("http://www.test.com") gave 403 error, so the ServerAlias is not working.
P.P.S.  Apparently only the name that appears in hosts file works. e.g if I switch the entry in hosts file to [www.test.com]("http://www.test.com") then typing test.com in url would give 403 error but [www.test.com]("http://www.test.com") would connect. But should ServerAlias take  care of that?


p.p.p.s Sorry about this, it is getting ever more confusing.
now with ServerName [www.test.com](www.test.com) and ServerAlias test.com and hosts file set for [www.test.com](www.test.com) both url work in Firefox and Opera, except in Chrome where using the Alias (the one without www) gives 403 error, so it seems that only Chrome is not handling alias properly. But if ServerNAme is test.com (without www) and ServerAlias is [www.test.com](www.test.com) and hosts file set to test.com (without www) then all browsers gave 403 errors for  the Alias. ??? !!

---

### Post by bab1 on 2015-06-13
> **monkeybrain20122 said:**
> I checked that the NameVirtualHost directive (first line in test.conf) is a feature of Apache2.2 but there is no mention of it in Apache2.4 which is the version in 15.04. [http://httpd.apache.org/docs/2.4/vhosts/name-based.html](http://httpd.apache.org/docs/2.4/vhosts/name-based.html)

After commenting out the NameVirtualHost line in test.conf and restarting Apache all browsers (Firefox, Opera and Chrome) connect to test.com but Chrome can no longer connect to localhost (standard apache2 greeting) by typing "localhost" in the url bar, but have to type in 127.0.0.1 to access that page. But for Firefox and Opera typing 'localhost' in the url bar still works. 

What happens?

In summary, my configuration now is as my first post except the first line was commented out

```
NameVirtualHost *:80
```

P.S. It seems that test.com has worked all along but [www.test.com]("http://www.test.com") gave 403 error, so the ServerAlias is not working.
P.P.S.  Apparently only the name that appears in hosts file works. e.g if I switch the entry in hosts file to [www.test.com]("http://www.test.com") then typing test.com in url would give 403 error but [www.test.com]("http://www.test.com") would connect. But should ServerAlias take  care of that?


p.p.p.s Sorry about this, it is getting ever more confusing.
now with ServerName [www.test.com](www.test.com) and ServerAlias test.com and hosts file set for [www.test.com](www.test.com) both url work in Firefox and Opera, except in Chrome where using the Alias (the one without www) gives 403 error, so it seems that only Chrome is not handling alias properly. But if ServerNAme is test.com (without www) and ServerAlias is [www.test.com](www.test.com) and hosts file set to test.com (without www) then all browsers gave 403 errors for  the Alias. ??? !!
It's all so confusing... :-(

Post the complete content of virtual host conf file.  Have you modified any other Apache configuration files?  You should only need to create a .../sites-available/test.conf file and use a2ensite 

FYI Apachev2.2 uses different directives than Apache v2.4

It is also worth noting that you can have the DocumentRoot anywhere in the file system as long as you have world read for the entire path.  I keep my DocumentRoot data at /srv/share/www.  The directory ownership at the DocumentRoot is:  user:usergroup.  With directory permissions of 0775.  I've never had any problems with AppArmor using this setup.

---

### Post by bab1 on 2015-06-13
> **nerdtron said:**
> AppArmor, Ubuntu's version of SELinux. It basically strengthens security by limiting application access to their intended directories. In this case, apache is intended to access /var/www/html. If you point your document root to another directory, then you'll get "Access Forbidden" because apache is not allowed to access that directory. This can't be solved by making all files world readable.

This is not true at all.  The Apache user (www-data) only needs read access and does not need to own any of the files it reads.  So world readable (e.g o=w) is perfectly fine.  AppArmor shouldn't complain at all.


Edit:  I personally wouldn't put the DocumentRoot in my home directory however.

---

### Post by monkeybrain20122 on 2015-06-14
hi, bab1

Current virtualhost config
```

#NameVirtualHost *:
<VirtualHost *:80>
 ServerAdmin webmaster@webtest
 ServerName [www.test.com]("http://www.rwebtest.com")
 ServerAlias test.com
 DocumentRoot /home/monkeybrain/www/webtest

 <Directory /home/monkeybrain/www/webtest/>
  Options Indexes FollowSymLinks
  AllowOverride all
  Allow from all
  Require all granted
 </Directory>
  
 ErrorLog ${APACHE_LOG_DIR}/webtest/error.log
 CustomLog ${APACHE_LOG_DIR}/webtest/error.log combined
```

I have removed the NameVirtualHost directive from the first line since it apparently is not mentioned in Apache2.4's documentation so I think it
is no longer required (shown here as commented out for clarity).

I have also interchanged ServerName and ServerAlias so that ServerName now has www and ServeeAlias does not. I edited my hosts file accordingly

My /etc/hosts
```
127.0.0.1    localhost
127.0.1.1    monkeybrain-localhost
127.0.0.1    www.test.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

My questions:

1) Right now, Chrome, Firefox and Opera can all connect to [www.test.com]("http://www.test.com") in the url bar. But for Chrome typing in just test.com (without www) results in 

```
**Forbidden**

[COLOR=#000000][FONT=Times New Roman]You don't have permission to access / on this server.[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.[/FONT][/COLOR][HR][/HR]Apache/2.2.29 (Unix) mod_ssl/2.2.29 OpenSSL/1.0.1e-fips mod_bwlimited/1.4 Server at test.com Port 80



```

So does it mean that Chrome doesn't respect Alias?


2)Typing in localhost (default) in the URL bar for Opera and Firefox shows  the standard Apache2 greeting page, but typing localhost in Chrome  results in searching google, typing in 127.0.0.1 in Chrome's url bar  does bring up the apache2 greeting page.


3)I have a subfolder in /home/monkeybrain/Webtest which I have some test scripts. In Firefox I can type in the url bar either "www.test.com/scripts/testscript" or "test.com/scripts/testscript" to run the testscript but in Opera either "www.test.com/scripts/testscript" or "test.com" hit enter (so url entry becomes [www.test.com](www.test.com)), and then append "with /scripts/testscript" in url bar but typing in "test.com/scripts/testscript" does not work, it returns 404 not found. Why this discrepancy?

4) A reason I set the document root in my home is that I don't have to sudo to edit files and I don't want to change permissions in /var/www (since I don't know what it may entail, I have seen conflicting opinions all over the internet and I decide it is better not to mess with it) Is there any other way to achieve that?

5) I would like to have a subdirectory in webtest where  my test scripts can write to and upload images. How should I set my permission in such a way that doesn't compromise security? (I want to do it in a realistic fashion so that chmod 777 would not do)

Thanks.

---

### Post by bab1 on 2015-06-14
Hi @monkeybrain20122

I think you have a combination of problems with your setup. 
> ...  does it mean that Chrome doesn't respect Alias?
My feeling is that you have not set the aliases correctly.  
> ...but typing localhost in Chrome results in searching google

[scripts]does not work, it returns 404 not found. Why this discrepancy?
I think both or these are due to your misconfiguration.
> A reason I set the document root in my home is that I don't have to sudo to edit files and I don't want to change permissions in /var/www (since I don't know what it may entail, I have seen conflicting opinions all over the internet and I decide it is better not to mess with it) Is there any other way to achieve that?

How should I set my permission in such a way that doesn't compromise security?
I assume you mean having access to a directory outside of your home directory that you can access without using sudo.  This is very easy. 

Let's start with the last 2 questions and set up a directory for your virtual hosts outside of your home directory.  Some explanation first.  The apache user (www-data) only needs read permissions on all files and execute (descend/traverse rights) on all directories in the file system path to the files.  The user (you) needs read-write permissions on the files in the directory and execute (descend/traverse) rights on all directories.  I suggest that you use the /srv branch of the file system to test with,  I also suggest that you create a www directory below /srv so you can add additional virtual host doc roots as needed.  To do that we use this command (which will make all the directories in one command)```
sudo mkdir -p /srv/www/test
```
At this point you can read any file in the /srv/www/test file system but you can create or write to any file or directory.  To allow you read write (rw) permissions you need to first change the ownership to your username.  You can do this to allow rw permissions on /srv/www and below
```
sudo chown -R <user>:<group>:/srv/www
```...where <user> : <group> are your username and group.

Now you can set the permissions to 775 on the directories.  This will allow you to have rw permissions (no sudo needed) and all others have read only permissions.  Use this command to change the permissions (note that we are only changing permissions on the directories as there are no files yet)```
sudo chmod -R 775 /srv/www
```

At this point you can check that all is correct.  You should own the www and www/test directories below /srv and the permissions shoud be 776.  Post the output of these commands```
ls -l /srv

ls -l /srv/www
```...if all is well you should be able to create a file in /srv/www/test with this command```
touch /srv/www/test/test.txt
```

I suggest that you create a new virtual host site.  Since you already have a test.conf file I would use that.  Here is my test.conf file```

<VirtualHost *:80>
        ServerAdmin webmaster@test
        ServerName test
        ServerAlias www.test
        DocumentRoot [COLOR="#0000FF"]**/srv/www/test**[/COLOR]

[COLOR="#FF0000"] <Directory[/color][COLOR="#0000FF"] /srv/www/test[/COLOR][COLOR="#FF0000"]>
    Options FollowSymlinks
    AllowOverride none
    Require all granted
  </Directory>[/COLOR]

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```...note the parts in red and blue.  This is for Apache 2.4 not Apache 2.2.  Your apache2.2 directives are the cause of the permissions and 404 problems.  I always use the virtual-hostname only and a [www.virtual-hostname](www.virtual-hostname) when using a dev or test server. 

Remember to reload apache when you make any changes with this command```
# if using systemd
sudo systemctl restart apache2

# if using upstart
sudo service apache2 reload
```

Lastly we have the hostname settings in /etc/hosts.  If you are using a single machine then you can resolve all the virual-hostnames to 127.0.1.1 or somesuch.  If you have more then 1 machine and you want to dispaly the web pages on all hosts on the LAN then you need ot resolve the name to a NIC IP address that is attached to the LAN (i.e. eth0).  My host is named maui.  My host file looks like this```

127.0.0.1       localhost

192.168.1.6     maui www.maui test www.test webfaqs www.webfaqs # These are also virtual hosts on Apache2.4
```

---

### Post by monkeybrain20122 on 2015-06-14
Hi, Thanks for the detailed help. 

A couple of questions.
> 
Now you can set the permissions to 775 on the directories.  This will  allow you to have rw permissions (no sudo needed) and all others have  read only permissions.  Use this command to change the permissions (note  that we are only changing permissions on the directories as there are  no files yet)

The directories already have permission 755 so I already have rw permission as the owner after the chown command, so chmod 775 adds w permission to my group, can you please explain what the significance of that is, since I am the only member of my group.

The outputs of the ls -l commands are as follows:

```
ls -l /srv
total 4
drwxrwxr-x 3 monkeybrain monkeybrain 4096 Jun 14 18:57 www

```
```

ls -l /srv/www
total 4
drwxrwxr-x 5 monkeybrain monkeybrain 4096 Jun  9 17:02 test

```


  > Your apache2.2 directives are the cause of the permissions and 404 problems.  I always use the virtual-hostname only and a [www.virtual-hostname]("http://www.virtual-hostname") when using a dev or test server. 

The Apache2.2  declarative "NameVirtualHost *:80" was commented out. I keep this only to indicate edit history.
What is the difference between a hostname and a www hostname? Are they supposed to be interchangeable if ServerAlias is set?

In your vhost configure file 

```
[COLOR=#FF0000]<Directory[/COLOR][COLOR=#0000FF] /srv/www/test[/COLOR][COLOR=#FF0000]>
    Options FollowSymlinks
    AllowOverride none
    Require all granted
  </Directory[/COLOR]
```

Shouldn't there be a forward slash after test in the Directory directive? i.e <Directory /srv/www/test/> I don't know what difference does it make 
but on several tutorials I find online they made an emphasis that there is a forward slash, but without explaining why 
(as usual in that kind of cookbook tutorials)

---

### Post by monkeybrain20122 on 2015-06-14
Hi bab1, in order not to clutter my posts I will continue with some questions here.

After the changes above 1) and 3) in post #11 have been solved, but I think that is mainly just by adding both [www.test.com]("http://www.test.com") and test.com to /etc/hosts instead of just one and doesn't have to do with other changes 

instead of 
```
127.0.0.1    www.test.com
```

I now have
```
127.0.0.1    www.test.com test.com
```

I thought setting ServerAlias makes the names interchangeable but it seems that I still need to specify them separately in the hosts file.

2) still the same. In Chrome typing localhost in the url bar still get google search whereas in Opera and Firefox the apache2 greetings are displayed.

Some other questions:

**As indicated above I need to have a subfolder in www/test where I  can upload an image. Do I need to add www-data to my group so that it  has write permission? But then wouldn't it have write permission to my  home as well**?

I am still not quite sure why it is not a good idea to put webroot in /home. Can you explain what are the considerations?

---

### Post by volkswagner on 2015-06-14
Your /etc/hosts file is a substitution for DNS A records. This file allows your machine to know what ip address tranlates
from test.com domain name. The same way a DNS server can help resolve hostnames to ip addresses.

Your vhost file containing servername and/or serverAlias, just tells apache to associate the domain name with the directives in 
the same host file.

Simplistically, the vhost file is a listen directive, where the host file is a pointer or goto directive.


I hope this clears things up.

Theoretically, with the [www.test.com](www.test.com) and test.com entries in your hosts file... will still point to your servers ip (or loopback ip). If the domain
name did not exist in any vhost file, the default or catchall vhost file should serve it's content. This is why, 000-default.conf doesn't have
any hostname listed, as it will server any request not explicitly listed in another vhost file.

---

### Post by bab1 on 2015-06-14
> **monkeybrain20122 said:**
> Hi, Thanks for the detailed help. 

A couple of questions.


The directories already have permission 755 so I already have rw permission as the owner after the chown command, so chmod 775 adds w permission to my group, can you please explain what the significance of that is, since I am the only member of my group.

FYI: there are 3 types of users in Linux.  They are: the root user (uid=0), system users (typpically (uid= 1 to 500 or so (999 on Ubuntu) and mortal users (uid=1000 >).  The system users have no login and are not used by mortals.  Such users are for application processes.  www-data is such a user.

There is no practical different between 775 and 755 if you are the only mortal user on the system.   
> 

The outputs of the ls -l commands are as follows:

```
ls -l /srv
total 4
drwxrwxr-x 3 monkeybrain monkeybrain 4096 Jun 14 18:57 www

```
```

ls -l /srv/www
total 4
drwxrwxr-x 5 monkeybrain monkeybrain 4096 Jun  9 17:02 test

```

The Apache2.2  declarative "NameVirtualHost *:80" was commented out. I keep this only to indicate edit history.
What is the difference between a hostname and a www hostname? Are they supposed to be interchangeable if ServerAlias is set?

The hostname is the name of the host ( the machine running the OS).  A virtual-host is the name is an Apache construct that denotes a web site and may not have anything to do with the machines hostname.  The alias (what you called a "www hostname") is just as you said; it is an alias of the virtual hostname.
> 

I try and make my naming make sense without having to think about things too much.  The hostname may laptop (OS) is maui.  One of my vitualhosts is wwwfaqs and it's alias is [www.wwwfaqs](www.wwwfaqs).  If I was using a registered TLD (Top Level Domain) I would add that (e.g. wwwfaqs.org / [www.wwwfaqs.org](www.wwwfaqs.org))

In your vhost configure file 

```
[COLOR=#FF0000]<Directory[/COLOR][COLOR=#0000FF] /srv/www/test[/COLOR][COLOR=#FF0000]>
    Options FollowSymlinks
    AllowOverride none
    Require all granted
  </Directory[/COLOR]
```

Shouldn't there be a forward slash after test in the Directory directive? i.e <Directory /srv/www/test/> I don't know what difference does it make 
but on several tutorials I find online they made an emphasis that there is a forward slash, but without explaining why 
(as usual in that kind of cookbook tutorials)
The trailing / is used if there is any ambiguity in the name.  If you had a file named test in the directory /srv/www then you would have to use the trailing / to indicate the directory ( /srv/www/test = file and /srv/www/test/ = the directory) of course no one would actually have a situation as obvious as naming a file the same as a subdirectory the same; would they?  ;-)

---

### Post by bab1 on 2015-06-14
> **monkeybrain20122 said:**
> Hi bab1, in order not to clutter my posts I will continue with some questions here.

After the changes above 1) and 3) in post #11 have been solved, but I think that is mainly just by adding both [www.test.com]("http://www.test.com") and test.com to /etc/hosts instead of just one and doesn't have to do with other changes 

You should not add the http:// part.  That is a directive for the browser.  It is a hint to the browser that you are looking for a web page.  The hosts file is a DNS primitive.  It was there before there was DNS.  It is there to map hostnames (or virtual-hostnames (and aliases)) to the IP address.
> 

instead of 
```
127.0.0.1    www.test.com
```

I now have
```
127.0.0.1    www.test.com test.com
```

I thought setting ServerAlias makes the names interchangeable but it seems that I still need to specify them separately in the hosts file.

Although all 127.0.0.0/8 addresses refer to the loopback device I tend to separate the host, v-host and alias from the localhost like this
```
127.0.0.1 localhost
127.0.1.1 hostname v-host  v-host-alias    # You can add all the v-hosts and their aliases on the one line

``` 
> 

2) still the same. In Chrome typing localhost in the url bar still get google search whereas in Opera and Firefox the apache2 greetings are displayed.

My instance of Chrome does not do this.  I would try my host file mappings before anything else is said.  Also; browsers tend to cache previous requests.  I would try this in the "url bar": [http://localhost](http://localhost)
> 

Some other questions:

**As indicated above I need to have a subfolder in www/test where I  can upload an image. Do I need to add www-data to my group so that it  has write permission? But then wouldn't it have write permission to my  home as well**?

The user www-data is a system user and should never have write permissions to the doc root area.  The is a major security risk.  You will have the site hacked within minutes in a pubic facing Apache web server.  If you have active content you need to set up a separate area (a CGI directory).  This is an ongoing debate with Joomla! and Druple users.

If you have data that needs to be uploaded to the doc root use a ssh/sftp or ftps (vsftp) method not a web based method that Involves the Apache user (www-data).

If you have multiple mortal users that need to access the doc root you should create a separate user-group.  I create *www-content* or you can use the user-group *users*.  Then you have to set the group ownership and inheritance of the /srv/www/test directory to something like this root:www-content.  No one user owns the directory.  With the group permissions set to 7 (as in 775) the users have rw access to all of the doc root.  You could use different group names if you have different users connected to each virtual-host (i.e. www-test as a user group).
> 

I am still not quite sure why it is not a good idea to put webroot in /home. Can you explain what are the considerations?
Re-read the paragraphs above again.  If you use your home directory and also allow the Apache user to have write access you will most certainly be hacked if the web server is user on the public Internet.  Best practices start with development servers.  From the very beginning you should user security correct methods.

---

### Post by monkeybrain20122 on 2015-06-14
> **bab1 said:**
> 

My instance of Chrome does not do this.  I would try my host file mappings before anything else is said.  Also; browsers tend to cache previous requests.  I would try this in the "url bar": [http://localhost](http://localhost)
Typing http:// in front of localhost does bring up the apache2 greetings in Chrome.

> The user www-data is a system user and should never have write permissions to the doc root area.  The is a major security risk.  You will have the site hacked within minutes in a pubic facing Apache web server.  If you have active content you need to set up a separate area (a CGI directory).  This is an ongoing debate with Joomla! and Druple users.


I know that. But can I create a separate upload folder inside  /srv/www/test, say /srv/www/test/uploads and give www-data write access to only that folder? i.e retaining same ownership but allow w for others on only that folder. In my test this is actually a kind of temp folder, I need to invoke a script to output a graph and show it on the browser and the image will be deleted afterwards so the folder is empty if except when the the script is called. Or is it possible to create it outside the webroot and give www-data write access? Or better, can I allow apache to write to /tmp?


> If you have multiple mortal users that need to access the doc root you should create a separate user-group.  I create *www-content* or you can use the user-group *users*.  Then you have to set the group ownership and inheritance of the /srv/www/test directory to something like this root:www-content.  No one user owns the directory.  With the group permissions set to 7 (as in 775) the users have rw access to all of the doc root.  You could use different group names if you have different users connected to each virtual-host (i.e. www-test as a user group).

and add www-data to www-content? Otherwise it still has the problem or apache not being able to write to folder.

> Re-read the paragraphs above again.  If you use your home directory and also allow the Apache user to have write access you will most certainly be hacked if the web server is user on the public Internet.  Best practices start with development servers.  From the very beginning you should user security correct methods.


But if the permission is exactly the same  as what you did  in /srv (755 or 775)  why would it be hacked but putting the webroot in /srv would not?

Thanks again for the patient explanation.

---

### Post by monkeybrain20122 on 2015-06-14
Sorry for multiple edits, somehow UF is glitchy and I keep seeing the wheel spinning when try to update post.

---

### Post by bab1 on 2015-06-14
> **monkeybrain20122 said:**
> 
I know that. But can I create a separate upload folder inside  /srv/www/test, say /srv/www/test/uploads and give www-data write access to only that folder? i.e retaining same ownership but allow w for others on only that folder. In my test this is actually a kind of temp folder, I need to invoke a script to output a graph and show it on the browser and the image will be deleted afterwards so the folder is empty if except when the the script is called. Or is it possible to create it outside the webroot and give www-data write access? Or better, can I allow apache to write to /tmp?

The idea is for you, as the system admin to limit the damage that can happen.  I would suggest reading all you can about **Apache 2.4 dynamic content security**.
> 
and add www-data to www-content? Otherwise it still has the problem or apache not being able to write to folder.

No you do not ad www-data to the www-content group.  Only users that can login should be allowed rw permissions inside the doc root.  You will have to learn how to use cgi and php scirpts safely.  This is part of Apache 2.4 Dynamic Content Security.
> 

But if the permission is exactly the same  as what you did  in /srv (755 or 775)  why would it be hacked but putting the webroot in /srv would not?

If the webroot is not in the /home directory then personal data is not hacked.

---

### Post by monkeybrain20122 on 2015-06-14
so how about /tmp, can www-data write to /tmp?

---

### Post by bab1 on 2015-06-15
Yes system users such as www-data can write to /tmp.  In fact all users have rw permissions to /tmp.  It is not the place to normally do what you want to do but it should work for your non-public facing Apache server.

Once again if you want the server to be secure properly read the documentation for Apache and others.

---

