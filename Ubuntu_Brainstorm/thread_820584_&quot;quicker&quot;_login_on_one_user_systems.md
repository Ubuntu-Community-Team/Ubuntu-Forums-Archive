---
title: "&quot;quicker&quot; login on one user systems"
date: 2008-06-06
forum: Ubuntu Brainstorm
---

### Post by tom56 on 2008-06-06
My suggestion is this - on systems where there is only one user, GDM should have autologin enabled for that user and the following command should be set to run in the startup session
```
gnome-screensaver-command --lock
```

When the computer is booted, the user is logged in and their screen instantly locked.

Though login time is essentially the same, the point is that by the time the login screen appears, all programs and panels are loaded. As far as I can tell this is just as secure as logging in through GDM.

This is how I have it set on my laptop so that when I turn it on in the morning I can leave it to boot up whilst I go and make some coffee.

---

### Post by Rufe0 on 2008-06-07
what a good idea

---

### Post by wdaniels on 2008-06-07
> **Rufe0 said:**
> what a good idea

I like that idea too, and I think I might do that with my Eee PC.

Not sure about it being configured as default behaviour though; imagine a new user doing a fresh install with a single user, in which case presumably it would end up configured like this. She then goes and adds a second user, but she doesn't know that she also needs to go and disable the auto login and the lock command... Adding code to the user manager to (un)configure all that for a single user case is not really appropriate.

---

### Post by mikazo on 2008-06-07
Thanks for the good idea, I've set it up for myself also. I was just wondering the other day if there was some way of doing this.

---

### Post by Mazza558 on 2008-06-08
What about the Gnome Keyring? If you have autologin (e.g bypassing GDM somewhat), you still have to enter your password again to get access to wireless.

---

### Post by smartboyathome on 2008-06-08
> **Mazza558 said:**
> What about the Gnome Keyring? If you have autologin (e.g bypassing GDM somewhat), you still have to enter your password again to get access to wireless.

I thought GDM did that for you, and the autologin still goes through GDM, so it would allow this to happen. :confused:

---

### Post by Mazza558 on 2008-06-08
> **smartboyathome said:**
> I thought GDM did that for you, and the autologin still goes through GDM, so it would allow this to happen. :confused:

I'll give it a go now. (I'm on Gutsy though, so might be different.)

---

### Post by smartboyathome on 2008-06-08
> **Mazza558 said:**
> I'll give it a go now. (I'm on Gutsy though, so might be different.)

Shouldn't be, Gutsy and Hardy use the same GDM version because the new one is considered too "unstable" due to the addition of OpenGL compositing via Compiz.

---

### Post by Mazza558 on 2008-06-09
Nope, Still asks for my password after I log in.

---

