---
title: "Custom compile... Apache &amp; MySql... Start at boot..."
date: 2005-03-29
forum: Server Platforms
---

### Post by CrustyDOD on 2005-03-29
Hey

I'm new to linux OS and i have to say that ubuntu is just cool!
So to my problem :)

I compiled apache and mysql manually (yeah i know i could just use apt-get, but i didn't!:)) and now i want to start them on boot and 'kill' them correctly on reboot/shutdown.

What to put into /etc/init.d folder?

Can i just create 2 files one for each and insert into files just that line that i use when i manually start mysql and apache?
ex: sudo /usr/local/apache2/bin/apachectl start

Where do i have to put scripts to stop them (reboot/shutdown), what folder?

---

### Post by alastair on 2005-03-29
You need to do some research on unix "runlevels" and initscripts e.g.

[http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-boot](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-boot)

But there will be many web docs around that explain this better.

Then, take a simple /etc/init.d service - look at it, strip it down and make a "dummy" test service.
Add the links (S/K) e.g. see :

man update-rc.d

and see what happens.

---

### Post by CrustyDOD on 2005-03-29
Great!
Thanks for that link!

Will see what i came up with :)

---

### Post by alastair on 2005-03-29
Another (possibly) interesting link :

Hands-on Guide to the Debian GNU Operating System
[http://colt.projectgamma.com/tmp/hands-on.html#BSADM-SERVICES](http://colt.projectgamma.com/tmp/hands-on.html#BSADM-SERVICES)

It's OK to play around with this (apache etc.) - I can't see how you'd break anything, and it's a good way to learn.

---

### Post by CrustyDOD on 2005-03-29
That is also good! Now please stop for now with the links  :mrgreen: 

Saw also that there's an example script skeleton... Will be interesting tomorow when i try this :)

One question i currently have is this:
Now i don't want to reboot each time to see if the script works, so is it ok/possible to just run the script ex: "sudo /etc/init.d/apache start" to see if it fires up? Will this gave me the same output as if i would reboot the system?

---

### Post by alastair on 2005-03-30
Yes, perfectly OK to run the /etc/init.d programs manually. In fact, I sometimes do this to stop/start things. The output will be as given on boot/shutdown.

---

### Post by CrustyDOD on 2005-03-30
Works like a charm!

I just copied startup scripts for apache and mysql into init.d, did update-rc.d thingy with defaults, chmoded 755 both scripts, rebooted system, voila :smile: 

And i have learned something new about linux startup thingy!

Thanks!!

---

