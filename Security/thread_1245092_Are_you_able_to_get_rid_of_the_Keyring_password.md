---
title: "Are you able to get rid of the Keyring password ?"
date: 2009-08-20
forum: Security
---

### Post by Rick Abraham on 2009-08-20
Hi guys whenever I boot up Ubuntu my PC automatically trys to connect with my wireless network which is ok but before it connects it asks for the Keyring password.
Are you able to somehow get rid of that popup and have it that my password automatically gets detected ?????

---

### Post by duanedesign on 2009-08-21
To get passwordless networkmanager login working with 9.04.

   1. Applications-> Accessories-> Passwords and Encryption Keys
   2. Select Passwords tab
   3. Right click on  Passwords:login,  choose Change Password
   4. Enter current password and LEAVE THE NEW AND CONFIRM FIELDS BLANK


i hope this helps.

There is a slightly more destructive method here if you do not have any luck with the above steps.
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by Agent ME on 2009-08-22
Don't set the new password to blank. Set it to be the same as your account password; it will automatically decrypt the keyring when you login then. Setting no password will make the keyring unencrypted.

---

### Post by Napu5 on 2009-08-22
I don't enter my password when I boot up. It logs in automatically. I suspect that's why setting the keyring password to the account password doesn't work. I might try setting it blank. Does the keyring store any passwords other than for the wireless? I don't mind that being in plaintext really.

An other possible solution I saw: Edit the wireless connection and check "Available to all users"

---

