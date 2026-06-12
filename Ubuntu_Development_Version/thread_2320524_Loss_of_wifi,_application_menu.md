---
title: "Loss of wifi, application menu"
date: 2016-04-14
forum: Ubuntu Development Version
---

### Post by dFlyer on 2016-04-14
Any one else having problems with loss of wifi after suspend or main menus of applications? I know all I have to do is log out to restore menus but wifi requires a hard boot. Most all is working well except for these two minor problems as both have work around. Anyone know of a solid fix for either?

---

### Post by cariboo on 2016-04-15
Up until yesterdays Network Manager updates, I was having the same problem, wireless would still work, but I couldn't see any of the networks I usually see when checking what's available. Running:

```
sudo service NetworkManager restart
```

solved the problem for me.

**Edit:** I guess I spoke to soon, after a kernel update today, the problem is back :(

---

### Post by dFlyer on 2016-04-16
> **cariboo said:**
> Up until yesterdays Network Manager updates, I was having the same problem, wireless would still work, but I couldn't see any of the networks I usually see when checking what's available. Running:

```
sudo service NetworkManager restart
```

solved the problem for me.

**Edit:** I guess I spoke to soon, after a kernel update today, the problem is back :(

At least that works. Still loosing network on suspend. Also noticed suspend doesn't work right away on lid close but will wait for the timeout period to expire. At times with opening the laptop Unity Login Screen freezes, crashes to black screen then auto restarts the login screen. This is on the daily build from the 15th April with all current update.

---

### Post by dFlyer on 2016-04-19
Todays updates doesn't seem to fix anything. Suspend on lid close still now working until the timeout period has expired for non use in my case 10 minute. Suspend does work if I let it time out or I click suspend under main menu. I've notice also that the network crash happens with the suspend issue. Anyone know of a fix for these issues? hopefully they get fixed in the next two days.

---

