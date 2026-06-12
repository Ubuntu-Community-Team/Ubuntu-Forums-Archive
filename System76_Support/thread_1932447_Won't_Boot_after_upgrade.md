---
title: "Won't Boot after upgrade"
date: 2012-02-27
forum: System76 Support
---

### Post by tgs1952 on 2012-02-27
Hi,

Have a koala mini purchased from System 76.

After a recent network upgrade, I get:

cannot execute /etc/apparmor/initramf

a bunch of stuff (normal) then goes by until

checking battery status

after which it goes black

---

### Post by isantop on 2012-02-27
By network upgrade, do you mean from one version of Ubuntu to another (11.04 to 11.10, for example) or updating Ubuntu normally through update manager? Also, which version of Ubuntu did you upgrade from (if applicable), and what version are you currently running?

---

### Post by tgs1952 on 2012-02-27
Sorry, it was the update manager.

I am sorry to say that I am not sure what the new version, but I think the version I had was 9.04

---

### Post by 23dornot23d on 2012-02-27
Copy this into a terminal and press return then post the results please .....

[B]cat /etc/lsb-release; uname -a

[/B]thats if you can get to a $ prompt .....

Ctrl + Alt + F2

when it gets to checking battery status

---

### Post by tgs1952 on 2012-02-27
I do not get to a prompt. I have tried that command.

---

### Post by 23dornot23d on 2012-02-27
Looking at the error and googling it shows 9.10 was the version with the problem you have repeated messages for the same error in the link below.

There are some answers in the threads here but they are all very old [[COLOR=Blue]_**LINK**_[/COLOR]]("https://www.google.com/search?q=%2Fetc%2Fapparmor%2Finitramf")  year 2010 .

You may be better installing a later version alongside your existing installation ..... as fresh installs tend to have less problems ......  gives you a dual boot until you can repair the problem ( takes 30 mins once you have the CD ).

2010 April
Lucid 10.04 ..... [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

2011 April
Natty 11.04 .... [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

New one to be released shortly but its still in testing .....

---

