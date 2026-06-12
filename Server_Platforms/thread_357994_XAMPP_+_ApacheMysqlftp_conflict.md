---
title: "XAMPP + Apache/Mysql/ftp conflict"
date: 2007-02-10
forum: Server Platforms
---

### Post by TinBane on 2007-02-10
I have a ubuntu server running dapper, using apache/mysql/php as installed from Synaptic. I'm also using vsftp to host ftp files.

However, I need to install XAMPP, however it won't start because things are already installed.

Is there any way to install all the features onto XAMPP so I can install something that needs XAMPP, or is there a way to port my apache/mysql/php stuff over to XAMPP?

Cheers,
Adrian

---

### Post by localzuk on 2007-02-10
What are you trying to do? XAMPP simply stands for LinuX, Apache, Mysql, PHP, Perl and is a way of easily installing these components.

If you already have them installed then you don't need XAMPP. Can you give more detail as to what it is you are wanting to run?

---

### Post by TinBane on 2007-02-10
It has some other stuff doesn't it (ruby or something)?

The reason I want to use it, is because I want to use WiiCR to stream onto my wii, and the installation requires XAMPP. 

So either I need to learn how to install WiiCR onto XAMPP, or to move my gallery2 onto XAMPP.

---

### Post by localzuk on 2007-02-10
According to the apachefriends site, XAMPP contains:

```
Apache, MySQL, PHP & PEAR, Perl, ProFTPD, phpMyAdmin, OpenSSL, GD, Freetype2, libjpeg, libpng, gdbm, zlib, expat, Sablotron, libxml, Ming, Webalizer, pdf class, ncurses, mod_perl, FreeTDS, gettext, mcrypt, mhash, eAccelerator, SQLite and IMAP C-Client.
```

All of these, as far as I am aware, can be installed via apt/synaptic. I would advise you to try installing WiiCR into your /var/www/ (where the instructions say to put it into /opt/lamp). Give it a try and post the results.

---

### Post by TinBane on 2007-02-11
Thanks very much, I'll give it a shot :)

---

