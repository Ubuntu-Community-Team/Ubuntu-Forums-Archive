---
title: "New Sign-on Dialogue Box"
date: 2021-07-21
forum: Security
---

### Post by electrosteam on 2021-07-21
Lubuntu 21.04
5.11.0-25-generic

Laptop with auxiliary monitor.
Normal power-on is both displays the same with identical sign-on dialogue boxes, with user name shown in full,
Background is default - a pleasant flowery display in mottled greens and browns.

Power on an hour ago.
It showed a new dialogue box with user shown as first name on the auxiliary monitor only
Colors were dark green/blue with a symbol of a flame to the left of the dialogue box.
Dark neutral color on the laptop.

Cycled the power.
Both displays came up as normal.
Security upgrade prompted, and installed.

Was that a security threat ?
Is there anything else I should do ?

John.

---

### Post by guiverc on 2021-07-22
> **electrosteam said:**
> 
Normal power-on is both displays the same with identical sign-on dialogue boxes, with user name shown in full,
Background is default - a pleasant flowery display in mottled greens and browns.


This sounds like `sddm` which is correct & normal

> **electrosteam said:**
> 
Power on an hour ago.
It showed a new dialogue box with user shown as first name on the auxiliary monitor only
Colors were dark green/blue with a symbol of a flame to the left of the dialogue box.
Dark neutral color on the laptop.


This sounds more like a xscreensaver unlock box; are you sure you didn't suspend?

(the xscreensaver login will look a little like [https://i.stack.imgur.com/OspNh.png](https://i.stack.imgur.com/OspNh.png) which is a very old version; but as the creators of xscreensaver don't like their logo being altered, Lubuntu don't touch it... It's got a little more color today; but it's still equally ugly in my opinion today as it was when this picture was taken in 2009)

You seem to be describing two different lock screens that both exist in Lubuntu. The greeter (`sddm`) which you get before a user has logged in, plus the lock screen when a user is logged in but has locked the session because they're away.  I frequently *suspend* this desktop overnight, so I see the `xscreensaver` login when I wake it in the morning.

---

### Post by electrosteam on 2021-07-22
guiverc,

Thanks for that, I feel a bit sheepish.
Not sure how it got into that state as for the few years running Linux, I have never suspended, but I will now do some experimenting.

Keep well,John.

---

