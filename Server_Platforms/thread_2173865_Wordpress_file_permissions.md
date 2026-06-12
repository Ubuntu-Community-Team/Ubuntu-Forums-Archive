---
title: "Wordpress file permissions"
date: 2013-09-11
forum: Server Platforms
---

### Post by Colin_Mills on 2013-09-11
Linux newb be gentle

I have successfully installed my lamp stack and wordpress which all runs great - but I'm having problems with the file and directory permissions of wordpress in var/www.

I need to change the owner from root to my user account - Can this be done without having to sudo chown each dir and file individually?

TIA

---

### Post by Colin_Mills on 2013-09-11
I've since run gksu nautilus to change owner and permissions of the var/www directory - However; whilst in nautilus the directory and all sub directories and files show as me the owner - but when I exit nautilus they show as root - Any idea why this is?

---

### Post by Habitual on 2013-09-11
make backups!
```
sudo tar -pczf /root/archive.tar.gz /var/www
```

```
sudo chown **[COLOR=#ff0000]user[/COLOR]**:**group** /var/www/* -R
```
**group** is probably www-data or similar and I'd leave that alone but if it is, include it after **[COLOR=#ff0000]user[/COLOR]**:**www-data**

**[COLOR=#ff0000]user [/COLOR]**[COLOR=#ff0000][/COLOR]being your login username.

---

### Post by SeijiSensei on 2013-09-12
You do realize that Wordpress needs to write into some of its directories, right?  That means the "www-data" user must have write privileges as well as you.  I take the path of putting www-user in the same group as the WP owner, but I don't have a real user own the Wordpress tree.  I created a user that only owns websites.  If you put yourself in that user's group as well as the www-data user, you'll all be able to read and write in the WP tree.

---

### Post by Vegan on 2013-09-12
try chmod and set the permissions to 777, easier than messing around with various packages

---

### Post by CharlesA on 2013-09-12
> **Vegan said:**
> try chmod and set the permissions to 777, easier than messing around with various packages

Not when the files are being served by a web server. That effectively gives www-data full access to the files.

It would be a better idea to do as SeijiSensei suggests.

---

### Post by Habitual on 2013-09-13
> **Vegan said:**
> try chmod and set the permissions to 777
Very bad advice, sorry. It leaves **all content open to exploits.**

Convenience at the price of Security is neither convenient nor secure.

[http://wordpress.org/support/topic/directory-and-file-permissions](http://wordpress.org/support/topic/directory-and-file-permissions)

---

### Post by icebox83 on 2013-09-13
> **SeijiSensei said:**
> You do realize that Wordpress needs to write into some of its directories, right?  That means the "www-data" user must have write privileges as well as you.  I take the path of putting www-user in the same group as the WP owner, but I don't have a real user own the Wordpress tree.  I created a user that only owns websites.  If you put yourself in that user's group as well as the www-data user, you'll all be able to read and write in the WP tree.

Can you clarify this please? Who is www-user? Who is the WP owner? Who is the www-data user? I'm facing a similar problem as the original poster and tried sudo chown user:www-data /var/www -R to no avail because when I create a new directory within /var/www I have to chown all over again. This is such a pain. Can't I set it up so that I can both modify, delete, add files via sFTP AND have WP be able to write to its directory?

---

### Post by CharlesA on 2013-09-13
> **icebox83 said:**
> Can you clarify this please? Who is www-user? Who is the WP owner? Who is the www-data user? I'm facing a similar problem as the original poster and tried sudo chown user:www-data /var/www -R to no avail because when I create a new directory within /var/www I have to chown all over again. This is such a pain. Can't I set it up so that I can both modify, delete, add files via sFTP AND have WP be able to write to its directory?

www:data is the user your web server runs under.

Make yourself the owner of the files and add www-data as the group.

---

### Post by icebox83 on 2013-09-14
> **CharlesA said:**
> www:data is the user your web server runs under.

Make yourself the owner of the files and add www-data as the group.

Which is fundamentally sudo chown user:www-data /var/www right? And throwing -R in there also applies the chown to all subdirectories and files?

---

### Post by CharlesA on 2013-09-14
> **icebox83 said:**
> Which is fundamentally sudo chown user:www-data /var/www right? And throwing -R in there also applies the chown to all subdirectories and files?

Correct.

---

### Post by icebox83 on 2013-09-14
> **CharlesA said:**
> Correct.

Sweet! Some of this is starting to make some sense now. But now the problem is that this allows my user to write to the directory, but WordPress still can't. Any suggestions?

Clarification: If the WordPress directory is already in /var/www when I chown /var/www the config file writes just fine. But if I chown /var/www and then add the wordpress directory, that's where I run into problems with WordPress not being able to write its config file.

---

### Post by CharlesA on 2013-09-14
> **icebox83 said:**
> Sweet! Some of this is starting to make some sense now. But now the problem is that this allows my user to write to the directory, but WordPress still can't. Any suggestions?

Clarification: If the WordPress directory is already in /var/www when I chown /var/www the config file writes just fine. But if I chown /var/www and then add the wordpress directory, that's where I run into problems with WordPress not being able to write its config file.

I set my sites up like this:

/var/www/blog.charlesa.net/wordpress, which the DocumentRoot set to /var/www/blog.charlesa.net/wordpress.

So you would need to chown user:www-data /var/www/blog.charlesa.net/wordpress and see if the web server can write to it and if so, you are good to go.

I prefer not to give full permissions unless absolutely needed, so I would suggest changing the permissions from 660 back to 640 for files and 750 for directories after you have finished configuring wordpress.

Note: I don't really have much experience with WP, as I am just starting out, but I do not believe anything needs write access unless you are doing uploads.

---

### Post by Colin_Mills on 2013-09-18
Sorry for the late response guy's, been on vacation. 

Thanks to all for your wealth of knowledge, I decided to go down the xampp root as this is only a development server. Everything up and running just fine.

---

