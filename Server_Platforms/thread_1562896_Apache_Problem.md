---
title: "Apache Problem"
date: 2010-08-28
forum: Server Platforms
---

### Post by GoodHumperdink on 2010-08-28
Hello all [IMG]http://www.computerforum.com/images/smilies/smile.gif[/IMG]  I'm trying to get Apache up and running on my computer (which uses the  Ubuntu 10.04 OS). I've been doing this under the guidance of Apache's  own documentation ([http://httpd.apache.org/docs/2.2/install.html](http://httpd.apache.org/docs/2.2/install.html))  and so far I've managed fairly well. However, when I get close to the  very end of the operation - typing "make install" into the terminal so  Apache can create the appropriate directories etc., it says "permission  denied" for creating all the appropriate directories and at the end says  "Error 1". So my question is: "How do I grant Apache permission to  create these directories?". Thanks in advance for any help offered.

---

### Post by 0004tom on 2010-08-28
Try running make install as root

```
sudo make install
```

Apache is in the repos.. you could have installed it with 

```
sudo apt-get install apache2
```

Would have saved the effort in compiling it,

---

### Post by tad1073 on 2010-08-28
you need to do "sudo make install" w/o the quotes

---

### Post by GoodHumperdink on 2010-08-28
> **0004tom said:**
> Try running make install as root

```
sudo make install
```Apache is in the repos.. you could have installed it with 

```
sudo apt-get install apache2
```Would have saved the effort in compiling it,

Thanks for the help 0004tom :) Much appreciated. Also, I have one final problem. After I've done all this, I must test it (as shown in the documentation: [http://httpd.apache.org/docs/2.2/install.html](http://httpd.apache.org/docs/2.2/install.html)), but I'm not sure what to insert into the terminal. I've tried: ```
/bin/apachect1 -k start
``` ```
bin/apachect1 -k start
``` ```
/usr/local/apache2/bin/apachect1 -k start
``` and ```
/usr/local/apache2 -k start
``` But I always get the same message: "No such file or directory".

---

### Post by 0004tom on 2010-08-28
What prefix did you use when you ran /oonfigure ?

for example ./configure --prefix=/usr/share/bin

---

### Post by =ChAoS= on 2010-08-28
If its running and your just adding some stuff to test ...
 
As local user => sudo /etc/init.d/apache2 reload
 
As Root you don't need to start with sudo.

---

### Post by GoodHumperdink on 2010-08-28
> **0004tom said:**
> What prefix did you use when you ran /oonfigure ?

for example ./configure --prefix=/usr/share/bin

I just ran "httpd-2.2.16/configure".

---

### Post by 0004tom on 2010-08-28
If you didn't set a location prefix when you configured. Then the documention says it uses the default. The path would then be

```
/usr/local/apache2/bin/apachect1 -k start
```

But you already tried that. All I can think of is if you try and find this apachect1

```
whereis apachect1
locate apachect1
```

---

### Post by GoodHumperdink on 2010-08-28
> **0004tom said:**
> If you didn't set a location prefix when you configured. Then the documention says it uses the default. The path would then be

```
/usr/local/apache2/bin/apachect1 -k start
```But you already tried that. All I can think of is if you try and find this apachect1

```
whereis apachect1
locate apachect1
```

No luck I'm afraid. But I'll keep trying.

---

### Post by Lars Noodén on 2010-08-28
Make sure your configuration has correct syntax:

```

/etc/init.d/apache2 configtest 

```

If there are errors, apache won't load.  Also, if you are using ports http (80) and https (443) then you will need to run the scripts as root:


```

/etc/init.d/apache2 configtest && sudo /etc/init.d/apache2 graceful

```


That's the old way, with init.d.   upstart is a little different.  

You can allow some or all of the following to a group of admins via sudoers:

```

# in /etc/sudoers

%webmasters ALL=(ALL) PASSWD: /usr/bin/nano /etc/apache2/sites-available/*

%webmasters ALL=(ALL) PASSWD: /usr/sbin/a2enmod, /usr/sbin/a2dismod, \
  /usr/sbin/a2ensite, /usr/sbin/a2dissite, /usr/sbin/apache2ctl, \
  /etc/init.d/apache2

```

---

