---
title: "ngx_pagespeed"
date: 2020-05-06
forum: Server Platforms
---

### Post by paweltech on 2020-05-06
Hi everyone
I can't install Nginx with the pagespeed module
I launch this script:

```

bash <(curl -f -L -sS https://ngxpagespeed.com/install)      --nginx-version latest

```

```
nginx: [emerg] unknown directive "pagespeed" in /etc/nginx/conf.d/esempio.com.conf:5
```
Thank you

---

### Post by TheFu on 2020-05-07
Which OS and which release of nginx?  Does the version you have support pagespeed?  Last time i looked, it required downloading the source and compiling myself.

---

### Post by paweltech on 2020-05-08
Thank you for your support
After much research I discovered this:

```

nginx -v
nginx version: nginx/1.14.1

```

```

2>&1 nginx -V | tr -- - '\n' | grep _module
http_ssl_module
http_v2_module
http_realip_module
http_addition_module
http_xslt_module=dynamic
http_image_filter_module=dynamic
http_sub_module
http_dav_module
http_flv_module
http_mp4_module
http_gunzip_module
http_gzip_static_module
http_random_index_module
http_secure_link_module
http_degradation_module
http_slice_module
http_stub_status_module
http_perl_module=dynamic
http_auth_request_module
mail_ssl_module
stream_ssl_module


```

but

```

/usr/local/nginx/sbin/nginx -V | tr -- - '\n' | grep _module
nginx version: nginx/1.18.0
configure arguments: --add-module=/root/incubator-pagespeed-ngx-latest-stable

```

In practice I have compiled well, but the correct nginx is not currently active
I think it depends on the init script ... is it possible?
Thank you

---

### Post by TheFu on 2020-05-08
I would only have 1 version of nginx installed, so removing the unwanted, packaged, version seems like a reasonable step.  Of course, you'll probably want to very carefully move all the configs and settings you thought were being used to the /usr/local/ areas.

---

