---
title: "[SOLVED] PHPmyAdmin install config misstake."
date: 2008-05-30
forum: Server Platforms
---

### Post by BMOE on 2008-05-30
Hello.

Im quite new with ubuntu and linux, started to use it for about 6 month ago and have used as my desktop OS on one of my computers.
Now im trying to setup a server and when I was installing phpmyadmin under the auto config option I accidently shose apache instead of apache2. How can I fix this?
I tryed removing phpmyadmin with sudo apt-get remove phpmyadmin, and then installing it again but then I did not get to chose.
Can you help me?

/MK

---

### Post by quelx on 2008-05-30
reinstall phpmyadmin and try ```
sudo dpkg-reconfigure phpmyadmin
```

if that doesn't work then try ```
sudo apt-get --purge remove phpmyadmin
```
then reinstall, if that doesn't work I'm willing to bet it doesn't matter and do ```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
``` and restart apache ```
sudo /etc/init.d/apache reload
```

---

### Post by BMOE on 2008-05-31
Thank you very much.

This line did it for me. 
```
sudo dpkg-reconfigure phpmyadmin
```

Damn I got a long way to go :)

---

