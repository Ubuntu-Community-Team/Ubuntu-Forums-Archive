---
title: "Google Auth for GUI login works.  tty allows login without 2 factor how to fix"
date: 2015-10-17
forum: Security
---

### Post by MechaMechanism on 2015-10-17
Two factor GUI login is working for LightDM.  I use Google Authenticator.  However I can log on without two factor authentication using just a password on the virtual terminals, tty1,2,3 etc.  How do I fix this security loophole.  I want to enable Google Auth for all log ons, ssh, tty*, GUI.

I have full disk encryption with a long complex password.  For user log ons I have set the machine to use easier to remember passwords with two factor auth for local accounts and made sure no SSH server or any other server is present.

Any help is appreciated.  If you help me I will report back with success or failure.

---

### Post by veddox on 2015-10-19
A quick DDG search turned up this: 

[http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/](http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/)
[http://www.allyourlinux.com/blog/ubuntu-how-to-disable-extra-ttys-in-upstart](http://www.allyourlinux.com/blog/ubuntu-how-to-disable-extra-ttys-in-upstart)

I haven't tried it myself, so there is no guarantee that it works, and use at your own risk. I couldn't find anything on how to use Auth with a tty. But if you can disable the non-graphic ttys, that should be you set up, shouldn't it?

BTW, don't forget to disable root login via grub.

---

### Post by MechaMechanism on 2015-10-19
I already knew about the SSH one.  I don't want to disable the tty because sometimes I use about 3 or 4 at once.  I'll contact the Google Auth upstream src and see what they say.

---

