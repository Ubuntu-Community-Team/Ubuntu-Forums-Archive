---
title: "another no0b gufw question"
date: 2011-05-24
forum: Security
---

### Post by al111 on 2011-05-24
GUFW...can I just set it and forget it?

Basically, I installed it (with graphic interface), checked 'ENABLED', minimized it, and now it sits on the left side of my panel....

I'm a Windoze refugee, where everything needed to be configured and tweaked to death...

Is GUFW just that easy, or am I missing the big picture?

All I do really is surf, check email and login to a few forums....

thanks-

---

### Post by mikewhatever on 2011-05-24
If that's all you do, there is no need for a firewall. It's safe to disable it and uninstall the graphical front-end.

---

### Post by al111 on 2011-05-24
You're probably right, but is gufw doing anything by default, or does it have to be configured to work (block anything)?

---

### Post by bodhi.zazen on 2011-05-24
> **al111 said:**
> You're probably right, but is gufw doing anything by default, or does it have to be configured to work (block anything)?

gufw is a graphical front end to ufw which in turn is a command line front end to iptables (which in turn is a front end to net filter).

gufw configures your firwall. Once it is configured you can close the graphical tool and your firewall will be active.

You can see all the rules if you wish 

```
sudo iptables -L -v -n
```

this migh thelp

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

as will reading the security sticky ;)

Most Desktop users do not need to activate their firewall and of those that to

```
sudo ufw enable
``` is sufficient without installing gufw.

gufw is helpful if for some reason you need to configure or change the default rules.

---

### Post by al111 on 2011-05-24
@bodhi.zazen

Thanks!

---

