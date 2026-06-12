---
title: "kerying issue"
date: 2009-06-04
forum: Security
---

### Post by zelalem on 2009-06-04
hi all, i was troubled with keyring issue and after reading some thread, i deleted the file, defaul.keyring from `.gnome/keyring folder. but now i can't no longer use my password. i have my pc still open. what can i do/ i am really frsutrated. please help me.

---

### Post by lovinglinux on 2009-06-04
Follow this:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by zelalem on 2009-06-05
hi thank you for your response. i tried that one. it asks me to enter my old password and then new password. i tried all my passwords but failed do it it says;
<big><b>Couldn't change keyring password</b></big>

Access Denied

so, i don't know what i can do. isn't there any means that i can get my password again. i am really frustrated.

---

### Post by zelalem on 2009-06-05
Hi, the problem is now solved. You know I am using VMware and it had made some problem with my keyboard setting. If you see my previous posting there are no caps letters while I tried to use the shift key. I didn't associate my problem with it. I then realised the problem and tried to search why my shift key and caps lock are not working and found out the reason and also a solution. I used the following command to restore my keyboard: setxkbmap. So, my password is now working. You know it contains caps letters and also some special characters on top of the numbers. Otherwise my password was not changed as I thought. I was afraid to boot my PC. Thanks again for your help.

---

