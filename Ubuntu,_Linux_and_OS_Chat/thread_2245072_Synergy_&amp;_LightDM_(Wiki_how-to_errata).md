---
title: "Synergy &amp; LightDM (Wiki how-to errata)"
date: 2014-09-20
forum: Ubuntu, Linux and OS Chat
---

### Post by Greg_Kerr on 2014-09-20
I don't know how to fix a wiki page  ... would be could to have a comments section like WikiPedia.

[https://help.ubuntu.com/community/SynergyHowto?action=login&login=1](https://help.ubuntu.com/community/SynergyHowto?action=login&login=1)

If one follows the instructions on that page on how to add synergy to ligthdm - one ends up with a non-bootable system.

Because there is no lightdm.conf, creating it and adding the line:

greeter-setup-script=/myscriptpath

Causes lightdm to fail startup with "Failed to load configuration from /etc/lightdm/lightdm.conf: Key file does not start with a group"

It needs '[SeatDefaults]' to precede it.


(Ubuntu 14.10 dev)

---

### Post by cariboo on 2014-09-21
You should be able to use your SSO login ID to log in and edit the wiki page.

---

### Post by spinningmonkey on 2015-03-30
Thanks for the post Greg_Kerr, this helped me. I've updated the documentation.

---

