---
title: "Hellanzb &amp; encryption"
date: 2008-08-07
forum: Security
---

### Post by technotika on 2008-08-07
Hi Guys I have set up stunnel and hellanzb for encrypted newsgroup access.

However I am not entirely sure its working. When I run the command to start stunnel it fires up no errors.

Then I fire up hellanzb and then the stunnel tab in terminal says its connected to the 10 connections in Hellanzb. Down loading is fine 
but all that stunnel says is thats its connected should I be seeing things happening during downloads like this packet sent and recieved etc.

In the hellanzb config I set the SSL opntion to true and that start stunnel losing connections and nothing downloads in HELLANZB  - I presume this isnt required as it wasnt in the instructions.

Just wondered if anyone else uses this and can they conform this is working or not??

guide followed
[http://ubuntuforums.org/showthread.php?t=324710&highlight=hellanzb+encryption](http://ubuntuforums.org/showthread.php?t=324710&highlight=hellanzb+encryption)

---

### Post by jmh87 on 2008-08-20
technotika, if you set ssl = True in hellanzb.conf then you do not need to run the connection through stunnel, and set your news server back to news.xxxxx.xxx instead of localhost:119. Thats how mine is set up and it seems to be working fine.

---

### Post by technotika on 2008-09-07
Thanks mate - didnt see this post for ages. Just had to reinstall and was faffing about with that stunnel thing again and it didnt work for some reason. Saw your post made the changes and bingo , much simpler. Had to download some psyssl package which hellanzb complained about and also change port to 443 and it works perfect. Thanks!!!!!:popcorn:

---

