---
title: "firestarter"
date: 2005-09-07
forum: The Cafe
---

### Post by gold4tune on 2005-09-07
Now that i have firestarter, i can't share my folder and i cna't browse folder on the other computers on the network (we are behind a router). What should i do...

thx

---

### Post by robert_pectol on 2005-09-07
Why did you install Firestarter?  If you are already behind a router, you probably don't need to bother with a local firewall on your Ubuntu box... especially if you aren't running any outward facing daemons (none on Ubuntu by default).  There are exceptions to this but generally speaking, most users are only inconvenienced by running a local firewall in a scenerio such as this.  There are situations where local firewalls make sense and maybe your situation is one.  But unless you have a compelling reason, just disable it and save yourself the aggravation!

Luckily, you can disable Firestarter and remove it from the startup processes fairly easily using the update-rc.d tool.

---

### Post by gold4tune on 2005-09-07
Oky, thx...  I'm a new linux user...  And i bring some bads habits form windows!!!  thx again

---

