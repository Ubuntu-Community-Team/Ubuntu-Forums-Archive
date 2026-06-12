---
title: "looking for information on webserver"
date: 2009-10-01
forum: Server Platforms
---

### Post by tontaloj on 2009-10-01
I want to make a web server so i can access my files from any room in the house in web base form...I have apache2 and php5 setup already. any help in the right direction would be most appreciated.


Thanks

J

---

### Post by cyrusthevirus on 2009-10-01
you can create an alias in your apache default site configuration (/etc/apache2/sites-available/default) that points to the folder with the files you wish to share in your  like this:

i. edit the file: /etc/apache2/sites-available/default using your favorite text editor.

```

sudo gedit /etc/apache2/sites-available/default
or
sudo nano /etc/apache2/sites-available/default

```ii. add the alias configuration at the end of the file

```

Alias /files/ "/path/to/files/"
<Directory /path/to/files/>
       Options Indexes 
       Order allow,deny
       allow from all
</Directory>

```iii. restart apache.
```

sudo /etc/init.d/apache2 restart

```iv. You can now browse to your files from a web browser like this:
```

http://<your ip address >/files/

```make sure you include the slash(/) at the end of the url.

You can read more about configuring apache here: [https://help.ubuntu.com/9.04/serverguide/C/httpd.html](https://help.ubuntu.com/9.04/serverguide/C/httpd.html)

I hope this helps.

---

### Post by tontaloj on 2009-10-02
Thats exactly what i wanted to do. Thanks a lot for pointing me in the right direction.

J

---

### Post by openfly on 2009-10-02
You sure samba isn't what you are looking for?

And if you are hell bent on web... you may want to look into web dav support.

---

### Post by tontaloj on 2009-10-02
I have Samba setup to share files between my computers right now.  I want to create a web interface to search for file on my network from a far as well. For example, let say i wanted to find a particular .pdf in the folder out of a 1000 .pdf files. I don't want to scroll through them all. i would like to search for a keyword in the document to find it.


Thanks,

J

---

### Post by openfly on 2009-10-02
So like a search engine of sorts.

---

### Post by tontaloj on 2009-10-02
exactly a search engine


J

---

