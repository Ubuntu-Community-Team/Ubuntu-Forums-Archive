---
title: "Ubuntu server security setup?"
date: 2008-11-03
forum: Server Platforms
---

### Post by WhiteShepherd on 2008-11-03
I have quite a few questions so I hope some of you can help answer where you can?

I currently run a free community service hosting web pages for artists.  I've done this for almost a decade and there is no advertising on my site.  I simply pay the fees for the servers out of pocket and do my best to maintain the server software myself.

Over the years the site has grown to 3,000+ hosted websites.  A few years ago I switched the system to Xampp for win32 with open_basedir.  Performance was good.  However the problem at hand is that as the years progress net kiddies are turning vandalism more into a popular public sport.  We've been hit twice this year via PHP exploits that did a lot of damage to other member accounts.

So I have decided to switch from Windows 2k3 to Linux (Ubuntu) to try and improve the level of security.  From what I've read (aside from patches like Suhosin) while keeping good performance I've read of a couple of ways? 

Of what I've found (suphp)is to put web accounts as their own Linux members so they have no permissions to other member files.  The other (libapache2-mod-chroot) seems to be to chroot Apache or better yet might even chroot each virtual host??  So if they hack a user account they don't have access to other part of the file system.  

Is this the way to go or is there a better solution?  

Also when I looked into Ubuntu server I saw it used Lampp.  A few months earlier I was asking on the Xampp forums about Lampp and they told me to NOT use it in a production environment. Is this not the case, fixed in Ubuntu, or are we expected to add the security?

Looking at all the apache modules (from apt-get) there seems to be zillions of options. :confused:  I'm new to Linux (I can get around but still learning) so if a secure server can be put together with "apt-get" all the better!  

Thanks for any helpful advice.

  WS

---

### Post by WhiteShepherd on 2008-11-03
Or how do some of you handle web member security on your Ubuntu server?

---

