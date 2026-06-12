---
title: "Please help me understand Ubuntu 8.04 and apache2"
date: 2009-03-14
forum: Server Platforms
---

### Post by sp0nge on 2009-03-14
Hello again! 

I have a home server that runs 8.04, Apache2.2.8, and PHP/5.2.4-2. I had it running rather well with a few test php pages when I got the itch to start experimenting with virtual hosting. I bought a couple domain names and followed [this basis tutorial]("http://www.corey-m.com/blog/?p=315")which got me up and running when I dropped a simple index page into the htdocs directory for each site. 

Since this seemed to be going well, I wanted to install phpMyAdmin as I want to start learning to use SQL to create dynamic web pages. I did install via apt, which seems to have put phpMyAdmin in /usr/share. I was having trouble accessing phpMyAdmin, so I tried to turn off the virtual hosting  by editing /etc/apache2/apache2.conf. The only change I made was commenting out this line:

```
Include /etc/apache2/sites-enabled
```

Well I was unable to get phpMyAdmin working properly, so I wanted to change the virtual hosting back, I uncommented the above line and now it seems the whole thing is horked! When I point the browser to [www.myurl1.com](www.myurl1.com), the proper index page is displayed, but when I point to [www.myurl2.com](www.myurl2.com), the page is still for url1.com!

So I started digging through the documentation, but everything points to httpd.conf which apparently ubuntu doesn't use, there have been several other references that haven't been quite right and unfortunately, I am too new to know what the heck I am doing!

Can someone point me to resources that can help me better understand the specifics of ubuntu 8.04 and apache2 so I can sort this all out?

TIA!

---

### Post by EmanresuusernamE on 2009-03-14
Personally, on my webserver, after everychange I make to Apache I have to restart the daemon before it will use the new changes.

And from what I can tell, "/etc/apache2/sites-enabled" is key for Apache knowing what websites is can and cannot use and without it, Apache won't work at all.  (It thinks there are no websites enabled at all if it's not there/disabled.)

---

### Post by windependence on 2009-03-15
Yes, the problem is you did not restart Apache after the changes.

-Tim

---

### Post by EmanresuusernamE on 2009-03-15
Real quick question, it seems real silly to me to have to restart Apache after every change made, is there any way to make changes dynamically?  Wouldn't web servers with really massive amounts of virtual hosts have major down time having to restart Apache after every change?

---

### Post by volkswagner on 2009-03-15
> **EmanresuusernamE said:**
> Real quick question, it seems real silly to me to have to restart Apache after every change made, is there any way to make changes dynamically?  Wouldn't web servers with really massive amounts of virtual hosts have major down time having to restart Apache after every change?

I don't think one would ever want dynamic changes.  Many times when performing changes, upgrades, additions, etc., these are often multi-step processes.  This allows one to complete the task before going live.

The restarting of apache is quick in my opinion.  I believe large scale web servers don't have one instance of apache on one machine, thus I have no Idea how they do it. :)

---

