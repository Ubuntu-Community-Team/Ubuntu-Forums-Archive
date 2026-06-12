---
title: "Storing passwords in root owned .htaccess files"
date: 2008-06-02
forum: Security
---

### Post by stickmangumby on 2008-06-02
I'm writing some PHP that will end up on a shared webhost. Naturally, I don't want my database passwords to be readable by anyone with a shell account on this server. 

I've been googling and came across the practice of storing sensitive information in .htaccess files, and making them readable only by me/root. The idea is that, when apache2 is started as root, it can read the .htaccess file. Then, when it is running normally as nobody, it can no longer access the .htaccess file, nor can anyone else with a shell account on the server (or some exploit of my PHP).

I can successfully set environment variables in .htaccess files using SetEnv, and access them in PHP in the $_SERVER array, but **only** when the .htaccess files are world readable. Making them readable only by me or by root returns a 403 Forbidden error when I try to go to the index of my site.

My apache2 error log has the following error:
"Permission denied: /var/www/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable"

Am I misinformed? Does apache not start as root? If so, what alternative solutions are there for protecting plaintext database credentials?

---

### Post by hyper_ch on 2008-06-02
You can't really prevent people from reading the database password.

If the webserver has somehow access to it then anyone who can create files on the server (hence has a shell login or so) can read the password. There's nothing you can prevent them to access it.

However you can make it a bit more difficult. What I did with my confixx setup is this:

(1) all websites are stored in /var/www/webX and it contains several folder like /var/www/webX/files and /var/www/webX/html. The webroot for a site is the html folder

(2) I only allow secure connections (SCP) BUT I don't want them to have a shell login. So I installed MySecureShell and restricted them to only access the html folder and forbid SSH access.

(3) I did then create an according database connection file in the files folder with the according data. This data gets included with a php script --> require_once(../files/config.inc.php)

So, they could just include the file or rather read and echo it. It must be readabe by the webserver otherwise it is of no use and you'll get an error. So even if that was not a php file (which needs to be executable) but a .htaccess file, the server still needs to read it and hence its also possible to print the content.

What it will prevent, however, is that if PHP engine fails for some reason and the php scripts are shown as text documents then the database credentials won't be directly visible.

---

### Post by cdenley on 2008-06-02
It doesn't need to be world-readable, just readable for the "www-data" user. I don't think .htaccess files are read until after it is running as www-data when clients make requests. I think the vhost configurations are read as root, though.

---

### Post by Sporkman on 2008-06-03
> **hyper_ch said:**
> What it will prevent, however, is that if PHP engine fails for some reason and the php scripts are shown as text documents then the database credentials won't be directly visible.

Is that possible? I don't want my PHP scripts readable...

---

### Post by cdenley on 2008-06-03
> **Sporkman said:**
> Is that possible? I don't want my PHP scripts readable...

It will happen if you run
```

sudo a2dismod php5

```
If apache is not configured to handle php files, a .php file extension will be like any unknown extension, and the clients will be sent the source code since apache isn't configured to interpret it. If you include a php file from a non-web-accessible directory, it will not be accessible if you disable the php module. Just don't run the command above or delete the module's links in /etc/apache2/mods-enabled.

---

### Post by Sporkman on 2008-06-03
> **cdenley said:**
> It will happen if you run
```

sudo a2dismod php5

```
If apache is not configured to handle php files, a .php file extension will be like any unknown extension, and the clients will be sent the source code since apache isn't configured to interpret it. If you include a php file from a non-web-accessible directory, it will not be accessible if you disable the php module. Just don't run the command above or delete the module's links in /etc/apache2/mods-enabled.

...so I'm not really in danger of PHP files becoming readable then (as long as PHP was configured to run correctly in the first place) - i.e. if the PHP module were to crash, then hopefully apache would simply stop serving up php files...

---

### Post by stickmangumby on 2008-06-03
After a bit more mucking around, I can confirm that apache2.conf and vhost configurations are read as root, but .htaccess files aren't. This is because changes in .htaccess files need to be reflected without restarting apache.

hyper_ch's suggestion seems the next best thing, but as he says, it relies on security through obscurity (if anyone on the same shared host knows the name of the file you're storing your database creditials in, they can easily access it). However, it seems like there is no better solution unless you have root access, or can get an admin with root access to do something for you :(

---

