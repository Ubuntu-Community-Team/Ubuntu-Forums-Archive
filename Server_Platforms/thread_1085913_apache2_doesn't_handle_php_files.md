---
title: "apache2 doesn't handle php files"
date: 2009-03-03
forum: Server Platforms
---

### Post by M03BIUS on 2009-03-03
Hello, I am having problems with apache2, php5 phpmyadmin

Firefox asks me to download .php or phtml files and doesn't view them...
other browsers can't handle the .php files...

When I first installed LAMP it worked fine... but then I installed drupal5 and it screwed up everything.( or I did ) ... could someone please help...

How do I completely remove everything:

apache2
mySQL
phpmyadmin (broken) I can't remove it I get a error.

and I mean completely... every trace of the files.

I think I might just nuke Ubuntu and reformat...

---

### Post by cdenley on 2009-03-03
```

sudo apt-get --purge remove ^libapache.* ^apache.* ^mysql-server.* phpmyadmin

```

---

### Post by Caesonia on 2009-03-03
> **cdenley said:**
> ```

sudo apt-get --purge remove ^libapache.* ^apache.* ^mysql-server.* phpmyadmin

```

Hope it works. Just had the same bloody thing happen on 8:10 for me. Love the stuff, ut then these silly things come up. Come ON lads and lasses, we can only kill the MS domination by limiting these sort of emergency tweaks....

---

### Post by M03BIUS on 2009-03-03
Yes, it worked but now when I reinstall apache2 I get this.... not sure what to do at this point as I am new to this... but when I go to my browser and do localhost... it says "It works!"

```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by cdenley on 2009-03-04
> **M03BIUS said:**
> Yes, it worked but now when I reinstall apache2 I get this.... not sure what to do at this point as I am new to this... but when I go to my browser and do localhost... it says "It works!"

```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```

It looks like you have two instances of apache running. You probably did not stop it correctly.
```

sudo /etc/init.d/apache2 stop
sudo killall apache2
sudo lsof -n -i :80
sudo /etc/init.d/apache2 start

```

---

### Post by Caesonia on 2009-03-04
> **cdenley said:**
> It looks like you have two instances of apache running. You probably did not stop it correctly.
```

sudo /etc/init.d/apache2 stop
sudo killall apache2
sudo lsof -n -i :80
sudo /etc/init.d/apache2 start

```

Actually, if you have a ny ideas....

Doing the purge didn't help. It uninstalled a lot, and still php files aren't handled. Firefox keeps asking what to do with them. I also got responses saying that php5 didn't5 exist on my system. However, if I try and install it, it says it can't find any packages, and adds nothing.

I accept I am relatively new at Linux, but I have successfully gotten apache2 up and running on Ubuntu 8.04LTD with little trouble. Never had this oddity before. 

So, where do I go from here?

---

### Post by cdenley on 2009-03-04
> **Caesonia said:**
> I also got responses saying that php5 didn't5 exist on my system. However, if I try and install it, it says it can't find any packages, and adds nothing.

Responses from what? What packages? What commands are you running and what is the output?
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by M03BIUS on 2009-03-04
> **cdenley said:**
> It looks like you have two instances of apache running. You probably did not stop it correctly.
```

sudo /etc/init.d/apache2 stop
sudo killall apache2
sudo lsof -n -i :80
sudo /etc/init.d/apache2 start

```


Well I tried what you said and now I get this.... still doesn't work.

```

myuser@mydomain:~$ sudo /etc/init.d/apache2 stop
[sudo] password for myuser: 
 * Stopping web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
myuser@mydomain :~$ sudo killall apache2
apache2: no process killed
mmyuser@mydomain:~$ sudo lsof -n -i :80
COMMAND   PID     USER   FD   TYPE DEVICE SIZE NODE NAME
lighttpd 5928 www-data    4u  IPv6  17237       TCP *:www (LISTEN)
firefox  6544  myuser   52u  IPv4  21738       TCP 192.168.1.100:59210->91.189.94.9:www (ESTABLISHED)
firefox  6544  myuser   59u  IPv4  21765       TCP 192.168.1.100:59219->91.189.94.9:www (ESTABLISHED)
myuser@mydomain:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by cdenley on 2009-03-04
That's because you already have a web server running.
> 
lighttpd 5928 www-data    4u  IPv6  17237       TCP *:www (LISTEN)

You can only have one server listening on port 80. Either choose between lighttpd and apache, or configure one to listen on a port other than 80.

---

### Post by M03BIUS on 2009-03-04
> **cdenley said:**
> That's because you already have a web server running.

You can only have one server listening on port 80. Either choose between lighttpd and apache, or configure one to listen on a port other than 80.

Ok I understand that now... I don't even know how lighttpd got installed...but I get this error still... sorry I am a noob to this.

```

 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by cdenley on 2009-03-04
```

sudo apt-get remove lighttpd
sudo /etc/init.d/apache2 restart

```

---

### Post by M03BIUS on 2009-03-05
I restart apache2 and it still won't start up... I don't know what's wrong... I've done everything I could think of including what you people have said to do.  I guess I am going to switch to Gentoo and so goodbye to Ubuntu... there are just too many bugs with 8.10.

---

### Post by cdenley on 2009-03-05
> **M03BIUS said:**
> I restart apache2 and it still won't start up... I don't know what's wrong... I've done everything I could think of including what you people have said to do.  I guess I am going to switch to Gentoo and so goodbye to Ubuntu... there are just too many bugs with 8.10.

A user error is not a bug. I already told you the problem was because you have another server running on port 80. Gentoo can't run two servers on port 80 either.

---

### Post by M03BIUS on 2009-03-05
> **cdenley said:**
> A user error is not a bug. I already told you the problem was because you have another server running on port 80. Gentoo can't run two servers on port 80 either.


Yes.... I know, and I did what you said and I know you can't have Two servers running on port 80.  I uninstalled lighttpd  and and did that other command that tells you if you have any servers running... and no there isn't. Still the server won't start. If you would have read the post before that I explained what error it was after uninstalling lighttpd.

This error: 
```

 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

``` 
I have no other servers trying to us port 80 at least I I don't see any. It just won't start. 

Yes, I am a noob at this, I understand that you arrogantly think I am a dumbass. I do realize that a "user" error is "not a bug". I would appreciate it if you would refrain from saying such things.  I am glad your willing to supply me with help but to state that "A user error is not a bug" where you really mean to say is "Your a dumbass" kinda makes me angry :) .  

But anyway, now this thread will probably be deleted because of all this... but still... I am left with no other option because "A user error is not a bug" to reformat my drive and install Ubuntu over again because something happened to my dependencies.  Thanks for your help and yes I am not having a good day and yes I am a dumbass.

---

### Post by cdenley on 2009-03-05
If you have no servers listening on port 80, then I wouldn't expect you to get an error indicating you already have a server listening on port 80. You must have missed a step, and haven't posted any output to suggest otherwise.
```

sudo lsof -n -i :80
sudo /etc/init.d/apache2 restart

```

---

### Post by M03BIUS on 2009-03-05
> **cdenley said:**
> If you have no servers listening on port 80, then I wouldn't expect you to get an error indicating you already have a server listening on port 80. You must have missed a step, and haven't posted any output to suggest otherwise.
```

sudo lsof -n -i :80
sudo /etc/init.d/apache2 restart

```

This the result of the sudo lsof -n -i :80 command:
```

myuser@mydomain:~$ sudo lsof -n -i :80
[sudo] password for myuser: 
COMMAND  PID   USER   FD   TYPE DEVICE SIZE NODE NAME
firefox 6486 myuser   67u  IPv4  67762       TCP 192.168.1.100:52063->96.17.74.152:www (ESTABLISHED)

```

and this is the result of the sude /etc/init.d/apache2 restart command:
```

myuser@mydomain:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Mar 05 15:38:58 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Mar 05 15:38:58 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
myuser@mydomain:~$ 

```

I think I mentioned before...everything was working fine until I installed drupal5.  I think it might have overwritten a file or two or configs but I am lost.  I know I must be missing something simple... I just don't have enough experience with apache on linux.

---

### Post by cdenley on 2009-03-05
You must have a line like this TWICE in your apache configuration files.
```

Listen 127.0.0.1:80

```
This command might indicate where.
```

grep Listen /etc/apache2/*.conf /etc/apache2/sites-enabled/* /etc/apache2/mods-enabled/*

```
Only way I could think of that you can have the output you posted.

---

### Post by M03BIUS on 2009-03-05
> **cdenley said:**
> You must have a line like this TWICE in your apache configuration files.
```

Listen 127.0.0.1:80

```
This command might indicate where.
```

grep Listen /etc/apache2/*.conf /etc/apache2/sites-enabled/* /etc/apache2/mods-enabled/*

```
Only way I could think of that you can have the output you posted.

This is the result of the grep Listen /etc/apache2/*.conf /etc/apache2/sites-enabled/* /etc/apache2/mods-enabled/* command:

```

myuser@mydomain:~$ grep Listen /etc/apache2/*.conf /etc/apache2/sites-enabled/* /etc/apache2/mods-enabled/*
/etc/apache2/ports.conf:Listen 80
/etc/apache2/ports.conf:    Listen 443
/etc/apache2/sites-enabled/ports.conf:Listen 127.0.0.1:80
myuser@mydomain:~$ 

```

---

### Post by cdenley on 2009-03-05
This file probably shouldn't be there:
/etc/apache2/sites-enabled/ports.conf
```

cat /etc/apache2/sites-enabled/ports.conf
mkdir ~/backup
mv /etc/apache2/sites-enabled/ports.conf ~/backup
sudo /etc/init.d/apache2 restart

```

---

### Post by M03BIUS on 2009-03-05
> **cdenley said:**
> This file probably shouldn't be there:
/etc/apache2/sites-enabled/ports.conf
```

cat /etc/apache2/sites-enabled/ports.conf
mkdir ~/backup
mv /etc/apache2/sites-enabled/ports.conf ~/backup
sudo /etc/init.d/apache2 restart

```

Well that time it started and didn't fail but it still says this:
```

* Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Mar 05 16:20:53 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Mar 05 16:20:53 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [ OK ]

```

---

### Post by cdenley on 2009-03-05
That's typical and harmless. If you really want it to go away, add an entry in your /etc/hosts file for your FQDN, edit /etc/hostname to use your FQDN, then run
```

sudo hostname myfqdn.com

```
replacing "myfqdn.com" with your actual FQDN.
[http://en.wikipedia.org/wiki/FQDN](http://en.wikipedia.org/wiki/FQDN)

---

### Post by M03BIUS on 2009-03-05
> **cdenley said:**
> That's typical and harmless. If you really want it to go away, add an entry in your /etc/hosts file for your FQDN, edit /etc/hostname to use your FQDN, then run
```

sudo hostname myfqdn.com

```
replacing "myfqdn.com" with your actual FQDN.
[http://en.wikipedia.org/wiki/FQDN](http://en.wikipedia.org/wiki/FQDN)

ok cool, thanks!  But do you know why my Firefox, IE, Safari ask me to download php files?  I made a website that uses php but I can't view it. It does the same thing in Windows... asks me to download the php files and PHTML.

---

### Post by kanikilu on 2009-03-05
Sorry to jump in here, but I had the same problem you did (although it was on a new install, not after installing something like drupal). Anyways, I can't remember exactly what fixed it, but I recall:

- checking to make sure my php scripts were executable

- clearing my browser cache (probably didn't help anything there, but...)

- checking to make sure the PHP module is indeed loaded, you can do that by using **apache2ctl -t -D DUMP_MODULES** and look for **php5_module** in the output

---

### Post by cdenley on 2009-03-05
> **M03BIUS said:**
> ok cool, thanks!  But do you know why my Firefox, IE, Safari ask me to download php files?  I made a website that uses php but I can't view it. It does the same thing in Windows... asks me to download the php files and PHTML.

```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by M03BIUS on 2009-03-05
ok cool, I did what both of you said and I now have php5 loaded.  But the problem I am having now is... inside my /var/www directory where my .html and .php files are.. they still won't show up. I get a 404 Not Found error.

---

### Post by M03BIUS on 2009-03-05
Ok fixed my problem I had to do the following:

sudo nano /etc/apache2/apache2.conf

and I have to add the following into my conf file:

# DocumentRoot: The directory out of which you will serve your
# documents. By default, all requests are taken from this directory, but
# symbolic links and aliases may be used to point to other locations.
#
DocumentRoot "/var/www"

once I did that I did a apache2 restart:

sudo /etc/init.d/apache2 restart

and now my .php pages my /var/www root directory works and everything works fine.  Thank you for your help everyone!

---

### Post by Caesonia on 2009-03-06
> **cdenley said:**
> Responses from what? What packages? What commands are you running and what is the output?
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

 sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libapache2-mod-php5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-php5 has no installation candidate
caesonia@Athena:~$ sudo a2enmod php5
ERROR: Module php5 does not exist!
caesonia@Athena:~$ 

This is the sort of thing.

Now, I do have the php5 directory under /etc/php5 with a php.ini inside, but its for some reason been placed in the cgi directory.

I have never seen that before. Usually its floating directly in the /etc directory, especially in RHEL and CentOS.

Anyways, I have done several straightforward Ubtunu installations starting with Heron, and its all gone quite smoothly.

Now suddenly I cant seem to get it going. You see the output above.

---

### Post by neilevan814 on 2009-03-07
"
That's typical and harmless. If you really want it to go away, add an entry in your /etc/hosts file for your FQDN, edit /etc/hostname to use your FQDN, then run
Code:

sudo hostname myfqdn.com"




I would like that message to go away when I reload apache2.  What would my FQDN actually be if my DN is webwork.thruhere.net what exactly would I add to fully qualify?

---

### Post by Caesonia on 2009-03-11
> **neilevan814 said:**
> "
That's typical and harmless. If you really want it to go away, add an entry in your /etc/hosts file for your FQDN, edit /etc/hostname to use your FQDN, then run
Code:

sudo hostname myfqdn.com"




I would like that message to go away when I reload apache2.  What would my FQDN actually be if my DN is webwork.thruhere.net what exactly would I add to fully qualify?

I am not worried about. I am worried about the fact that running 8:10, I can't seem to get php files served on my server. I've never hada problem installing it on other Ubuntu's. though I am a newer user, so I can't understand what's mucked it.

---

### Post by cdenley on 2009-03-11
> **Caesonia said:**
> 
Package libapache2-mod-php5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-php5 has no installation candidate


It looks like there is a repo branch you need but have disabled, because it can't find the package. Post this output
```

cat /etc/apt/sources.list

```
Or if you have a GUI:
System>Administration>Software Sources

---

### Post by cdenley on 2009-03-11
> **neilevan814 said:**
> I would like that message to go away when I reload apache2.  What would my FQDN actually be if my DN is webwork.thruhere.net what exactly would I add to fully qualify?

As explained in the link I provided, webwork.thruhere.net is a fully qualified domain name.

---

### Post by neilevan814 on 2009-03-11
Thanks cdenley, I will then try adding my fqdn to my /etc/hostname file and give that a go.

---

