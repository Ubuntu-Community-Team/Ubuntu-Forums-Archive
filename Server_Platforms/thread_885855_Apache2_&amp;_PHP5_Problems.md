---
title: "Apache2 &amp; PHP5 Problems"
date: 2008-08-10
forum: Server Platforms
---

### Post by NES Player on 2008-08-10
So I have installed the LAMP stack using sudo in the Terminal. I have done this same thing several times prior to the Hardy release and it worked fine. But now that I installed Hardy and installed the LAMP, Apache2 seems to have problems communicating with PHP5. Instead of executing PHP files, I get a dialog box asking me to open or save to disk. Anyone had this problem and know how to repair this? Please help. Thanks in advance. :KS

---

### Post by kaivalagi on 2008-08-10
> **NES Player said:**
> So I have installed the LAMP stack using sudo in the Terminal. I have done this same thing several times prior to the Hardy release and it worked fine. But now that I installed Hardy and installed the LAMP, Apache2 seems to have problems communicating with PHP5. Instead of executing PHP files, I get a dialog box asking me to open or save to disk. Anyone had this problem and know how to repair this? Please help. Thanks in advance. :KS

You might need to "enable" the php5 mod in apache2

Try running this:

```
sudo a2enmod php5
```

You might also need to reload and/or restart apache afterwards, you can do this with:

```
sudo /etc/init.d/apache2 force-reload
```

and

```
sudo /etc/init.d/apache2 restart
```

Hope that helps

---

### Post by y@w on 2008-08-10
Do you have the php module installed for apache? Just run 'sudo apt-get install libapache2-mod-php5' (assuming you're using php5 on apache2).

---

### Post by NES Player on 2008-08-10
Oh I found the real problem, it appeared I was using the [http://localhost/](http://localhost/) domain. I used 127.0.0.1 and it worked. I guess I found out that PHP doesn't work on localhost, at least not on my computer, I am running a fresh copy of Ubuntu.

Thanks for trying to help me though :D

---

### Post by kaivalagi on 2008-08-10
> **NES Player said:**
> Oh I found the real problem, it appeared I was using the [http://localhost/](http://localhost/) domain. I used 127.0.0.1 and it worked. I guess I found out that PHP doesn't work on localhost, at least not on my computer, I am running a fresh copy of Ubuntu.

Thanks for trying to help me though :D

Please mark the thread as solved

Thanks

---

