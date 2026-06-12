---
title: "403 Forbidden Apache2 on Ubuntu Desktop"
date: 2008-09-06
forum: Server Platforms
---

### Post by frmdstryr on 2008-09-06
Hello all, as the title says, I setup an apache2 sever.  However whenever I try to get onto any other page than the index.html (or if i move that it shows a list of the files on the root), It displays a 403 Forbidden message and says I do not have permission to access bla bla bla.  I've been trying two nights now to figure out what it is and can't seem to find the problem. My apache2.conf and sites-available are all default settings. Thanks.

---

### Post by windependence on 2008-09-06
OK try this:

```
sudo chown -R root:root /var/www

sudo chmod -R 755 /var/www

sudo /etc/init.d/apache2 restart 
```

Try and then let us know.

-Tim

---

### Post by frmdstryr on 2008-09-06
Worked!!! Thank you soo much. How would I go about putting password protection on a certain folder?

---

### Post by windependence on 2008-09-06
Easiest way is to use an .htaccess file.

Here is the easy to follow Ubuntu documentation on this:

[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

This will probably help you also:

[http://ubuntu-tutorials.com/2007/10/06/limiting-access-to-websitesdirectories-with-htaccess/](http://ubuntu-tutorials.com/2007/10/06/limiting-access-to-websitesdirectories-with-htaccess/)

Enjoy!

-Tim

---

### Post by gbradley on 2009-07-17
Worked for me! Thanks so much!

---

### Post by mahrizal on 2011-05-03
@[windependence]("http://ubuntuforums.org/member.php?u=291170") :
thank you , it works for me

---

