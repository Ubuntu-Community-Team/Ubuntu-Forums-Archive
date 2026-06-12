---
title: "System can't remember username password."
date: 2011-06-04
forum: Security
---

### Post by Simeno on 2011-06-04
Hi every one. I've been using ubuntu 9.10 for years and never been asked for username and password, always started straight away. Today I started the computer, it's asking for them and doesn't accept the password so it's trapped in a loop. I changed the password, no luck, the username when starting seems to be different from the one when I'm changing it. Something like "Mart Di", versus "mart". Tried both with new and old passwords. Does the password expireor something? Can anyone help, please?

---

### Post by Soul-Sing on 2011-06-04
afaik 9.10 isn't supported anymore.

---

### Post by Rubi1200 on 2011-06-04
Hi and welcome to the forums Simeno :-)

Did you use this guide to change the password?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Simeno on 2011-06-04
Thanks Rubi1200. I tried something similar at [http://ubuntuguide.net/reset-the-forgotten-password-in-ubuntu](http://ubuntuguide.net/reset-the-forgotten-password-in-ubuntu). Now I tried that and doesn't work either. With both instructions the password gets changed but the system remains in a loop. If I enter an old password or a random password it says "authentication failure" as normal, with the new password, it shows the Ubuntu screen as if it were starting but goes back to asking the username and password. I never forgot the password, the system doesn't want to accept it. I'm trapped in a loop.
Leoquant: perhaps should I upgrade, but now I can't even load my 9.10.

---

### Post by Dave_L on 2011-06-04
Are you saying that it started asking for a user name and password spontaneously, without your making any changes?

Do you have a Live CD from which you can boot and run a file system check?

---

### Post by ohadcn on 2011-06-04
press ctrl+alt+f1
enter your username
enter your password
if your log in is successfull - it's desktop problem (try removing the content of /tmp?)

---

### Post by Simeno on 2011-06-05
I found the solution in other threads. Apparently there are 3 main reasons for that problem, one of them is simply that the disk is full. That was my problem. I managed to move some files to the external hard disk using a live CD following the instructions in other threads again. 


               :D :D :D :D   THANKS EVERYONE!!!  :D :D :D :D

---

### Post by Soul-Sing on 2011-06-06
> **Simeno said:**
> I found the solution in other threads. Apparently there are 3 main reasons for that problem, one of them is simply that the disk is full. That was my problem. I managed to move some files to the external hard disk using a live CD following the instructions in other threads again. 


               :D :D :D :D   THANKS EVERYONE!!!  :D :D :D :D

Don't forget to upgrade your Ubuntu version/system.

---

