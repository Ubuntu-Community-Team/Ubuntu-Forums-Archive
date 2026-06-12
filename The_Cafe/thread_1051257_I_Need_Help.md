---
title: "I Need Help"
date: 2009-01-26
forum: The Cafe
---

### Post by shadowman444 on 2009-01-26
Im a complete idiot. I got sick of having people enter my computer so I changed my username and password and I forgot my username. Is there any way to get back in to change my username back?

I have Ubuntu Gnome Version 2.22.2
Is there a way to get to a terminal and perhaps activate my root account without logging in?

---

### Post by Tomosaur on 2009-01-26
> **shadowman444 said:**
> Im a complete idiot. I got sick of having people enter my computer so I changed my username and password and I forgot my username. Is there any way to get back in to change my username back?

I have Ubuntu Gnome Version 2.22.2
Is there a way to get to a terminal and perhaps activate my root account without logging in?

Reboot your machine and log in to the root terminal (recovery mode), then use the following command to find users with a home directory:

```

cat /etc/passwd | grep /home

```

If you haven't added new users, your own user account will normally be lasted last.

---

