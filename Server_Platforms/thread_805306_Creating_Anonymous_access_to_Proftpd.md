---
title: "Creating Anonymous access to Proftpd"
date: 2008-05-23
forum: Server Platforms
---

### Post by guitarman on 2008-05-23
Hi all,
I just configured my Ubuntu 8.04 server with Proftpd and it works great.  I am able to ftp to it on the local lan as well as from my public IP address provided by my ISP.  I created a firewall rule in my router that sends all ftp traffic to this server.  
Got one question though:  Currently I can only access it with my username and password but Proftp currently disables Anonymous access into a public folder which is what I want to achieve.  I looked at the proftpd.conf file but am not sure what to uncomment out or add to enable anonymous.  I do not want to mess up the current running config.

Once I modify this config file do I need to create a Anonymous user account and create a "public" directory under that user's home so that users from the internet can upload/download file to?

thanks !

---

### Post by K.Mandla on 2008-05-29
Moved to Server Platforms.

---

### Post by The Devil Is A Squirrel on 2008-05-29
Maybe this helps: [http://ubuntuforums.org/showthread.php?t=810766](http://ubuntuforums.org/showthread.php?t=810766)

---

### Post by guitarman on 2008-05-29
Thanks let me try this and see if it works for me.

---

