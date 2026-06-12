---
title: "ubuntu server via amazon ec 2, problems visualizing picture"
date: 2011-06-06
forum: Ubuntu Cloud and Juju
---

### Post by acnow on 2011-06-06
Ok.. I have a php application on amzon ec2 (via rightscale) and right now we are running the code with limit access by ip address on live server..
the problem we are facing is that all the pictures on local server are not showing on live server once live server is updated via ftp...--it should not be a code problem since it runs fine in a local server where pictures are showing..
Please, any clue where I have to look or settings that need to be changed in the server??
thanks in advance,
AC

---

### Post by kim0 on 2011-06-08
Try the apache logs for the missing pictures, it might be looking for the pictures in the wrong location or something

Otherwise, contact the developers or community of the application you're running. They should be able to better help I guess

---

