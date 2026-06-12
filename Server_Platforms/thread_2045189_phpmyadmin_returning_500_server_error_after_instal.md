---
title: "phpmyadmin returning 500 server error after install."
date: 2012-08-20
forum: Server Platforms
---

### Post by jelatin on 2012-08-20
Alright, I've been following [this guide]("http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp") (along with others to double check) to attempt to get a working lamp stack installed on 12.04 LTS (VM), but phpmyadmin always throws an HTTP 500 server error.  PHP executes fine, it's just PHPmyadmin that will not work.

I uninstall the entire lamp stack each time and start from scratch.  I did notice step 6 which says:

    apt-get install php5-mysql php5-curl php5-gd php5-intl php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl

Returns the following error:

    The following packages have unmet dependencies:
    php5-intl : Depends: libicu44 (>= 4.4.1-1) but it is not installable
    E: Unable to correct problems, you have held broken packages

Even if I install all of the other packages except this one and try to install phpmyadmin, it returns a 500 server error. 

Any assistance would be appreciated.

---

### Post by Wim Sturkenboom on 2012-08-21
Anything in the apache logs?

/var/log/apache2/error.log
/var/log/apache2/access.log

---

### Post by jelatin on 2012-08-21
Nope, nothing relevant, just some info about a missing favicon.ico on my apache test page.

---

### Post by rukiaEnix on 2012-08-21
Most of the time the 500 error is for permissions. Who is the user that owns the phpmyadmin folder and files inside it? And what are the permissions that the folder and the files inside it have?

---

### Post by HugoSerrano on 2012-08-21
Just a possibility, check for a .htaccess file.

Regards!

---

### Post by lisati on 2012-08-21
> **Wim Sturkenboom said:**
> Anything in the apache logs?

/var/log/apache2/error.log
/var/log/apache2/access.log

There's also /var/log/apache2/error.log

---

### Post by Wim Sturkenboom on 2012-08-22
> **lisati said:**
> There's also /var/log/apache2/error.logDidn't I already referred to that one in the post you quoted?

:)

---

### Post by rukiaEnix on 2012-08-22
Please post the result of:

```

ls -l

```

And what permissions do your other web files have?

---

