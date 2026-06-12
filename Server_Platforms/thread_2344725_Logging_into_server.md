---
title: "Logging into server"
date: 2016-11-27
forum: Server Platforms
---

### Post by gain74 on 2016-11-27
Hello,

I have just installed, for the first time, Ubuntu Server 14.04 LTS and created 4 users. However, the system only allows 1 user to log into the server (I did not notice if it was the first user to be created). The other accounts are properly displayed in the login screen but, after entering the password, a black screen appears for a second or two and then the login screen appears again.

I tried to set them all up as administrator accounts but with the same result.

Please help.

Thank you very much.

---

### Post by wildmanne39 on 2016-11-27
*Thread moved to **Server Platforms**.*

---

### Post by cariboo on 2016-11-27
Can all the users log in from a console? Have you installed openssh-server, and if you have, can all the users log in remotely/

---

### Post by darkod on 2016-11-28
First, ubuntu server has no GUI that shows login screen with multiple users. That sounds like ubuntu desktop login screen.

So you either installed the desktop version (even if you plan to use the system as a server) or you added a GUI interface etc... Which one is it?

In any case, any user with a valid password can log in, unless expressly prohibited. Maybe you did something wrong when adding the GUI?

---

### Post by gain74 on 2016-11-29
Hello,

Thanks for the replies.

Darko: yes, I installed the server version (14.04 LTS) and after ubuntu desktop package was installed. System does not report that password is incorrect (if I try to enter an invalid password, I get an error... so that is working) but simply blinks blank and back to login screen.

Cariboo: I do not remember having installed openssh but I can try tomorrow. About logging from a console, I am sorry but I am not sure how to do that without first logging into the system. If you have a link with the instructions handy how to do that I would appreciate it, otherwise, I will research it. I will try it and let you know.

I will update thread tomorrow evening.

Thanks everyone for helping.

---

### Post by cariboo on 2016-11-29
Once you are at the log in screen, press Ctrl-Alt-F1. This will bring you to a console. If you can log in from there, you have a video problem.

---

### Post by steeldriver on 2016-11-29
Possibly the other users don't have suitable home directories. How exactly did you create the additional accounts?

---

### Post by gain74 on 2017-01-12
Hello,

Thanks for all the replies and sorry for the delay.

After deleting and recreating the accounts that were having issues, it works.

Thanks again.

---

