---
title: "Password Policy"
date: 2015-08-18
forum: Security
---

### Post by ryan176 on 2015-08-18
Alright so i don't know how to change the password policies in Ubuntu 14.04.  In, specific I would like to know how to change the password expiration date, min and maxium length, and if possible how to require letters and numbers in the password.   Any and all help would be great!!!!!!!!!! thank you

---

### Post by TheFu on 2015-08-18
[https://askubuntu.com/questions/156850/how-do-you-set-requirements-such-as-minimum-length-on-passwords](https://askubuntu.com/questions/156850/how-do-you-set-requirements-such-as-minimum-length-on-passwords)
and
[https://help.ubuntu.com/lts/serverguide/user-management.html#password-policy](https://help.ubuntu.com/lts/serverguide/user-management.html#password-policy)

---

### Post by ryan176 on 2015-08-19
Thank you very much for your help and fast response.

---

### Post by HermanAB on 2015-08-19
Howdy,

Passwords are managed by PAM.  You can edit PAM config files in /etc manually, but be very careful, since any mistake can render you unable to log in.

---

