---
title: "Parent dir owner set to www-data, php mkdir still not working..."
date: 2009-09-29
forum: Server Platforms
---

### Post by woodsonoversoul on 2009-09-29
Hello all, I'm running php5 on a xampp server and I'm getting a permission denied error when I try to use mkdir(). For example, if the script using mkdir() is in /opt/lammp/htdocs/mainFolder/callingFolder

And the location it's attempting to create a new directory is:
/opt/lammp/htdocs/mainFolder/secFolder/thirdFolder

and lampp, callingFolder, mainFolder, htdocs, secFolder, and thirdFolder all have ownerships set to www-data with create/delete privileges. Do I need to set opt to be owned by www-data? that seems wrong, but what else?

---

### Post by CyberJack on 2009-09-29
What happens when to become www-data (su - www-data) and try to create the directory manualy?

---

### Post by woodsonoversoul on 2009-09-29
I get an authentication error after entering my password. Where would I find/set/change the password for www-data?

---

### Post by CyberJack on 2009-09-30
First become the root user, then type "su - www-data".
Then you don't need a password.

---

### Post by woodsonoversoul on 2009-09-30
I set a password for www-data (using bernied's instructions from this post: [http://ubuntuforums.org/showthread.php?t=330058](http://ubuntuforums.org/showthread.php?t=330058) ). Then when I tried su - www-data it adds the user and set www-data as current user. From there I can mkdir no problem...

---

### Post by woodsonoversoul on 2009-09-30
Tried to delete this post but can't find the option

---

### Post by woodsonoversoul on 2009-09-30
Anyone else have an idea why I keep getting permission denied errors?

---

### Post by woodsonoversoul on 2009-10-01
Bump for the day crew...

---

