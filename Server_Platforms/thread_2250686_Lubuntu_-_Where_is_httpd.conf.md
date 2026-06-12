---
title: "Lubuntu - Where is httpd.conf"
date: 2014-10-30
forum: Server Platforms
---

### Post by guit4eva on 2014-10-30
Where would I find httpd.conf? And also, how would I edit PDO as in this thread:

[http://serverfault.com/questions/66347/why-is-the-response-on-localhost-so-slow/444338#444338](http://serverfault.com/questions/66347/why-is-the-response-on-localhost-so-slow/444338#444338)

Thanks so much!

---

### Post by slickymaster on 2014-10-30
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by mcduck on 2014-10-30
*/etc/apache2/apache2.conf* is the file you are looking for.

The PDO stuff is about a a coding problem the people in that thread have with their PHP application. May I ask what are you trying to do?

(also the thread is 5 years old, about older Apache version, and Windows rather than Linux)

---

### Post by guit4eva on 2014-10-30
Thank you for your speedy response. I'm basically just trying to speed up my localhost by following the tips in that ServerFault link I posted above. For some reason my localhost is going really slowly - it spends a lot of time "waiting for localhost".

---

### Post by mcduck on 2014-10-30
IN that case the question is *what* spends lots of time waiting for localhost?

Localhost just means anything on your own computer. That thread is specifically about Apache web server being slow to serve pages to the same machine, not a generic tip for speeding up your PC or fixing every possible application that uses network protocols inside your own computer...

---

