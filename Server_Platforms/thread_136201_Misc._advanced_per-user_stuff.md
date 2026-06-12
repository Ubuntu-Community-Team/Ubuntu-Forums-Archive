---
title: "Misc. advanced per-user stuff"
date: 2006-02-25
forum: Server Platforms
---

### Post by colo on 2006-02-25
Hello there,

I'm considering running dapper, once it's gone final, on my server box hosting things for a few of my friends and me. I'd like to do a few nifty things on a per-user-basis, however, I'm not quite sure about how to realise those. Tips and suggestions on how to implement the following would be highly appreciated!

#) I'd like to run a non-virtual hosting environment, in which every user got a sub-directory in his ~, accessible only by himself (and the httpd, of course). However, I'm not sure about if there's a mechanism allowing the httpd (I'd like to stay away from apache2 and use lighttpd instead, if possible) to do some kind of "multiple chroot" at a time - so that the instance of lighttpd serving [http://domain.example/~user1/](http://domain.example/~user1/) may not mess up ANYTHING in user2's $HOME/public_html, which is to be accessed via [http://domain.example/~user2/](http://domain.example/~user2/)

#) There are ulimits for things like maxlogins, maxnprocs and so on, which I'm going to use. However, I'm looking for a way to restrict a user's possibility to bind programs to sockets(ports) above 1024, so that, say, user1 is allowed to bind to ports 30001-30100, user2 to bind to 30101-30200, and so on. Is there anything less compliacted than SELinux (I heard it was possible to do so with SELinux, but I don't really want to have to dig into that) enabling this for me?

#) It's crucial for me to monitor which user (and ideally, which user's files served via http as well) account how much traffic. I would be very happy if there was some tool you could point out out there allowing me to set per-user quotas for traffic just as I'm doing right now with diskspace, which I have missed as of yet.


That's everything for now, I guess.

Great thanks for spending your precious time with reading this posting, have a nice day!

Cheers,
- colo

---

### Post by colo on 2006-03-21
*bump*

---

### Post by al108 on 2006-03-25
As this is an advanced stuff you're taliking about here I would suggest to start looking for your answers in Debian community. No offence to anybody but Ubuntu hasn't been out as long and most users here are just starting.
[http://www.debian.org](http://www.debian.org)
[http://www.aboutdebian.com/](http://www.aboutdebian.com/)


Good luck
Alex

---

### Post by peanut butter on 2006-03-25
if u findanything about that tell me im looking for something similar

---

