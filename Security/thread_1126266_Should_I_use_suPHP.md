---
title: "Should I use suPHP?"
date: 2009-04-15
forum: Security
---

### Post by scooter77 on 2009-04-15
I'm setting up an Apache web server which is going to run several PHP applications as well serve some static pages. Some of these applications have MySQL databases and of course the DB credentials have to be stored in files accessible to the PHP scripts. This is not a shared hosting environment, it's a dedicated server. Nevertheless, I'm concerned that one little  PHP application that someone installs and forgets about may have some security vulnerability in it that would allow an attacker to execute arbitrary code as the web server user, which would allow them full access to all the databases for all the other applications.

I'd like to limit the amount of damage an attacker could do even if he did exploit one of the applications. I'm thinking of using suPHP and running each PHP application that stores sensitive data (such as DB passwords) as a separate user and allowing access to the sensitives files for the application only to this user. Is this the way to go or would anyone recommend some other way to achieve the same goal?

On a more general note, are there any more "preventative" security steps to take to harden a web server, apart from this, mod_security and the Suhosin patch?

---

### Post by drubin on 2009-04-15
I haven't ever needed this but I know shared hosting do something similar. You don't ever want to have issues like the one mentioned [here]("http://ubuntuforums.org/showthread.php?t=302137").

So as for the suphp it sounds like a plan but I don't know if that is the best package to use or if there is any others. I will ask around and see if any one I know has used this or something similar.

---

### Post by scooter77 on 2009-04-16
Thanks, that would be good.

open_basedir is something to consider as well. Should I use it in addition to suPHP?

---

### Post by drubin on 2009-04-16
> **scooter77 said:**
> Thanks, that would be good.

open_basedir is something to consider as well. Should I use it in addition to suPHP?
I never used either, but I think the standard install of cpannel uses open_basedir (cpannel is used on most hosting providers).

So I think going with both couldn't hurt. Post back how it worked out and if there was any thing serious you need to change/config to get it up and running. I am pretty interested to know the outcome. 

Maybe set up a base install in a VM and that way you can always revert back if something doesn't work with your current configs. once that is stable repeat the steps for dev/live. :)

---

### Post by drubin on 2009-04-16
> **scooter77 said:**
> Thanks, that would be good.

open_basedir is something to consider as well. Should I use it in addition to suPHP?
I never used either, but I think the standard install of cpannel uses open_basedir (cpannel is used on most hosting providers).

So I think going with both couldn't hurt. Post back how it worked out and if there was any thing serious you need to change/config to get it up and running. I am pretty interested to know the outcome. 

Maybe set up a base install in a VM and that way you can always revert back if something doesn't work with your current configs. once that is stable repeat the steps for dev/live. :)

---

