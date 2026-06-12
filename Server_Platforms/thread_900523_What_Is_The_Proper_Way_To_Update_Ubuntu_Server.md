---
title: "What Is The Proper Way To Update Ubuntu Server"
date: 2008-08-25
forum: Server Platforms
---

### Post by wbelk7777 on 2008-08-25
I have an LTS 8.04 Ubuntu Server running.  If I want to download the latest updates and patches for the server (not upgrade to next server version), what is the command I should issue?  Thanks.

---

### Post by crachel on 2008-08-25
apt-get update (as root)

---

### Post by moonpup on 2008-08-25
```
sudo apt-get update
```
This will update your sources/repos list

```
sudo apt-get upgrade
```
This will update your installed packages, but not do a full fledged distribution upgrade.

---

### Post by wbelk7777 on 2008-08-25
Thanks for the reply.  This is what I did.

sudo apt-get update
sudo apt-get upgrade

I wanted to check and make sure I had done the right thing.  I was sure the part about updating my sources was correct sudo apt-get update, but the sudo apt-get upgrade sounded too much like trying to do a version upgrade, thanks for the confermation.  What is the syntax for doing an upgrade to the next server version, once the next LTS is released?  Thanks.

---

### Post by damis648 on 2008-08-25
> **wbelk7777 said:**
> Thanks for the reply.  This is what I did.

sudo apt-get update
sudo apt-get upgrade

I wanted to check and make sure I had done the right thing.  I was sure the part about updating my sources was correct sudo apt-get update, but the sudo apt-get upgrade sounded too much like trying to do a version upgrade, thanks for the confermation.  What is the syntax for doing an upgrade to the next server version, once the next LTS is released?  Thanks.

What you did was completely correct. To do a full distribution upgrade, do
```
sudo apt-get dist-upgrade
```
Cheers!

---

### Post by sciurus on 2008-08-31
I can't think of any reason to use apt-get instead of aptitude.

For normal updates, do

```

sudo aptitude update
sudo aptitude dist-upgrade

```

For upgrades to a new version of Ubuntu (e.g. 7.10 to 8.04), do:

```

sudo aptitude install update-manager-core
sudo do-release-upgrade

```

---

### Post by damo12 on 2008-08-31
I'm still pretty new to Ubuntu server but I am the administrator of 2 servers both running Webmin and accessed remotely.  I'm not sure if this is an approved method or not but I have a cron job scheduled to run each day with the command:

aptitude -y update && sudo aptitude -y upgrade && sudo aptitude

and that works fine for me.

---

### Post by windependence on 2008-08-31
So what if an update breaks your server? Something to think about.

-Tim

---

### Post by HermanAB on 2008-08-31
Exactly.  If your server is working properly, then an update cannot make it better, it can only leave it the same or worse.

Consequently, I don't update servers automatically.  Once the servers are working, I leave them alone and re-install Linux in a year or three with a new version.  

Constant updates is just make work and looking for trouble.

---

### Post by tubezninja on 2008-08-31
> **HermanAB said:**
> Exactly.  If your server is working properly, then an update cannot make it better, it can only leave it the same or worse.

I have to disagree with that.  If you want to keep up with security patches, then you pretty much need to check for and install updates from time to time.

I realize that quite a few linux sysadmins (including a few I work with) have no qualms with running a server that has various software packages and the linux kernel way out of date (one I saw was three years old), but there are certain things that can't wait.  The recent OpenSSL/SSH issues is one of them, for instance.

And in any case, for as long as I've been running ubuntu, updates have not once made my servers worse off.  Though I have made sure to test the updates on a non-critical server before proceeding with the rest.  that's generally how it's supposed to be done if your servers are mission critical.

---

### Post by Vegan on 2008-08-31
Anyone got a shell script I can tie to cron? To automatically update every week?

---

### Post by Oldsoldier2003 on 2008-08-31
it would be trivial to add it to your crontab you really don't need a script :)

---

### Post by Oldsoldier2003 on 2008-08-31
So as not to appear that I am brushing you off I'll explain further. You could put a script in cron.weekly or you could just add the command apt-get update && apt-get upgrade to roots crontab, set for whatever date/time you want it to run.

---

### Post by Vegan on 2008-08-31
I have 3 files in /etc/cron.weekly/
and 1 in /etc/cron.monthly/

so I presume these are run with su privilege so I can run updates?

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo aptitude install update-manager-core


This way I can chuck the sudo command.

I am new to Linux server, sorry

---

