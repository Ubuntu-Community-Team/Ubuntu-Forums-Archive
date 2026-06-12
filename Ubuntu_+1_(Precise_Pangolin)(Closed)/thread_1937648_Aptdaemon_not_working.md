---
title: "Aptdaemon not working?"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by screaminj3sus on 2012-03-08
I was updating yesterday, and got an error that "This task cannot be controlled or monitored", and that aptdaemon may have crashed. I ran the updater again, it asked for my password and completed successfully.

Before that I didn't need my password for running software update or installing apps in ubuntu software center, not it asks for it every time, even after rebooting.

---

### Post by cariboo on 2012-03-08
I don't use either the software centre or update-manager, but I believe it is only update-manager that allows you to update already installed packages without a password.

I personally use synaptic for both installing and updating packages, and I have to enter a password, every time I start synaptic.

---

### Post by tekstr1der on 2012-03-08
> **screaminj3sus said:**
> I was updating yesterday, and got an error that "This task cannot be controlled or monitored"

I previously reported a bug for this problem on the natty release. I was never able to reproduce so it fell off my radar, but other users were affected too so I know it wasn't isolated to my install. 

The report has since expired due to inactivity, but you can re-open if you wish:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/798184](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/798184)

---

