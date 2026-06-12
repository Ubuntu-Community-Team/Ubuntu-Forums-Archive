---
title: "Joomla and FTP on ubuntu 11.10"
date: 2011-11-18
forum: Server Platforms
---

### Post by alain.roger on 2011-11-18
Hi,

today i migrated my windows web testing server (joomla) to ubuntu 11.10 and  therefore i'm having new issues/questions regarding the best way how to  manage it.

1. what is the best and unified way to change user permissions (for the whole joomla  installation) do you use an FTP client or did you do it using a simple  terminal ?

2. which FTP server did you setup (or fit the best) for updating and managing users' permissions ?

3. Who should be owner of root directory where will be installed Joomla ?
should it be root or the user ?

4. Who should be owner for the content of root directory (sub directories and files)
should it be root or the user

if my ubuntu web server user (to install and use joomla) is called "alain", should it be a member of web server administrators and owner of files/folders or should it be "root" ?

Thank a lot,

A.

---

### Post by HugoSerrano on 2011-11-18
Hello.

If you got a default apache installation you got to put your joomla installation at /var/www/

Then you need to change the owner to the apache user. By default it's www-data.

$sudo chown -R www-data:www-data /var/www/

---

### Post by alain.roger on 2011-11-18
ok, so i installed pure-ftp but i have a problem with root directory for my account.
I used the tutorial available on [https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

basically i setup the root directory as following:
```

sudo pure-pw useradd alain -u ftpuser -d ~alain/www/
```

however when user alain connects to ftp server, he's directly rooted to ~alain/ and not to ~alain/www/

where is the mistake ?
thx.

---

