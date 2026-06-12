---
title: "Apache Not Serving Multiple Sites"
date: 2007-11-20
forum: Server Platforms
---

### Post by ctlw83 on 2007-11-20
Hey all,

I have Feisty running Apache and MySQL, yes I know I should upgrade but, having a RAID setup made the initial install a headache so, upgrading will have to wait.

Anyway, I have managed to get Apache to serve out one of the virtual hosts' sites live to the net.  (it isn't up right now though as the server is off when I go to work)  However, PHPMyAdmin, won't work, and neither will any other sites.  I do have name-based virtual server set up for each domain I want to serve as well as my PHPMyAdmin and they are in the sites-active directory.

My Webmin application does work though, but is not located in my /vars/www/ folder but, in a different one.  PHPMyAdmin is in /vars/www/ as are all of the sites I want to run live. 

I will post my configurations and such in the morning but, any ideas off-hand?

I've tried setting the alternate sever names to:
localhost/websitename
127.0.1.1/websitename
192.168.2.120(internal network IP)/websitename

and none of these make a difference at all.

At first I thought it might be a router loopback issue but, I can access the one site that works both through the internal network IP and through the site address on-line (when the server is on).  I can also access webmin through my network IP as well, but, again I can't access PHPMyAdmin or any other sites.

Thanks a bunch.

God Bless,
Chris

---

### Post by reckless2k2 on 2007-11-20
well let's take it one step at a time. did you install phpmyadmin from apt-get or synaptic? if so then you have to symlink it to /var/www. then when you restart apache it'll work. when you fudge around, you have to restart apache and possibility mysql depending on what you are doing.

---

### Post by ctlw83 on 2007-11-20
I did an Apt-Get install and it worked fine originally,  but, I did mess with Apache's settings a while back.  It wasn't serving the sites with the default setup either, so I removed the default virtual server and started from scratch.  I have restarted Apache and MySql several times with no change.

Webmin, which aslo uses MySQL is working but, again, it isn't in with the other sites like PHPMyAdmin is.

I'll post what all of my configuration files have tomorrow morning.  That will probably make whatever mistake I have made more apparent.

I tried re-installing PHPMyAdmin today and that didn't work either.

What exactly is a symlink? I have no idea how to do that.

---

### Post by twistedtwig on 2007-11-21
a symlink is a symoblic link from one place to another in your system.  As I understand it it is a "bit" like a shortcut in windows.  It points to another place.  But it takes it a bit further.  It actually looks like the folder to the view.  You can quiz and use it like it was acutally there.

Not sure how security works on it. (I think it is what ever is set on the "real" folder.

---

### Post by ctlw83 on 2007-11-21
OH, ok.  Then I think I do have a symlink because the phpmyadmin folder does have a little arrow above it.

---

### Post by ctlw83 on 2007-11-21
Ok,

I got it to serve out both existing sites now.  The problem was Webmin was only making sites in httpd.conf and not making individual entries in sites-available and sites-enabled.  I have since fixed that.

However, phpmyadmin still won't load.

not sure what I should do about that.

God Bless,
Chris

---

### Post by reckless2k2 on 2007-11-21
check the phpmyadmin.conf file in apache2 directory. sounds to me like it's not configged right. i don't know if you want to view on another computer or not. if so you have to change from localhost to your domain.

---

