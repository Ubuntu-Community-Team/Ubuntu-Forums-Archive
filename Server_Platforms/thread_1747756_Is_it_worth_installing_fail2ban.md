---
title: "Is it worth installing fail2ban?"
date: 2011-05-03
forum: Server Platforms
---

### Post by rainleader on 2011-05-03
Is installing fail2ban on a standard LAMP stack running Ubuntu 10.10 worthwhile? I've read mixed reviews across the net, what do you think?

Also, does it ship with reasonable/sensible defaults or is it a blank/empty configuration out of the box?

Thanks in advance for your help.

---

### Post by falko on 2011-05-03
I'd always install fail2ban to prevent break-in attempts. For SSH and Apache, the defaults should work; for other services you might have to tweak the configuration (take a look at [http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p5](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p5) ).

---

### Post by a2j on 2011-05-04
it works great for me.

---

### Post by rainleader on 2011-05-05
Thanks guys.

---

