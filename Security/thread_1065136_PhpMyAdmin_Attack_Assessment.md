---
title: "PhpMyAdmin Attack Assessment"
date: 2009-02-09
forum: Security
---

### Post by sjokomunn on 2009-02-09
Hey folks,

I will list the evidence that I've gathered and my overall assessment of the attack(s) in hopes that I can get some suggestions/opinions on the matter. I'm running phpmyadmin 2.11.3deb1ubuntu1.1 on ubuntu server 8.04.

I was checking my webstats as I regularly do (AWstats) and noticed the following:

```
url						Viewed	Average size	Entry	Exit	 
/phpmyadmin/index.php				33	7.99 KB	 	1	0
/						2	14 Bytes	2	2
http://XX.XX.XX.XX:80/phpmyadmin/		2	3.97 KB		1	0	
/phpmyadmin/libraries/select_lang.lib.php	1	344 Bytes	0 	1	
/phpmyadmin/main.php				1	7.95 KB		1	0 
```

These requests came from the following users:

```
			GeoIP Country	GeoIP City	Pages	Hits	Bandwidth	Last visit
210.219.173.17		South Korea	Seoul		35	35	271.72 KB	01 Feb 2009 - 10:18
rsloves.sloves.sk	Unknown		Unknown		2	2	8.28 KB		07 Feb 2009 - 00:22
```

This was an obvious attack since I have not authorized anyone to use phpmyadmin on this server. I wasn't really sure how to investigate further so I  tried:

```
cd /var/log/apache2
cat * | grep 210.219.173.17
```

Which revealed the following requests:

```
"HEAD http://XX.XX.XX.XX:80/mysql/admin/ HTTP/1.1" 404 - "-" "revolt"
"HEAD http://XX.XX.XX.XX:80/mysql/dbadmin/ HTTP/1.1" 404 - "-" "revolt"
"HEAD http://XX.XX.XX.XX:80/mysql/sqlmanager/ HTTP/1.1" 404 - "-" "revolt"
"HEAD http://XX.XX.XX.XX:80/mysql/mysqlmanager/ HTTP/1.1" 404 - "-" "revolt"
"HEAD http://XX.XX.XX.XX:80/phpmyadmin/ HTTP/1.1" 200 - "-" "revolt"
"GET http://XX.XX.XX.XX:80/phpmyadmin/ HTTP/1.0" 200 8136 "-" "revolt"
"GET /phpmyadmin/index.php?pma_username=root&pma_password= HTTP/1.1" 302 - "-" "revolt"
"GET /phpmyadmin/index.php?lang=en-utf-8&token=b540d99d1c08d0916a04829b0b8b5ae0 HTTP/1.1" 200 8184 "-" "revolt"
"GET /phpmyadmin/index.php?pma_username=root&pma_password=root HTTP/1.1" 302 - "-" "revolt"
"GET /phpmyadmin/index.php?lang=en-utf-8&token=920c6ef7d039f84fd204d464b9921bd6 HTTP/1.1" 200 8185 "-" "revolt"

```

etc. etc. there were about 30 more failed attempts at the root password over the next 30 seconds or so. Am I correct in thinking this was simply a (failed) automated attack to determine whether the server runs exploitable database management software and/or a weak root password?

I also found that the connection from Slovakia used the /phpmyadmin/libraries/select_lang.lib.php bug to determine the phpmyadmin install path. What is the value of this information? Can nastiness be wrought upon a myphpadmin installation after determining the install path? Is there a way to prevent this? Any insights or suggestions appreciated. Thanks!

-SM

---

### Post by HermanAB on 2009-02-09
It is very easy to stop this type of nonsense. Iptables nowadays has a very nice rate limit module which can prevent all kinds of abuse in one line:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

Cheers,

Herman

---

### Post by sjokomunn on 2009-02-10
Thanks for the replies folks. I will implement iptables rate limiting as suggested. Any comments on the bug that discloses the install path? It doesn't appear that the information was put to any sort of use against this particular server but presumably it must be good for something. Cheers.

-SM

---

### Post by kpm on 2009-03-21
> **HermanAB said:**
> It is very easy to stop this type of nonsense. Iptables nowadays has a very nice rate limit module which can prevent all kinds of abuse in one line:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT


When I attempt this command, the server responds with "iptables v1.4.0: bad rate `-burst'"
btw, I am VERY green with iptables :-)

---

### Post by hyper_ch on 2009-03-22
or .htaccess protect pma

---

