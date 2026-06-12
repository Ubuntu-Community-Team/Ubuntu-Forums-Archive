---
title: "ModSecurity - I can't find workable install/configure instructions."
date: 2014-04-20
forum: Security
---

### Post by Luft on 2014-04-20
I think ModSecurity must have changed recently because all of the instructions for configuring it tells me to modify **/etc/apache2/mods-available/mod-security.conf**.  This file does not exist.

I have tried the instructions found [here]("http://www.thefanclub.co.za/how-to/how-install-apache2-modsecurity-and-modevasive-ubuntu-1204-lts-server") and [here]("https://www.digitalocean.com/community/articles/how-to-set-up-mod_security-with-apache-on-debian-ubuntu").

Can anyone point me to instructions that will work on Ubuntu 14.04?

Thank you.

---

### Post by Habitual on 2014-04-20
> **Luft said:**
> I think ModSecurity must have changed recently because all of the instructions for configuring...Did you in fact, install with a package manager?

---

### Post by Luft on 2014-04-20
I followed the instructions in the sites listed.  From a terminal:
sudo apt-get install libxml2 libxml2-dev libxml2-utils
sudo apt-get install libaprutil1 libaprutil1-dev
sudo apt-get install libapache-mod-security
sudo mv /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf
sudo nano /etc/modsecurity/modsecurity.conf  
Made some configuration changes suggested.
Then I'm instructed to edit mod-security.conf: 
sudo nano /etc/apache2/mods-enabled/mod-security.conf

It isn't there.  This looks wrong to me anyway.  I would expect to find it in mods-available but it isn't there either.

---

### Post by Luft on 2014-04-20
It looks like apt-get is installing a newer package:

The following extra packages will be installed:
  libapache2-mod-security2 liblua5.1-0 modsecurity-crs

I looked in the list of files that libapache2-mod-security2 installs and mod-security is not among them.  It does install the following:
/etc/apache2/mods-available/security2.conf
/etc/apache2/mods-available/security2.load
/etc/modsecurity/modsecurity.conf-recommended
/etc/modsecurity/unicode.mapping
/usr/bin/mlogc
/usr/lib/apache2/modules/mod_security2.so
/usr/share/doc/libapache2-mod-security2/NEWS.Debian.gz
/usr/share/doc/libapache2-mod-security2/README.Debian
/usr/share/doc/libapache2-mod-security2/README.TXT
/usr/share/doc/libapache2-mod-security2/changelog.Debian.gz
/usr/share/doc/libapache2-mod-security2/copyright
/usr/share/doc/libapache2-mod-security2/doc/README.txt
/usr/share/doc/libapache2-modsecurity/README.mlogc
/usr/share/doc/libapache2-modsecurity/mlogc-default.conf

---

### Post by Habitual on 2014-04-21
> **Luft said:**
> ...
Then I'm instructed to edit mod-security.conf: 
sudo nano /etc/apache2/mods-enabled/mod-security.conf

It isn't there.  This looks wrong to me anyway.  I would expect to find it in mods-available but it isn't there either.

I would treat that as a typo, and go with /etc/modsecurity/modsecurity.conf

---

### Post by Luft on 2014-04-21
I agree, that must have been a typo.  

The most recent instructions I'm finding on the Web for Ubuntu are all telling me to edit mod-security.conf in the** /etc/apache2/mods-available/** directory.  This file is suppose to tell apache where to look for the CRS rules.  But this file does not exists.  

I'm guessing that the instructions are out of date.  Finding installation/configuration instructions on the web is easy.  Finding even one set that actually works with the current libapache2-modsecurity package pointed to by Ubuntu 14.04 is proving to be a challenge.  I, unfortunately, am a beginner at this so I can't draw on previous knowledge.

I appreciate any help and suggestions.  When I do get this figured out I'll post clear  instructions that will, hopefully spare other people from having to fight with this.  (At least until they change libapache2-modsecurity again!) :)

---

### Post by Luft on 2014-04-21
Okay, I see what's going on now.  The libapache2-modsecurity package used by Ubuntu 14.04 does not use mod-security.conf.  It installs security2.conf and security2.load.  It also puts the conf files in /usr/share/modsecurity-crs.  After I test everything I'll write up some install instructions and post them.

---

### Post by Habitual on 2014-04-23
[Great write-up]("http://ubuntuforums.org/showthread.php?t=2219109") on your experiences installing and configuring this, btw.
Mad Props.

---

