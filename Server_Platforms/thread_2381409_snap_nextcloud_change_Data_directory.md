---
title: "snap nextcloud change Data directory"
date: 2017-12-30
forum: Server Platforms
---

### Post by cazz on 2017-12-30
Hi
Have install nextcloud with snap and it works greate.
but I like to change the Data directory to another harddrive and I have mount, format and copy the data folder and also change config.php file.
But when I trying to access it say 

> Internal Server Error

The server encountered an internal error and was unable to complete your request.
Please contact the server administrator if this error reappears multiple times, please include the technical details below in your report.
More details can be found in the server log.


and the log say
```
getpwuid couldn't determine user name from uid you probably need to modify the user directive
```

Not sure if that is the error I looking for but I guess it have something with that snap apache can't connect to the new folder??
Have never work with snap so not sure what to do or it even use www-data

---

### Post by TheFu on 2017-12-30
I've never dealt with snaps, but run nextcloud.  All the data needs to be owned by the web-server userid. That is normally www-data for Ubuntu systems.  How to move the data around is documented in the nextcloud docs and normal Unix user/group permissions need to be handled.  I followed those about a yr ago and moved the data on my installation. Don't remember anything difficult or funny about it. Sorry.

If you don't have a good grasp of Unix file and directory permissions, I'd strongly encourage you to learn that ASAP. It has been around since 1970 and won't be changing in the foreseeable future for any Unix-like OS. That means that learning this stuff is going to pay off for pretty much any OS you will use, with 1 exception - MS-Windows.

---

### Post by cazz on 2017-12-31
Thanks for the replay
I know about the permissions but the strange is that when I looking at the nextcloud folder I see it own by the root/root
Also data own by root/root

I did find that I can add a external storage but have not find how I can set it as default when I run nextcloud app from my computer and my phone.

---

### Post by LHammonds on 2017-12-31
Snapd is a specialized install designed to be quick-n-easy, not customizable. 

I setup my own databases and web servers to be separate and more secure which also allows me to be highly customizable. 

The downside to my approach is that you have to know more than just the quick-n-easy install methods which typically (like in this case) installs the database and web servers along with the website. 

I don't use snap so I cannot help troubleshoot.

Sorry,
LHammonds

---

### Post by cazz on 2017-12-31
is ok I have run both easy way and not the easy way so I try and see what is best for me.

---

### Post by TheFu on 2017-12-31
Thanks for answering.

If the files are root:root, then you should **chown** them as directed in the nextcloud instructions.
If that doesn't work, I'd ask which file system is being used?  NTFS (or any of the FAT32/vfat/exfat) generally doesn't support different Unix permissions, so a Linux file system is required.

---

### Post by cazz on 2017-12-31
mmm I did look and find a www-data group so I did chown it to the group.
It almost work but still got error.
But it was no problem to connect it as "external storage" in nextcloud

It is ext4

---

### Post by TheFu on 2017-12-31
```
drwxrwx---  9 www-data www-data 4096 Dec 31 06:34 nc-data/

```
are the ownership and permissions for my NC data.  I put it in /opt/nc-data/.
Everything below there is owned by www-data, even the per-userid data areas.  Generally with 640 file permissions and 750 for directories. Different addons create directories here and some are 755.

All are owned by the userid running the web server.

I use external storage mounts too - but those are all for files I manage outside nextcloud and they are NFS read-only mounts managed via autofs.  They only get mounted when requested by NC.  They are mainly audio and photos (surprise).

I should mention that I do not consider nextcloud to be secure enough to be generally available over the internet.  It is only accessible via a VPN or using ssh as a SOCKS proxy to the internal network.  I just don't trust php web-apps, having been burned and knowing lots and lots of people who were also burned too.

---

### Post by LHammonds on 2017-12-31
If the database or web service is being run under the root account, I sure hope your site is not accessible via the Internet.

LHammonds

---

### Post by cazz on 2017-12-31
no not yet and that is strange that they have done that.
I mean the point to have nextcloud is to connect it to the internet and have access where ever I'm

---

### Post by TheFu on 2017-12-31
> **cazz said:**
> no not yet and that is strange that they have done that.
I mean the point to have nextcloud is to connect it to the internet and have access where ever I'm

Use a VPN or ssh-tunnel. ssh tunnels are pretty simple.  VPNs are a little harder, but easier for non-technical users and android devices. I use openvpn for android.  I use ssh for a SOCKS proxy from laptops.

OTOH, it is your choice what is and isn't available to anyone in the world. You might have a much higher risk tolerance than me.

---

### Post by cazz on 2017-12-31
mm have already VPN but like to easy connect to the nextcloud
I did follow this guide
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-16-04)

They did have a old guide how to install nextcloud and SSL but no more?

---

### Post by TheFu on 2017-12-31
SSL doesn't actually help security. It helps privacy of the data, nothing else.  It doesn't prevent someone from running 1 billion userids/passwords to hack in.  It doesn't help against web-app programming errors either.

A VPN stops most of those issues, immediately.

Be careful out there.

---

### Post by cazz on 2017-12-31
yes I know I just mean I like to have SSL when I run nextcloud
But I have also see that snap i very very populare to use to install program on linux so I wonder how secure is snap?

---

### Post by LHammonds on 2018-01-01
> **cazz said:**
> yes I know I just mean I like to have SSL when I run nextcloud
But I have also see that snap i very very populare to use to install program on linux so I wonder how secure is snap?
I have never liked the all-in-one packages that roll everything together.

The main reason is that I have over 100 servers and cannot afford to waste precious RAM/CPU resources by having a database and web server on each and ever server.  It is also a real pain to keep system security nice and tight if you have to remember to apply a security fix or reconfiguration to 20 different servers with MySQL on it.

I have one MariaDB (MySQL) dedicated server and I keep her locked down and maintained well.  If I try to follow the various "quick-n-easy" installs out there for WordPress, MediaWiki, etc., I would be install LAMP stacks on every server I setup.  You cannot use "apt-get install wordpress" if you want to use a dedicated database server that already exists...it will install its own along with a web server.

I have only ever used these all-in-one packages to just try out the app on a test/throwaway server for the purpose of evaluating the service to see if I even want to spend the time making a production-level variation.

I typically install a base [Ubuntu Server with my standard configuration ]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=220")of separated partitions, maintenance scripts/schedules and basic security systems in place.

Then I'll turn it into an application-specific server such as [MariaDB database server]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=225"), [MediaWiki web server]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=226"), [ownCloud server]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=234") and so on.  But they will be installed in such a way that it does not auto-deliver components I already maintain...such as a dedicated database.

Even if I only had a single server, I would still install the database and web server myself and then bolt on the web application (like NextCloud) which would be extremely easy like any other database-driver web application.

**EDIT:** HAPPY NEW YEAR!!!!

LHammonds

---

### Post by cazz on 2018-01-01
Same here


THANKS

---

### Post by TheFu on 2018-01-01
> **cazz said:**
> yes I know I just mean I like to have SSL when I run nextcloud
But I have also see that snap i very very populare to use to install program on linux so I wonder how secure is snap?

Snaps include all the dependencies with them. That means that snap patch management is something you have to do.  It might be included. IDK.  It will certainly be larger packages and the package maintainer might assume that everyone is using their configuration, not a customized one.  These are things I'd want to absolutely know before trusting any snap.  And what happens if the snap package maintainer team gets lazy and doesn't move to newer libraries as quickly as security patches dictate?  For an internal LAN webapp, that isn't nearly as important as an internet-facing webapp.

Of course, if you require VPN use for access, then the risks are much lower.  And using a VPN always with every portable device on an outside network is just good sense.  I fear people just aren't paranoid enough, but I worked in telecom for a decade.

---

### Post by cazz on 2018-01-01
It feel that snap Nextcloud feel a little slow then the last time I did install nextcloud (that time as not snap)
I going this year build a whole new serverpark from the ground so right now I just try snap to see how it works so if someone I know want to make they own Nextcloud I can tell them to try snap (I'm the only one of my friends that know linux best but have not so much time to help them) 
And even Nextcloud self tell how to use snap with Nextcloud.

To bad that I did have a nice guide how to install Nextcloud with SSL but that guide is gone and only I can find is to use snap or some guide that look too complicated to use.

---

### Post by LHammonds on 2018-01-11
> **cazz said:**
> To bad that I did have a nice guide how to install Nextcloud with SSL but that guide is gone and only I can find is to use snap or some guide that look too complicated to use.
I am in the process now converting my ownCloud servers to NextCloud.  I'm also converting my ownCloud "how-to" [guide for NextCloud]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=239") and should be done in a few days depending on how much free time I have.

**EDIT** (2018-01-13) - I have finished my NextCloud install guide and should be accurate now.  Once I get some more time away from the guide, I will go through again with a fresh install and re-verify all the steps from scratch.  Also posted in [Ubuntu Tutorial Forums](https://ubuntuforums.org/showthread.php?t=2382463)

LHammonds

---

### Post by DuckHook on 2018-01-12
> **LHammonds said:**
> …guide for NextCloud and should be done in a few days…
Simply awesome guide. Up to your usual quality. Can't wait for you to complete it. =d>

---

