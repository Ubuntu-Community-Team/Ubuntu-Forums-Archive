---
title: "Good GUI for administrating apache2 and ftp?"
date: 2009-08-17
forum: Server Platforms
---

### Post by grantemsley on 2009-08-17
I'd do it from the command line with vi...but my coworker does not like that idea.

I need to setup a webserver (apache2, php, mysql) and some sort of GUI for it.

I plan on installing ubuntu-desktop to take care of a gui for installing updates and such.

But I'm not aware of any GUI packages to:
- Configure apache virtual hosts
- Administer FTP users and permissions (any FTP server will do)

Any suggestions?

I've thought about setting up webmin or ispconfig, but they don't want a web solution, and those are both overkill for what they need to be able to do.

---

### Post by KayakJim on 2009-08-17
Webmin will probably do for what you want plus a little more.

---

### Post by jamesrfla on 2009-08-17
If you don't like webmin you can try phpmyadmin. You can get it by ```
sudo apt-get install phpmyadmin
``` Then you can access it by [http://serverip/phpmyadmin/](http://serverip/phpmyadmin/)

---

### Post by KayakJim on 2009-08-17
PHPMyAdmin does not configure Apache hosts nor FTP users.

---

### Post by Maheriano on 2009-08-17
Don't install a desktop, it's not needed on a server. Just use Webmin as posted or even try xPanel. They're both good, I use Webmin.

---

### Post by KayakJim on 2009-08-17
I apologize for missing your statement that you do not want a web-based solution.

The *best* option is for your coworker to suck it up and learn how to edit the files using vi, emacs, or some other editor.

Installing a desktop on a server opens your server up to further security exploits. Is that really worth it just for someone to edit a file?

---

### Post by cariboo on 2009-08-17
There are a couple of gui apps in the repository for managing proftpd and apache2, gproftpd for proftpd and rapache for apache2. I have had a look at both, personally I find it easier to use a text editor (nano) to edit the config files.

---

### Post by grantemsley on 2009-08-20
Believe me, I'd LOVE for my coworkers to learn the command line.  But they come from the windows world, and are pretty much scared of it.  Hence the need for the desktop environment.

Myself, I just edit config files in vi.  So much simpler.

I'll probably end up using webmin, even though they don't want it to be web based.

---

