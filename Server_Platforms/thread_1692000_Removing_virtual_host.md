---
title: "Removing virtual host"
date: 2011-02-20
forum: Server Platforms
---

### Post by whosherox on 2011-02-20
How do i remove a virtual host? i created it and i need to remove it from site-available

---

### Post by volkswagner on 2011-02-21
To remove the host file just delete it.

If you just want to dissable the site, use

```
sudo a2dissite sitename
```

Restart apache2
```
sudo /etc/init.d/apache2 reload
```

Again to remove (delete)it completely from the system,
```
sudo rm /etc/apache2/sites-available/sitename
```

I would also disable it first before deleting the file.

---

### Post by mciverza on 2011-02-22
> **volkswagner said:**
> To remove the host file just delete it.

If you just want to dissable the site, use

```
sudo a2dissite sitename
```

Restart apache2
```
sudo /etc/init.d/apache2 reload
```

Again to remove (delete)it completely from the system,
```
sudo rm /etc/apache2/sites-available/sitename
```

I would also disable it first before deleting the file.

+1 
excellent advice

---

### Post by sangramanand on 2012-12-14
Thanks...

---

