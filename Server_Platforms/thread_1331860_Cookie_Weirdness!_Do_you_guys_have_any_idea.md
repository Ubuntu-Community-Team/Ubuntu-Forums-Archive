---
title: "Cookie Weirdness! Do you guys have any idea??"
date: 2009-11-19
forum: Server Platforms
---

### Post by sands on 2009-11-19
Cookies are working fine in elinks, but not in firefox. Not just on this machine (localhost), viewing from other machines too. I made a fresh install of ubuntu desktop, then taskel lamp, then generated ssl. installed phpmyadmin.

Even phpmyadmin works in elinks, but not in ff. I attached some screenshots. I refreshed the page a million times, bt the same result. 

This is the code I used to test cookies

[php]
<?php 

error_reporting(E_ALL);

setcookie ('test', 'test', time() + 60); 

print_r($_COOKIE);

echo strftime('%c');

?>[/php]Do you guys have any idea??

---

### Post by Drezard on 2009-11-19
Can you take a couple of screen shots of your perferences in Firefox? (I would tell you which page exactly, but on a work pc with IE only)... I'm looking mainly for the privacy settings about cookies.

---

### Post by sands on 2009-11-19
> **Drezard said:**
> Can you take a couple of screen shots of your perferences in Firefox? (I would tell you which page exactly, but on a work pc with IE only)... I'm looking mainly for the privacy settings about cookies.

Hi Drezard,

I appreciate your response. :)
But I think the problem is something with the server. Server machine's firefox is as fresh as Starbucks coffee, so it has the default factory settings. I installed Ubuntu 1 hour before my 1st post. Also, in all the browsers, on other machines that I tested, cookies work fine. I mean, I can login into gmail and other sites fine. This new server is the only site creating this problem.

By the way, this new Ubuntu installation is on a work PC (Actually a Mac) :p
Tell the tech people at your work to upgrade from Windows to Linux, atleast a Mac.. Just kidding :p

---

### Post by sands on 2009-11-20
> **sands said:**
> Hi Drezard,

I appreciate your response. :)
But I think the problem is something with the server. Server machine's firefox is as fresh as Starbucks coffee, so it has the default factory settings. I installed Ubuntu 1 hour before my 1st post. Also, in all the browsers, on other machines that I tested, cookies work fine. I mean, I can login into gmail and other sites fine. This new server is the only site creating this problem.

By the way, this new Ubuntu installation is on a work PC (Actually a Mac) :p
Tell the tech people at your work to upgrade from Windows to Linux, atleast a Mac.. Just kidding :p


I tested it just now. It is working only in Safari, not in FF or Chrome. 
I have adblockplus and firebug installed in FF. 

Also, this is how the domain names are set up

[http://webservices/cook.php](http://webservices/cook.php)
[http://webservices.abc.xyg.edu/cook.php](http://webservices.abc.xyg.edu/cook.php)

Both point to the same server. Also, machine is intranet only.
Do you think it is because of the domain names?

Another clue: cook.php is able to read the cookies already set by xyg.edu (tested only in firefox).

---

### Post by sands on 2009-11-20
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/325266](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/325266)

---

