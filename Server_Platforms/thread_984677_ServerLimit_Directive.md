---
title: "ServerLimit Directive"
date: 2008-11-16
forum: Server Platforms
---

### Post by jamesrfla on 2008-11-16
I am trying to allow apache2 to allow more client support. It can support up to 300 clients but no more. I went hear [http://httpd.apache.org/docs/2.2/mod/mpm_common.html#serverlimit](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#serverlimit) I went to /etc/apache2/apache2.conf but wasn't sure were to put ServerLimit 4000 and what else to change. Any Ideas? #apache on free node gave me no help.

---

### Post by Philio on 2008-11-16
This is all well and good however if you have 4000 connections and only 20 Apache processes then you will have 3880 requests queued!!!

There are a few config options to control number of processes, here are some links to the docs:

MaxClients [http://httpd.apache.org/docs/2.2/mod/mpm_common.html#maxclients](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#maxclients)

StartServers [http://httpd.apache.org/docs/2.2/mod/mpm_common.html#startservers](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#startservers)

MinSpareServers [http://httpd.apache.org/docs/2.2/mod/prefork.html#minspareservers](http://httpd.apache.org/docs/2.2/mod/prefork.html#minspareservers)

MaxSpareServers [http://httpd.apache.org/docs/2.2/mod/prefork.html#maxspareservers](http://httpd.apache.org/docs/2.2/mod/prefork.html#maxspareservers)

Depending on the content your serving, you can use MPM worker rather than MPM prefork, which uses multiple threads rather than multiple processes and is faster in some situations.

Remember though as much as you can tweak Apache your still limited by the processing power of the server and eventually you'll reach a point (if you have a lot of traffic) that you will need additional hardware, either load balancing additional web servers, upgrading your existing machine or perhaps serving static and dynamic content from separate machines.

---

### Post by jamesrfla on 2008-11-16
I need to get at least 3000 requests. I am benchmarking apache2. It works in Windows Server 2008 Web server edition but not on Ubuntu server edition with apache2. The people in #apache gave me those links but they confused me. I know I have to add the syntax in the /etc/apache2/apache2.conf but where? What syntax do I have to add?

---

### Post by narco3000 on 2008-11-17
In the apache2.conf:

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#
ServerLimit 500


:)

---

### Post by jamesrfla on 2008-11-17
I went ahead and added that to my config file and stopped and started apache2 but no luck. I went ahead and reformatted and tried benchmarking the default apache2 web page the It works!! one. I was able to benchmark it up to 1000 clients without any config to apache2.conf. So I went ahead and put back the web page I was using as a benchmark and I wasn't able to go that high. Only up to 350 clients. I went hear [http://www.debuntu.org/book/export/html/91](http://www.debuntu.org/book/export/html/91) and changed it and added ServerLimit 1000 but still no luck. I also turned off my firewall but that didn't help. Any other ideas?

---

