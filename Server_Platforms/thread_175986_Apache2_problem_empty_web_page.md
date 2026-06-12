---
title: "Apache2 problem: empty web page"
date: 2006-05-14
forum: Server Platforms
---

### Post by linuxone on 2006-05-14
Hi,

I run Ubuntu Server (x86) on all my Internet servers and basicly it runs fine. Unfortunately I have a really mysterious Apache related problem which I can't solve:

One Apache SSL based VirtualHost runs a PHP portal (own development) for a private, closed user group. After login you'll see a specific PHP page depending on your user level.
Mostly everything runs fine. But sometimes you see an empty **blank page** into the main frame after login. The menu bar into a second frame is correctly displayed each time. Logout and login again the same page is seen correctly. This happens on Linux and Windows with different browsers.

This blank page is noticed into the ssl_request.log by this line:

88.138.77.192 SSLv3 DHE-RSA-AES256-SHA "GET /start/trainingseinheiten_8_12.php HTTP/1.1" -

If you see the web page correctly, the log contains this line:

88.138.77.192 SSLv3 DHE-RSA-AES256-SHA "GET /start/trainingseinheiten_8_12.php HTTP/1.1" 6315

It cannot be a PHP related problem, because mostly the same PHP page is displayed correctly. No error message in any log file (apache, php, syslog)!

I'm using: apache2, apache2-prefork, php4, mysql-4.0
(due to compatibility issues I can't use php5 nor mysql4.1/5)

Hardware is an AMD Athlon 64 Processor 3700 with 2 GB RAM and fast S-ATA discs on a 3ware Raid-5 controller. (used kernel: 2.6.12-10-k7)

I tried several configurations:
- with and without ZendOptimizer 2.6.2/3.00
- with and without Apache2 mod_cache and mod_disk_cache
- increase prefork settings (MaxClients + ServerLimit 500)
- with and without HTML meta header "expires 0"

What else can I try to stop this blank page problem, what could be the reason for the empty GET request? Any idea is welcome!

Thanks,
Thomas

---

