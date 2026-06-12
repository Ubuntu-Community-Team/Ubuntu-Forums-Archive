---
title: "Problem in installing webmin"
date: 2010-12-07
forum: Server Platforms
---

### Post by mahmoodn on 2010-12-07
Hi,
When I want to install webmin debian package, I get this error:
```
mahmood@localhost:~$ sudo dpkg -i webmin_1.530_all.deb 
(Reading database ... 309297 files and directories currently installed.)
Preparing to replace webmin 1.530 (using webmin_1.530_all.deb) ...
Unpacking replacement webmin ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on apt-show-versions; however:
  Package apt-show-versions is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 webmin

```
Then I decided to install the required libraries. However I get this:
```
mahmood@localhost:~$ sudo apt-get install libnet-ssleay-perl libio-pty-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  webmin: Depends: libauthen-pam-perl but it is not going to be installed
          Depends: apt-show-versions but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
I have to say that '-f' option also didn't work. What is the problem?

---

### Post by Johnley on 2010-12-07
you did run 

```
sudo apt-get -f install
```

instead of just plain apt-get? it has to have root permissions.

---

### Post by mahmoodn on 2010-12-07
Interesting.... I logged in as root and run only 
```
apt-get -f install
```
Here is the complete output message:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  apt-show-versions libapt-pkg-perl libauthen-pam-perl libio-pty-perl libnet-ssleay-perl
The following NEW packages will be installed:
  apt-show-versions libapt-pkg-perl libauthen-pam-perl libio-pty-perl libnet-ssleay-perl
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 403kB of archives.
After this operation, 1,819kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libnet-ssleay-perl 1.35-2ubuntu1 [204kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libauthen-pam-perl 0.16-2 [33.9kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main libio-pty-perl 1:1.07-2build1 [42.4kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid/main libapt-pkg-perl 0.1.24 [88.5kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid/universe apt-show-versions 0.16 [33.7kB]
Fetched 403kB in 6s (57.8kB/s)
Selecting previously deselected package libnet-ssleay-perl.
(Reading database ... 309297 files and directories currently installed.)
Unpacking libnet-ssleay-perl (from .../libnet-ssleay-perl_1.35-2ubuntu1_i386.deb) ...
Selecting previously deselected package libauthen-pam-perl.
Unpacking libauthen-pam-perl (from .../libauthen-pam-perl_0.16-2_i386.deb) ...
Selecting previously deselected package libio-pty-perl.
Unpacking libio-pty-perl (from .../libio-pty-perl_1%3a1.07-2build1_i386.deb) ...
Selecting previously deselected package libapt-pkg-perl.
Unpacking libapt-pkg-perl (from .../libapt-pkg-perl_0.1.24_i386.deb) ...
Selecting previously deselected package apt-show-versions.
Unpacking apt-show-versions (from .../apt-show-versions_0.16_all.deb) ...
Processing triggers for man-db ...
Setting up libnet-ssleay-perl (1.35-2ubuntu1) ...
Setting up libauthen-pam-perl (0.16-2) ...
Setting up libio-pty-perl (1:1.07-2build1) ...
Setting up libapt-pkg-perl (0.1.24) ...
Setting up apt-show-versions (0.16) ...
** initializing cache. This may take a while **

[COLOR="Red"]Setting up webmin (1.530) ...
Webmin install complete. You can now login to https://localhost:10000/
as root with your root password, or as any user who can use sudo
to run commands as root.
[/COLOR]
```
As you can see at the end of the output, it says that webmin is installed, and I can access from outside of LAN with IP address. Notice the http**s**://W.X.Y.Z:10000/

Thanks for your help

---

### Post by zarthur on 2013-04-23
The link below has a complete overview of the WebMin installation process and how to overcome the issues: [http://mametrockafella.wordpress.com/2010/08/12/how-to-install-webmin-ubuntu-10-04/](http://mametrockafella.wordpress.com/2010/08/12/how-to-install-webmin-ubuntu-10-04/)
In my case **sudo apt-get install apt-show-versions** and then **sudo apt-get -f install** made Webmin installed.

---

