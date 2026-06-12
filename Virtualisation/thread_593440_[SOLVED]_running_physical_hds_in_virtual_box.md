---
title: "[SOLVED] running physical hds in virtual box"
date: 2007-10-27
forum: Virtualisation
---

### Post by campkillgemma on 2007-10-27
Im running ubuntu gusty gibbon with win xp in a vm. How do I get my vm to see my physical hard drive to transfer files? I have looked at the other threads in this fourm and nothing seems to work.

Id be very grateful if you can help

---

### Post by Steve1961 on 2007-10-27
Decide which folder on your hard drive you want to share, then enter those details in the shared folders section of the virtualbox settings.  Launch XP, open the dos prompt and type:

net use x: \\vboxsvr\sharename

This would create a drive X under my computer.  Make sure you change 'sharename' to whatever your shared folder is called

Note: there is a space between x: and \\

---

### Post by campkillgemma on 2007-10-27
Its working now, Thank you  :D

---

### Post by Steve1961 on 2007-10-27
Easy once you know how :)

---

