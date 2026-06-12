---
title: "Unable to Run PHP Server"
date: 2011-02-18
forum: Server Platforms
---

### Post by zzzliperzzz on 2011-02-18
Hello,

I want to ask for help for this problem:
I was running an Apache Server not on its default place. Now, I don't know how to run or configure PHP to bind with my Apache Server. The Apache Server works but it does not interpret the PHP script code.

Any help is much appreciated.
Thanks.;)

---

### Post by rudelgurke on 2011-02-18
And how you installed PHP ? Which package you've choosen ?

---

### Post by zzzliperzzz on 2011-02-19
I downloaded the Apache Server from the httpd site. It has a tar.gz extension. I extracted it and installed to my home folder.
Now I downloaded the PHP using ```
sudo apt-get install php5
```. I tried running a php file but it only shows the php code. It does not interpret it.

---

### Post by Philio on 2011-02-19
You need to enable mod_php in the Apache config file.
You'll probably need to add some mime types for any php extensions you want to use too.

---

### Post by zzzliperzzz on 2011-02-19
> **Philio said:**
> You need to enable mod_php in the Apache config file.
You'll probably need to add some mime types for any php extensions you want to use too.


How can I enable the mod_php and how to add mime types for php extensions?
Anyway, thanks for the help. :D

---

