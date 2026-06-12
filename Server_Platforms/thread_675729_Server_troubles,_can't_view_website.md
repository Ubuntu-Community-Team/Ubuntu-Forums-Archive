---
title: "Server troubles, can't view website"
date: 2008-01-23
forum: Server Platforms
---

### Post by twoweektrial on 2008-01-23
Hey, this is one of my first posts so forgive me if I do something incorrect.

I just installed ubuntu LTS LAMP server, i put a website in /var/www that has worked on other servers. When I put my IP or my domain name in my browser I cannot connect. I am forwarding port 80 correctly, and I haven't done anything fancy.

I've tried installing a few other OSs (netbsd, slackware, gentoo) and wasn't a big fan and switched, I'd never gotten it to work on those among other things, perhaps one of those messed with my router's configuration? I don't know, so if any of you can help I would appreciate it. Let me know what information I need to post and I will.

Thanks
-Bean

---

### Post by burbankmarc on 2008-01-23
this may sound stupid, but are you sure apache is started, and are you sure /var/www is your document root?

---

### Post by twoweektrial on 2008-01-23
yes, and yes. apache is on, and /var/www is the default

---

### Post by omgitsjeckle on 2008-01-23
Are you able to access your site through localhost at all? My reason for asking, is prehaps your router does not support loop back; I know this is the case with my AirPort Extreme and I have to access through a different router to be able to view my sites through the external IP or domain names. 

*shrug* This may or may not be the problem in your case, but something possibly worth looking into.

---

### Post by scizzo on 2008-01-23
The OSes shouldn't mess or even touch the router config. This sounds more like the server is not responding or simular. Are you getting any error in the browser and test the thing that twoweektrial said.

---

### Post by twoweektrial on 2008-01-24
I can access it through localhost, I've never had this problem before, just after this most recent reformat, which leads me to believe the router problem mentioned isn't my deal : (. Thank you anyway though, and I appreciate any help you guys give.

---

