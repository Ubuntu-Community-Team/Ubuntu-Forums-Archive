---
title: "Ubuntu 11.10 Apache2 won't move from default DocumentRoot"
date: 2011-12-30
forum: Server Platforms
---

### Post by garyheelas on 2011-12-30
I am tearing my hair out with Ubuntu 11.10 and Apache2 trying to get the basics working.  I had it working fine under Ubuntu 10.xx but I don't know whether it's 11.10 causing the issues or something else.

I've tried everything I can think of in apache2.conf but it just sticks to /var/www.  As an example, I created a directory test under /var/www, copied the default index.html into it and then edited it so I knew when it was correctly being selected.  Do a restart of apache2 and [http://localhost](http://localhost) still gives the index.html in /var/www

Comments/questions most welcome before I go bald through hair pulling.

---

### Post by lisati on 2011-12-30
I've found that sometimes I need to clear my browser cache when I've modified my web site in some fashion and it doesn't seem to change when I'm viewing it.

---

### Post by garyheelas on 2011-12-30
> **lisati said:**
> I've found that sometimes I need to clear my browser cache when I've modified my web site in some fashion and it doesn't seem to change when I'm viewing it.


Nah, tried that.

I should add that if I modify the index.html in /var/www I see the change reflected in my web browser.  But as detailed in the first post, it won't move away from that default directory.

---

### Post by agreenfi on 2012-01-01
Which config file are you editing exactly?  You need to edit /etc/apache2/sites-availabe/default

---

### Post by mapreri on 2012-01-01
> **agreenfi said:**
> Which config file are you editing exactly?  You need to edit /etc/apache2/sites-availabe/default

sorry, but the correct file is /etc/apache2/sites-enabled/000-default

---

