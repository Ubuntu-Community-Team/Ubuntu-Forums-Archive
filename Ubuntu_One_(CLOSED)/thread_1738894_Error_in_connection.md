---
title: "Error in connection"
date: 2011-04-25
forum: Ubuntu One (CLOSED)
---

### Post by arpit22x on 2011-04-25
Hi When I try to connect UbuntuOne, it gives an error -"The process did not finish successfully."
Pl help me to get rid of it.

---

### Post by duanedesign on 2011-04-26
Sorry to hear Ubuntu One is not working as expected. What version of Ubuntu are you using? Where do you see this error? Do you have anything in this file:

~/.cache/ubuntuone/log/syncdaemon-exceptions.log

thank you,
duanedesign

---

### Post by arpit22x on 2011-04-26
Hi,

When I launch ubuntuone on ubuntu Natty, I get two options either to join or I already have account. I have already created an account on one.ubuntu.com but it shows my machine (computer) not connected. I have also tried to join by creating another account but it can't load CAPTCHA used in the process.

the above file tells-

2011-04-26 18:14:31,790 - twisted - ERROR - Unhandled error in Deferred:
2011-04-26 18:14:31,790 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.linux.dbus_interface.NoAccessToken: CredentialsNotFound

---

### Post by arpit22x on 2011-04-26
Now, I have uninstalled and reinstalled ubuntu one. but the problem turns bitter. Now, it says that "unable to find the server at login.ubuntu.com". I have tried many times.

Plz anybody help!!

---

### Post by arpit22x on 2011-04-27
After reading many posts on other blogs, I found that Empathy, ubuntuone do not work behind proxy. This is the case because I use proxy. 

But I have an alternate server also which provides direct connection. But in that case also, both the applications are not able to connect.

Can anybody help!!

---

### Post by Buggrit on 2011-05-05
Plus one here.

Same issue. I've installed Natty and now I'm unable to log-on to Ubuntu one. I can log-on to the web-based Ubuntu One and also access the back-end (normal) sync service directly from my old laptop (Maverick10.10) but not from this fresh install of Natty 11.04.

I have run through the password reset procedure and anyway,  as I can log-on elsewhere, I can be sure it's not a credential issue (it would return a credential issue error message if it was that). So we're left with a problem.

Anyone know how to get past it?

Thanks

JB

---

### Post by Buggrit on 2011-05-05
> **Buggrit said:**
> Plus one here.

Same issue. I've installed Natty and now I'm unable to log-on to Ubuntu one. I can log-on to the web-based Ubuntu One and also access the back-end (normal) sync service directly from my old laptop (Maverick10.10) but not from this fresh install of Natty 11.04.

I have run through the password reset procedure and anyway,  as I can log-on elsewhere, I can be sure it's not a credential issue (it would return a credential issue error message if it was that). So we're left with a problem.

Anyone know how to get past it?

Thanks

JB
Oops. Sorry for the above message. I restarted the computer and tried again. (The Microsoft Solution) and it connected without a hitch.  Ho Hum... nothing to see here... move along now...

JB

---

