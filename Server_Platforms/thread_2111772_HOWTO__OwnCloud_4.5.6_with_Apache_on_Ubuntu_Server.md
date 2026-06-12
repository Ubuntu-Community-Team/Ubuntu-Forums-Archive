---
title: "HOWTO : OwnCloud 4.5.6 with Apache on Ubuntu Server 12.04 LTS"
date: 2013-02-02
forum: Server Platforms
---

### Post by samiux on 2013-02-02
According to Wikipedia, there are many types of [cloud computing]("http://en.wikipedia.org/wiki/Cloud_computing").  I am going to talk about Storage as a service (STaaS) private cloud.

I am going to introduce [OwnCloud]("http://owncloud.org/") which is developed by PHP and it is working great on LAMP (Linux, Apache, MySQL and PHP) environment but Windows and Mac OS should work ([4.5 Admin manual]("http://doc.owncloud.org/server/4.5/admin_manual/") and [5.0 Admin manual]("http://doc.owncloud.org/server/5.0/admin_manual/")).

OwnCloud has a lot of useful [features]("http://owncloud.org/features/"), such as synchronize your files (including movies and photos), sharing your files (including OwnCloud registered users and non-registered users), viewing ODF and ePub (ebook) formatted documents (such as .odt, odp, .ods, .epub) on your browser, calendars, to-do-list, galleries, notes editing and etc.  It also can mount your external storages (such as Dropbox and GDrive).  It also can manage users and groups from LDAP or AD instance.

The latest stable version of OwnCloud is 4.5.x and the development version is 5.0.x at this writing.  The outdated version is 4.0.x.  It is recommended to build your OwnCloud server dedicatedly and use hardware RAID 1, 5 or 6 when necessary.  You can test the software with their [online demo]("http://demo.owncloud.org/index.php") before installing it or purchase the service.

You are required to install OwnCloud Client to synchronize data and the client software is suitable for Windows, Mac OS and Linux systems.  You can manage the files as similar as you are doing on your desktops ([OwnCloud Client user manaul]("http://doc.owncloud.org/desktop/1.1/")).  The user manaul for using OwnCloud Server can be obtained at the official site ([4.5 user manual]("http://doc.owncloud.org/server/4.5/user_manual/") and [5.0 user manual]("http://doc.owncloud.org/server/5.0/user_manual/")).

The most interest thing is that you can customize the logo and colour very easily in order to suit your desire or company style.

Now, I would like to show you how to install OwnCloud 4.5.6 with Apache on Ubuntu Server 12.04 LTS.  This [tutorial]("http://samiux.blogspot.com/2013/02/howto-owncloud-with-apache-on-ubuntu.html") also covers security matters, such as IPS (Intrusion Prevention System) and Apache hardening.

Hope you enjoy!

Samiux

---

### Post by donniezazen on 2013-02-03
I have been hearing a lot about OwnCloud. Can it be used to browse and edit server driver over internet in a web browser?

---

### Post by samiux on 2013-02-03
> **donniezazen said:**
> I have been hearing a lot about OwnCloud. Can it be used to browse and edit server driver over internet in a web browser?

It is possible when the file is a text file (or program file) and it is in the directory of the OwnCloud.

Samiux

---

### Post by donniezazen on 2013-02-03
> **samiux said:**
> It is possible when the file is a text file (or program file) and it is in the directory of the OwnCloud.

Samiux

To be more precise I meant ability create, delete, move, rename, change permissions, etc. of files and folder of any kind like videos, movies, text files. More or less as if I am accessing the storage as in a file manager.

Thanks.

---

### Post by samiux on 2013-02-03
> **donniezazen said:**
> To be more precise I meant ability create, delete, move, rename, change permissions, etc. of files and folder of any kind like videos, movies, text files. More or less as if I am accessing the storage as in a file manager.

Thanks.

There are two methods to access OwnCloud, one is via the web interface and the other is via your desktop file manager (just like Dropbox and Ubuntu One).

If you access your OwnCloud via your desktop file manager, you can create, change file permission and etc just like on your real desktop.

Meanwhile, OwnCloud can play a certain of media file formats via the web interface, that is streaming.

Samiux

---

### Post by donniezazen on 2013-02-03
I am not really looking for playing music or video. There are Subsonic and Plex for that. I am looking for some good web file manager.Thanks I will check it out.

---

