---
title: "Ubuntuone CredentialsError"
date: 2012-10-17
forum: Ubuntu One (CLOSED)
---

### Post by survive on 2012-10-17
Hello everyone, I recently installed Ubuntu 12.0.4 on my Mac. I now dual boot with a Linux partition of about 100GB. I've loved Ubuntu, makes my life quicker and more customizable.

Anyway more to the point: Ubuntuone of course automatically comes with the install. 
When I first launched ubuntuone, I was given the following error:

Sorry, an error has occurred and Ubuntu One needs to close.

Details:

CredentialsError
DBusException(dbus.String(u'Process/usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1'),)

Really in need of a solution, thanks to everyone in advance!
-D

---

### Post by Scooby-2 on 2013-07-01
I have a similar problem on a PC running Ubuntu 12.04 LTS - Firstly I get File Sync error auth failed (AUTH FAILED) then a box headed "Ubuntu One experienced an error" and with "Sorry, an error has occurred and Ubuntu One needs to close."

This thread has had 280+ reads and no replies so I guess it's only us then! I tried to remove and reinstall from [this page]("https://answers.launchpad.net/ubuntuone-client/+faq/778"), but as I have no menu item for Passwords and Encryption Keys under Accessories I am unable to complete it. I've posted separately for that.

Did you get to the bottom of your problem?

Edit: I resolved the missing menu item using
```
sudo apt-get install seahorse
```
as suggested by, and with thanks to [**Irihapeti**]("http://ubuntuforums.org/member.php?u=346442")

---

