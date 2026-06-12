---
title: "Help a newbie set up his server"
date: 2007-07-08
forum: Server Platforms
---

### Post by Nevon on 2007-07-08
I've searched through the tips & tutorials-section without any luck. I need someone to walk me through installing the following:
- Apache 2
- PHP5 with GD
- Ruby on Rails
- Perl (optional)
- MySQL
- PhpMyAdmin

I also need help with setting it all up (I've done it before in a windows environment, but never in Linux). I could for example need help setting the appropriate security settings and making sure I have a password for phpmyadmin etc.

I also need someone to teach me how to make it "autostart" whenever I log onto ubuntu. As an added bonus, I would also like to have some simple way of starting/stopping/restarting the services.

One last thing, is it possible to install all this on Ubuntu, and then use the same databases if I install MySQL on a windows partition (on the same machine, duh)?

I hope someone is willing to help me. :)

---

### Post by turinglabs on 2007-07-09
Hello-

You're asking for someone to setup and configure your server for you, quite a large undertaking, especially in this format. You'll get a much better response if you make an attempt at these various tasks and post the problems you are having, one at a time, along with your specific requirements for each.

---

### Post by bukwirm on 2007-07-09
You should be able to at least get a start [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Servers"). Read though that, try some stuff, then ask if you have more specific questions.

It seems likely that you'll want to install the LAMP server version of Ubuntu, which has Apache, MySQL, and PHP pre-installed and configured for you.

All the scripts for starting/stopping/restarting services should come with the application, and usually get put in /etc/int.d/ (for example, "/etc/init.d/apache2 restart" restarts Apache2).

Most services are automatically configured to autostart whenever you turn your computer on.

---

### Post by Nevon on 2007-07-09
After about 19 tries I managed to get everything but Ruby on Rails to work, so I think I'll just forget about that one. 
Thanks anyway guys!

---

### Post by az on 2007-07-09
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)
[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

