---
title: "Apache behind proxy getting refused when fetching XML"
date: 2008-05-13
forum: Server Platforms
---

### Post by ogryn on 2008-05-13
Hi,

I'm currently trying to setup a webserver behind a company proxy/firewall. The machine can view pages normally and even wget the same file from the terminal that I'm trying to get from PHP, but when run as the webserver I'm getting:

Warning (2): file_get_contents([http://feeds.bbc.co.uk/weather/feeds/rss/obs/id/3438.xml](http://feeds.bbc.co.uk/weather/feeds/rss/obs/id/3438.xml)) [function.file-get-contents]: failed to open stream: Connection refused

Is there something special I need setting up in Apache to get it to recognise the proxy it needs to connect through? I have the open url setting to ON in php.ini, and Safe Mode off.

Thanks,
Dave :)

---

### Post by beniwtv on 2008-05-13
Hey Dave,

Do you need to specify a proxy server in your web browser to get it to display pages, or is this a transparent proxy?

If you need to specify a proxy, then you also need to specify a proxy for PHP. However, I do not know if it's possible to do it with file_get_contents.

You can do it with curl, however (by using the CURLOPT_PROXY attribute):
[http://www.php.net/curl](http://www.php.net/curl)

Quick guide to curl:
[http://www.decodephp.com/2007/02/26/php-curl-insight-and-a-php-alternative-example/](http://www.decodephp.com/2007/02/26/php-curl-insight-and-a-php-alternative-example/)

Cheers.

---

### Post by ogryn on 2008-05-13
Hi,

Yup, I do have to specify a proxy on a specific port in both Gnome and Firefox. 

Strangely I don't have this issue on CentOS. I know Apache is packaged very differently in Debian so I'm wondering if this is a flag in a config or part of mod_proxy or something?

Thanks,

---

