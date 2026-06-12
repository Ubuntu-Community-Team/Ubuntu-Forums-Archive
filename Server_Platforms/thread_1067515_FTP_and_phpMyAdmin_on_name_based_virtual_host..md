---
title: "FTP and phpMyAdmin on name based virtual host."
date: 2009-02-11
forum: Server Platforms
---

### Post by skunkbad on 2009-02-11
Ubuntu 8.04 Server
Name based virtual hosts

I have phpMyAdmin installed, but how could I make it so that each website on my server had a seperate phpMyAdmin? Maybe each website just needs a different user with different access rights?

Any tutorials?

Also, how to control each website FTP, so that users can't access each other's websites, but only their own. Right now I use SSH through Filezilla to access like FTP, but I think I just need standard FTP.

---

### Post by Poleh on 2009-02-12
phpmyadmin is set up to be multi-user so it's best to only install it once and then let your mysql users log in to that. Everything you see within phpmy admin is controlled by what you're allowed to see in mysql - so you definately don't need to have multiple instances of phpmyadmin for each user...

---

### Post by skunkbad on 2009-02-12
OK, I'm figuring it out. Thanks for your input.

---

