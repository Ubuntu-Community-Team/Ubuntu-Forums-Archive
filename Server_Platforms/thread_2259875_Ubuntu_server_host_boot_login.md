---
title: "Ubuntu server host boot login"
date: 2015-01-07
forum: Server Platforms
---

### Post by Roel_Schimmer on 2015-01-07
I have succesfully installed Ubuntu server 14 but when i boot it asks me to login to my host? Don't know what that means nor what i must type in.
Help please?

[http://rbgeek.files.wordpress.com/2012/06/119.jpg](http://rbgeek.files.wordpress.com/2012/06/119.jpg) <----This

---

### Post by Doug S on 2015-01-07
Hi and welcome to Ubuntu forums,

It just wants you login.

First, and what is in the screen shot you provided, it is asking for your username. Your username should be the one you providing during the installation sequence (I mean I assume you haven't added any other users yet). Next it will ask for your password, which you should also have setup during the installation sequence.

 Note that it will not echo your typing during password entry, and we get many questions from people thinking something is broken at this step. It isn't broken.
 
Hope this helps.

Edit: And Oh, by the way it seems you installed version 12.04 and not 14.04, based on your screen shot.

---

### Post by MAFoElffen on 2015-01-07
Welcome to Ubuntu Forums.

But... If server services are installed, those services "load" on boot. You don't usually need to log into the physical server unless you need to. (And I usually do that through ssh.) Your configured services, for example some type of file share, domain services, dhcp, dns, web services, etc... are loaded and their specific listners are listening to be connected to over your network through their specific ports.

After the initial install, thats when the personalized work starts after the install to configure your specific settings...

Most my server sit their running, without any kind of a local user for most of their life. They are configured that way, in case the server goes down (for some reason), it boots back up and the services are back up (unattended service). 

But yes, it you need to log into it locally, enter the credentials you configured during the install, or afterwards, if you added other user accounts.

---

