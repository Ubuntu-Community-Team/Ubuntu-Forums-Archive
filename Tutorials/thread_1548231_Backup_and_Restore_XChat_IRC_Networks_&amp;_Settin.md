---
title: "Backup and Restore XChat IRC Networks &amp; Settings"
date: 2010-08-08
forum: Tutorials
---

### Post by cmuxed on 2010-08-08
***Question:  Where does XChat store it's network list and custom settings?***

[I]For some this may seem a relatively basic tutorial however I hope not only does it serve the obvious cause but also serves as an example for new users that often the easy answer is only a man page away as it was for me!

[/I] I was posed with the need to restore various settings from my old Karmic installation to a fresh install of Lucid.  The Karmic machine no longer booted and I did not want to simply copy the entire home directory to my shiny new Lucid install.  One of the applications I did require my settings restored for was the[COLOR=RoyalBlue] [XChat IRC]("http://xchat.org")[/COLOR] client of which I had quite a number of custom networks and favorite channels and also custom settings (proxy, dcc save location etc).  

If you dont have XChat and want to find out what packages are available from the command line type:

```
apt-cache search xchat
```After mindless searching around the old partition for XChat configuration files, I consulted the XChat man pages:

```
man xchat
```Which gave me the argument I required to show the user config directory:

```
xchat -u --configdir
```This returned the line /home/%username%/.xchat2

So I proceeded to call up that directory and take a look at the files therein:

```
ls /home/%username%/.xchat2
```The files I was interested were blatantly obvious:

[LIST]
[*]servlist_.conf - A list of all the networks
[*]xchat.conf - Custom user settings
[/LIST]
The main file I was interested in was the servlist_.conf file on my previous installation, so I backed up my new servlist_.conf file and proceeded to copy the old one with all my old network setting to my new XChat config directory:

```
mv servlist_conf servlist_conf.base
cp /media/%oldpartition%/home/%username%/.xchat2/servlist_.conf servlist_.conf
```I then started up my XChat client and voila!  My networks were there and those selected for auto connect, did so as I wished!

Hope this helps someone...

Cheers,

cmuxed[INDENT][I]

;)  On a side note, I copied both the fresh servlist_.conf file and my old servlist_.conf file to my new Ubuntu One 'Backup' Sync folder and amended my 'conf file backup script' scheduled with cron to make a copy of the live servlist_.conf file on a regular basis so I will have it wherever I am, even if my hdd explodes.  I am new to Ubuntu One and find it is great for automated incremental file system backups, important conf files, notes etc.  I might post about it one day.[/I]
[/INDENT]

---

### Post by AjAMz BoY on 2010-09-10
Thank you, this is what I was looking for!

---

### Post by m3ld4r10n on 2011-02-04
ta :]

---

### Post by Po0dle on 2011-10-31
Thanks a lot, exactly what I was looking for :)

---

