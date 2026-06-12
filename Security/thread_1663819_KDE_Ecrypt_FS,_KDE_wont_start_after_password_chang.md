---
title: "KDE: Ecrypt FS, KDE wont start after password change"
date: 2011-01-10
forum: Security
---

### Post by roomey on 2011-01-10
Summary: Error when launching KDE, can't log in 
Error: kstartupconfig4 can not be launched or failed error code 3. 
 
It seems Users profile password was changed using graphical KDE tool, but this did not update the encryption password.
Logged in via terminal (ALT+F2). Manually mounted encrypted directory using  mount-private-directory command, then asked user to change their  password using command line passwd. This properly updated both  encryption passphrase and profile password. User can now login.

---

