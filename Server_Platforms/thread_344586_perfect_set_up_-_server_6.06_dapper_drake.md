---
title: "perfect set up - server 6.06 dapper drake"
date: 2007-01-23
forum: Server Platforms
---

### Post by magpy on 2007-01-23
Dear all

I am trying to get the server environment up and running.

I am following an online tutorial at this location:


[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)


I am having trouble with step 7 of the tutorial.  I need some packages which are not on the ubuntu server cd.  This was the command for the apt-get installation of around 10 different packages.  See below:

apt-get install binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev g++

Does anyone know where I can hold of these packages as a whole or will I have to get them individually then burn them to a cd or back up to floppy.  I found what I think might be some of them.  For example if I was looking for the fetchmail package would this be the right location of that repository?


[http://rpm.rutgers.edu/repository/ubuntu/pool/main/f/fetchmail/](http://rpm.rutgers.edu/repository/ubuntu/pool/main/f/fetchmail/)

as with

"binutils"

[http://rpm.rutgers.edu/repository/ubuntu/pool/main/b/binutils/](http://rpm.rutgers.edu/repository/ubuntu/pool/main/b/binutils/) 


Help/advice needed SOS SOS

---

### Post by Rippey on 2007-01-23
apt should get the packages automaticly, if you're connected to the internet, if you are and it doesn't you should have a look at your /etc/apt/sources.list, try commenting out your cd in there, if there are no other repositories in there have a look at _[this]("http://www.ubuntu-nl.org/source-o-matic/")_ site.

---

### Post by magpy on 2007-01-23
Thanks

The ubuntu computer is not connected by the way - does that mean if I select

*ubuntu supported packages* 

and 

*ubuntu community unsupported packages*


in step two of the form that I will get all the packages I needed that were in the apt-get list
I posted?

I completed the form and got this:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

----

As I am not connected to the net would this command still work?

---

### Post by Rippey on 2007-01-23
if you're not connected I'm afraid I won't be much help, I've never had a ubuntu install without internet connection :(

---

### Post by chrisfay on 2007-01-23
If you are not connected to the internet on that machine you will have to manually download from another machine and install them or download a different Ubu version disk with the packages on it. You obviously won't be able to connect to the online repositories if you're offline.

---

### Post by magpy on 2007-01-24
Cheers

Would it be a case of getting each file manually?

After I have my list of files would I then just burn them to disk and place them into the ubuntu machine when prompted?

If so I tried this method and it did not work.  I got the fetchmail package from this source:

[http://rpm.rutgers.edu/repository/ubuntu/pool/main/f/fetchmail/fetchmail_6.2.5-13ubuntu3.3_i386.deb](http://rpm.rutgers.edu/repository/ubuntu/pool/main/f/fetchmail/fetchmail_6.2.5-13ubuntu3.3_i386.deb)


I burnt it to cd, I tried to apt-get install fetchmail using the cd which I just burnt.  ubuntu displayed:

*E: "couldn't find package fetchmail"*

Any ideas



----


or does anyone know where there is a source to get all the packages in one hit? [see below]



apt-get install binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev g++

---

