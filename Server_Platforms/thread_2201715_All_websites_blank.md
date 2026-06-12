---
title: "All websites blank"
date: 2014-01-25
forum: Server Platforms
---

### Post by AexbYRB on 2014-01-25
I just transferred to new ubuntu server. 
I believe everything is configured with correct permissions, but all my websites show blank when I type the domain name into the browser, and appear normally when I type IP/webfoler/ eg studentforums.biz and 111.90.150.92/studentforums/

This must be a simple problem but I dont know what it is

---

### Post by AexbYRB on 2014-01-25
My host says:

I believe you are using an application to crate and manage your site.  This issue usually happen due to problematic theme or plugin you install  in your application. Kindly please check with your developer regarding  this.

---

### Post by CharlesA on 2014-01-25
Do you remember what the permissions on the old server were? Unless the web server is writing data, it shouldn't have to be the owner of the web root.

---

### Post by AexbYRB on 2014-01-25
yes www-data
this is the apache user

---

### Post by AexbYRB on 2014-01-25
It is a fresh ubuntu install - th web folders are just copied into /var/www/

---

### Post by AexbYRB on 2014-01-25
There is no source code displayed on the blank pages

---

### Post by CharlesA on 2014-01-25
What web application are you trying to use?

Check the logs in /var/log/apache2 to see if it is showing any errors.

---

### Post by AexbYRB on 2014-01-25
server is down I think

---

### Post by CharlesA on 2014-01-25
You need to give more information before anyone can help you.

What did you migrate from, what software you are trying to run, what errors show up in the logs? Are you using shared hosting or a dedicated server/VPS?

If the web server is working, it should display an error instead of 'nothing'

If the site is inaccessible, you would have to check with your host to see if there is a problem with your server.

---

### Post by AexbYRB on 2014-01-26
Ok server is up at last.
It is a dedicated server. Our last server was also a dedicated server running lamp.
The websites are now accessible using ip/webfolder eg 111.90.150.92/studentforums/
but I cant load studentforums.biz in a browser

---

### Post by CharlesA on 2014-01-26
Check your web server configuration.

---

### Post by AexbYRB on 2014-01-26
Here is a part of apache logs file

98.255.1.101 - - [26/Jan/2014:09:58:56 -0500] "GET /announce.php?passkey=ed77992c4534ebdd0d6e60651580732a&info_hash=%27%a4%fdpl%89%9f%0aotT%ef%1f%1d%e2N%5d7D%ce&peer_id=-UM1840-%06s%7b%2b%12u%ac%dc%fa%fa%20X&port=62348&uploaded=346357760&downloaded=352321536&left=9804555191&corrupt=2097152&key=59F7BF23&event=stopped&numwant=0&compact=1&no_peer_id=1 HTTP/1.1" 404 472 "-" "uTorrentMac/1840(29446)"
98.255.1.101 - - [26/Jan/2014:09:58:57 -0500] "GET /announce.php?passkey=ed77992c4534ebdd0d6e60651580732a&info_hash=%f7%d6z%a6%27%f0%23~%60%86%22%14%e4%ff%18%1a%17%8eB%07&peer_id=-UM1840-%06s%7b%2b%12u%ac%dc%fa%fa%20X&port=62348&uploaded=180211657&downloaded=392400841&left=0&corrupt=0&key=59F7BF23&event=stopped&numwant=0&compact=1&no_peer_id=1 HTTP/1.1" 404 472 "-" "uTorrentMac/1840(29446)"
98.255.1.101 - - [26/Jan/2014:09:58:57 -0500] "GET /announce.php?passkey=ed77992c4534ebdd0d6e60651580732a&info_hash=%27%a4%fdpl%89%9f%0aotT%ef%1f%1d%e2N%5d7D%ce&peer_id=-UM1840-%06s%7b%2b%12u%ac%dc%fa%fa%20X&port=62348&uploaded=346357760&downloaded=352321536&left=9804555191&corrupt=2097152&key=59F7BF23&event=stopped&numwant=0&compact=1&no_peer_id=1 HTTP/1.1" 404 472 "-" "uTorrentMac/1840(29446)"
98.255.1.101 - - [26/Jan/2014:09:58:57 -0500] "GET /announce.php?passkey=ed77992c4534ebdd0d6e60651580732a&info_hash=%f7%d6z%a6%27%f0%23~%60%86%22%14%e4%ff%18%1a%17%8eB%07&peer_id=-UM1840-%06s%7b%2b%12u%ac%dc%fa%fa%20X&port=62348&uploaded=180211657&downloaded=392400841&left=0&corrupt=0&key=59F7BF23&event=stopped&numwant=0&compact=1&no_peer_id=1 HTTP/1.1" 404 472 "-" "uTorrentMac/1840(29446)"
98.255.1.101 - - [26/Jan/2014:09:58:57 -0500] "GET /announce.php?passkey=ed77992c4534ebdd0d6e60651580732a&info_hash=%27%a4%fdpl%89%9f%0aotT%ef%1f%1d%e2N%5d7D%ce&peer_id=-UM1840-%06s%7b%2b%12u%ac%dc%fa%fa%20X&port=62348&uploaded=346357760&downloaded=352321536&left=9804555191&corrupt=2097152&key=59F7BF23&event=stopped&numwant=0&compact=1&no_peer_id=1 HTTP/1.1" 404 472 "-" "uTorrentMac/1840(29446)"
127.0.0.1 - - [26/Jan/2014:09:58:57 -0500] "OPTIONS * HTTP/1.0" 200 126 "-" "Apache/2.2.22 (Ubuntu) (internal dummy connection)"
157.55.32.190 - - [26/Jan/2014:09:58:57 -0500] "GET /index.php/?location=A+Level%2FLaw%2FEdexcel%2F2012+Jun HTTP/1.1" 200 9740 "-" "Mozilla/5.0 (compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)"

---

### Post by Doug S on 2014-01-26
I think the directory mapping in your apache configs has issues. Note that [http://studentforums.biz/studentforums/](http://studentforums.biz/studentforums/) gives the same page as [http://111.90.150.92/studentforums/](http://111.90.150.92/studentforums/)
(well the java scripts and such have issues, because they aren't mapped correctly either, so the page doesn't actually render properly).

---

### Post by AexbYRB on 2014-01-27
Really interesting. Reading up on directory mapping

---

### Post by AexbYRB on 2014-01-27
It might sound stupid, but the website folders should be in /var/www/?

---

### Post by AexbYRB on 2014-01-27
I found this excellent tutorial
[https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts](https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts)
It all works

---

