---
title: "Permission denied"
date: 2011-09-21
forum: Server Platforms
---

### Post by Jumeira on 2011-09-21
Permission denied ..

Hello there ..*

Im get a problem with my server that i format it and i put the version 10.4 and it facing me problem that when i want to creat a file or directory it showing me permission denied *..*

I would like some one to help me :(!*

And thanks*

---

### Post by haqking on 2011-09-21
> **Jumeira said:**
> Permission denied ..

Hello there ..*

Im get a problem with my server that i format it and i put the version 10.4 and it facing me problem that when i want to creat a file or directory it showing me permission denied *..*

I would like some one to help me :(!*

And thanks*

Do you have write permission in the location where you are trying to make the file or directory ?

what is the location ?

Are you an admin user ?

Are you using sudo appropriately if required  ?

read here [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Jumeira on 2011-09-21
> **haqking said:**
> Do you have write permission in the location where you are trying to make the file or directory ?

what is the location ?

Are you an admin user ?

Are you using sudo appropriately if required  ?

read here [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

Im trying to do in file var an file "etc"

Yes i have the admin user .. 

But if u just explain for me the sudo how  i do it ?

---

### Post by haqking on 2011-09-21
> **Jumeira said:**
> Im trying to do in file var an file "etc"

Yes i have the admin user .. 

But if u just explain for me the sudo how  i do it ?

What exactly are you trying to put into /var and/etc ?

They are system directories owned by root and so **please do not change the permissions**.

What do you need to put in there and why ?

you can do so using sudo, and if you read the link i posted to [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") it will explain.

Cheers

---

### Post by Jumeira on 2011-09-21
Im Trying to Upload in /var/etc/CCCam.cfg 


and i cant because of the permission

---

### Post by haqking on 2011-09-21
> **Jumeira said:**
> Im Trying to Upload in /var/etc/CCCam.cfg 


and i cant because of the permission

like i have said in answer to both your PM and on this thread now, if you dont have write access to something, then as an admin you can change that though for a system directory or file you should not.

And to perform a write if you so require to then you can use sudo, for which i have provided the link twice now and in answer to your PM.

cheers

---

### Post by Jumeira on 2011-09-24
Any another solution ?:(

---

### Post by haqking on 2011-09-24
> **Jumeira said:**
> Any another solution ?:(

What is wrong with the solution i have mentioned already ?

use **sudo** if you must place files in there

---

### Post by Demaki on 2011-09-24
Like haqking said, you should use **sudo**:
```

sudo cp CCCam.cfg /etc/where_u_want_it_to_be

```

---

### Post by Jumeira on 2011-09-25
[LEFT]My Fiends the problem not only for creating folder ?

I need a solution for the access which is Permission denied

Which is i cant get on root file & lost+found and more ?


[FONT=Times New Roman][SIZE=3][IMG]http://img683.imageshack.us/img683/7658/1212ce.jpg[/IMG][/SIZE][/FONT]
[/LEFT]

---

### Post by haqking on 2011-09-25
> **Jumeira said:**
> [LEFT]My Fiends the problem not only for creating folder ?

I need a solution for the access which is Permission denied

Which is i cant get on root file & lost+found and more ?


[FONT=Times New Roman][SIZE=3][IMG]http://img683.imageshack.us/img683/7658/1212ce.jpg[/IMG][/SIZE][/FONT]
[/LEFT]

I dont know how many other ways to tell you.  ROOT is locked by default, do not enable and do not log on as root.  Do not change permission od root folders either.

If you are an admin then you can access root priveleges using [SUDO]("https://help.ubuntu.com/community/RootSudo")

---

### Post by lisati on 2011-09-25
The question has already been answered twice: see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thread closed.

---

