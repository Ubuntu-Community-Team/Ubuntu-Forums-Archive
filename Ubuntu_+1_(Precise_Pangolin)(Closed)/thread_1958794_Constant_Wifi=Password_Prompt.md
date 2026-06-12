---
title: "Constant Wifi=Password Prompt"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by The_Autonomist on 2012-04-14
Ever since upgrading to 12.04, everytime i either log on or wake up my laptop, i have to type in my wifi password to my home wifi. I've never had to do this before now. I've already checked my wifi settings and it's already set to Connect Automatically. I even have to type it in 2-3 times before it connects. 

Ayy ideas? This has gotten to the breaking point of REALLY FRICKING ANNOYING. It happens every. single. time i wake up my laptop.

---

### Post by cariboo on 2012-04-14
You obviously have auto-login enabled, you should be able to use the same method as with previous versions to bypass the keyring password.

---

### Post by The_Autonomist on 2012-04-15
i don't know how i bypassed the method on previous versions. it just did it by itself, it was automatic. 

any ideas how? i'm about to throw this fricking computer.

---

### Post by The_Autonomist on 2012-04-16
*bump*

does no one know how to disable this autologin stuff??? how to bypass keyring password? it's nice to know what's wrong, but would be even nicer to know how to fix it...

---

### Post by Peter09 on 2012-04-16
If you go to the wireless Icon and in the dropdown menu select edit connections - select your wireless access. 
 
Do you have the allow all users box ticked?

---

### Post by The_Autonomist on 2012-04-16
No, there was no "all users" box anywhere. 

I did go into my settings and type in my key in the box that said "key" and when i did, THEN an "all users" box appeared. i left it unchecked. 

hopefully this helps.

---

### Post by Peter09 on 2012-04-16
You need to check the allusers box, then it will not ask you for a password again.

---

### Post by 3rdalbum on 2012-04-16
I have a different theory.

If it's actually asking for the wifi key and it takes a few attempts before it will actually work, then I believe it's probably a problem with bringing the wifi device back up properly. Asking for the password can be the symptom of pretty much any problem in router or wifi device!

I don't have a definite solution. A workaround might be to wait a few seconds before putting in your password, and by that time the wifi device should be stable enough to connect properly. You could try filing a bug report but frankly I doubt it would help much unless you file it to the developer of the wifi driver. Maybe the driver's speed problem has been fixed in a later version, and manually compiling a later version of the driver will help.

---

### Post by The_Autonomist on 2012-04-17
^^ That's actually what it was doing. It was asking for it multiple times. 

BUG, i went into my wifi settings, saved my key, and then checked the all users box. I haven't had the problem since...

Thanks guys. Sorry for such a n00b question.

---

