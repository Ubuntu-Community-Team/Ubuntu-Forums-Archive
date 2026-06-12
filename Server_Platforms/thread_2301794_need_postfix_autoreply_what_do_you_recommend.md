---
title: "need postfix autoreply what do you recommend"
date: 2015-11-05
forum: Server Platforms
---

### Post by Gorm_Lindbk on 2015-11-05
Hi
what do you recommend for postfix autoreply?
Gorm.

---

### Post by SeijiSensei on 2015-11-05
You can set up an autoreply if you [install procmail]("http://wiki.kartbuilding.net/index.php/Procmail_-_setup_with_postfix") as the default delivery agent.  You can see an example of how to set up the autoreply here: [http://linux.die.net/man/5/procmailex](http://linux.die.net/man/5/procmailex)

Procmail is the default agent on RedHat-flavored distributions and has been for years, but I don't think that is the case for Debian/Ubuntu.  It's basically the "swiss-army-knife" of mail tools.

---

