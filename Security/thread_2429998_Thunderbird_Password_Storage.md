---
title: "Thunderbird Password Storage"
date: 2019-10-26
forum: Security
---

### Post by janvi2 on 2019-10-26
installed Ubuntu 18.04 Desktop almost without complaints what contained the Thunderbird Mail Client. I transferd my pop/smtp accounts from W10 thunderbird 60.9.0 by copy of the xxxxxx.default directory and changed profiles.ini to point to that data. I can see accounts and mail successfully and even access to the mail server seems ok. Obviously, the passwords for all accounts are not stored inside the default data directory. Thunderbird always asks for the password and repeats every time regardless if I tick the checkbox "Use Password Manager to remember this password". 

Edit->Preferences->Security->SavedPasswords refuse to show any stored passwords and the "ShowPasswords" button reimains grey. This way, its impractically to use the mail client. Afterward I remember that I installed KeepassXC to transfer my passwords from old W10 PC: Therefore I removed another unknown password manager. Probably it was the one used by thunderbird. Unfortunately I cannot remember its name to re-install.  Suggestions like  thunderbird reinstall?

---

### Post by janvi2 on 2019-10-27
Workaround: Create all accounts new, enter passwords again and accounts are functional. Then only copy mail directories without modifying profiles.ini into newxyz.default profile directory. 
Incompability of W10 data seems to come with absolute path c:\users\jv\appdata instead /home/jv/snap/thunderbird/.... inside prefs.js

---

