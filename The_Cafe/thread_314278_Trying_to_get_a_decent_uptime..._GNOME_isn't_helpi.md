---
title: "Trying to get a decent uptime... GNOME isn't helping!"
date: 2006-12-07
forum: The Cafe
---

### Post by BarfBag on 2006-12-07
I ditched Mepis.  As much as I like the stability and maturity of the distro, it's just so hard to use!  So I'm back on Ubuntu.

Anyway, I'm trying to build up a decent uptime.  Right now, I'm close to 24 hours.  It should be fine.  But it's not.  There's a type delay!  The only thing it was doing last night was downloading something.  What's with this?  I suppose I could restart GNOME, but it's so inconvenient.  :confused:

---

### Post by mips on 2006-12-07
> **BarfBag said:**
> I ditched Mepis.  As much as I like the stability and maturity of the distro, it's just so hard to use!  So I'm back on Ubuntu.


May I ask what is so hard to use about Mepis seeing Mepis is basically Kubuntu, just more polished. Can do everything in Mepis you can in Kubuntu ?

---

### Post by bonzodog on 2006-12-07
Whether Gnome works correctly or not should not affect Uptime - The desktop is not a core part of the OS. If you have any doubts, logout, hit ctrl+alt+F1 and issue:

```
$sudo /etc/init.d/gdm restart
```

That will effectively restart X for you without you rebooting.

My uptime is:
```
~ -> uptime
 15:38:26 up 5 days, 21:47,  2 users,  load average: 0.06, 0.14, 0.12

```

---

### Post by BarfBag on 2006-12-07
> **mips said:**
> May I ask what is so hard to use about Mepis seeing Mepis is basically Kubuntu, just more polished. Can do everything in Mepis you can in Kubuntu ?

That's what I thought.  Things just kept going wrong, though.  And a lot of things didn't work.  So I gave up.

> Whether Gnome works correctly or not should not affect Uptime - The desktop is not a core part of the OS. If you have any doubts, logout, hit ctrl+alt+F1 and issue:

Thanks!  That's nice!

---

