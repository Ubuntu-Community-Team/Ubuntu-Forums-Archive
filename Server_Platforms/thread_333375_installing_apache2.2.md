---
title: "installing apache2.2"
date: 2007-01-07
forum: Server Platforms
---

### Post by deRusett on 2007-01-07
Hello,  New to the forms,  and new kinda new to linux, having played with it on and off mainly with Mandriva, and SUSE for 3 years or so.

I am attempting to set up a LAMP server. using  Xubuntu 6.10  since I didn't think I was ready to go all command line I wanted a light GUI.  my Problem is  apt-get only seems to have apache 2.0.55  and I would like to install apache2.2.3  

I go about downloading it, httpd-2.2.3.tar.bz2  which downloads to my desktop with firefox,  

What would the best course of action be here?   where do I untar this too?  and how do I go about doing that.


I have read [http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu](http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu)  figuring this would be easy,  but I'm not sure about file structure yet,  best place to install things to and such,  having been a Windows user I used to install Apache to  C:\Apache2 and php to C:\php  but I am sure that is not how it is done in Linux.

any advice would be great,  thank you.


EDIT

Ok so I have downloaded  apache 2.2.3 and unpacked it

```

 $ wget -c http://apache.mirrors....httpd-2.2.3.tar.gz
  $ tar -xvf httpd-2.2.3.tar.gz 

  $ cd httpd-2.2.3

```

but now when I attempt to
```

./configure --prefix=/usr/local/apache2

```

I get  
configure: error: expected an absolute directory name for prefix: usr/local/apache2

and now I am stuck again.

---

### Post by Brazen on 2007-01-07
Is there any reason you need 2.2 instead of 2.0?  If there are not any specific features you need from 2.2, then you would be better off just using 2.0 from the repo.

Otherwise, generally you just extract the downloaded files, open a command line, change to the directory of the extracted files and run these three commands:

sudo configure
sudo make
sudo make install

If you want a more "automated" install, try finding a deb package for 2.2.

---

### Post by Koybe on 2007-01-07
Do you really need apache 2.2? Because installing without package will make installation and maintaining of your server a lot harder.

Anyway if you want to make it from source you'll need to compile. So get build essentials :

```
apt-get install build-essential
```and then untar your file and compile apache.
```
tar -jxvf httpd-2.2.3.tar.bz2
cd httpd-2.2.3
./configure
make
sudo make install
```

---

### Post by deRusett on 2007-01-07
My Windows Server that this will be replacing is apache 2.2.3,  so I'd like to remain with apache 2.2.3   

though if this is going to prove troubling,  I think only the php mysql and tomcat installs the version matters for,

---

### Post by deRusett on 2007-01-07
> **Brazen said:**
> Is there any reason you need 2.2 instead of 2.0?  If there are not any specific features you need from 2.2, then you would be better off just using 2.0 from the repo.

Otherwise, generally you just extract the downloaded files, open a command line, change to the directory of the extracted files and run these three commands:

sudo configure
sudo make
sudo make install

If you want a more "automated" install, try finding a deb package for 2.2.

sudo configure:command not found

---

### Post by deRusett on 2007-01-07
Koybe

thanks  I needed that apt-get install build-essential



so apache2 seems to be installed,  but when I try

/usr/local/apache2/bin/apachectl -k start

I get
```

httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for servername
(13)Permission denied: make_sock: could not bind to address [::] :80
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
$

```


what am I missing

as a side note  mousepad wont let me write to the httpd.conf  file

---

### Post by gaebriel on 2007-01-07
1. You need to be root to bind to ports lower than 1024 so start apache with sudo: 
```
sudo /usr/local/apache2/bin/apachectl -k start
```

2. update the 'ServerName' directive in /usr/local/apache2/conf/httpd.conf to the name of your local box, and update your /etc/hosts file to make sure you have the same name and correct IP. 

3. You'll also need to make sure the 'User' and 'Group' directives in the httpd.conf file have users that exist on the system and the directory permissions for the log directories allow write access for those users. 

HTH

---

### Post by kebes on 2007-01-07
As gaebriel said the issue here is that you need to run those commands as root, so do:

sudo /usr/local/apache2/bin/apachectl -k start

Note, however, that in a typical install of apache using apt-get, you would do "sudo /etc/init.d/apache2 start" to bring up the server... do you have an "apache2" service listed in "/etc/init.d/" ?
ls /etc/init.d/apache*


Similarly, the httpd.conf is probably owned by root (which it should be), so to edit it you have to go:
sudo nano /etc/apache2/httpd.conf
or
gtksudo mousepad /etc/apache2/httpd.conf

---

### Post by mohdridha on 2007-01-23
> **gaebriel said:**
> update the 'ServerName' directive in /usr/local/apache2/conf/httpd.conf to the name of your local box, and update your /etc/hosts file to make sure you have the same name and correct IP. 

3. You'll also need to make sure the 'User' and 'Group' directives in the httpd.conf file have users that exist on the system and the directory permissions for the log directories allow write access for those users. 

HTH

can you be a little bit detail?
what is local box? is it the name of my machine on network?

update /etc/hosts to have the same name and correct IP
same name with?

Thanks

---

