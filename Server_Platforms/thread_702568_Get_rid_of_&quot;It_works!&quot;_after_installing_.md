---
title: "Get rid of &quot;It works!&quot; after installing Apache"
date: 2008-02-20
forum: Server Platforms
---

### Post by altonbr on 2008-02-20
I can't say I've ever had problems with install Apache in Debian/Ubuntu, but something must have changed over the past couple of months.

I always run this code to set up a localhost install into my home directory:
```
sudo sudo aptitude -y install apache2.2-common php5 &&
sudo rm -r /var/www &&
mkdir /home/$USER/localhost &&
sudo ln -s /home/$USER/localhost /var/www &&
echo 'Congratulations! Your localhost install was successful! You may now begin making websites in your <tt>~/localhost</tt> folder' | tee /home/$USER/localhost/index.html
```

However, whenever I do so now, Apache's default splash page shows up:
```
<html><body><h1>It works!</h1></body></html>
```

But I can't find where it's coming from.

Without touching anything, I've been able to use that script for over a year... does anyone know what might be going on or how I can get a directory listing of /home/$USER/localhost like it should?

---

### Post by Rogers on 2008-02-20
Try looking at the default site's location..........

> grep Directory /etc/apache2/sites-enabled/default

That should give you the output, you may need to sudo.

---

### Post by altonbr on 2008-02-20
Well that's the thing, I know Apache's root is /var/www so it should work when I symlink it from there to /home/$USER/localhost.

It has worked in the past and I see nothing new in /etc/apache2/sites-available/default that needs to be changed. I can even change the directory from /var/www/ to /home/$USER/locahost (with $USER being my username) and it still only says "It's works".

Yes, for future reference, I've rebooted and reloaded the server.

---

### Post by lespaul_rentals on 2008-02-20
Don't use a symbolic link, either put the files in */var/www* or modify your *site-enabled* configuration file to point to the new directory.

---

### Post by altonbr on 2008-02-20
> **lespaul_rentals said:**
> Don't use a symbolic link, either put the files in */var/www* or modify your *site-enabled* configuration file to point to the new directory.

I did do that, this is my current 'default' file, which I usually never have to modify:
```
<VirtualHost *>

        DocumentRoot /home/brett/localhost
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/brett/localhost>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ServerSignature Off

</VirtualHost>

```
Like I said, a symlink usually works on its own.

---

### Post by lespaul_rentals on 2008-02-20
Did you 644 it?

---

### Post by altonbr on 2008-02-20
> **lespaul_rentals said:**
> Did you 644 it?

Everything is 755, except for files which are 644. My home directory - including /home/brett/localhost - is 755, else it returns a forbidden message

---

### Post by altonbr on 2008-02-20
I have even ran
```
sudo rgrep "<html><body><h1>" /*
```
to see where the file is coming from, but no luck on finding the file yet.

---

### Post by p_quarles on 2008-02-20
That file is here:
```
/var/www/apache2-default/index.html
```
Or, at least it should be if you have the normal Ubuntu/Debian Apache2 setup.

---

### Post by altonbr on 2008-02-20
> **p_quarles said:**
> That file is here:
```
/var/www/apache2-default/index.html
```
Or, at least it should be if you have the normal Ubuntu/Debian Apache2 setup.

But I got rid of that in my code cited here: [http://ubuntuforums.org/showpost.php?p=4369634&postcount=1](http://ubuntuforums.org/showpost.php?p=4369634&postcount=1)

---

### Post by p_quarles on 2008-02-20
> **altonbr said:**
> But I got rid of that in my code cited here: [http://ubuntuforums.org/showpost.php?p=4369634&postcount=1](http://ubuntuforums.org/showpost.php?p=4369634&postcount=1)
Yeah, I saw that, but that's the only place where that file exists. Have you double-checked to ensure that the directory was succsesfully removed? 

I'm aware that this is weird, but it is true that enough things have changed from Ubuntu 7.04 to 7.10 that an old script could wind up broken.

---

