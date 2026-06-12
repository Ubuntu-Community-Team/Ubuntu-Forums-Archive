---
title: "Starting a forum"
date: 2009-08-03
forum: Ubuntu Studio
---

### Post by ArmenianLeader4 on 2009-08-03
If I wanted to start a forum on my webpage, what kind of server would be recommended, as well as what kind of HTML would be required?

---

### Post by madnessjack on 2009-08-04
I'm assuming you want to set up your own server? All you need is something to host PHP and MySQL. I've never tried it, but you could install Ubuntu Server edition.

Then you'll need to set up LAMP (Linux, Apache, MySQL and PHP)
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

PHP will manage the HTML for you :)

Then I would recommend installing PHPBB, but I'm not sure other more experienced personnel on this forum would agree! :D

I can't get on their website at the minute (not a good sign really), but a quick google for phpbb will direct you.

There's ample documentation for all things I've listed above on Google. After setting all that up you'll want to broadcast the forum, so make sure your ISP gives you a static IP adress. If you're connected to the internet through a router, you're going to have to set up "port forwarding".

---

### Post by fahadsadah on 2009-08-04
phpBB is the best, unless you want to pay for vBulletin.

Install Ubuntu Server, with the LAMP role preconfigured. Then download the phpBB source code to your document root.

---

