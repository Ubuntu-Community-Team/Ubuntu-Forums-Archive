---
title: "Running Apache on localhost"
date: 2012-07-22
forum: Security
---

### Post by afton on 2012-07-22
I'm testing MediaWiki on my computer so I'm running the 
usual Apache, MySQL, and PHP.

Would this somehow be accessible from outside?

Is there any precaution that I should take?

---

### Post by CharlesA on 2012-07-22
By default, apache listens on the external interface. From what I can tell mysqld only listens on localhost.

You can either firewall Apache or just tell it to listen on localhost, which would probably be easier:

[http://ubuntuforums.org/showpost.php?p=6550756&postcount=5](http://ubuntuforums.org/showpost.php?p=6550756&postcount=5)

After you change that setting restart the apache2 service:

```
sudo service apache2 restart
```

---

### Post by afton on 2012-07-22
Thanks Charles! :)

---

