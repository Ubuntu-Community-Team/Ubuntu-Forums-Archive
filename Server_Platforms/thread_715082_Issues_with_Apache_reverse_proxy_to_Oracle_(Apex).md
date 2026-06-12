---
title: "Issues with Apache reverse proxy to Oracle (Apex)"
date: 2008-03-04
forum: Server Platforms
---

### Post by Gordster on 2008-03-04
Hi All,

I have searched the forums, and learned a ton - but I still haven't been able to solve my issue(s)...

I have a 'host' server running Gutsy - and VMWare server 1.0.4 
2 Unbuntu Gutsy VM's installed
A) is apache2 w/ virtual hosting (3 sites) - all working now thanks to Faulkes
B) is Oracle XE and Apex - working internally (can SQLPlus & Web browser to it)

I am behind a router / firewall.

I can access Oracle and Apex from within my network, but I want to forward certain websites to Apex.
I have added in the proxy stuff as outlined in many posts (but not the mod_rewrite - code to follow), and tested it by forwarding to google - which worked except for images...  But when I try to reverse proxy to Oracle I get problems...
```
        ProxyPass /Test/ http://my.int.ip.addy:8080/apex/
        ProxyPassReverse /Test/ http://my.int.ip.addy:8080/apex/
```

I did put in:
```
        <Directory proxy:http://my.int.ip.addy:8080/apex/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
```
One thing I tried was to change the Oracle port from 8080 to 80, but that started to really get messy.  The listener would still start, but there wasn't an entry for http any more.  Looing into the listener logs showed:
```
Error listening on: (Description=(Address=(Protocol=tcp)(Port=80)(Host=))(Presentation=HTTP)(Session=RAW)) 
```
 but when I change it back to 8080, it shows up again
```
 (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=OracleXE.my_domain.ca)(PORT=8080))(Presentation=HTTP)(Session=RAW))
```
I began to think that I didn't have the correct permissions - as I can use SQL+Plus as my normal user - but not when I sudo.  So I thought maybe I couldn't actually change the listener port using the
```
 exec dbms_xdb.sethttpport('80');
``` in SQLPlus with out being root.

One other thing I'd like to make work - but second to the proxying, is to be able to point a machine INSIDE my network to a URL of one of the sites I have hosted, and have it work.  I get "cannot display webpage' (IE7) and "connectioned timed out" (Firefox).

I can show any and all pertinent info as needed  :-p

Thanks in advance,

Corey

---

### Post by Gordster on 2008-03-06
I have been looking at the error logs for apache, and get the following:
 
```
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 6615 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 6540 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 7359 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 6617 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 6618 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 7393 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 7440 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 7438 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 7394 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 6827 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 6828 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 7439 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] (10)No child processes: cannot send signal 10 to pid 7442 (non-child or already dead)
[Tue Mar 04 04:22:28 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Mar 04 04:22:38 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Tue Mar 04 04:22:44 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/TERST
[Tue Mar 04 04:22:50 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/intl, referer: http://www.ABC.ca/TEST
[Tue Mar 04 04:22:50 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/images, referer: http://www.ABC.ca/TEST
[Tue Mar 04 04:23:12 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/intl, referer: http://www.ABC.ca/TEST
[Tue Mar 04 04:23:26 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/apex
[Tue Mar 04 04:26:43 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to my.internal.ip.33:8080 (ABC-ora1.my-domain.ca) failed
[Tue Mar 04 04:26:43 2008] [error] ap_proxy_connect_backend disabling worker for (ABC-ora1.my-domain.ca.ca)
[Tue Mar 04 05:55:02 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/wpad.dat
[Tue Mar 04 08:46:37 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/wpad.dat
[Tue Mar 04 10:25:01 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Mar 04 10:25:01 2008] [error] [client ::1] File does not exist: /htdocs
[Tue Mar 04 10:25:01 2008] [error] [client ::1] File does not exist: /htdocs
[Tue Mar 04 10:25:01 2008] [error] [client ::1] File does not exist: /htdocs
[Tue Mar 04 10:25:01 2008] [error] [client ::1] File does not exist: /htdocs
[Tue Mar 04 10:25:01 2008] [error] [client ::1] File does not exist: /htdocs
[Tue Mar 04 10:25:01 2008] [error] [client ::1] File does not exist: /htdocs
[Tue Mar 04 10:25:11 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Tue Mar 04 10:28:35 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to my.internal.ip.33:8080 (ABC-ora1.my-domain.ca) failed
[Tue Mar 04 10:28:35 2008] [error] ap_proxy_connect_backend disabling worker for (ABC-ora1.my-domain.ca.ca)
[Tue Mar 04 18:13:05 2008] [error] [client 70.68.24.177] File does not exist: /var/www/DEF/favicon.ico, referer: http://www.DEF.ca/
[Wed Mar 05 03:20:56 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to my.internal.ip.33:8080 (ABC-ora1.my-domain.ca) failed
[Wed Mar 05 03:20:56 2008] [error] ap_proxy_connect_backend disabling worker for (ABC-ora1.my-domain.ca.ca)
[Wed Mar 05 03:43:24 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/my-domain.ca/wpad.dat
[Wed Mar 05 03:58:27 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/my-domain.ca/wpad.dat
[Wed Mar 05 04:58:39 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/my-domain.ca/wpad.dat
[Wed Mar 05 05:14:26 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/my-domain.ca/wpad.dat
[Wed Mar 05 07:03:28 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/wpad.dat
[Wed Mar 05 07:03:28 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/wpad.dat
[Wed Mar 05 07:04:43 2008] [error] [client my.internal.ip.32] File does not exist: /var/www/ABC/wpad.dat
[Wed Mar 05 08:27:03 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to my.internal.ip.33:8080 (ABC-ora1.my-domain.ca.ca) failed
[Wed Mar 05 08:27:03 2008] [error] ap_proxy_connect_backend disabling worker for (ABC-ora1.my-domain.ca.ca)
[Wed Mar 05 15:37:21 2008] [error] [client 69.36.158.34] File does not exist: /var/www/DEF/robots.txt
[Wed Mar 05 22:28:44 2008] [error] [client 69.36.158.32] File does not exist: /var/www/ABC/robots.txt
[Thu Mar 06 02:30:47 2008] [error] [client 69.36.158.38] File does not exist: /var/www/my-domain.ca/robots.txt
[Thu Mar 06 05:12:03 2008] [error] [client 194.72.238.61] File does not exist: /var/www/DEF/cobalt-images
```

So I am thinking my issue is with my router - but I don't want to open port 8080 to the outsie...
It is a cisco PIX 501

Or maybe the issue is with the port change (80 to 8080), and if I was able to switch oracle to also listen on port 80 everything would work...

Anyone have any direction to point me in - cause I just seem to be going in circles...?

Thanks,

Corey

---

