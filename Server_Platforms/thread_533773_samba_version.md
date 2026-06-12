---
title: "samba version?"
date: 2007-08-24
forum: Server Platforms
---

### Post by Nevstah on 2007-08-24
i realise this subject has been discussed before, but i thought i would touch on it again...

i'm running 6.06 LTS server and have samba version 3.0.22 installed by apt, which insists all is up to date.

current samba release is 3.0.25c and i was wondering if there is a reason apt doesnt upgrade this version? are there known problems? or should i upgrade it manually? it strikes me 3.0.22 is a year old and may not be as secure as it should be?

many thanks

nev

---

### Post by p_quarles on 2007-08-24
The applications available in distro-based repositories are rarely the same version as the most current source package. This is because they all have to be packaged to work with the specific distro. Your version of Samba is "up-to-date" in the sense that Canonical still supports Dapper with security patches. 

In other words, even though your version number is a year old, it will still get patched with security updates (if any).

---

