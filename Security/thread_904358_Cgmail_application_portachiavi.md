---
title: "Cgmail application: portachiavi"
date: 2008-08-29
forum: Security
---

### Post by dalrmi on 2008-08-29
Hy everybody, not sure if this is the right place to post my question! :confused:

I installed the CGMAIL application, a simple notifier about new mail on my gmail account, everything is ok but each time I log in in my Ubuntu 8.04 I receive the window: see the attached file (Schermata.png).

Sorry for the Italian language but I believe that it's a problem about security configuration, do you know how to configure in order to avoid this message at each logon ?

Thanks everybody will want to help me.

Best regards, Roberto.

---

### Post by forger on 2008-08-29
1) close cgmail
2) execute this command (it will delete your cgmail configuration):
```
rm -rf $HOME/.gconf/apps/cgmail/
```
3) download the latest cgmail (0.5):
[http://cgmail.tuxfamily.org/](http://cgmail.tuxfamily.org/)
double click on the .deb file to install it.
4) run cgmail again, go to edit > preferences, check the autostart("start cgmail automatically...")
Also, at the "Advanced" tab, it might help if you choose "Use a plain file"

Sorry for the english, don't know italian translations of all these :)

---

### Post by dalrmi on 2008-08-29
Thank you Forger, now it's ok, I think that the solution was to set plain text otherwise other method to save the password.

Bye, Roberto.

---

