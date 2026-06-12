---
title: "Roundcube Problems!"
date: 2011-04-08
forum: Server Platforms
---

### Post by thunderclap on 2011-04-08
After installing roundcube apache fails to load. I can't stop it, start it, remove it, install it... nothing. I try to uninstall roundcube and get an error about roundcube-core.

How do I get rid of roundcube completely to get my site back up? Help!

---

### Post by falko on 2011-04-08
Are there any errors in Apache's error log?

To completely uninstall a package, you can run
```
apt-get purge *package*
```

---

### Post by thunderclap on 2011-04-08
I tried purge but get the same error.

Error opening terminal: vt-100.
Debconf: dialog output the above errors, giving up!
Dpkg: error processing roundcube-core (--configure)
Sub-process installed post-installation script returned error exit status 255
Errors were encountered while processing
Roundcube-core

---

### Post by thunderclap on 2011-04-08
I'm starting to think vt-100 is the problem as I can't open the editor to look at the apache log. But I don't know how to resolve the problem.

---

### Post by thunderclap on 2011-04-08
I've manually removed the roundcube files and that seems to have resolved installation and uninstall problems. But apache2 still fails on start.  No error message there, and I can't get into the log file because I get the vt100 terminal error.

---

### Post by thunderclap on 2011-04-08
Got it back up.

---

### Post by elico on 2011-04-08
how?

---

