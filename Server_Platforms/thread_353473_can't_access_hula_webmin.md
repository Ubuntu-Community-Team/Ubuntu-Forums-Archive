---
title: "can't access hula webmin"
date: 2007-02-04
forum: Server Platforms
---

### Post by reckless2k2 on 2007-02-04
I've installed the LAMP stack on Ubuntu 6.10 then added Hula following the instructions from the Ubuntu Hula wiki. Despite it saying that everything started fine, I can't access WebAmin to setup accounts and such. Can anyone help?

[http://myserver:89](http://myserver:89) produces unable to connect error. I can't login via [http://myserver:8080](http://myserver:8080) either. If I type [http://myserver](http://myserver) I can navigate to the hula folder and that starts as if I logged in to [http://myserver:8080](http://myserver:8080) but I obviously can't access since no users have been setup. 

I'm sure it's something simple I'm missing. I've tried to reboot as well with no luck. 

Any help would be appreciated. My wife really wants to get the calendar sharing feature up and running for the whole family.

---

### Post by Mave^ on 2007-02-04
Try [http://myserver:10000](http://myserver:10000) or [https://myserver:10000](https://myserver:10000) 8)

---

### Post by reckless2k2 on 2007-02-04
I mis-printed webmin ([http://myserver:10000](http://myserver:10000)) instead of the webamin tool used for hula ([http://myserver:89)](http://myserver:89)). I'm looking to access the WebAdmin GUI for Hula.

---

### Post by reckless2k2 on 2007-02-04
Are there by any chance any Hula guru's in this forum or have a good tutorial on another open source calendar server?

---

### Post by dwar on 2007-02-07
There are 2 versions of hula.
The old one with a control pannel(You have to start it first, i beleve "hulamanager" or some).
The new version without controlpannel, only a commandlinetool, "hula-admin"

---

