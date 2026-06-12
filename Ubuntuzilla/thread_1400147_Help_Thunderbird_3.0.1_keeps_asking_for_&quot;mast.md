---
title: "Help: Thunderbird 3.0.1 keeps asking for &quot;master password&quot;"
date: 2010-02-06
forum: Ubuntuzilla
---

### Post by jobbesat on 2010-02-06
I'm on karmic and just updated Thunderbird to version 3.0.1.
It seems everything's fine, it imported all my preferences, mails, addresses and so on, but when i start thunderbird it asks for a master password which i don't have!
Is there a way to get rid of this request?
Thanks a lot in advance

---

### Post by nanotube on 2010-02-06
> **jobbesat said:**
> I'm on karmic and just updated Thunderbird to version 3.0.1.
It seems everything's fine, it imported all my preferences, mails, addresses and so on, but when i start thunderbird it asks for a master password which i don't have!
Is there a way to get rid of this request?
Thanks a lot in advance

either it's something that got ported from your previous porfile, or you accidentally set... try starting with a fresh profile.

---

### Post by ramseys on 2010-03-08
I fixed the problem myself by deleting the master password, which in my case was also the root password. I do not remember entering it into thunderbird 3, but I did copy my profile over from thunderbird 2, so that may have been the case.

---

### Post by costre on 2010-03-12
How did you accomplish this? I copied all my settings from my old thunderbird installation, and the new thunderbird keeps asking me for this password. I have tried my root password, my PGP-password, nothing works. 

How did you "delete the master password"?

[EDIT]
After browsing the preferences in Thunderbird for .. three seconds ... I found the settings I was looking for :)
But I still can't disable it, since I don't know what it is! Or why Thunderbird is asking for it!

[EDIT 2]
I found a solution! By deleting key3.db in ~/.thunderbird/YOURPROFILE/ the password got reset, or disabled, or something. All is well, I even got PGP working with an update suggested by Thunderbird!

---

