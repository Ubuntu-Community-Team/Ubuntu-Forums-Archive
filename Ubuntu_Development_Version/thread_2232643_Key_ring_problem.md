---
title: "Key ring problem"
date: 2014-07-03
forum: Ubuntu Development Version
---

### Post by Ramesh_Jude_Fernando on 2014-07-03
Hi I still seem to be getting keyring login for an old e-mail account I setup for login with empathy. I removed empathy, removed e-mail for that account,  but it persists, and asks for passpord more than a dozen+ times before finally letting me get to the desktop and Unity interface and startup Firefox and/pr Cjrp,es  I followed instructions here
[http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/](http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/)
[http://askubuntu.com/questions/191190/i-continue-to-get-this-when-trying-to-log-into-ubuntu-one-from-the-ubuntu-deskto](http://askubuntu.com/questions/191190/i-continue-to-get-this-when-trying-to-log-into-ubuntu-one-from-the-ubuntu-deskto)

but it doesn't appear to work any suggestions as to how I can remove keyring enter when I restart/reboot  and login newly to my account.  It's very annoying, I noticed a thread back in 2010  about gnome key ring and Ubuntu which did have something in regards to keyring.

---

### Post by philinux on 2014-07-03
Look in your home folder for .local/share/keyrings

You can delete the contents of the sub folders and the system will ask for passwords like from new.

---

