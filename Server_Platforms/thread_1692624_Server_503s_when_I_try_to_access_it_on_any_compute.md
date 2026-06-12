---
title: "Server 503s when I try to access it on any computer!"
date: 2011-02-21
forum: Server Platforms
---

### Post by eL3ET on 2011-02-21
So i'm making my Xubuntu Desktop computer into a web server and these are the instructions i've followed to get to the error:

sudo tasksel install lamp-server [no errors]

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite [no error]

gksudo gedit /etc/apache2/sites-available/mysite [no error]

Changed DocumentRoot to the location I wanted /home/el3et/public_html/

Changed <Directory /var/www/> to <Directory /home/el3et/public_html/>

Saved the file. [no error]

sudo a2dissite default && sudo a2ensite mysite [no error]

sudo /etc/init.d/apache2 restart [no error]

echo '<b>Hello! It is working!</b>' > /home/el3et/public_html/index.html

Browsed to [http://localhost](http://localhost) on firefox and it says:

[IMG]http://i51.tinypic.com/210kphu.jpg[/IMG]

---

### Post by CharlesA on 2011-02-21
Are the permissions correct?

---

### Post by eL3ET on 2011-02-21
> **CharlesA said:**
> Are the permissions correct?

I'm new to linux systems, I don't really know how I would give the permissions to my Public_HTML file to make it viewable.

What folder permissions do I need to change, and to what do I need to change them too...

---

### Post by CharlesA on 2011-02-21
It should be 755 (rwxr-x-r-x) for directories and 644 (rw-r--r--) for files.

---

### Post by eL3ET on 2011-02-21
> **CharlesA said:**
> It should be 755 (rwxr-x-r-x) for directories and 644 (rw-r--r--) for files.

How do I do this from terminal?

---

### Post by rubylaser on 2011-02-21
```
find /var/www -type d -print0 |xargs -0 chmod 755
```

This will recursively search your directory tree (starting at the /var/www directory) and chmod 755 all directories only.

Similarly, the following will chmod all files only (and ignore the directories):

```
find /var/www -type f -print0 |xargs -0 chmod 644
```

That should work.

---

### Post by shairozan on 2011-02-21
Another thing to make sure is that Apache owns whatever directory your files are hosted in. By default, apache will look to /var/www. Thus, you could do
```

sudo chown -R www-data /var/www
```

Replacing /var/www with whatever directory you are using as the document root. Then just restart apache with 

```
sudo /etc/init.d/apache2 restart 
```

and check it

---

