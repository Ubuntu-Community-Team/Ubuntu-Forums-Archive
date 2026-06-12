---
title: "minimum disk size for JeOS"
date: 2008-10-22
forum: Server Platforms
---

### Post by rgerhards on 2008-10-22
Hi,

I hope this is the right place for this kind of question (if not, please bear with me, I am new to the forum...).

I am trying to create a virtual logging appliance and Ubuntu JeOS looks very appealing to me. This is my first shot at this. What I need to install is a simple base system, LAMP, rsyslog and phplogcon. I ended up with a .vmdk size of roughly 800MB after I cleaned out anything I did not need. As a .tar.gz, it is around 320MB.

Quite honestly, I had expected a somewhat smaller disk size. Can anybody provide me some idea if that is within the expected range or if I likely messed up somewhere (I re-tried the install and ended up at a similar result).

Feedback is appreciated.

---

### Post by cariboo on 2008-10-22
That looks about the right size  for a basic server installation with lamp.

Jim

---

### Post by rgerhards on 2008-10-23
excellent. This makes me feel much better that I did not do anything wrong (of course I did, but it is not yet soo obvious ;)).

Thanks!

---

### Post by EmmEff on 2008-10-23
Don't forget to do a 'apt-get clean' to remove the package cache (/var/cache/apt).  That will clear out 200+ MB.

---

### Post by eyebuntu on 2009-05-08
I'm sure by now you've already setup your appliance, but anyone stumbling upon this as I did while looking up something else might consider turnkey linux:

[http://www.turnkeylinux.org/appliances/bootstrap](http://www.turnkeylinux.org/appliances/bootstrap)  -- 67 Meg
[http://www.turnkeylinux.org/appliances/core](http://www.turnkeylinux.org/appliances/core)         -- 102 Meg
[http://www.turnkeylinux.org/appliances/lamp](http://www.turnkeylinux.org/appliances/lamp)        -- 154 Meg

Choose your starting point from core all the way up to, in this case, a LAMP setup that's probably very close to what was wanted.

---

### Post by windependence on 2009-05-09
FreeBSD would be eve smaller, and using lighthttp for the web server would save even more space.

What exactly would this appliance do that it needs LAMP?

-Tim

---

