---
title: "Webmin won't install"
date: 2006-08-18
forum: Server Platforms
---

### Post by Triikan on 2006-08-18
*Warning: Newb Ahead (at least at linux)*
I've got an Ubuntu LAMP Server installation.  It's fresh besides installing Torrentflux.

Okay, I'm trying to install Webmin.  I've used wget to download both the deb package and the .tar.gz file.  However, I get errors when trying to run either:


jon@uTriikanServer:~$ tar zxvf webmin-1.290.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

and with the deb package it says that it's:

jon@uTriikanServer:~$ sudo dpkg -i webmin_1.290.deb
Password:
dpkg-deb: `webmin_1.290.deb' is not a debian format archive
dpkg: error processing webmin_1.290.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 webmin_1.290.deb


Before this I thought my first adventure into command line only since DOS was going pretty good.  Any help would greatly be appreciated.

Also, I installed everything to an old 8GB drive to make sure nothing was written (as far as system files) to the 80GB storage drive that I put in it as well (After installation was done) (to make sure I could swap out the 80gb without my installation being bricked); how do I mount it in command line?  It's already formatted (used gparted live cd)

---

### Post by dazedandconfused on 2006-08-20
I had no problem with webmin that I downloaded using lynx instead of wget. It sounds like a corrupt download. Try installing Lynx or links and pulling the files down with that. I tried both deb and tarball versions and it worked on both. Also, make sure you have perl's SSLEAY module installed if you want to access Webmin through an SSL secred commection.

Cheers,

Jools

---

### Post by dazedandconfused on 2006-08-20
Oops, forgot the Newb Ahead warning.

Lynx and Links are text based web browsers. You can install them on the CLI using:

sudo apt-get install links or sudo apt-get install lynx.

If you don't mind running a desktop on your LAMP machine you can ease your life by installing a GUI desktop using:

sudo apt-get install ubuntu-desktop

Be careful to back up any modified configs you have set up though as installing Ubuntu Desktop butchered my LDAP/PDC setiings which I'd spent all evening writing (you live and learn).

Any probs post back,

Cheers,

Jools

---

### Post by itzdata on 2006-08-22
I too have been having trouble installing Webmin. I have followed the instuctions and installed the links and PERL stuff needed. I don't know how to actually use links to pull a file in and then install.

I know I have to access Webmin via a browser on port 10000 but thats all. Any info would be gratefully accepted. 

The reason I am installing Webmin is because a friend of mine told me that this is the only really easy way to load, configure and use Apache2.

Thanks in advance.

Cheers
Jeff

---

### Post by SlowYaRoll on 2006-09-01
I just figured out how to install Webmin on Ubuntu and avoid most of the problems with installing it.


[http://ubuntuforums.org/showthread.php?t=195093&page=4](http://ubuntuforums.org/showthread.php?t=195093&page=4)

---

### Post by jimm on 2006-09-01
Hi,

I installed it from the archive instead of using the deb or apt, the reason is if you use the deb install some of the third party modules give you grief because stuff gets installed in strange places.

I had no issues installing it from the tar package off the webmin site. I just unpacked it and ran the install and it worked fine.

Thanks,
James

---

