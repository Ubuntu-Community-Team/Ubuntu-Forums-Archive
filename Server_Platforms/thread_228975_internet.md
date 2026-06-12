---
title: "internet"
date: 2006-08-03
forum: Server Platforms
---

### Post by jkblitz on 2006-08-03
hi iv psted some content in side apache and i can view it in my network but i cant view it out of my network by useing my ip

im useing a wrt54gs

---

### Post by makenaa on 2006-08-03
If you are behind a router, (which is very smart due to security reasons), you must tell your router to open port 80, and foreward that port to the local ip of your webserver. Instructions on how to do this differ, but it should be easy to find in your router manual. (if you are behind one.)

Also, you must place your files in the apache folder var/www/.
Lastly, if you plan to setup these files to function via a domain, you must change the sources.list file in the /etc/apache/sites-available/ directory. You may also want to double check this file, even if you are not using a domain.

Hope this helps ;) ,
makenaa

---

### Post by jkblitz on 2006-08-03
iv gone into my router and i did the port forwording it still dident work any more ideas?

---

### Post by jkblitz on 2006-08-04
any one got what i should do now?

---

### Post by Sam on 2006-08-05
Check your firewall settings with [this page](https://www.grc.com/x/ne.dll?bh0bkyd2) (click "Proceed" then "All service port" to run the test). Port 80 should be red (open). If it's the case, check that you haven't any directive like:
```
Order allow,deny
Deny from all
Allow from 192.168.1
```

---

