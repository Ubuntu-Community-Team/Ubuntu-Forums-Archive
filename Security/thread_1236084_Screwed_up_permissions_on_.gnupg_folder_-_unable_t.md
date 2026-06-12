---
title: "Screwed up permissions on .gnupg folder - unable to fix with chown"
date: 2009-08-09
forum: Security
---

### Post by ahawesome on 2009-08-09
As you can probably tell, I am unable to access any of my encryption keys or the .gnupg folder under my normal user account. However I can access them as root. I have tried chown to change permissions, but it has only seemed to make things worse. Am I using this command incorrectly? I think I have tried: ```
sudo chown alexhamlin.alexhamlin ~/.gnupg
```but it doesn't seem to work (and yes, I think i've tried running it without sudo). I can only access the folder (and my keys via Seahorse) as root. If it helps, the output of 'ls -lah ~/.gnupg' is:

```

ls: cannot access /home/alexhamlin/.gnupg/pubring.gpg~: Permission denied
ls: cannot access /home/alexhamlin/.gnupg/.: Permission denied
ls: cannot access /home/alexhamlin/.gnupg/random_seed: Permission denied
ls: cannot access /home/alexhamlin/.gnupg/trustdb.gpg: Permission denied
ls: cannot access /home/alexhamlin/.gnupg/gpa.conf: Permission denied
ls: cannot access /home/alexhamlin/.gnupg/..: Permission denied
ls: cannot access /home/alexhamlin/.gnupg/secring.gpg: Permission denied
ls: cannot access /home/alexhamlin/.gnupg/pubring.gpg: Permission denied
ls: cannot access /home/alexhamlin/.gnupg/gpg.conf: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
-????????? ? ? ? ?                ? gpa.conf
-????????? ? ? ? ?                ? gpg.conf
-????????? ? ? ? ?                ? pubring.gpg
-????????? ? ? ? ?                ? pubring.gpg~
-????????? ? ? ? ?                ? random_seed
-????????? ? ? ? ?                ? secring.gpg
-????????? ? ? ? ?                ? trustdb.gpg

```

Also, when attempting to retrieve a key, I get these messages:

```

gpg: failed to create temporary file `/home/alexhamlin/.gnupg/.#lk0x90612b0.apc.24404': Permission denied
gpg: keyblock resource `/home/alexhamlin/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/alexhamlin/.gnupg/.#lk0x9061330.apc.24404': Permission denied
gpg: keyblock resource `/home/alexhamlin/.gnupg/pubring.gpg': general error

```

As I said before, I tried chown to change the ownership to my username (alexhamlin), but it doesn't seem to work. Thank you in advance for any help.

---

### Post by ahawesome on 2009-08-09
I'VE RESOLVED THE ISSUE! To do this, I set the permissions of the .gnupg folder and the files in it to the settings on the LiveCD. I will post a how-to later of how to fix this.

---

### Post by ahawesome on 2009-08-09
HOWTO

If you are unable to access your encryption keys and/or are having problems with gpg/the .gnupg folder in your home directory, do the following:

1. Start Nautilus as root by pressing Alt+F2 and typing 'gksudo nautilus'. Enter your password if prompted.
2. Go to your home directory (click 'Up', then double-click the 'home' folder. Double-click the folder with your username).
3. Show hidden files (press Ctrl+H)
4. Find the .gnupg folder, right click it, and select 'Properties'. Go to the 'Permissions' tab.
5. Set the permissions as follows:

Owner: your username
Folder access: Create/delete files
File access: ---

Group: your username
Folder access: none
File access: ---

Other
Folder access:none
File access: ---

Execute: A blank orange box (not unchecked or checked)

See Image 1 for more info.

6. Click 'Close'. Then, double-click the .gnupg folder. Select all the files in it, right click them, and select 'Properties'. Go to the permissions tab.
7. Set everything as follows:

Owner: your username
Access: Read and write

Group: your username
Access: none

Others
Access: none

Execute: unchecked

See Image 2 for more info.

8. Click close. Close the file browser. You should now be able to use gpg normally. To keep from ever having to do this again, remember to NEVER RUN GPG AS ROOT!!! Run it as yourself.

---

### Post by lightstream on 2009-12-02
Or just use the 'recursive' flag on chown:

```
sudo chown -R alexhamlin.alexhamlin ~/.gnupg
```

---

### Post by Amndeep7 on 2012-11-06
Sorry for bringing this thread back up, just wanted to say that lightstream's solution worked.

---

### Post by wildmanne39 on 2012-11-07
Old thread closed.

---

