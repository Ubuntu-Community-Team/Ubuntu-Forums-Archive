---
title: "Apache2 problems DocumentRoot error"
date: 2012-10-01
forum: Server Platforms
---

### Post by CptSqueel on 2012-10-01
I'm getting this interesting errors, have tried google it but with no luck.

Warning: DocumentRoot [/var/www/test.com/html/] Does not exist
Warning: DocumentRoot [/var/www/test.com/html/] Does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

I have looked in both of the conf files that contains the search-way but it looks alright.

Any help would be nice :)

Regards
Sebbe

---

### Post by Bachstelze on 2012-10-01
Well, does the directory exist?

---

### Post by CptSqueel on 2012-10-01
yes, I have used 
mkdir -p /var/www/test.com/html

and I can find the dir and so on but when i try to restart apache it gives me these errors.

---

### Post by volkswagner on 2012-10-01
What are the permissions?  Is that directory readable by apache?  Also check for capital letters as it is case sensitive.

---

### Post by CptSqueel on 2012-10-01
Hum, I did notice that I cant rename or delete the file. Could that be the problem?

---

### Post by sandyd on 2012-10-01
make sure the folders have the correct permissions.
Apache runs under www-data:www-data, so

```
sudo chown -R www-data:www-data /var/www/
``` should sort you out.

---

### Post by SeijiSensei on 2012-10-01
That should be 

```
sudo chown www-data:www-data -R /var/www/
```

---

### Post by CptSqueel on 2012-10-01
I tried to remove the file that the warning vas telling me about and remake it. it took care of it :)
Tnx For all the help, I think I'll need more soon anyway xD

---

### Post by SeijiSensei on 2012-10-03
I'll just add that if you do change the permissions on /var/www so it is owned by www-data, it is imperative that you do not grant write permissions in this directory or any of its subdirectories.  That opens an enormous security hole if your server is ever owned.

A better approach if you intend to author pages as an ordinary user, say "CptSqueel," is to grant full permissions to that user and read privileges to www-data like this:

```

cd /var
sudo chown -R CptSqueel:www-data www 
sudo chmod 755 www
cd www
sudo chmod 644 *
sudo chmod 755 subdir1 subdir2 ...
sudo chmod 644 subdir1/* subdir2/* ...

```

replacing "subdir1", "subdir2", etc., with the names of any directories below /var/www.  If the subdirectories themselves have subdirectories and follow the same procedures as for subdir1, etc.

---

