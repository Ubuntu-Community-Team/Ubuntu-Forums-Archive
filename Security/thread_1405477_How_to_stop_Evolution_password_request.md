---
title: "How to stop Evolution password request"
date: 2010-02-12
forum: Security
---

### Post by sparky2 on 2010-02-12
After I've booted my machine I can browse the internet over my wireless network just fine, but when I start Evolution email it prompts for my admin password before connecting to ISP. 

Can I automate / avoid my respnse to this password prompt ?

---

### Post by kiranmurari on 2010-02-16
Hi,

It's not asking for admin password. It's asking the current user's password to unlock that user's keyring.

This issue arises if auto-login option is enabled. So, can you confirm if auto-login option is enabled??

Evolution uses the gnome-keyring to store email account passwords, and it is the gnome -keyring that is asking for a password. You can automatically unlock gnome-keyring on auto-login, by setting an empty password to the gnome-keyring so it'll automatically unlock without asking for a password. You can also create an extra gnome-keyring to store the evolution passwords and don't set a password for this one if you want to use a password for the standard gnome-keyring.

Please see the following bug report on launchpad for further details:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264)
   
But using the gnome-keyring gives extra security to passwords storage. If this is disabled, anyone who can access your PC, would be able to peek into the passwords file and know the stored passwords.
   
Hope this helps.

---

### Post by sparky2 on 2010-02-17
Hi Kiran

That sounds like my problem. I am the only user on thsi machine and almost certainly set auto-login during install. Certainly I don't log in to O/S after boot up. 

I went to the link you provided but stumbled at first step:

WORKAROUND * Go to System/Preferences/Encryption and Keyrings;

There is no such entry under System/Preferences ??

Any further suggestions much appreciated.

---

### Post by kiranmurari on 2010-02-17
In Ubuntu 9.10, the place is Applications -> Accessories -> Passwords & Encryption Keys

---

### Post by sparky2 on 2010-02-18
yep, all good now
many thanks

---

