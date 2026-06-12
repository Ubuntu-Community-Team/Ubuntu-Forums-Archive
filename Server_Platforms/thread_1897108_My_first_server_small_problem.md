---
title: "My first server small problem"
date: 2011-12-18
forum: Server Platforms
---

### Post by Rifts on 2011-12-18
Hey guys! 

I just finished this tutorial
[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

everything works perfectly, I can add a website and it's open to the internet. 

The problem I'm having is this, I installed phpmyadmin when I go to mywebsite.com/phpmyadmin the page loads fine, I enter my login details but when I hit submit the page just refreshes and nothing happens, no errors nothing.

I searched and read through a few long posts about it and none of them solved the problem.

As this is my first server I'm not really sure what to do or where to start now?

if you need any information just let me know.

thanks

---

### Post by dargaud on 2011-12-18
[haven't read the page you link] but before phpmyadmin can work you need to do a few things manually with mySQL, namely give a password to the root admin (this is entirely different from the linux 'root' user). From there you should at least have a functionning phpmyadmin.

If not, check the access.log and error.log files. It's a good idea to place a "tail -f error.log" on them before doing something that doesn't work in a browser.

---

### Post by brighty22 on 2011-12-18
I've never experienced that with phpMyAdmin, but the first thing I'd do is clear your browser cache, cookies.. the lot, then close all instances of your browser and try again. pMA can be quite fussy.

If that doesn't work, have a look in the pMA config file.. can't tell you where it is on your system as I use the manual install from the pMA website (it's far easier to customize imo). Specifically the authentication section - you may need to set a blowfish secret or change the authentication method to session or cookie.

If still no luck, try logging into mysql using the cli interface - if that works you can be sure the problem lies with pMA.

---

### Post by Rifts on 2011-12-18
see the weird thing is no matter what login info I enter I get no errors it just refreshes the page and nothing happens.

heres a link to my site to see what I mean

<snip>

---

### Post by brighty22 on 2011-12-18
> **Rifts said:**
> 
<snip>

Times out. Check your router.

---

### Post by Rifts on 2011-12-18
sorry its back up now

---

### Post by Rifts on 2011-12-18
well just for the heck of it I tried using firefox instead of chrome and it works perfectly then went and restarted chrome and tried again still doesn't work on there....

wtf?

---

### Post by brighty22 on 2011-12-18
Yep.. fussy :)

Have you completely cleared all of your browsing data in Chrome?

---

### Post by Rifts on 2011-12-18
Yeah I've done that like 8 times lol

---

### Post by Dry Lips on 2011-12-18
Are you logging in with the phpmyadmin **root** account or one you've created? Try to enter **root **as the
user and then use your MySQL root password... I remember having similar trouble, but I was always able
to login via root.

---

### Post by Rifts on 2011-12-18
yeah I only use root

---

