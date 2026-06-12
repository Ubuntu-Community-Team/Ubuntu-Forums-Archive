---
title: "Where is mod_auth_ldap for apache2 in gutsy?"
date: 2007-12-21
forum: Server Platforms
---

### Post by tavasti on 2007-12-21
Where is mod_auth_ldap for apache2? 

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=mod_auth_ldap&searchmode=searchword&case=insensitive&version=gutsy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=mod_auth_ldap&searchmode=searchword&case=insensitive&version=gutsy&arch=i386)

---

### Post by tavasti on 2007-12-21
In gutsy apache2 is apache 2.2, and functionality is in mod_authnz_ldap

---

### Post by FakeOutdoorsman on 2007-12-21
You may already have the module and just need to enable it:
```
sudo a2enmod authnz_ldap
```

Now restart Apache:
```
sudo /etc/init.d/apache2 force-reload
```

---

