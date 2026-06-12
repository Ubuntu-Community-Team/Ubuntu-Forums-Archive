---
title: "webmin install"
date: 2010-02-17
forum: Server Platforms
---

### Post by rdema19403 on 2010-02-17
i am trying to install webmin on my server(9.10) by command line 
what is the command to see if it is installed or not

---

### Post by pirateghost on 2010-02-17
browse to it from another computer on the network?

[https://ipaddressofserver:10000](https://ipaddressofserver:10000)

---

### Post by rdema19403 on 2010-02-17
that is not working this is the response i get from fire fox Firefox can't establish a connection to the server at 192.168.1.104:10000.
Iam able to ping the ip address or if i typpe the ip address it says  it works
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

---

### Post by lisati on 2010-02-17
You might need to use https instead of http in your browser.

---

### Post by pirateghost on 2010-02-17
webmin runs its own 'webserver' so apache running means nothing.

how did you install it?

did you add the repos and install it via apt-get install webmin or did you install all the dependencies and use dpkg -i webmin.deb ?

---

### Post by rdema19403 on 2010-02-17
i used this command apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
then i tried dpkg --install webmin_1.500_all.deb
this is what i get from the terminal 
root@test:/home/test19403# apt-get install webmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webmin has no installation candidate
root@test:/home/test19403# apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
Reading package lists... Done
Building dependency tree        
Reading state information... Done
perl is already the newest version.
libnet-ssleay-perl is already the newest version.
openssl is already the newest version.
libauthen-pam-perl is already the newest version.
libpam-runtime is already the newest version.
libio-pty-perl is already the newest version.
libmd5-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by CharlesA on 2010-02-17
you can always run dpkg -l to get a list of installed packages.

Did you already download the deb and install it using dpkg -i?

---

### Post by pirateghost on 2010-02-17
> **rdema19403 said:**
> i used this command apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
then i tried dpkg --install webmin_1.500_all.deb
this is what i get from the terminal 
root@test:/home/test19403# apt-get install webmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webmin has no installation candidate
root@test:/home/test19403# apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
Reading package lists... Done
Building dependency tree        
Reading state information... Done
perl is already the newest version.
libnet-ssleay-perl is already the newest version.
openssl is already the newest version.
libauthen-pam-perl is already the newest version.
libpam-runtime is already the newest version.
libio-pty-perl is already the newest version.
libmd5-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


webmin is not in the default repositories, you need to add the repository to your /etc/apt/sources.list or download the .deb file and run dpkg -i webmin.deb (or whatever the actual filename is)

so, no you did not install webmin, merely the dependencies for it

---

### Post by rdema19403 on 2010-02-17
is this the wright way to run it in the terminal 
test19403@test:~$ dpkg -i webmin_1.500_all.deb
dpkg: requested operation requires superuser privilege
test19403@test:~$ sudo su
[sudo] password for test19403: 
root@test:/home/test19403# dpkg -i webmin_1.500_all.deb
dpkg: error processing webmin_1.500_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 webmin_1.500_all.deb

---

### Post by pirateghost on 2010-02-17
first of all, dont use sudo su
sudo is just fine here.

yes those commands look proper, however make sure it is flagged as executable
```
sudo chmod 777 webmin_1.500_all.deb
```
then run
```
sudo dpkg -i webmin_1.500_all.deb
```

---

### Post by makingtheswitch on 2010-02-17
you need to 
```
 wget http://prdownloads.sourceforge.net/webadmin/webmin_1.500_all.deb
```and then 
```
  dpkg --install webmin_1.500_all.deb
```At least that is what it looks like.  To me it seems you've done everything -except- DL the webmin .deb package.  Which is what the first line of code will get you.  The second will install it.

[edited to correct code and make sense]

---

### Post by rdema19403 on 2010-02-17
thanks for everybody's input i am a noobie at this but it works now I really appreciate it. I am on a big learning curve with this it is frustrating sometimes and other times rewarding.

---

