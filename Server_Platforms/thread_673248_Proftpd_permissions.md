---
title: "Proftpd permissions"
date: 2008-01-20
forum: Server Platforms
---

### Post by GoldNugget on 2008-01-20
I have a server set up with Apache 2.2.4. I am using Proftpd and was able to log in to the server but I was getting a 'Permission Denied' error and could not overwrite or delete files. I changed the permissions of my /var/www folder to Others: Read/Write as suggested on another forum. It works fine now, but it feels insecure to me. Is there a better way?

---

### Post by smileypaul on 2008-01-20
Excuse my confusion.. but to clarify, you are runing a webserver.. and also proftp on the box so you can ftp into it to upload files... correct?

Make sure in the /etc/proftpd.conf  you have AllowOverwrite Yes  ..

other than that, it is just a permissions thing, add yourself to the proper group, and then remove the others read and write... i guess it all depends on who will be writing to that folder..

you can also restrict this in the proftpd conf file

---

### Post by GoldNugget on 2008-01-20
Yes, I am attempting to upload files to my webserver via proftpd. Thank you for your suggestions.

---

