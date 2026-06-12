---
title: "Cannot access phpmyadmin login page"
date: 2014-08-18
forum: Server Platforms
---

### Post by filipo2 on 2014-08-18
I have just installed phpmyadmin on my server and have tried to login with [http://myserverurl/phpmyadmin](http://myserverurl/phpmyadmin) and received a 404 not found error.

What have I done wrong?

---

### Post by steeldriver on 2014-08-18
can you access a basic webserver index page i.e. http://myserverurl

---

### Post by filipo2 on 2014-08-19
> **steeldriver said:**
> can you access a basic webserver index page i.e. [http://myserverurl](http://myserverurl)

Sorry for the delay, I have to get up at 3.00am for work so I was in bed when you posted.

Yes, at the moment I get the Apache index page. (No content loaded yet).

Philip

---

### Post by nerdtron on 2014-08-19
What is the contents of the /var/www folder?

---

### Post by filipo2 on 2014-08-19
> **nerdtron said:**
> What is the contents of the /var/www folder?

I have a html folder wich contains index.html.

---

### Post by ubudog on 2014-08-19
See if this helps (from [http://stackoverflow.com/questions/6893799/phpmyadmin-is-not-working-after-i-installed-it](http://stackoverflow.com/questions/6893799/phpmyadmin-is-not-working-after-i-installed-it)):
Add this line to /etc/apache2/apache2.conf:
```
Include /etc/phpmyadmin/apache.conf
```

Open /etc/phpmyadmin/apache.conf and comment (#) out this line:
```
Include /etc/phpmyadmin/apache.conf
```

Restart Apache:
```
sudo service apache2 restart
```

---

### Post by filipo2 on 2014-08-20
> **ubudog said:**
> See if this helps (from [http://stackoverflow.com/questions/6893799/phpmyadmin-is-not-working-after-i-installed-it](http://stackoverflow.com/questions/6893799/phpmyadmin-is-not-working-after-i-installed-it)):
Add this line to /etc/apache2/apache2.conf:
```
Include /etc/phpmyadmin/apache.conf
```

Open /etc/phpmyadmin/apache.conf and comment (#) out this line:
```
Include /etc/phpmyadmin/apache.conf
```

Restart Apache:
```
sudo service apache2 restart
```

That sorted it - Thank you very much. I didn't have to comment out the line in /etc/phpmyadmin/apache.conf as it wasn't  there in the first place.

I have a couple of installation errors which I'm going to look at now.

Philip

---

