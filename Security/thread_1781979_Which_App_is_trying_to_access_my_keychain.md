---
title: "Which App is trying to access my keychain?"
date: 2011-06-14
forum: Security
---

### Post by farproc on 2011-06-14
I am used to, on starting Ubuntu on my Netbook, being prompted with a password challenge to open my Keychain required to authenticate against the WPA enabled WiFi network.

Now, Ive recently installed Ubuntu on a desktop PC, along with some dev tools (Code::Blocks etc.) but it gives me a keychain access challenge about 4 times on startup. I can't seem to figure out which app is trying to (get my permission to) access my keychain, and for what Purpose.

(By contrast: on my Mac, when an application tries to open the keychain, the application, its certificate, and the search data of the matching key that will be accessed are all displayed making it much easier to determine what app is being naughty) How do I do simular diagnostics with Natty?

When I cancel these requests, nothing "breaks".

---

### Post by farproc on 2011-06-27
nothing?

---

### Post by FuturePilot on 2011-06-28
Ubuntu One?

---

### Post by farproc on 2011-08-03
That does seem to be the culprit. Well, I can only assume it is. Still no way I can see to really *know*.

---

### Post by cariboo on 2011-08-03
If you disable auto-login, you won't have to enter a keyring password.

---

