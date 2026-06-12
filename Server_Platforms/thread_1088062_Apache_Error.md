---
title: "Apache Error?"
date: 2009-03-05
forum: Server Platforms
---

### Post by basotl on 2009-03-05
Hey everyone I have an issue and was hoping someone may know of a common pitfall that would have caused this.

I was just setting up some virtual hosts on my web server. It has Ubuntu 8.04 and is a Drupal/LAMP server. I was setting it up for three sites. I followed this how to to remember the order. [http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

I initially set up two sites and it worked fine. I then set up the third site and after restarting Apache I couldn’t connect to the sites. I then checked localhost and couldn’t connect to that. 

Is there a common pitfall I could have done mistakingly? What are some good trouble shoot ideas/commands. 

I have checked the hosts file it looks ok and did some other trouble shooting but haven’t had this issue before so I was hoping someone had a bright idea.

The only error I’m getting so far is when I stop Apache.

httpd (nopidfile) not running

I’m some what confused Ubuntu doesn’t use httpd.conf is that error referencing something else?

---

### Post by kanikilu on 2009-03-05
> **basotl said:**
> The only error I&#8217;m getting so far is when I stop Apache.

httpd (nopidfile) not running Sounds like apache's not running. Can you do ```
sudo /etc/init.d/apache2 start
``` If that doesn't work, check the log file at /var/log/apache2/error.log

---

### Post by basotl on 2009-03-06
Ok figured it out. Log file wasn't set up properly, causing it to not start. Thanks.

---

