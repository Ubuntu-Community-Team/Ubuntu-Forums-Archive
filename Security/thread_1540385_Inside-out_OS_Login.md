---
title: "Inside-out OS Login"
date: 2010-07-27
forum: Security
---

### Post by jskeen on 2010-07-27
Specs:
Lenovo Thinkpad W500
Ubuntu 10.04

I am relatively new to Ubuntu and Linux in general (a few weeks since I seriously started using it).  So far, everything has functioned properly and I have been pleased.  But today I decided to fiddle around and try to get the fingerprint reader working.  After an hour or two, I had installed a few different packages and poked around enough to realize that it just wasn't going to work.  I then locked my screen and walked away.  When I returned I correctly entered my password, but it gave me the message, "Not permitted to gain access at this time."  After clicking "Switch User" and entering my password again, I was greeted with "Permission denied."  After freaking out for a few minutes I realized that typing random characters as a password would log me in.  I logged out and tried other random characters.  It logged in.  Logged out, typed my password. "Password denied."  I uninstalled everything I installed (I think), but it still only authenticates a user with an incorrect password.  Any ideas?
BTW: typing password for sudo commands still works properly.  It is only the login that is problematic.

---

### Post by Bachstelze on 2010-07-27
It's probably caused by something you've done while trying to make your fingeprint reader work.  It will probably be quite tedious to find out what it is and revert it, so I'd just reinstall.

---

### Post by stlsaint on 2010-07-28
Have you tried changing the password?

---

