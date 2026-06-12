---
title: "need help from Squid expert (reverse proxy)"
date: 2010-10-20
forum: Server Platforms
---

### Post by jenjohnson on 2010-10-20
I understand a little about squid, but obviously not enough.
here's my problem.

I have an internal server (internal ip address). It has a status page that I need to see from outside.
I don't want to use VPN, as I want to be able to access this page from everhwhere. Cell phone, library, friend's house etc.. And I can't do port forwarding, as this is not a local network, it's in the cloud, and I have limited tools

I figured, I have an server on the same network with Squid (that has an external ip) on it, so I should use that.

I've tried the guides out there, but nothing works. I guess I just don't understand how it's supposed to work.

Here's my understanding. 

Squid listens on port 80, and, as it's also internal, it can access my status page.

so I have my squid.conf like this

http_port 80                            # Port of Squid proxy
httpd_accel_host ip_of_internal_server          # IP address of web server
httpd_accel_port 80                     # Port of web server
httpd_accel_single_host on              # Forward uncached requests to single host
httpd_accel_with_proxy on               #
httpd_accel_uses_host_header off

My issue is, How does this forward to the page I want, which is ip_of_iternal_server/status.html ?
Somehow I need to tell squid that I only want to send it to the status.html page

I also get an error when I start squid that gives
```
Bungled squid.conf line 2: http_port 80
```

---

### Post by SeijiSensei on 2010-10-20
It's probably easier to accomplish this with the Apache webserver.  Run "sudo apt-get install apache2" then read [this page]("http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#forwardreverse") about how to set up a reverse proxy.  Apache will listen for requests on port 80 at one address and forward them to another machine.

Another approach is to use the ancient but reliable [tcpproxy]("http://www.tux.org/pub/sunsite/system/network/tcpproxy-1.1.6.tar.gz") software to send TCP requests for a port on one machine to another machine and optionally a different port as well.

You can also accomplish this task with [iptables rules]("http://www.debian-administration.org/articles/595").

I'm not saying you can't do it with Squid, just that these are easier methods to accomplish the same task.

> Somehow I need to tell squid that I only want to send it to the status.html page

Well, you could either create a directory that contains only status.html, or you could use Apache's [<Files> directive]("http://httpd.apache.org/docs/2.2/mod/core.html#files") on the server to limit access to only the file named "status.html".

---

