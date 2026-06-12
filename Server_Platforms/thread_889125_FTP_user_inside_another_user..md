---
title: "FTP user inside another user."
date: 2008-08-13
forum: Server Platforms
---

### Post by maidei on 2008-08-13
what i am trying to achieve is as follows.

I have set-up a website [www.test1.com](www.test1.com)
the directory for [www.test1.com](www.test1.com) is on /var/www/test1

What I need to set now is to have a friend upload(FTP) her photos to my site
but HAVE this friend only access one page where her photos are.

where do i created the directory for her so that she can be able to upload(FTP) her photos,
without changing anything on website.

I tried this
/var/www/test1
mkdir friend
but didn't work.

Thanks

---

### Post by guilly on 2008-08-14
I'm thinking you'll have to modify your proftpd.conf file to allow that user only access to /var/www/test1/friend1

I'm sure there is probably a way in your proftpd.conf file to also redirect that particular user to that folder only as the root folder when she/he logs into your ftp server as well. That way in her eyes that is the only folder on the system on the server.

If you need an example of how to set up the permissions

---

### Post by maidei on 2008-08-16
Thanks heaps Guilly, an example will be much appreciated.

regards

Maidei

---

