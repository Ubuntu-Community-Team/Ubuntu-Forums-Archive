---
title: "Help i entered wrong sudo password"
date: 2011-06-30
forum: Security
---

### Post by WanchoPiskado on 2011-06-30
Hello.
I joined the active directory with likewise open, running ubuntu 10.04 lts. I logged in as a active directory normal user. Then i tried to run an antivirus scan in terminal. It asked me for sudo password. I entered the wrong password twice. Logged out. Now i cannot login with my 'normal user' active directory username and password. It says authentication failure. Help. How can i regain access to this account?
Thank you

---

### Post by WanchoPiskado on 2011-06-30
I just waited an hour and now i can login again. Yaay.

---

### Post by Lars Noodén on 2011-06-30
You can also clear sudo's user timestamp by **sudo -k** or **sudo -K**, rather than waiting for the timeout.

---

### Post by WanchoPiskado on 2011-06-30
Thank you very much! Save a bit a bit of time .:p

---

