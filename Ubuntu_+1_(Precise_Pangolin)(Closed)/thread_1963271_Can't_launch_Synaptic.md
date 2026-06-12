---
title: "Can't launch Synaptic"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by normcross on 2012-04-22
If I try to run Synaptic from Launcher or Dash I get a requester for password. Once entered, the requester disappears and nothing happens.

I can only successfully run Synaptic from a Terminal with sudo synaptic. 

Is this just me?

---

### Post by rburkartjo on 2012-04-22
works fine on my end no problems

---

### Post by Frogs Hair on 2012-04-22
I don't have this problem . Usually when the password dialog disappears it is due to an incorrect password. If you are able to launch it from the terminal this would not apply . I would attempt reinstalling it. There was bug related to synaptic and the Gnome Shell on 12.04.

---

### Post by cariboo on 2012-04-22
@normcross, if you open a terminal and type:

```
gksu synaptic
```

what happens?

---

### Post by mc4man on 2012-04-22
> **Frogs Hair said:**
> Usually when the password dialog disappears it is due to an incorrect password.  I would attempt reinstalling it. There was bug related to synaptic and the Gnome Shell on 12.04.

When the password box disappears it generally means the password was correct

currently synaptic can be started from gksu (or sudo though not a good idea), though the current default is to use policy-kit to auth

So from terminal that would be (repeated attempts should be from  new terminals
```
synaptic-pkexec
```

In any event when getting an accepted password but synaptic fails to show maybe then open ~/.xsession-errors, scroll to end area & see if any related error message

---

### Post by szabouk on 2012-04-22
perhaps this will help

```
rm  /var/cache/apt/*.bin
```

---

### Post by normcross on 2012-04-22
reinstall was no help.

@cariboo907, using gksu synaptic it opens fine.

@Mc4man, Ah, we're getting somewhere. synaptic-pkexec I get the password dialog and then:- (synaptic:2226): Gtk-WARNING **: cannot open display: :0

---

### Post by mc4man on 2012-04-22
Well you've messed something up as far as permissions or related
(can't say I've seen this with pkexec, so can't offer a for sure fix

From man pkexec - 
> The environment that PROGRAM will run it, will be set to a minimal known and safe environment in order to avoid injecting code through LD_LIBRARY_PATH or similar mechanisms. In addition the PKEXEC_UID environment variable is set to the user id of the process invoking pkexec. As a result, pkexec will not allow you to run X11 applications as another user since the $DISPLAY and $XAUTHORITY environment variables are not set. ..ect.

You may want to create a new administrator user, log in & see if synaptic starts ok.

If so you could switch over to that user.

If someone can't fix & you don't want to or can't use a new user then a fresh install will solve

A hack would be to edit synaptic.desktop to use gksudo instead but that really is a poor solution & doesn't address the real issue

---

### Post by normcross on 2012-04-22
Ok, understood. I would have quite happily carried on using the terminal, but you're quite right. If you don't just bury a problem, but fix it, then it will never come back and haunt you.

I'll try a new user  and if not re-install. 

Many thanks for all the help.

---

### Post by normcross on 2012-04-23
This problem was completely solved with a fresh install.

---

