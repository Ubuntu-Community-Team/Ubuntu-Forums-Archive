---
title: "Apache not letting me host from other folders"
date: 2011-06-03
forum: Server Platforms
---

### Post by DukeBoxer on 2011-06-03
I just did a new install of 11.04 because I got a new ssd and now when I try to host my site from /home/USER/www/ apache says "You don't have permission to access / on this server" 403 Forbidden.  I had the same exact configuration files on my other install of 11.04 and everything worked fine. One thing I did notice is that when apache installed it did not create a www-data group. I also serve a folder for music on another port and I can get to that fine. Any help at all, since I am basically stuck!!

---

### Post by DukeBoxer on 2011-06-03
Actually, the only folder I can host from on port 80 is /var/www

---

### Post by sixcorners on 2011-06-03
So what user account is apache running under? It seems like it's just not able to read from that directory.  You can always check the log:
tail /var/log/apache2/error.log

---

### Post by DukeBoxer on 2011-06-03
Forget it, I'll mark this as SOLVED. My home folder is encrypted and that was the reason why I couldn't host from there. I moved it to my /media/Storage (which is a 1TB HDD, unencrypted) and it works fine. The only way I found this out was from reading the comments on this page

[http://www.cyberciti.biz/faq/apache-403-forbidden-error-and-solution/](http://www.cyberciti.biz/faq/apache-403-forbidden-error-and-solution/)

about a folder being encrypted on Win Vista. Sometimes there is more info in the comments then the post itself!!!

---

