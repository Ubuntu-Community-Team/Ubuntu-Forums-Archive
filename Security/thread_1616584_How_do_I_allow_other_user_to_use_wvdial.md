---
title: "How do I allow other user to use wvdial"
date: 2010-11-08
forum: Security
---

### Post by lonewolf454 on 2010-11-08
I have (my) main account, which I have root access.  I also have other users which can login, I setup wvdial shortcut on their desktop, but it won't allow them to use it because they aren't in sudoers list.  I do not and don't want them to have access to other hard drives or root. How do I accomplish this?  I did a chown on the wvdial file in ppp to myself, and added read access for other users, but still won't let them use wvdial due to sudoeers.

This is in ubuntu hardy with a multiboot vista/xp/hardy laptop.  BTW, wvdial works great in my account/desktop.

---

### Post by sisco311 on 2010-11-08
Add the users to the **dip** and **dialout** gruops:
```
sudo gpasswd -a **username** dip
sudo gpasswd -a **username** dialout
```

See: [uhelp]community/DialupModemHowto/SetUpDialer[/uhelp]

---

### Post by lonewolf454 on 2010-11-08
No go, same problem.  

user Not in sudoers file, this incident will be reported.

---

### Post by sisco311 on 2010-11-08
> **lonewolf454 said:**
> No go, same problem.  

user Not in sudoers file, this incident will be reported.

Run the command as a regular user, don't use sudo.

---

### Post by lonewolf454 on 2010-11-08
Duh, I should have tried that, here now on the guest account.  However, now pap/chap secrets flaky problem,

 Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Nov  8 18:44:44 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8564
--> Using interface ppp0

ideas?  As I said, internet does connect, dont want security problems though. Thanks for the help-

---

