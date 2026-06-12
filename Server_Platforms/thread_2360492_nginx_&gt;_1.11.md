---
title: "nginx &gt; 1.11"
date: 2017-05-05
forum: Server Platforms
---

### Post by evertmdc on 2017-05-05
Hello,

I was wondering if anyone had an idea when the stable release of Nginx 1.11 or higher would be planned?
There was some breadcrumb feature added that I would like to test.

[URL="https://www.nginx.com/blog/application-tracing-nginx-plus/"]https://www.nginx.com/blog/application-tracing-nginx-plus/
[/URL]
Also, 14.04 seems to run nginx 1.4.6 and 16.04 runs 1.10.0
I assume I need to reinstall my server to 16.04 to be able to upgrade?

Best regards,
Evert

---

### Post by TheFu on 2017-05-05
As you know.

[https://launchpad.net/~nginx/+archive/ubuntu/stable](https://launchpad.net/~nginx/+archive/ubuntu/stable) shows that 1.10.1 stable is available in that PPA.  That is where I'd watch for it.  In the meantime, you can grab the source and compile it yourself. Just be certain to re-grab it, recompile, re-install and patch constantly. Maintenance is your responsibility with source installations and bugs are found all the time.

Here's a patched, stock, 16.04 box built a few weeks ago:
```
$ dpkg -l|grep nginx
ii  nginx                              1.10.0-0ubuntu0.16.04.4                    all          small, powerful, scalable web/proxy server
ii  nginx-common                       1.10.0-0ubuntu0.16.04.4                    all          small, powerful, scalable web/proxy server - common files
ii  nginx-extras                       1.10.0-0ubuntu0.16.04.4                    amd64        nginx web/proxy server (extended version)

``` It is replacing a 12.04 system that has been running for 4+ yrs here. I'm not using the PPA, but might now that I've looked at it.

I haven't been watching nginx security too closely. Are there important security fixes that haven't been back-ported to 1.10.0?  Don't forget that the main goal of any LTS release is system stability. We want the APIs and features to be static throughout the life of any LTS distro.  New is the enemy of stable.

---

