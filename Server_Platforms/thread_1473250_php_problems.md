---
title: "php problems"
date: 2010-05-05
forum: Server Platforms
---

### Post by ndaugherty on 2010-05-05
Hi I have apache2 installed along with php5 and mysql5.0

I have installed them by themselves along with just installing the full LAMP install through terminal.

My problem is that I cannot parse php files, it will just download them instead. I did change my apache server to nick/projects (nick is my username)

If i navigate to localhost/index.html it works fine but will not parse the php files I have put there. I also have rails working fine in that folder too using apache2.

---

### Post by mysteron on 2010-05-05
From the terminal, go to:

/etc/apache2/mods-enabled

Are there these symbolic links two files there:

php5.conf -> ../mods-available/php5.conf
php5.load -> ../mods-available/php5.load

then do
```
ls -la ../mods-available/php5.*
```

if the php5 files are there, do:

sudo -s

Type in your sudo admin password.

Do

```
ln -s ../mods-available/php5.conf
ln -s ../mods-available/php5.load
```

After that do:
```
/etc/init.d/apache2 reload
```

type exit to log out of sudo shell mode.


/mysteron

---

### Post by terazen on 2010-05-05
If you installed through apt-get 'sudo a2enmod php5` would enable the modules.  Sounds like you installed from source, but just fyi.

---

### Post by ghost_ryder35 on 2010-05-05
[http://ubuntuforums.org/showthread.php?t=1466591&highlight=php+problem](http://ubuntuforums.org/showthread.php?t=1466591&highlight=php+problem)

---

### Post by ndaugherty on 2010-05-06
Thanks mysteron that worked.

I had done what ghost ryder said last night an it still didn't work. Not sure if you have to do both or not. (incase anyone else reads this)

---

### Post by windependence on 2010-05-06
You should probably mark this thread as solved.

-Tim

---

### Post by Vegan on 2010-05-06
an easier way to get a web server with php working is

```
sudo tasksel lamp
```

its that easy

---

### Post by windependence on 2010-05-06
> **Vegan said:**
> an easier way to get a web server with php working is

```
sudo tasksel lamp
```its that easy
Read the second line of his first post. He already tried that.

-Tim

---

