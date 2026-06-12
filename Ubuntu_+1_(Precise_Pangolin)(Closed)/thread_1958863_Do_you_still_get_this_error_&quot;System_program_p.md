---
title: "Do you still get this error &quot;System program problem detected&quot;"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shuttleworthwannabe on 2012-04-15
It has been with me since the Alpha 2 days--so I installed afresh the using daily build from 13 April 2012 x64 version. With all the current updates/upgrades. What app do you think is causing this? How do I check what is causing this?

---

### Post by xyzzyman on 2012-04-15
> **shuttleworthwannabe said:**
> It has been with me since the Alpha 2 days--so I installed afresh the using daily build from 13 April 2012 x64 version. With all the current updates/upgrades. What app do you think is causing this? How do I check what is causing this?

What happens when you report the problem?

---

### Post by phibxr on 2012-04-15
I have the same issue, and when I opt to report the issue I get "This problem has already been reported", with no further information.

---

### Post by shuttleworthwannabe on 2012-04-15
same here. Wonder what this means?

---

### Post by Gyokuro on 2012-04-15
Have you already tried to clean up /var/crash? After that the message should go away.

---

### Post by cariboo on 2012-04-15
The message is normal when running a development version, the message should stop popping up within the next couple of days as we transition to the final versions of the packages that will be included in the final release.

Apport is set to report almost any crash during the development cycle, even if it something small that doesn't affect the way your system operates. The sensitivity will be changed before the final release to report only major crashes that do affect the way things work.

---

### Post by exploder on 2012-04-15
The error has not shown up for me for a few days now but I do appreciate the explanation cariboo907 provided.

---

### Post by jbicha on 2012-04-15
You can disable those automated crash reports by editing /etc/default/apport. Those reports will be disabled automatically in the next few days any way.

---

### Post by shuttleworthwannabe on 2012-04-16
Thanks, I thought as much--but wanted to be sure it was not just me.

---

### Post by ventrical on 2012-04-16
I have  had a few of my machines reporting this and then , others not. My Dell Inspiron B130 has yet to report an apport crash since the development transition in December.

---

### Post by rburkartjo on 2012-04-16
jb tks for the info

---

