---
title: "SeamlessRDP auto login/logoff"
date: 2010-09-22
forum: Virtualisation
---

### Post by Frgo10 on 2010-09-22
So, I've got seamlessrdp up and running on a XP guest in vbox, the only thing thats left is to make the vm run headless and the rdesktop command on ubuntu boot. However, I do still have to login and logout at the front-end of XP "physically" and thus killing the seamless part of RDP.

The auto login is not a problem as it can easily be configured in XP, it's the auto logoff thats bugging me!
What I've thought of so far is to set XP to automatically logoff after a sec of inactivity, and while that would work great for the initiall startup, it would be pretty useless while actually using remote apps, or does perhaps the remote connection itself  counts as "activity"?

---

### Post by CharlesA on 2010-09-25
Once you connect to an XP by with RDP, it is "locked." However, once you disconnect/logoff from a RDP session, it is not unlocked, so you'd have to unlock the machine from the "physical" console.

---

