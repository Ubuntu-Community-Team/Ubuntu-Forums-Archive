---
title: "Lunar Ubuntu Desktop live: no longer a standard user with a blank password"
date: 2023-02-07
forum: Ubuntu Development Version
---

### Post by sudodus on 2023-02-07
I noticed that the live Lunar Ubuntu Desktop (standard Ubuntu) arrives at a page that prompts to enter user name and password, in other words, there is no longer a standard user with a blank password.

You, who are developing/maintaining community flavours, should keep an eye on possible complications like what affected Lubuntu Lunar, [bugs.launchpad.net/ubuntu/+source/casper/+bug/2004092](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/2004092)

---

### Post by zebra2 on 2023-02-10
I just booted today's Ubuntu ISO. Feb 10, and have no problems.

---

### Post by maglin2 on 2023-02-10
As I understand the bug a 'fix' has been applied that changes the UID used by casper to avoid a clash with systemd-journald.
This fix has been rejected though (to maintain compliance with debian policy), so the next upload should cause regression to the behaviour described by sudodus unless there is a fix applied to systemd before then.

---

### Post by zebra2 on 2023-02-11
As it turns out my Feb 10th ISO didn't require a PW but aborted and attempt to install.  I just install today's Feb 11 Pending ISO and it installed just fine. Putting my programs back now.

---

### Post by sudodus on 2023-02-11
Yes, I notice that too with today's (2023-02-11) daily iso files:

- Lubuntu Lunar *live* still uses the numerical user ID 1000 with the default user name 'lubuntu', and

- Ubuntu Lunar *live* has changed since last time I tested it. Now it behaves like Lubuntu: again uses the numerical user ID 1000 with the default user name 'ubuntu'.

I will keep an eye on this until bug #2004092 is squashed.

---

