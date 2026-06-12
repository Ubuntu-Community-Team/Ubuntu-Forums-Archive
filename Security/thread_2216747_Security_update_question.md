---
title: "Security update question"
date: 2014-04-13
forum: Security
---

### Post by gabmuks on 2014-04-13
[ATTACH=CONFIG]252023[/ATTACH]

This screen pops up when I try to install updates from automatic update manager.
Should I disregard this warning?

I do not know what these updates are for.
I just trust that Update Manager has selected the correct updates.

Will it be safe to install these updates?

Thank you for your time.

---

### Post by cariboo on 2014-04-14
I'd suggest you open a terminal and run:

```
sudo apt-get update
```

Then run the update manager again, the untrusted packages message should go away.

---

### Post by gabmuks on 2014-04-14
> **cariboo907 said:**
> I'd suggest you open a terminal and run:

```
sudo apt-get update
```

Then run the update manager again, the untrusted packages message should go away.
Yes that worked!

Thank you much!

I will close this thread

---

### Post by gabmuks on 2014-05-07
[SIZE=3][/SIZE]Am having problem with updates again.

The "sudo apt-get updates" does not work anymore.

The message I keep getting from update manager is: [SIZE=3][B]"Requires installation of untrusted packages."


[/B][/SIZE]

If I click on "Details", it says:**[SIZE=3] "gthumb gthumb-data"[/SIZE]**

Does anyone know why this happens and how to fix?
It only happens on my laptop computer. Never happens with my desktop PC.

---

### Post by cariboo on 2014-05-07
It looks like you may have check for updates in Software & Updates to something other than daily, or notification is set to weekly. I run Utopic, so I update a couple of times a day, so I never see any notification.

---

