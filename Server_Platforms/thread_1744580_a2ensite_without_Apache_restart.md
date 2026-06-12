---
title: "a2ensite without Apache restart"
date: 2011-04-30
forum: Server Platforms
---

### Post by JoeCoder on 2011-04-30
Hello,

I'm running apache with suexec to run a service for lots of users.  Each user's account is a separate apache site.  On my home page, I want to make it as simple as possible for new users, so I allow the m to sign up on the home page with only a few fields and instantly create a new site.

At first I was using mod_vhost_alias, but I don't think it's possible to make this work with suexec?  service apache2 restart and service apache2 reload all cause a few seconds of downtime.  After creating a site, the first thing I do is redirect the user to it, but with the current setup apache is in the middle of restarting.  I could add a delay in the redirect, but I still don't want to be frequently having downtime for everyone else.

Ideas?

---

### Post by ekool on 2011-05-01
You could write a script to check for new files in the sites-available directory and do an apache reload when it detects something new... but have it only check at say, 15 minute intervals.

There's no ideal solution for what you want without creating at least brief interruptions in Apache though.

---

### Post by volkswagner on 2011-05-01
Are the user you mention system users?

Are the user sites unique domains or subdomains of yours?

I know it is not as elegant, but if the restarts are a big issue AND you can get away with new sites added as a subdirectory you may look into userdir_mod.

If the users are not system users, you can still use the subdirectory approach.  I do have a feeling you won't like this answer... LOL

[www.yourdomain/~username](www.yourdomain/~username) or [www.yourdomain/newusersite](www.yourdomain/newusersite).


Actually [this]("http://httpd.apache.org/docs/2.0/vhosts/mass.html") may be more of what you are after.  Got it from [falko]("http://ubuntuforums.org/member.php?u=184550") from another thread!

---

### Post by ekool on 2011-05-01
> **volkswagner said:**
> Are the user you mention system users?

Are the user sites unique domains or subdomains of yours?

I know it is not as elegant, but if the restarts are a big issue AND you can get away with new sites added as a subdirectory you may look into userdir_mod.

If the users are not system users, you can still use the subdirectory approach.  I do have a feeling you won't like this answer... LOL

[www.yourdomain/~username](www.yourdomain/~username) or [www.yourdomain/newusersite](www.yourdomain/newusersite).


Actually [this]("http://httpd.apache.org/docs/2.0/vhosts/mass.html") may be more of what you are after.  Got it from [falko]("http://ubuntuforums.org/member.php?u=184550") from another thread!

That's pretty cool, new to me! Thanks for the link.

---

