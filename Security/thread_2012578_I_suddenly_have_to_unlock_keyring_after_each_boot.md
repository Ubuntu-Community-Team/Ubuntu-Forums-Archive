---
title: "I suddenly have to unlock keyring after each boot"
date: 2012-06-29
forum: Security
---

### Post by xedi on 2012-06-29
My Ubuntu 12.04 install suddenly started to display following message: "the login keyring did not get unlocked when you logged into your computer" after each time I boot my computer. It did not do this before today (or yesterday? Can't remember but it is definitely a recent change) and I have not changed any account configurations or passwords, I never had automatic login enabled where you would expect such behavior.

Do you have any idea what caused it and how I can fix it? Is it possibly a bug I should report?

Thanks for your replies in advance

---

### Post by cprofitt on 2012-06-29
Did you change your login password?

Did you change the keyring password to match?

---

### Post by vasa1 on 2012-06-29
> **cprofitt said:**
> Did you change your login password?

Did you change the keyring password to match?
I can get this behavior by logging out of an Xfce 4.10 session to a Unity session and then back to an Xfce 4.10 session all with the password unchanged.

---

### Post by vasa1 on 2012-06-29
To fix it, I have to open "Passwords and Keys", right-click on "login" and select "change password". I then enter my regular password, which is the one with which I log in and use for sudo, and then in the lower box I just hit enter without entering anything. I get a warning that it's unsafe and I choose to proceed anyway. I'm no longer bothered with the keyring pop-up until I choose another session, say Unity, and then revert to Xfce.

---

### Post by xedi on 2012-06-29
> **cprofitt said:**
> Did you change your login password?

Did you change the keyring password to match?

1. No

2. No, no changes whatsoever, the problem came out of nowhere it seems. 

> **vasa1 said:**
> To fix it, I have to open "Passwords and Keys", right-click on "login" and select "change password". I then enter my regular password, which is the one with which I log in and use for sudo, and then in the lower box I just hit enter without entering anything. I get a warning that it's unsafe and I choose to proceed anyway. I'm no longer bothered with the keyring pop-up until I choose another session, say Unity, and then revert to Xfce.

So essentially you just removed the keyring password? I don't really want all my passwords to be unencrypted even though that should solve the problem.

---

### Post by vasa1 on 2012-06-29
> **xedi said:**
> ...
So essentially you just removed the keyring password? I don't really want all my passwords to be unencrypted even though that should solve the problem.
Yes. The warning makes the risk clear.

---

### Post by mpsz on 2012-07-09
> **vasa1 said:**
> To fix it, I have to open "Passwords and Keys", right-click on "login" and select "change password". I then enter my regular password, which is the one with which I log in and use for sudo, and then in the lower box I just hit enter without entering anything. I get a warning that it's unsafe and I choose to proceed anyway. I'm no longer bothered with the keyring pop-up until I choose another session, say Unity, and then revert to Xfce.

I did the same but instead of leaving the new password empty I wrote my regular password again.
I had chenged my user password so the keyring password was still my older one.
This fixed the problem and If I'm not wrong also kept the keyring protected with a password.

I read some couldn't find "Passwords and Keys" in settings, it's not there it's in the "Applications" menu.

Regards

---

