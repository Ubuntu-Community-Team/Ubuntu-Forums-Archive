---
title: "troubleshooting localhost where only index.php will load"
date: 2018-02-03
forum: Server Platforms
---

### Post by nickdc on 2018-02-03
Mt partner has a small website which functions properly on its remote host site. It also functioned properly on her local desktop running Ubuntu 12.04. After upgrading to 16.04 (with a fresh installation) I struggled to remember how I'd originally set it up for her!:oops: After a bit of online reading I thought I'd got it working, but actually when entering "localhost" in Firefox only the home page (index.php) loads; none of the links on that page work. They don't produce a 404 page, simply a grey blank (with the correct file name in the address bar). I strongly suspect it's a simple configuration issue - eg I've read that there have been changes in recent versions of WAMP, which maybe affect LAMP too ..? I'm hoping if I list exactly what I did someone more experienced will quickly spot where the problem is likely to be. So, here's what I did:

1. Installed lamp-server after installing tasksel  ( see [https://linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-16-04/](https://linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-16-04/)  - but I ignored all the subsequent instructions on that site)
2. Edited /etc/apache2/mods-enabled/dir.conf so that index.php was first in the list  (this the only configuration change I made anywhere)
3. Restarted apache
4. Deleted the default index.html from /var/www/html
5. Copied the entire contents of the backed up website folder to /var/www/html
6. Restarted apache
7. Tried localhost in Firefox and found the home page loaded correctly but none of its links worked.

What next?:confused:

---

### Post by SeijiSensei on 2018-02-03
What links are you talking about in particular?  Ones that point to off-site resources, or ones that point to other pages within your partner's site?  If the latter, it depends a lot on how the URLs are entered.  In particular, if the links include a server part, they may not function correctly on a test bed.  Do the links look like "src=http://server/somepage.php" or just "/somepage.php?"  The latter should work even if the former does not.

What do you see in the Apache error logs?  Perhaps the PHP scripts cannot find a needed resource?

---

### Post by slickymaster on 2018-02-03
*Thread moved to **Server Platforms**.*

---

### Post by nickdc on 2018-02-03
Thanks for moving this to the right place.

---

### Post by nickdc on 2018-02-03
> **SeijiSensei said:**
> What links are you talking about in particular?  Ones that point to off-site resources, or ones that point to other pages within your partner's site?  If the latter, it depends a lot on how the URLs are entered.  In particular, if the links include a server part, they may not function correctly on a test bed.  Do the links look like "src=http://server/somepage.php" or just "/somepage.php?"  The latter should work even if the former does not.

What do you see in the Apache error logs?  Perhaps the PHP scripts cannot find a needed resource?

Thanks for coming to my assistance. The links point to other pages within the site; they're of the form "somepage.php". As I said, it was all working fine until we upgraded to 16.04 and UbuntuGnome instead of vanilla Ubuntu. That's why I'm convinced it's not a problem with the website page contents, but a configuration issue in one of the LAMP components. I'm out of my depth with the Apache error logs. Mainly repeated references to "Undefined variable"

Here's the whole thing:
```

[Thu Feb 01 11:40:54.003222 2018] [mpm_event:notice] [pid 4543:tid 3074320960] AH00489: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations
[Thu Feb 01 11:40:54.003580 2018] [core:notice] [pid 4543:tid 3074320960] AH00094: Command line: '/usr/sbin/apache2'
[Thu Feb 01 11:53:25.170453 2018] [mpm_event:notice] [pid 4543:tid 3074320960] AH00491: caught SIGTERM, shutting down
[Thu Feb 01 11:57:17.956605 2018] [mpm_event:notice] [pid 21056:tid 3074366016] AH00489: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations
[Thu Feb 01 11:57:17.968563 2018] [core:notice] [pid 21056:tid 3074366016] AH00094: Command line: '/usr/sbin/apache2'
[Thu Feb 01 11:58:20.106719 2018] [mpm_event:notice] [pid 21056:tid 3074366016] AH00491: caught SIGTERM, shutting down
[Thu Feb 01 11:58:21.332989 2018] [mpm_prefork:notice] [pid 27148] AH00163: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations
[Thu Feb 01 11:58:21.333350 2018] [core:notice] [pid 27148] AH00094: Command line: '/usr/sbin/apache2'
[Thu Feb 01 11:58:23.597911 2018] [mpm_prefork:notice] [pid 27148] AH00169: caught SIGTERM, shutting down
[Thu Feb 01 11:58:25.412021 2018] [mpm_prefork:notice] [pid 27252] AH00163: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations
[Thu Feb 01 11:58:25.412189 2018] [core:notice] [pid 27252] AH00094: Command line: '/usr/sbin/apache2'
[Thu Feb 01 12:10:16.242777 2018] [mpm_prefork:notice] [pid 27252] AH00169: caught SIGTERM, shutting down
[Thu Feb 01 12:10:17.233512 2018] [mpm_prefork:notice] [pid 28187] AH00163: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations
[Thu Feb 01 12:10:17.233672 2018] [core:notice] [pid 28187] AH00094: Command line: '/usr/sbin/apache2'
[Thu Feb 01 12:28:21.850283 2018] [mpm_prefork:notice] [pid 28187] AH00169: caught SIGTERM, shutting down
[Thu Feb 01 12:28:22.931721 2018] [mpm_prefork:notice] [pid 28305] AH00163: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations
[Thu Feb 01 12:28:22.931985 2018] [core:notice] [pid 28305] AH00094: Command line: '/usr/sbin/apache2'
[Thu Feb 01 13:29:38.912564 2018] [:error] [pid 28598] [client 127.0.0.1:41062] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12
[Thu Feb 01 13:29:38.924388 2018] [:error] [pid 28598] [client 127.0.0.1:41062] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 13
[Thu Feb 01 13:29:38.924441 2018] [:error] [pid 28598] [client 127.0.0.1:41062] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 14
[Thu Feb 01 13:29:38.924464 2018] [:error] [pid 28598] [client 127.0.0.1:41062] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 17
[Thu Feb 01 13:29:38.924485 2018] [:error] [pid 28598] [client 127.0.0.1:41062] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 18
[Thu Feb 01 13:29:38.924507 2018] [:error] [pid 28598] [client 127.0.0.1:41062] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 19
[Thu Feb 01 13:29:38.924529 2018] [:error] [pid 28598] [client 127.0.0.1:41062] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 20
[Thu Feb 01 15:55:44.209601 2018] [:error] [pid 29039] [client 127.0.0.1:41512] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12
[Thu Feb 01 15:55:44.238695 2018] [:error] [pid 29039] [client 127.0.0.1:41512] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 13
[Thu Feb 01 15:55:44.238734 2018] [:error] [pid 29039] [client 127.0.0.1:41512] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 14
[Thu Feb 01 15:55:44.238751 2018] [:error] [pid 29039] [client 127.0.0.1:41512] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 17
[Thu Feb 01 15:55:44.238767 2018] [:error] [pid 29039] [client 127.0.0.1:41512] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 18
[Thu Feb 01 15:55:44.238783 2018] [:error] [pid 29039] [client 127.0.0.1:41512] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 19
[Thu Feb 01 15:55:44.238828 2018] [:error] [pid 29039] [client 127.0.0.1:41512] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 20
[Thu Feb 01 15:55:55.509466 2018] [:error] [pid 29042] [client 127.0.0.1:41514] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12, referer: http://localhost/
[Thu Feb 01 15:55:55.509606 2018] [:error] [pid 29042] [client 127.0.0.1:41514] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 13, referer: http://localhost/
[Thu Feb 01 15:55:55.509630 2018] [:error] [pid 29042] [client 127.0.0.1:41514] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 14, referer: http://localhost/
[Thu Feb 01 15:55:55.509650 2018] [:error] [pid 29042] [client 127.0.0.1:41514] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 17, referer: http://localhost/
[Thu Feb 01 15:55:55.509670 2018] [:error] [pid 29042] [client 127.0.0.1:41514] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 18, referer: http://localhost/
[Thu Feb 01 15:55:55.509691 2018] [:error] [pid 29042] [client 127.0.0.1:41514] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 19, referer: http://localhost/
[Thu Feb 01 15:55:55.509710 2018] [:error] [pid 29042] [client 127.0.0.1:41514] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 20, referer: http://localhost/
[Thu Feb 01 15:55:55.519486 2018] [:error] [pid 29042] [client 127.0.0.1:41514] PHP Fatal error:  Uncaught Error: Call to undefined function xml_parser_create() in /var/www/html/php/xmlParser.php:114\nStack trace:\n#0 /var/www/html/artworkGallery.php(12): ArtworkGalleryGenerator('artwork/artwork...')\n#1 {main}\n  thrown in /var/www/html/php/xmlParser.php on line 114, referer: http://localhost/
[Thu Feb 01 15:56:58.246010 2018] [:error] [pid 28308] [client 127.0.0.1:41534] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12, referer: http://localhost/
[Thu Feb 01 15:56:58.250386 2018] [:error] [pid 28308] [client 127.0.0.1:41534] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 13, referer: http://localhost/
[Thu Feb 01 15:56:58.250408 2018] [:error] [pid 28308] [client 127.0.0.1:41534] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 14, referer: http://localhost/
[Thu Feb 01 15:56:58.250424 2018] [:error] [pid 28308] [client 127.0.0.1:41534] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 17, referer: http://localhost/
[Thu Feb 01 15:56:58.250440 2018] [:error] [pid 28308] [client 127.0.0.1:41534] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 18, referer: http://localhost/
[Thu Feb 01 15:56:58.250456 2018] [:error] [pid 28308] [client 127.0.0.1:41534] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 19, referer: http://localhost/
[Thu Feb 01 15:56:58.250472 2018] [:error] [pid 28308] [client 127.0.0.1:41534] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 20, referer: http://localhost/
[Thu Feb 01 15:56:58.250592 2018] [:error] [pid 28308] [client 127.0.0.1:41534] PHP Fatal error:  Uncaught Error: Call to undefined function xml_parser_create() in /var/www/html/php/xmlParser.php:114\nStack trace:\n#0 /var/www/html/artworkGallery.php(12): ArtworkGalleryGenerator('artwork/artwork...')\n#1 {main}\n  thrown in /var/www/html/php/xmlParser.php on line 114, referer: http://localhost/
[Thu Feb 01 15:57:10.398196 2018] [:error] [pid 28309] [client 127.0.0.1:41538] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12, referer: http://localhost/
[Thu Feb 01 15:57:10.398608 2018] [:error] [pid 28309] [client 127.0.0.1:41538] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 13, referer: http://localhost/
[Thu Feb 01 15:57:10.398720 2018] [:error] [pid 28309] [client 127.0.0.1:41538] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 14, referer: http://localhost/
[Thu Feb 01 15:57:10.398736 2018] [:error] [pid 28309] [client 127.0.0.1:41538] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 17, referer: http://localhost/
[Thu Feb 01 15:57:10.398751 2018] [:error] [pid 28309] [client 127.0.0.1:41538] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 18, referer: http://localhost/
[Thu Feb 01 15:57:10.398766 2018] [:error] [pid 28309] [client 127.0.0.1:41538] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 19, referer: http://localhost/
[Thu Feb 01 15:57:10.398782 2018] [:error] [pid 28309] [client 127.0.0.1:41538] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 20, referer: http://localhost/
[Thu Feb 01 15:57:10.398910 2018] [:error] [pid 28309] [client 127.0.0.1:41538] PHP Fatal error:  Uncaught Error: Call to undefined function xml_parser_create() in /var/www/html/php/xmlParser.php:71\nStack trace:\n#0 /var/www/html/since2000.php(12): ArtworkListGenerator('artwork/artwork...', 'since2000')\n#1 {main}\n  thrown in /var/www/html/php/xmlParser.php on line 71, referer: http://localhost/
[Thu Feb 01 15:57:20.145490 2018] [:error] [pid 29040] [client 127.0.0.1:41542] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12, referer: http://localhost/
[Thu Feb 01 15:57:20.148965 2018] [:error] [pid 29040] [client 127.0.0.1:41542] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 13, referer: http://localhost/
[Thu Feb 01 15:57:20.148994 2018] [:error] [pid 29040] [client 127.0.0.1:41542] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 14, referer: http://localhost/
[Thu Feb 01 15:57:20.149010 2018] [:error] [pid 29040] [client 127.0.0.1:41542] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 17, referer: http://localhost/
[Thu Feb 01 15:57:20.149025 2018] [:error] [pid 29040] [client 127.0.0.1:41542] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 18, referer: http://localhost/
[Thu Feb 01 15:57:20.149040 2018] [:error] [pid 29040] [client 127.0.0.1:41542] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 19, referer: http://localhost/
[Thu Feb 01 15:57:20.149056 2018] [:error] [pid 29040] [client 127.0.0.1:41542] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 20, referer: http://localhost/
[Thu Feb 01 15:57:20.149138 2018] [:error] [pid 29040] [client 127.0.0.1:41542] PHP Fatal error:  Uncaught Error: Call to undefined function xml_parser_create() in A lot of/var/www/html/php/xmlParser.php:71\nStack trace:\n#0 /var/www/html/diLifton.php(12): ArtworkListGenerator('artwork/artwork...', '1966to1975')\n#1 {main}\n  thrown in /var/www/html/php/xmlParser.php on line 71, referer: http://localhost/
[Thu Feb 01 23:12:48.685328 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12
[Thu Feb 01 23:12:48.692299 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 13
[Thu Feb 01 23:12:48.692336 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 14
[Thu Feb 01 23:12:48.692354 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 17
[Thu Feb 01 23:12:48.692369 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 18
[Thu Feb 01 23:12:48.692385 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 19
[Thu Feb 01 23:12:48.692425 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 20
[Thu Feb 01 23:12:52.023182 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12, referer: http://localhost/
[Thu Feb 01 23:12:52.023257 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 13, referer: http://localhost/
[Thu Feb 01 23:12:52.023275 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 14, referer: http://localhost/
[Thu Feb 01 23:12:52.023290 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 17, referer: http://localhost/
[Thu Feb 01 23:12:52.023306 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 18, referer: http://localhost/
[Thu Feb 01 23:12:52.023321 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 19, referer: http://localhost/
[Thu Feb 01 23:12:52.023336 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 20, referer: http://localhost/
[Thu Feb 01 23:12:52.047122 2018] [:error] [pid 29042] [client 127.0.0.1:43258] PHP Fatal error:  Uncaught Error: Call to undefined function xml_parser_create() in /var/www/html/php/xmlParser.php:71\nStack trace:\n#0 /var/www/html/since2000.php(12): ArtworkListGenerator('artwork/artwork...', 'since2000')\n#1 {main}\n  thrown in /var/www/html/php/xmlParser.php on line 71, referer: http://localhost/
[Thu Feb 01 23:14:11.056453 2018] [core:warn] [pid 28305] AH00045: child process 28308 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102694 2018] [core:warn] [pid 28305] AH00045: child process 28309 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102719 2018] [core:warn] [pid 28305] AH00045: child process 28310 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102733 2018] [core:warn] [pid 28305] AH00045: child process 28311 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102747 2018] [core:warn] [pid 28305] AH00045: child process 28312 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102761 2018] [core:warn] [pid 28305] AH00045: child process 28598 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102775 2018] [core:warn] [pid 28305] AH00045: child process 29039 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102789 2018] [core:warn] [pid 28305] AH00045: child process 29040 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102803 2018] [core:warn] [pid 28305] AH00045: child process 29041 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:11.102816 2018] [core:warn] [pid 28305] AH00045: child process 29042 still did not exit, sending a SIGTERM
[Thu Feb 01 23:14:12.123515 2018] [mpm_prefork:notice] [pid 28305] AH00169: caught SIGTERM, shutting down
[Fri Feb 02 14:56:40.720821 2018] [mpm_prefork:notice] [pid 1092] AH00163: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations
[Fri Feb 02 14:56:40.732294 2018] [core:notice] [pid 1092] AH00094: Command line: '/usr/sbin/apache2'
[Fri Feb 02 17:58:15.498628 2018] [core:warn] [pid 1092] AH00045: child process 1105 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:15.727281 2018] [core:warn] [pid 1092] AH00045: child process 1106 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:15.727316 2018] [core:warn] [pid 1092] AH00045: child process 1107 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:15.727332 2018] [core:warn] [pid 1092] AH00045: child process 1108 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:15.727347 2018] [core:warn] [pid 1092] AH00045: child process 1109 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:16.728420 2018] [core:warn] [pid 1092] AH00045: child process 1105 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:16.728486 2018] [core:warn] [pid 1092] AH00045: child process 1106 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:16.728501 2018] [core:warn] [pid 1092] AH00045: child process 1107 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:16.728513 2018] [core:warn] [pid 1092] AH00045: child process 1108 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:16.728526 2018] [core:warn] [pid 1092] AH00045: child process 1109 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:18.730623 2018] [core:warn] [pid 1092] AH00045: child process 1105 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:18.730693 2018] [core:warn] [pid 1092] AH00045: child process 1106 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:18.730708 2018] [core:warn] [pid 1092] AH00045: child process 1107 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:18.730721 2018] [core:warn] [pid 1092] AH00045: child process 1108 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:18.730734 2018] [core:warn] [pid 1092] AH00045: child process 1109 still did not exit, sending a SIGTERM
[Fri Feb 02 17:58:20.774046 2018] [mpm_prefork:notice] [pid 1092] AH00169: caught SIGTERM, shutting down
[Sat Feb 03 13:16:40.856852 2018] [mpm_prefork:notice] [pid 1099] AH00163: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations
[Sat Feb 03 13:16:40.882783 2018] [core:notice] [pid 1099] AH00094: Command line: '/usr/sbin/apache2'
[Sat Feb 03 13:21:29.473181 2018] [mpm_prefork:notice] [pid 1099] AH00171: Graceful restart requested, doing restart 
```

---

### Post by SeijiSensei on 2018-02-03
Here's the likely problem:

> ```
Fatal error:  Uncaught Error: Call to undefined function xml_parser_create() in /var/www/html/php/xmlParser.php:114
```

PHP is distributed with a number of modules that contain various sets of functions.  The xml_parser_create() function is part of the php-xml package.  It is not installed by default.  Use "sudo apt-get install php-xml" to install it. 

I recommend creating a file called info.php in /var/spool/html with the contents

```
<?php phpinfo() /?>
```

If you point a browser at that file, you'll get an exhaustive report on how Apache and PHP are configured.

Also these errors are pretty easily dispensed with:
> ```
PHP Notice:  Undefined variable: a in /var/www/html/php/includes/head.php on line 12
```

Just initialize $a somewhere at the top of head.php. Likely options are:
```

$a='';
$a=0;
$a=array();

```
depending obviously on whether $a is a string, a number, or an array.

---

### Post by nickdc on 2018-02-03
That's really helpful - thank you so much. Your first two suggestions I fully understand and can do. But I'm less confident about the last, "Just initialise $a somewhere at the top of head.php..." etc. Would mind unpacking that with a bit more guidance/explanation? (The website was created for my partner by someone who's now moved on. I'm trying my best to help but my understanding of html, php etc is rudimentary to say the least.)

---

### Post by LHammonds on 2018-02-04
Since we do not know what the code looks like, it can be several issues.

The actual problem might be that it could be referencing a global variable inside a function.  [Example](https://stackoverflow.com/questions/20391807/how-do-i-fix-undefined-variable-error-in-php)

Another difference might be that it was never defined before and the old server's [error reporting](http://php.net/manual/en/function.error-reporting.php) was less strict and let errors like this silently fail.  Typically, when you are developing code, you want error reporting as strict as possible to help you catch all the errors you can.  But once in production, you loosen up error reporting and let errors happen silently.  Examples of other methods [changing the report level](https://serverfault.com/questions/509559/change-php-error-reporting-to-hide-warnings-for-specific-site-only-debianubunt).

LHammonds

---

### Post by nickdc on 2018-02-04
OK, some progress made after installing php-xml: now all the links on the home page work. But nothing beyond that, and on one page, containing a grid of image thumbnails, themselves links, only some of the thumbnails appear, the rest being blank squares. All the links at the second level produce a 404 page. I'm still convinced it's a server configuration issue rather than code errors in the site content, as not only was it fully functioning locally until the local upgrade, but it's also functioning properly online at the host site, where I assume they keep reasonably up to date with new releases of server components. Thus I'm very reluctant to make changes to the local content, as that would put it out of sync with the live site or risk, if uploaded, knock-on errors on the live site. Does this make sense? Btw, I'd be happy to post a link to the live site, but is that acceptable?

Here's a link to today's error log after installing php-xml:

[https://paste.ubuntu.com/26518167/](https://paste.ubuntu.com/26518167/)

---

### Post by LHammonds on 2018-02-04
Another potential problem could be that the code was designed for PHP 5 and now you are running it on PHP 7.  Try uninstalling PHP 7 and install PHP 5 (and related libraries).

I have done this before (Ubuntu 16.04 + PHP 5) for PHP apps that were not compatible with PHP 7.  You can see how I set it up here: [How to install qdPM on Ubuntu Server 16.04](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=222)

I'd recommend trying this in a virtual machine (such as Oracle VirtualBox) before doing it on bare metal.

LHammonds

---

### Post by SeijiSensei on 2018-02-05
Apparently some of the images are being created on the fly rather than simply linked to in HTML.  Again the problem is a missing module, in this case, php-gd.  The [GD library]("http://php.net/manual/en/ref.image.php") contains the ImageCreateTrueColor() function that throws a not-found error.

I'd start by using the "grep" command to find all the missing function errors if any more exist like this:

```
grep 'undefined function' /var/log/apache2/error.log
```

As for the undeclared variable error, that arises when you use an expression with a variable that has yet to be defined.  A trivial example is
```

$b=$a + 1;

```
without an initialization statement for $a first:
```

$a=0;
$b=$a+1;

```
There's also an uninitialized array in those errors, 

> ```
4] PHP Notice:  Undefined index: imageThumb in /var/www/html/php/xmlParser.php on line 98, referer: http://localhost/dianneArmstrong.php
[Sun Feb 04 11:04:29.589925 2018] [:error] [pid 5379] [client 127.0.0.1:43414] PHP Notice:  Undefined index: urlTitle in /var/www/html/php/xmlParser.php on line 96, referer: http://localhost/dianneArmstrong.php
[Sun Feb 04 11:04:29.589950 2018] [:error] [pid 5379] [client 127.0.0.1:43414] PHP Notice:  Undefined index: title in /var/www/html/php/xmlParser.php on line 97, referer: http://localhost/dianneArmstrong.php
```

There's an array in parser.php that has those elements but not initialized like this:
```

$mypicture=array("ImageThumb"=>"","urltitle"=>"","title"=>"");

```
The actual array will be called something other than "mypicture," of course.

That creates an empty array with those three indexes.  If you add this before the array is used in parser.php, you'll get rid of those "undefined index" errors.

If the images being created by ImageCreateTrueColor() are used consistently over time, you should create static versions of those images and link to them directly rather than forcing the server to regenerate them on every visit to the page.

---

### Post by nickdc on 2018-02-06
> **LHammonds said:**
> Another potential problem could be that the code was designed for PHP 5 and now you are running it on PHP 7.  Try uninstalling PHP 7 and install PHP 5 (and related libraries).

I have done this before (Ubuntu 16.04 + PHP 5) for PHP apps that were not compatible with PHP 7.  You can see how I set it up here: [How to install qdPM on Ubuntu Server 16.04]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=222")

I'd recommend trying this in a virtual machine (such as Oracle VirtualBox) before doing it on bare metal.

LHammonds

Thanks for the advice and for the links. The trouble is: we're running on ancient machines, which struggle to run a VM. I had thought about trying to install PHP 5 on my own desktop, following your tutorial, but then I spotted some of the requirements, eg our machines are both 32bit, and I'm quickly out of my depth. But I shall keep your comments and demo links in mind for when I've (hopefully!) advanced further.

---

### Post by nickdc on 2018-02-06
Thanks, SeijiSensei, for your further assistance. Installing php-gd has sorted the missing thumbnails from the grid and grepping the log for 'Undefined function' brings up no further instances. So it's just the "undefined variable" and "undefined index" errors causing problems now. And those seem to be mainly in two files: head.php and xmlParser.php. To be honest I still only half understand your explanations, but it's made me realise I need to learn some basic coding! Any advice where I might start from scratch? Meanwhile, I thought it might be worth getting the code from those two files on the live website and comparing it with what we have here in the test site, as I suppose it's possible that the live ones have been updated by the site's creator at some stage without him passing it on to us.

I'm running short of time on this and may have to park it and return at a future stage, but again I want to thank you for your help, which has certainly moved me along. Cheers!

---

### Post by LHammonds on 2018-02-06
> **nickdc said:**
> our machines are both 32bitWhoops...that is ancient...or just 32-bit Windows installed on top of a 64-bit machine...most machines are 64-bit but because of various old devices (printers, usb hardware, etc.) 32-bit operating systems often were installed on 64-bit hardware for compatibility reasons.  Ubuntu Server is 64-bit only so you won't be able to run it in a VM on a 32-bit machine.

Make sure you document somewhere what libraries are needed for the next time you need to move/migrate this web application.

LHammonds

---

### Post by nickdc on 2018-02-06
> **LHammonds said:**
> Whoops...that is ancient...or just 32-bit Windows installed on top of a 64-bit machine...most machines are 64-bit but because of various old devices (printers, usb hardware, etc.) 32-bit operating systems often were installed on 64-bit hardware for compatibility reasons.  Ubuntu Server is 64-bit only so you won't be able to run it in a VM on a 32-bit machine.

Make sure you document somewhere what libraries are needed for the next time you need to move/migrate this web application.

LHammonds
7
Yep, it certainly is ancient; I built it myself back in the early 2000s. I tried to future-proof it, but never dreamed it would keep going this long, and of course it wouldn't have done were it not for Linux; I gave up with Windows yonks ago. But note: I'm not trying to run Ubuntu Server; I just have the lamp-server package installed on Ubuntu-gnome.

---

### Post by SeijiSensei on 2018-02-09
Here's a better example of an "undeclared variable" error from some code I was working on today.

```

$test=1;
if ($test == 1) { 
     $var=1;
}

```
If $test is not equal to one, what is the value of $var?  It is undefined.  I eliminated the error by initializing $var:
```

$var=0;
$test=1;
if ($test == 1) {
    $var=1;
}

```

---

### Post by nickdc on 2018-02-20
I'm back on the case, having made little progress. Thanks, SeijiSensei, for your last post explaining the variables error more clearly. It would be challenging for me, but I probably could work out what changes to make to the code so that it all works, but as I said before: the same code works fine on the host server. I've now confirmed that, as previously I was working on my partner's pc (it's her website) but now I've set up a lamp server on my own machine, which had no server previously installed. I made sure I was using php5.6 (using this guide: [https://gist.github.com/ericfledderman/6c4f0f7e6ffa3477372ebf5392bad6cd/revisions](https://gist.github.com/ericfledderman/6c4f0f7e6ffa3477372ebf5392bad6cd/revisions)), having confirmed with the hosting service that that was the version being used for my partner's site. And I downloaded the site content files afresh from the hosting site using Filezilla. I really expected it to work on localhost after that, but no, the same errors: "undefined index" and "undefined variable". It seems to me there are only two possibilities: 1. Discrepancies in the modules or configuration between the two sites cause the pages to load correctly on the remote site but not locally; or 2. the error messages in the apache2 log actually don't relate to the local page loading failures, which are caused by something else. But if 2. is the case, it should still be possible to get the local site working without changing the code. .... Surely? Or am I missing something obvious?

After further reading I'm becoming convinced that the "undefined variable" and "undefined index" messages in the apache2 error log are a red herring, in the sense that they are the result of stricter error reporting rather than indicative of what's stopping certain links from working. Obviously it's imortant to have robust and correct code, but for the moment i'm more interested in getting this test site fully functional. Much of it works now, and there's a common element to all the links that don't work, in that they all involve images: either thumbnails that work as links or links that should bring up pages containing further images. Could this be another missing module?

---

### Post by nickdc on 2018-02-22
I'm now more than ever convinced that possibility no. 2 in my previous post is correct, as last night I found some emails (which I'd completely forgotten :oops:) exchanged with the original developer when we first set up the site. I had exactly the same problem then setting up the local test site until I discovered that "register_globals" and "long_arrays" were turned off in the php.ini file. Once I turned them on, everything worked. So imagine my disappointment when I discover that from php5.6 those options are no longer available. I still don't understand how the site is working on its remote host, but I know, for example, they don't use apache, so perhaps their setup can still respond to whatever in the code requires globals and long arrays. But unless there's a work-around, I guess I have no alternative than to learn to code or find someone who does, so we can update the relevant files.

I'd appreciate any comments, before marking this thread "solved".

---

