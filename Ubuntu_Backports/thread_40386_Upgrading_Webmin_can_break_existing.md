---
title: "Upgrading Webmin can break existing"
date: 2005-06-08
forum: Ubuntu Backports
---

### Post by emendelson on 2005-06-08
This is about the 1.21 version of Webmin that's currently in staging.

A few weeks ago, I used the Upgrade Webmin module that's built into Webmin to upgrade it from 1.08 to 1.20. The upgrade went perfectly.

A few days ago, I tried to upgrade Webmin to the 1.21 version currently in the Backports staging. The result was that Webmin was no longer usable - I couldn't log in, and I couldn't uninstall it with apt-get. I ended up restoring my system from a backup.

If you already upgraded Webmin from inside it - be warned! Don't upgrade it a second time from the repositories. 

I haven't tried uninstalling my 1.20 Webmin, but I suppose that's probably the best thing to do before upgrading from the repository.

EDIT - I did manage to uninstall webmin by using the uninstall.sh command suggested on the webmin FAQ. This left broken packages from the initial install from the respositories; a few dpkg -r --force-remove attempts didn't fully clear them out. But installing and then removing from Synaptec seems to have cleared everything out nicely.

Thanks.

---

### Post by szdavid on 2005-08-06
[QUOTE=emendelson]This is about the 1.21 version of Webmin that's currently in staging.

A few weeks ago, I used the Upgrade Webmin module that's built into Webmin to upgrade it from 1.08 to 1.20. The upgrade went perfectly.

A few days ago, I tried to upgrade Webmin to the 1.21 version currently in the Backports staging. The result was that Webmin was no longer usable - I couldn't log in, and I couldn't uninstall it with apt-get. I ended up restoring my system from a backup.

If you already upgraded Webmin from inside it - be warned! Don't upgrade it a second time from the repositories. 

I haven't tried uninstalling my 1.20 Webmin, but I suppose that's probably the best thing to do before upgrading from the repository.

EDIT - I did manage to uninstall webmin by using the uninstall.sh command suggested on the webmin FAQ. This left broken packages from the initial install from the respositories; a few dpkg -r --force-remove attempts didn't fully clear them out. But installing and then removing from Synaptec seems to have cleared everything out nicely.

Thanks.[/QUOTE]
 Hello, 

I have got the same problem ; but i am not able to find the uninstall.sh script ; could you say me where to find it on the web ?

Thx

---

### Post by calt129 on 2006-01-20
This should be normally under */etc/webmin/uninstall.sh*. If you don't find it there, you can search for it with either:
```
sudo updatedb; locate unintall.sh
```
or:
```
sudo find / -name uninstall.sh
```

---

### Post by InfernalH on 2006-01-20
I can't understand why ubuntu version of webmin is so old, I'm not able to install any additional modules because they're all available only with the newest version (1.250)

---

### Post by calt129 on 2006-01-23
I've written a howto, see here:
[http://ubuntuforums.org/showthread.php?t=120533]("http://ubuntuforums.org/showthread.php?t=120533")

---

### Post by Velvet Elvis on 2006-01-24
Thanks! I've had this same problem though I never touched the backports packages.

---

