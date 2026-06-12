---
title: "How to authenticate for my test server"
date: 2010-07-05
forum: Server Platforms
---

### Post by leegold on 2010-07-05
Hi,

I installed LAMP and Drupal onto my Xubuntu 10.04 desktop as a test/development server and to learn. I installed things seperately from Synaptic and it all works well. One thing I see on Xampp (as a security option) and I'd like to implement is a sign-in user/password - As soon as localhost comes up in one's browser Xammp asks for authentication, if OK then you're taken to the Xampp management page - localhost/xampp. Since I'm not using xampp I just get "It works" message on localhost - which is OK. But I'd like it when anyone comes to localhost they must authenticate like xampp. Also I assume if anyone tries to open anywhere under the document root they will also be challenged. But I want only one challenge (per session(?)) - once they authenticate they are "in". I assume that's how Xampp behaves too...

How do I do that?

Thanks.

---

### Post by sjinks on 2010-07-05
[http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

---

