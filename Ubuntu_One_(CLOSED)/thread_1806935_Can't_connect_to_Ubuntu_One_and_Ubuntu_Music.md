---
title: "Can't connect to Ubuntu One and Ubuntu Music"
date: 2011-07-18
forum: Ubuntu One (CLOSED)
---

### Post by volkerbradley on 2011-07-18
My system is Natty with Gnome Shell, 64-bit.
When I open Firefox, I can log into [https://one.ubuntu.com/dashboard/](https://one.ubuntu.com/dashboard/) with my password.
When I open /usr/bin/ubuntuone-control-panel-gtk and try to log in with the same password, I see: Method "CreateItem" with signature "a{sv}(oayay)b" on interface "org.freedesktop.Secret.Collection" doesn't exist.
I also have a paid Ubuntu Music account.  When I bring up the Ubuntu One Music app on my android phone and try to log in, I see invalid email.  The email address is clearly correct.
Can you give me an approach to resolving these problems?  I've spent hours reading various suggestions but none work.

---

### Post by volkerbradley on 2011-07-18
Finally found the answers:
I downloaded and installed the deb file at [https://launchpad.net/ubuntu/+archive/primary/+files/ubuntu-sso-client_1.3.1-0ubuntu1_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/ubuntu-sso-client_1.3.1-0ubuntu1_all.deb)
Afer installing this file, I was able to log in to my Ubuntu One account.
The Ubuntu Music app now allows me to log in.  Just took several hours after I signed up for the service.

---

### Post by duanedesign on 2011-07-18
Awesome! thank you for updating your thread.

thank you,
duanedesign

---

