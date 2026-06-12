---
title: "Trying to run apache on port 85 but don't know where the /www folder should be"
date: 2009-04-02
forum: Server Platforms
---

### Post by pluckypigeon on 2009-04-02
I have apache running on port 80 and port 85 

[http://localhost:80](http://localhost:80) runs the index file fine but [http://localhost:85](http://localhost:85) says the file is not found:

```

Not Found

The requested URL / was not found on this server.
Apache/2.2.11 (Ubuntu) Server at localhost Port 85

```

Could someone help me shed some light on this? 

Thanks in advanced!!

---

### Post by superprash2003 on 2009-04-02
check out step 3 [http://www.prash-babu.com/2008/05/how-to-install-apache-and-setup.html](http://www.prash-babu.com/2008/05/how-to-install-apache-and-setup.html)

---

### Post by jigsaws on 2009-04-02
You depends on configuration. You can find configuration files at /etc/apache2/

---

### Post by pluckypigeon on 2009-04-02
> **superprash2003 said:**
> check out step 3 [http://www.prash-babu.com/2008/05/how-to-install-apache-and-setup.html](http://www.prash-babu.com/2008/05/how-to-install-apache-and-setup.html)

Your blog helped me but step 3 wasn't the problem, I had done that bit.

I had to add <VirtualHost *:85> to /etc/apache2/sites-available/default

Thank you very much for your help!!

---

