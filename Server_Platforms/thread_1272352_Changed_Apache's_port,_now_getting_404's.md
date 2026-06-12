---
title: "Changed Apache's port, now getting 404's"
date: 2009-09-22
forum: Server Platforms
---

### Post by apetickler on 2009-09-22
I changed the port specified in the "Listen" line and restarted Apache. Now, as expected, I don't find my machine at all on port 80, but when I point a browser to the new port, I get a 404 error.

I've Googled until I was blue in the face and haven't found any reference to this problem. Does anyone know what I might have done wrong? Thanks.

---

### Post by wojox on 2009-09-22
Did you change the port # in /etc/apache2/sites-available/default ?

---

### Post by apetickler on 2009-09-22
I surely did not. It's working now. Thanks a million!

---

