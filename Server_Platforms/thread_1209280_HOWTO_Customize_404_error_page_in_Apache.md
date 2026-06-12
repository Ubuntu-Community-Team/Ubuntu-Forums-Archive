---
title: "HOWTO: Customize 404 error page in Apache"
date: 2009-07-10
forum: Server Platforms
---

### Post by JohnLau on 2009-07-10
):P I have written a guide on how to customize the 404 page in Apache in my blog. I think it might be helpful too for you guys so I am going to paste the guide here.

1. You have to make sure that you have turned the rewrite module on in apache

You can follow the steps on [this post]("http://compustorm.no-ip.org/2009/07/apache-and-wordpress-permalink-on-ubunutu/") to enable it

2. Create _.htaccess_ in _/var/www_ or edit it if you already have one

3. Add the following line in the post
```
ErrorDocument 404 /the-filename-of-your-customized-404-page
```

In my case, it is
```
ErrorDocument 404 /404.php
```

That’s done!

[Please continue if you want to use the 404 page provided by your wordpress theme]("http://compustorm.no-ip.org/2009/07/customize-404-page-in-apache/")

Hope this can help you.
John

---

### Post by firedragoneater on 2011-07-15
Great. Thanks!

---

