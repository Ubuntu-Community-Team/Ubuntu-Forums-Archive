---
title: "[SOLVED] Ubuntuzilla accessing the Internet for updates - how to stop - how do I??"
date: 2007-09-23
forum: Ubuntuzilla
---

### Post by nowshining on 2007-09-23
ubuntuzilla in my logs show that it is checking the net for a newer version - if I uninstall it it leaves an orphaned lib file and if I remove that firefox will refuse to start up - so anyway I can stop it from accessing the internet.

---

### Post by nanotube on 2007-09-23
> **nowshining said:**
> ubuntuzilla in my logs show that it is checking the net for a newer version - if I uninstall it it leaves an orphaned lib file and if I remove that firefox will refuse to start up - so anyway I can stop it from accessing the internet.

hi,
yes, ubuntuzilla checks for version updates. this way if mozilla changes site layout, the update notifications will still be able to come through after an ubuntuzilla update.

if you want to stop it, you can uninstall the ubuntuzilla package.

i don't know what you mean by "orphaned lib file" - but the solution to that problem is obvious: if removing it breaks firefox, don't remove it. :)

you could also delete the file /etc/cron.daily/ubuntuzillaupdatecron, that will stop the ubuntuzilla auto-update job, as well.

there's also a separate cron job to check for updates to the mozilla products - that one is in your user crontab, and if you want to stop it, you can run ubuntuzilla with "removeupdater" action (see project site for usage details)

---

### Post by nowshining on 2007-09-24
thanks for the info. however it would be great if this stuff is known BEFORE downloading and or installing or while installing the ubuntuzilla program. :) unless of course I have missed it.

---

### Post by nanotube on 2007-09-24
> **nowshining said:**
> thanks for the info. however it would be great if this stuff is known BEFORE downloading and or installing or while installing the ubuntuzilla program. :) unless of course I have missed it.

hehe, yea, you've missed it - this functionality is listed right in the feature list on the main ubuntuzilla site:
[http://ubuntuzilla.wiki.sourceforge.net/#tochome3](http://ubuntuzilla.wiki.sourceforge.net/#tochome3)
(see third item from the bottom in the feature list)

---

