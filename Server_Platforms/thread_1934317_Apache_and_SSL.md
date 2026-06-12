---
title: "Apache and SSL"
date: 2012-03-01
forum: Server Platforms
---

### Post by musclemeth on 2012-03-01
I am needing help regarding SSL and redirects in htaccess

I have an SSL certificate good for [www.mydomain.com](www.mydomain.com) however it does not work for mydomain.com it requires the "www" prefix.

Is there any way to redirect the following:

From

[https://mydomain.com](https://mydomain.com)

To

[https://www.mydomain.com](https://www.mydomain.com)

thanks

---

### Post by SeijiSensei on 2012-03-02
I don't think so.  There would have to be a certificate for example.com to authenticate the redirect virtual host.  Generally speaking you're limited to the exact name that is registered unless you buy a "wildcard" certificate like *.example.com.

---

### Post by hawkmage on 2012-03-02
Also you can define a "Subject Alternate Name" when you generate the CSR.

---

