---
title: "Newb: Need help switching to apache2"
date: 2007-10-04
forum: Server Platforms
---

### Post by Smartin on 2007-10-04
Hi,

An OSX refugee here...

I'm wanting to use gnome-user-share and it relies on apache2 to work.

I have done an 'uninstal completely' of apache and installed apache2. I'm running Feisty.

If I go to [http://127.0.0.1/](http://127.0.0.1/) I get a list of two folders, one being apache2-default.

I also get 'Apache/1.3.34 Server at 127.0.0.1 Port 80' below that.

If I click on the apache2 link I get 'It works!'.

Questions: Why does it look as if apache(1) is still running?
How to I get apache2 to be my one and only webserver, replacing apache completely so that it serves [http://127.0.0.1/](http://127.0.0.1/) as opposed to inside another folder?

No-one seems to know how to get gnome-user-share going but that's a different story :-)

Thanks!

Simon

---

### Post by conjur3r on 2007-10-04
I've no idea how you managed to get Apache (1.x) installed with gnome-user-share.  The package lists Apache (2.x) as a dependency!

[http://packages.ubuntu.com/feisty/gnome/gnome-user-share](http://packages.ubuntu.com/feisty/gnome/gnome-user-share)

Whichever tutorial you followed needs to be updated.  What command did you use to remove apache 1?

---

### Post by Smartin on 2007-10-04
conjur3r,

Thanks for the prompt response.

I forget now but I must have installed apache2 as a dependency for gnome-user-share and apache separately. Isn't apache pre-installed?

I used the synaptic package manager to remove apache 'Completely'.

HTH.

Simon

---

### Post by conjur3r on 2007-10-04
Nope apache isn't preinstalled.

Not sure why apache 1.x is still serving.  I can't speak for the synaptic package manager.  I normally do everything via the terminal (apt-get, dpkg, etc).  Are you able to open up a terminal and run the following?

# dpkg -l | grep apache

---

### Post by Smartin on 2007-10-04
Hi,

I get:

ii  apache-common                              1.3.34-4.1                             support files for all Apache webservers
ii  apache-perl                                1.3.34-4.1                             versatile, high-performance HTTP server with
ii  apache-ssl                                 1.3.34-4.1                             versatile, high-performance HTTP server with
ii  apache2                                    2.2.3-3.2ubuntu0.1                     Next generation, scalable, extendable web se
ii  apache2-mpm-prefork                        2.2.3-3.2ubuntu0.1                     Traditional model for Apache HTTPD 2.1
ii  apache2-utils                              2.2.3-3.2ubuntu0.1                     utility programs for webservers
ii  apache2.2-common                           2.2.3-3.2ubuntu0.1                     Next generation, scalable, extendable web se
ii  libapache-mod-perl                         1.29.0.4-4.1                           integration of perl with the Apache web serv
ii  libapache2-mod-auth-mysql                  4.3.9-2.1ubuntu2                       Apache 2 module for MySQL authentication
ii  libapache2-mod-dnssd                       0.4-1.1build1                          Apache 2 module which adds Zeroconf support 
ii  libapache2-mod-php5                        5.2.1-0ubuntu1.4                       server-side, HTML-embedded scripting languag


I have just double-checked that I have all the dependencies for gnome-user-share installed, which I have.

Thanks again for your help.

Simon

---

### Post by conjur3r on 2007-10-04
Try searching for apache-ssl using the synaptic manager.  This *should* also remove its dependencies (which should be all of those non version 2 packages).  Confirm by doing a search in the manager for "apache" and see if those other non version 2 apache packages are installed.  If so, remove them also.

If you want to try the terminal, it is the following:
# sudo apt-get remove --purge apache-ssl

---

### Post by Smartin on 2007-10-04
Hi,

I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a libartsc0 libmtp5 pure-ftpd-common fftw3
  liblualib50 libcurl3-gnutls ruby1.8 ruby libavahi-qt3-1 python-sip4
  libtunepimp5 libifp4 libdbus-qt-1-1c2 libxvmc1 libmodplug0c2 libpulse0
  libqt3-mt liblua50 libruby1.8 libnjb5 libofa0 libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  apache-ssl*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1106kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125558 files and directories currently installed.)
Removing apache-ssl ...
 * Stopping apache-ssl 1.3 web server...                                 [ OK ] 
Purging configuration files for apache-ssl ...
dpkg - warning: while removing apache-ssl, directory `/etc/apache-ssl' not empty so not removed.

There are two files in etc/apache-ssl. apache-pem and what looks like a sym-link to a file called 30ce543d.

I guess they need to go? How do I do that?

Simon

---

### Post by conjur3r on 2007-10-04
I'm quite sure they are just the SSL keys the installation process created.  /etc/apache-ssl should be safe for removal.

# sudo rm -fr /etc/apache-ssl

You should try your apache2 now.

---

### Post by Smartin on 2007-10-04
Hi,

Did that and restarted for good measure.

I'm still getting:

 dpkg -l | grep apache
ii  apache-common                              1.3.34-4.1                             support files for all Apache webservers
ii  apache-perl                                1.3.34-4.1                             versatile, high-performance HTTP server with
ii  apache2                                    2.2.3-3.2ubuntu0.1                     Next generation, scalable, extendable web se
ii  apache2-mpm-prefork                        2.2.3-3.2ubuntu0.1                     Traditional model for Apache HTTPD 2.1
ii  apache2-utils                              2.2.3-3.2ubuntu0.1                     utility programs for webservers
ii  apache2.2-common                           2.2.3-3.2ubuntu0.1                     Next generation, scalable, extendable web se
ii  libapache-mod-perl                         1.29.0.4-4.1                           integration of perl with the Apache web serv
ii  libapache2-mod-auth-mysql                  4.3.9-2.1ubuntu2                       Apache 2 module for MySQL authentication
ii  libapache2-mod-dnssd                       0.4-1.1build1                          Apache 2 module which adds Zeroconf support 
ii  libapache2-mod-php5                        5.2.1-0ubuntu1.4                       server-side, HTML-embedded scripting languag

Traces of apache still there?

[http://127.0.0.1](http://127.0.0.1) looks the same, including the reference to apache as before.

I also did:

sudo apt-get remove --purge apache-ssl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache-ssl is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a libartsc0 libmtp5 pure-ftpd-common fftw3
  liblualib50 libcurl3-gnutls ruby1.8 ruby libavahi-qt3-1 python-sip4
  libtunepimp5 libifp4 libdbus-qt-1-1c2 libxvmc1 libmodplug0c2 libpulse0
  libqt3-mt liblua50 libruby1.8 libnjb5 libofa0 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Simon

---

### Post by conjur3r on 2007-10-04
I'm surprised it didn't remove them automatically.  Try removing them manually:

# sudo apt-get remove --purge apache-common apache-perl libapache-mod-perl

How are you starting apache 2?

---

### Post by Smartin on 2007-10-04
Hi,

sudo apt-get remove --purge apache-common apache-perl libapache-mod-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  apache-common* apache-perl* libapache-mod-perl*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 5562kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124444 files and directories currently installed.)
Removing apache-perl ...
 * Stopping apache-perl 1.3 web server...                                [ OK ] 
Purging configuration files for apache-perl ...
Removing libapache-mod-perl ...
Removing apache-common ...
Purging configuration files for apache-common ...

I'm starting apache2 just by having it ticked in the 'Services' window and it starts when the box boots. System > Administration > Services

Is this making any sense :-)

Simon

---

### Post by conjur3r on 2007-10-04
Yeah, it's making a lot of sense.  The other packages weren't removed because apache-perl required them and it wasn't instructed to be removed until just now.  All Apache 1.x software should now be gone from your system.

Ok, try apache 2 again however way you want.   In the terminal it's a number of ways but commonly:
# sudo apache2ctl restart

---

### Post by Smartin on 2007-10-04
Newsflash!

I restarted the box and [http://127.0.0.1](http://127.0.0.1) is now showing the same folders but also 
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at 127.0.0.1 Port 80

You're getting there!

How to I set the webserver root folder to be outside the apache2-default folder?

Simon

---

### Post by conjur3r on 2007-10-04
You will now need to edit your apache configuration.  There are a number of files and they all reside under /etc/apache2.  The file you want to edit is /etc/apache2/sites-available/default

Change DocumentRoot to be where ever you want it to go.  You will most likely need to edit the line underneath starting with <Directory as well.

All configuration changes require apache to be restarted.

---

### Post by Smartin on 2007-10-04
conjur3r,

Can't thank you enough! I'll leave you alone now! :-)

I'll have a bash at the rest myself and email the developer about gnome-user-share. Still need to figure that one out...

Thanks again!

Simon

---

### Post by conjur3r on 2007-10-04
No worries.  Anytime!

I haven't look at gnome-user-share too much but from what I saw, all needed software should be installed when you install the gnome-user-share package.  That's most of the pain taken away.  I would assume it's just a matter of configuring it the way you want now.

---

### Post by Smartin on 2007-10-04
I have emailed the developer. I can't make any sense out of it. There doesn't seem to be any interface to it whatever. The only options I get to shate is through SMB or NFS. Neither of which interest me at this stage.

I'll get there in the end! :-)

Thanks mate!

Simon

---

