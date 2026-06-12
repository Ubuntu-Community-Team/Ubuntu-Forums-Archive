---
title: "Just a heads-up for Gwibber users..."
date: 2009-10-31
forum: The Cafe
---

### Post by Keyper7 on 2009-10-31
Current version has a security problem that some people might not like.

Basically, it stores your passwords as plain text gconf keys ([launchpad bug](https://bugs.launchpad.net/gwibber/+bug/400120)) and, unlike Pidgin, does not offer an option to avoid saving them if you don't want to ([launchpad bug](https://bugs.launchpad.net/gwibber/+bug/421728)). The developers acknowledge this issue: Gwibber is supposed to use the gnome-keyring, but the implementation is buggy and disabled for the development version. However, this development version ended up being packaged for Karmic.

I'm currently using it anyway because I encrypt my home folder (which is where my gconf keys are, correct me if I'm wrong), but I'm posting this to warn anyone who's unaware.

---

### Post by Tibuda on 2009-10-31
Pidgin stores your passwords in a text file in your home folder.

---

### Post by Keyper7 on 2009-10-31
> **danielrmt said:**
> Pidgin stores your passwords in a text file in your home folder.

...and offers the option of *not* saving your passwords if you don't like this.

Gwibber does not.

---

### Post by pwnst*r on 2009-10-31
> **Keyper7 said:**
> ...and offers the option of *not* saving your passwords if you don't like this.

Gwibber does not.

told.

i never choose to save passwords for anything other than a forum or two.

---

### Post by Keyper7 on 2009-10-31
> **pwnst*r said:**
> i never choose to save passwords for anything other than a forum or two.

I never save passwords except when I have no choice. Currently, the apps that give me no choice are NetworkManager, Empathy and Gwibber.

But the first two at least use the keyring.

---

### Post by Keyper7 on 2009-10-31
Moderators, I'm not sure if this is more appropriate for the Cafe or the security forum. Feel free to move the thread if you think it should be somewhere else.

---

### Post by Keyper7 on 2009-11-04
Bumping, as the bug reports are completely silent and I feel this is important to share.

---

