---
title: "Firefox issue with Apparmor"
date: 2010-07-20
forum: Security
---

### Post by PHANTOM X on 2010-07-20
I followed the guide on generating a profile in apparmor for firefox and now it starts then closes out. I've tried following the rest of the code, but none works.

---

### Post by Rubi1200 on 2010-07-20
Put the profile in complain mode so you can log when errors are generated.

Open a terminal and run this:

```
tail -F /var/log/messages
```then try starting Firefox and see what errors you get.

It might also be helpful if you post the profile here so that someone can take a look at it.

Hope this helps.

---

### Post by PHANTOM X on 2010-07-21
> **Rubi1200 said:**
> Put the profile in complain mode so you can log when errors are generated.

Open a terminal and run this:

```
tail -F /var/log/messages
```then try starting Firefox and see what errors you get.

It might also be helpful if you post the profile here so that someone can take a look at it.

Hope this helps.

I tried that. Said command not found.

I'm not sure how to do that. Pretty new to Ubuntu and apparmor.

---

### Post by FuturePilot on 2010-07-21
There's no need to create a profile for Firefox from scratch. Use the one that is included with Ubuntu.

[https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?]("https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?")

---

### Post by PHANTOM X on 2010-07-21
> **FuturePilot said:**
> There's no need to create a profile for Firefox from scratch. Use the one that is included with Ubuntu.

[https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?](https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?)

Didn't know that. Just following the guide. Ended up reinstalling Ubuntu. Cool.:)

---

