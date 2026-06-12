---
title: "mod_proxy requests are failing in apache(ews) instance"
date: 2012-04-16
forum: Server Platforms
---

### Post by bharathreddy86 on 2012-04-16
Hi,

The mod_proxy requests are failing when we try to remove white spaces with mod_trim module.
Here  mod_trim is working fine with/without mod_proxy but mod_proxy requests  are failing and mod_trim module is meant for removing white spaces from a  page.

We had configured mod_proxy and mod_trim as below:

httpd.conf
#LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
#LoadModule proxy_ftp_module modules/mod_proxy_ftp.so
#LoadModule proxy_connect_module modules/mod_proxy_connect.


# add filtering--mod_proxy
FilterProvider trim-filter TRIM resp=Content-Type $text/css
FilterProvider trim-filter TRIM resp=Content-Type $text/js
FilterProvider trim-filter TRIM resp=Content-Type $text/js
FilterProvider trim-filter TRIM resp=Content-Type $text/htm
FilterChain trim-filter

http-module.conf:
#To remove white spaces--mod_trim
LoadModule filter_module modules/mod_filter.so
LoadModule trim_module modules/mod_trim.so

Appreciate for quick response and help us.

Thanks
Bharatth

---

