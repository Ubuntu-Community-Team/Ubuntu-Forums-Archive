---
title: "Webserver setup"
date: 2010-03-30
forum: Server Platforms
---

### Post by Datamac on 2010-03-30
I am stuck at the ending point of setting up a web server to do virtual  hosting for 3 sites.  I have created the individual virtual host files  and think that they are stored in the correct directories.  I am unable  to run a2ensite to finish this step of the process.  Can anyone here  help me understand the last two steps in the process.  I am following  the tutorial at: [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

### Post by Bachstelze on 2010-03-30
> **Datamac said:**
> I am unable  to run a2ensite to finish this step of the process.

What happens when you try?

---

### Post by terazen on 2010-03-30
I think the guide says this, but when you run `sudo a2ensite somefilename` it looks for the filename in /etc/apache2/sites-available/ and creates a link to it in /etc/apache2/sites-enabled/.

After you do that and reload apache the server will look into /etc/apache2/sites-enabled/ and see the new files to read.

With that being said it sounds like you either don't have the files in your sites-available or maybe you aren't spelling the filename correctly.

---

### Post by dudumomo on 2010-03-30
Yes indeed, check the name of your file.

You might want to check my how to: [http://www.freelydifferent.com/self-hosting/lamp-for-linux-apache-mysql-php/](http://www.freelydifferent.com/self-hosting/lamp-for-linux-apache-mysql-php/)

---

### Post by Datamac on 2010-03-30
file names are okay.  I paid great attention to detail in creating the directories and saving the file names.  I get site does not exist!  from the command line interpreter.

---

### Post by terazen on 2010-03-30
If you type `sudo a2ensite abcd` with abcd being the first characters of the filename, will hitting tab autocomplete the filename?

---

### Post by ICEB3AR on 2010-03-30
is it possible that a2ensite does not look for the filename but for the domainname.... i mean:
e.g. in sites-available there is a file website containing
```

<Virtualhost *:80>
  ServerName www.website.org
  ...
</Vritualhost>

```
I'm not completely sure and not able to test, but i would say you have to do 
```
sudo a2ensite www.website.org
# instead of
sudo a2ensite website

```

Just my idea

---

### Post by dudumomo on 2010-03-30
No a2ensite doesn't work like this.
I've just done a new virtualhost a couple of hours ago.

The URL was gallery.freelydifferent.com
and the name of the file, simply "gallery"

a2ensite gallery did good.

---

### Post by Ryan Dwyer on 2010-03-30
> **Datamac said:**
> I paid great attention to detail in creating the directories and saving the file names.

You shouldn't need to create any directories. Are you sure you made them in /etc/apache2/sites-available and not ~/etc/apache2/sites-available?

Running the following command should show a list of your files: ls /etc/apache2/sites-available

---

### Post by Datamac on 2010-03-30
Lots of comments here.  Thanks for the ideas.  I have 4 files in the sites-available directory.  "default and my 3 virtual website config files.  Now, I am getting "permission denied when I run sudo a2ensite filename.  This is driving me nuts to seem to loose permissions and privileges and I more forward.   Again, help!

---

