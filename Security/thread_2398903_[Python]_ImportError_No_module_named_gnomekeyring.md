---
title: "[Python] ImportError: No module named gnomekeyring"
date: 2018-08-19
forum: Security
---

### Post by amx23112 on 2018-08-19
Hi all,

In an effort to minimize the time spent typing in passwords, I have setup my laptop (Ubuntu Budgie 18.04) to sign in through bluetooth automatically if my raspberry pi is nearby. The pam module I am using is libpam_blue. When I am not at home (read: near the raspberry pi) I want to only be able to authenticate using my password. It works beautifully but needs some tweaks. 



The gnome-keyring does not prompt for a password when I sign in with my password (it matches).
When I sign in from bluetooth it always prompts for a password (passwords do not match).

What I am looking for is a command I can use to script the keyring unlocking automatically but only after signing in from bluetooth. To check the sign in method I was thinking about using /var/log/auth for log entries.



I have tried looking for ways to unlock the keyring. The most promising way I can find is from Python. I found a simple python script:

```

#!/usr/bin/python
import gnomekeyring
gnomekeyring.unlock_sync(None, 'password');

```

I am seeing an error however that the module gnomekeyring cannot be imported (no module named gnomekeyring).



Some alternatives:

[LIST]
[*]empty keyring password: not a good idea because after an unauthorised sign in (passwords can be changed from single user mode), all passwords are exposed
[*]making login keyring the default keyring: same as above
[/LIST]


Can anyone knowledgeable in Python explain why the module gnomekeyring cannot be found or knows a solution?

Thanks for taking the time to read this!

---

### Post by The Cog on 2018-08-19
That font is horrible. It really makes my eyes hurt as I try to read it. 

The command "apt search keyring" lists amongst others a package python-keyring. Info on this "apt show python-keyring" looks as though it might be what you want. Try "sudo apt install python-keyring".

---

