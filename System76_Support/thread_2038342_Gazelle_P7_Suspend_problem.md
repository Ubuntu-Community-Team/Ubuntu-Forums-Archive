---
title: "Gazelle P7 Suspend problem"
date: 2012-08-06
forum: System76 Support
---

### Post by MarkID on 2012-08-06
I posted this in the GazP7 thread and got no response.  Here it is on its own.

I have two new GazP7 and the suspend issue has occurred on both of them. Approximately one out of three or four times, when I open the lid, I get a black screen and a cursor. The machines are less than a week old, so I assume they have the most current kernel. Any ideas? Otherwise pretty slick machines, and with the SSD, boot and app start up times are almost instanateous.

---

### Post by ufugu on 2012-08-10
I'm having this too on a two week old Gazp7. It's not every time, but it doesn't resume properly every three or four wakes. The first time was when I was showing a friend my awesome new Linux laptop--he just laughed.

Kernel is 3.2.0-27-generic.

What is the recommended fix?  I thought this issue had been resolved.

---

### Post by isantop on 2012-08-10
> **ufugu said:**
> I'm having this too on a two week old Gazp7. It's not every time, but it doesn't resume properly every three or four wakes. The first time was when I was showing a friend my awesome new Linux laptop--he just laughed.

Kernel is 3.2.0-27-generic.

What is the recommended fix?  I thought this issue had been resolved.

Make sure you both have the most recent updates (there was a new kernel update recently), then run this command in a terminal and send me the output:

```
uname -r
```

---

### Post by cprofitt on 2012-08-12
Has the suspend issue been resolved?

---

### Post by ufugu on 2012-08-12
FWIW, this problem seems to go away if I suspend from gnome-shell instead of Unity.

Maybe it's complete coincidence, but I'm going to wait a few more days and see if it ever locks up using gnome-shell (so far I've woken up about a dozen times without issue, still using 3.2.0-27-generic).

---

### Post by philbert on 2012-08-12
> **ufugu said:**
> FWIW, this problem seems to go away if I suspend from gnome-shell instead of Unity.

Maybe it's complete coincidence, but I'm going to wait a few more days and see if it ever locks up using gnome-shell (so far I've woken up about a dozen times without issue, still using 3.2.0-27-generic).

After the most recent updates the current kernel is at 3.2.0,29-generic.
I did see this behavior a couple of times with 3.2.0-27-generic but I have not seen it yet with the current kernel level.

Until today.....sigh.

---

