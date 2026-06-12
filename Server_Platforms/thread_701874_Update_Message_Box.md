---
title: "Update Message Box"
date: 2008-02-19
forum: Server Platforms
---

### Post by mattc908 on 2008-02-19
How would I set something up on a website hosted by the server, were I can implement a text box that can be update by not updating the actual page it self, so I dont have to continually update the actual page rather some other form be able to update current news, and dates of certain events. If you get what Im trying to say.

---

### Post by erikx on 2008-02-20
I think that you should have a look in to Server Side Includes(SSI) [http://httpd.apache.org/docs/1.3/howto/ssi.html](http://httpd.apache.org/docs/1.3/howto/ssi.html)

Just include a text file into your html page. Update text file when needed.
Requiers ssh or ftp access.


Another way is to write some PHP with or without a Database to store your news.

It all depends on what your webserver supports..

---

