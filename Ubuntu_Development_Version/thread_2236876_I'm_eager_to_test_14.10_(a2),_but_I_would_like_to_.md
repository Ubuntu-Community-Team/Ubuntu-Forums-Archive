---
title: "I'm eager to test 14.10 (a2), but I would like to do without LXQT"
date: 2014-07-29
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2014-07-29
14.10 (alpha 2) is due for release [s]on July 31st[/s] in the first days of August.

However, I wonder if upgrading to Utopic (a2) won't turn my WHOLE system upside down, i. e. change everything in the base (GUI) system to QT versions? (including lxpanel and loads of others).

I would like to get all the updates (especially some of the major core updates, libstdc++6 v4.8 -> 4.9 etc) EXCEPT for the QT replacements for LXDE (since they're way too unstable still).

Is there any way to accomplish this, or is the only option for me to wait for 14.10 (final) if I want to keep all my GTK-based LXDE stuff?

---

### Post by bapoumba on 2014-07-29
I tried to install LXQt on Utopic > broken dependencies. LXQt is available from a ppa though, so if you do not work with this particular ppa, you will continue to have the regular lubuntu. LXQt wont probably make it to Utopic, I'l have to check the mailing list again for the schedule, 

I highly recommend you disable all ppa and third party repositories you may be using should you choose to upgrade, will save you time and trouble. You may even consider reverting all installed packages to their current Trusty version with ppa-purge. Will take less time to reinstall your stuff from ppas after upgrading (provided they have working packages for Utopic) rather than fix a broken upgrade.

Anyway, LXQt is quite nice :)

---

### Post by ibjsb4 on 2014-07-29
It is necessary to add the lxqt ppa, to get the qt respiratory, but as bapoumba has said, Its broke.

---

### Post by syntaxerror74 on 2014-07-29
> I highly recommend you disable all ppa and third party repositories you  may be using should you choose to upgrade, will save you time and  trouble.

Yes, that's a good advice.

> **ibjsb4 said:**
> It is necessary to add the lxqt ppa, to get the qt respiratory, but as bapoumba has said, Its broke.

You can't surprise me with that. :twisted:

BTW, beware, it's also in [Lubuntu daily repository]("https://launchpad.net/~lubuntu-dev/+archive/ubuntu/lubuntu-daily"). That's what I think is most insane! All the LXQT stuff should be neatly *separated* from Lubuntu daily so that people only install it who explicitly want it. Had I the will to "subscribe" to L-daily, I would probably already have messed up my whole system by this experimental QT stuff. Hey, thanks a lot.

---

### Post by bapoumba on 2014-07-29
But, but, but, if you do not install the lxqt-metapackage or other lxqt related packages, it wont jump at you like that, or I need to reconsider what I know of package managers and ppas :D

---

### Post by ibjsb4 on 2014-07-29
> **syntaxerror74 said:**
> You can't surprise me with that. :twisted:
BTW, beware, it's also in [Lubuntu daily repository]("https://launchpad.net/~lubuntu-dev/+archive/ubuntu/lubuntu-daily"). That's what I think is most insane! All the LXQT stuff should be neatly *separated* from Lubuntu daily so that people only install it who explicitly want it. Had I the will to "subscribe" to L-daily, I would probably already have messed up my whole system by this experimental QT stuff. Hey, thanks a lot.

Oh..
I guess things have been changed around since I installed, good to know.  Thanks

..Now you got me wondering if it works :)

---

### Post by syntaxerror74 on 2014-07-29
> **ibjsb4 said:**
> Oh..
I guess things have been changed around since I installed, good to know.  Thanks

You can bet your bottom dollar that they have. You're welcome.

---

### Post by syntaxerror74 on 2014-08-01
WHOHOO!

Everything worked perfectly - I'm on Utopic (a2) now! And gladly no LXQT to see anywhere so far in the package installation log...(feels very good :P)

---

### Post by ibjsb4 on 2014-08-04
> **syntaxerror74 said:**
> And gladly no LXQT
Yes, just like bapoumba said :)

---

### Post by sammiev on 2014-08-04
but like any test version you can expect some breakage. That is where the fun begins. :)

---

