---
title: "I Really Screwed Up My Apache"
date: 2012-04-01
forum: Server Platforms
---

### Post by theopfor on 2012-04-01
I'm using regular Ubuntu 11.10, not the server version. I use Ubuntu as my main OS, and I like to play around with web languages, so I installed Apache, PHP5, MySQL, and phpMyAdmin. Later, for some reason, I uninstalled it all. I had it all working fine. I reinstalled it a few days ago, but now I am having issues.

I installed Apache through Terminal, and the source (which I think makes a difference), screwed up httpd.conf, can't determine where the website files go, and I tried uninstalling it, but I had no success. 

How do I completely uninstall PHP5, MySQL, phpMyAdmin, and Apache? How do I properly reinstall these so that the website files will be located in /home/theopfor/public_html/?

This was the most relevant forum topic I could find for this. Anything helps.

---

### Post by CharlesA on 2012-04-01
By default, the document root is pointing to /var/www

Change the document root:
[http://www.ajopaul.com/2010/05/01/ubuntu-apache2-change-default-documentroot-varwww/](http://www.ajopaul.com/2010/05/01/ubuntu-apache2-change-default-documentroot-varwww/)

By default the httpd.conf file is empty.

---

### Post by theopfor on 2012-04-01
> To do this, we must create a new site and then enable it in Apache2.   
 To create a  new site:  
 Copy the default  website as a starting point. sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 
cp: cannot stat `/etc/apache2/sites-available/default': No such file or directory

There is no apache2 folder in my /etc, and I haven't been able to find it. That is why I think I need Apache to be reinstalled.

---

### Post by CharlesA on 2012-04-01
Install apache then:

```
sudo apt-get install apache2 php5
```

---

### Post by theopfor on 2012-04-01
I get the same error about the missing directory.

---

### Post by CharlesA on 2012-04-01
Hrm.

Try this:

```
ls -ld /etc/apache2
```

---

### Post by theopfor on 2012-04-01
I got another error.

> ls: cannot access /etc/apache2: No such file or directory

---

### Post by CharlesA on 2012-04-01
What did apt-get say when you tried to install apache?

---

### Post by theopfor on 2012-04-01
> theopfor@ubuntu:~$ sudo apt-get install apache2 php5
[sudo] password for theopfor:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
php5 is already the newest version.
The following package was automatically installed and is no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


That's all Terminal said.

---

### Post by CharlesA on 2012-04-01
Ok. Try running this then:

```
sudo apt-get install apache2 php5 --reinstall
```

---

### Post by theopfor on 2012-04-01
> theopfor@ubuntu:~$ sudo apt-get install apache2 php5 --reinstall
[sudo] password for theopfor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/2,592 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 363471 files and directories currently installed.)
Preparing to replace apache2 2.2.20-1ubuntu1.2 (using .../apache2_2.2.20-1ubuntu1.2_i386.deb) ...
Unpacking replacement apache2 ...
Preparing to replace php5 5.3.6-13ubuntu3.6 (using .../php5_5.3.6-13ubuntu3.6_all.deb) ...
Unpacking replacement php5 ...
Setting up apache2 (2.2.20-1ubuntu1.2) ...
Setting up php5 (5.3.6-13ubuntu3.6) ...


No apache2 folder in /etc.

---

### Post by CharlesA on 2012-04-01
It looks like it reinstalled it fine.

Try this:

```
sudo updatedb
locate apache2
```

---

### Post by theopfor on 2012-04-01
A lot of output. updatedb succeeded, but I don't know what that does...

locate returned things mainly from /usr/local/apache2, /usr/sbin/apache2, /usr/share/apache2, /var/cache/apache2, /var/lib/dpkg/info/, and /var/log/apache2.

---

### Post by CharlesA on 2012-04-01
Huh.

I have stuff in /etc/apache2, /usr/lib/apache2, /usr/share/apache2, and /var/log/apache2.

How did you install apache originally? Does this do anything?

```
sudo service apache2 start
```

EDIT: updatedb just updates the database of the file system, so you can search it. ;)

---

### Post by theopfor on 2012-04-01
First I installed it from the source, and it worked fine. Then I uninstalled it somehow, for some odd reason. Trying to get it to work about a week ago, I installed, and uninstalled various times through the Software Center, and through the source.

Like I said, I really screwed it up.

---

### Post by CharlesA on 2012-04-01
Well, that would explain why it is in /usr/local.

Does it do anything if you do this:

```
sudo apt-get purge apache2 php5
```

---

### Post by theopfor on 2012-04-01
> theopfor@ubuntu:~$ sudo apt-get purge apache2 php5
[sudo] password for theopfor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2* php5*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 57.3 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 363469 files and directories currently installed.)
Removing apache2 ...
Removing php5 ...
theopfor@ubuntu:~$ 


/usr/local/apache2 is still there.

---

### Post by CharlesA on 2012-04-01
Is it empty?

---

### Post by theopfor on 2012-04-01
Nope.

---

### Post by CharlesA on 2012-04-01
You should be able to uninstall it even if you compiled it from source by running make uninstall from the directory you compiled it from.

---

### Post by theopfor on 2012-04-01
"make uninstall" tells me

> theopfor@ubuntu:~/Downloads/httpd-2.2.22$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.


Or do you mean something else?

---

### Post by CharlesA on 2012-04-01
That was it.

Is the apache service running?

```
netstat -nl | grep 80
```

---

### Post by theopfor on 2012-04-01
> unix  2      [ ACC ]     STREAM     LISTENING     10805    @/tmp/dbus-DqxfIKy7CO
unix  2      [ ACC ]     STREAM     LISTENING     8079     /var/run/mysqld/mysqld.sock


I don't think apache is in there, but it does look like MySQL is.

---

### Post by CharlesA on 2012-04-01
Ok. Try installing apache again and see what happens.

---

### Post by theopfor on 2012-04-01
Apache installed, and when I try to start it with sudo service apache2 start, I get an error.

> theopfor@ubuntu:~$ sudo service apache2 start
.: 51: Can't open /etc/apache2/envvars


---

### Post by CharlesA on 2012-04-01
Well, the service appears to be there, but the apache2 folder is missing. Maybe try reinstalling it (again):

```
sudo apt-get install apache2 -reinstall
```

---

### Post by theopfor on 2012-04-01
Same error.

---

### Post by CharlesA on 2012-04-01
Back up your stuff and reinstall. That is probably the best thing to do now.

---

### Post by theopfor on 2012-04-01
I can't do that, sorry. But when the next version of Ubuntu comes out (next month I think), then would I be able to install Apache without this weird error thing?

---

### Post by CharlesA on 2012-04-01
I doubt it. Something is totally messed up with the OS, if even reinstalling apache doesn't create the apache2 folder.

---

### Post by theopfor on 2012-04-01
Could it be something to do with me following the PHP guide for setting it up with Apache and setting prefix to the default location when building Apache from the source?

---

### Post by CharlesA on 2012-04-01
I have no idea. I've only installed apache from the repos via apt-get.

---

### Post by theopfor on 2012-04-01
Darn. Oh well, thanks!

---

### Post by Dangertux on 2012-04-01
Have you tried

```


sudo /etc/init.d/httpd start


```

If you installed from source, everything defaults to httpd, not apache2 (that's a Ubuntu repo thing)

Let me know if that works.

---

### Post by SeijiSensei on 2012-04-02
Try running "locate httpd.conf" and "locate apache2.conf".  What directories are those files stored in?

If apache is running, what do you see when you run "ps ax | grep httpd"?  How about "ps ax | grep apache2"?

---

### Post by theopfor on 2012-04-02
That didn't work Dangertux.

/usr/local/apache2/conf/httpd.conf
/usr/local/apache2/conf/original/httpd.conf
/var/tmp/httpd.conf.swp

and 

/usr/share/doc/apache2.2-common/examples/apache2/apache2.conf.gz

Are what the locates returned, SeijiSensei.

3344 pts/0    S+     0:00 grep --color=auto httpd

and

 3346 pts/0    S+     0:00 grep --color=auto apache2

are what appeared with the ps ax stuff.

---

### Post by SeijiSensei on 2012-04-03
Apache isn't running, then.  On Ubuntu, "ps ax" should display half-a-dozen entries with "/usr/sbin/apache2 -k start" in them.

The locations under /usr/local indicate that the only copy of Apache on your server is the one you built from source.  

Are you sure you installed a version from the repositories with apt-get?  There's no evidence for this.  I see only the traces of the version you built.

---

### Post by theopfor on 2012-04-03
I uninstalled the one from apt-get, so no, it's not on my system.

---

