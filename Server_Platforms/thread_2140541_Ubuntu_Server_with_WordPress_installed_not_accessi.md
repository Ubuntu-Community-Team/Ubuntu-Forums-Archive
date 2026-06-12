---
title: "Ubuntu Server with WordPress installed not accessible outside Localhost"
date: 2013-04-30
forum: Server Platforms
---

### Post by thezobot1 on 2013-04-30
Hi all,
I have a friend who has setup an Ubuntu server with wordpress installed on it.
When he opens the wordpress installation path on his localhost ie localhost/wordpress for him, it works fine.
When I try to access the wordpress installation from hisserverip/wordpress it gives me an error of some php file not found.
When I visit *just *hisserverip, the default "This is a test page....." comes up.
What changes should I do to make the wordpress installation accessible from hisserverip/wordpress.
Also can these changes be done via SSH?
Thanks for your time,
TheZobot1

---

### Post by Doug S on 2013-04-30
Hi, and welcome to Ubuntu forums,

A [section on wordpress ]("https://help.ubuntu.com/13.04/serverguide/wordpress.html")has been added to the LAMP applications chapter in the Ubuntu server guide. See if that section helps. (It has only been published in the 13.04 guide, but would apply to earlier versions of Ubuntu server also.)
Yes, changes of that section should be able to be done via an ssh session.

---

### Post by tad1073 on 2013-04-30
> **thezobot1 said:**
> Hi all,
I have a friend who has setup an Ubuntu server with wordpress installed on it.
When he opens the wordpress installation path on his localhost ie localhost/wordpress for him, it works fine.
When I try to access the wordpress installation from hisserverip/wordpress it gives me an error of some php file not found.
When I visit *just *hisserverip, the default "This is a test page....." comes up.
What changes should I do to make the wordpress installation accessible from hisserverip/wordpress.
Also can these changes be done via SSH?
Thanks for your time,
TheZobot1

Does he a virtual host set up?

try this, a2dissite sitename then a2ensite sitename

---

