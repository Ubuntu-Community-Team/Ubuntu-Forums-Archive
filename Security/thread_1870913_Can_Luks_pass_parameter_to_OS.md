---
title: "Can Luks pass parameter to OS?"
date: 2011-10-28
forum: Security
---

### Post by mogliii on 2011-10-28
Hi,

I have a general and more hypothetical question:

Is it possible with LUKS full system encryption to define multiple passwords, and depending on the password to pass a parameter to the booting OS?

Scenario: One is forced to unlock the system. The normal password used would be A, but instead B is entered, which is configured to make LUKS pass a parameter to the OS after unlocking.
The parameter can then trigger a script which is executed during boottime (eg. delete files/folders and then the script itself).

Do current versions have such a feature? Are there similar ideas around?

Many thanks

---

### Post by HermanAB on 2011-10-28
Howdy,

LUKS supports multiple passwords, but it won't give any information away.

---

