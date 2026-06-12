---
title: "Why Can't I Make Apache2 Custom Error Files?"
date: 2007-03-04
forum: Server Platforms
---

### Post by zds on 2007-03-04
I can't seem to get rid of the stock 403 error messages in apache2. I've gone so far as to rename the error directory and remove that section of the config file, but I still get the stock message.

My real problem with it is all the system data served at the bottom:

**Apache/2.0.55 (Ubuntu) DAV/2 mod_ssl/2.0.55 OpenSSL/0.9.8a Server at xxxxx Port xxxxx**

I tried editing/getting rid of the include files but that didn't work either. Anyone have any suggestions?

Thanks!

---

### Post by kidders on 2007-03-04
Hi there,

That text doesn't tell people much more than they already know.

For instance, my Apache includes **Server: Apache/2.0.55 (Ubuntu) PHP/5.1.6** and **X-Powered-By: PHP/5.1.6** in the HTTP response headers to virtually every request. Naturally, any user seeing the message you mention will already know the hostname and port number, so there is little to be gained by removing the text from ErrorDocument footers.

Is there a particular reason you want to try to hide this information?

---

### Post by jtc on 2007-03-04
That part of the error message (or any other generated page for that matter) is controlled by the [ServerTokens]("http://httpd.apache.org/docs/2.0/mod/core.html#servertokens") directive.

---

