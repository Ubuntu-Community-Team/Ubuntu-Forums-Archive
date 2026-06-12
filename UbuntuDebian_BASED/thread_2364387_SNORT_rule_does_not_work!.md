---
title: "SNORT rule does not work!"
date: 2017-06-22
forum: Ubuntu/Debian BASED
---

### Post by pink-hat on 2017-06-22
hello


I have a problem.
I do these steps of snort for adjusting rule. (with Kali version in vmware)


1. cd /etc/snort/rules
2. sudo nano twitter.rules
3. reject tcp any any -> any any (content:"www.twitter.com";msg:"Block lists";sid:1000001; )
4. sudo nano /etc/snort/snort.conf
5. Add --> include $RULE_PATH/twitter.rules
6. sudo snort -A console -i eth0 -c /etc/snort/snort.conf -l /var/log/snort -K ascii


after this steps , I received this message "commencing packet processing"
but when I want to open twitter site , sometimes this site does not open but sometimes open!
and also the msg for rule does not appear!


I want to know why I can't block the site and get this message?!


thanks

---

### Post by coffeecat on 2017-06-23
*Thread moved to **Ubuntu/Debian BASED**.*

Please do not post Kali questions in the Ubuntu support areas.

---

