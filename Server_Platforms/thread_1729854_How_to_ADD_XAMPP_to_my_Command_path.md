---
title: "How to ADD XAMPP to my Command path"
date: 2011-04-15
forum: Server Platforms
---

### Post by spirit.986 on 2011-04-15
I have installed XAMPP to my Ubuntu.
Since I am using it quite frequently I have tried to add it into my command path by entering the following line into **.bashrc **
```
export PATH=$PATH:/opt/lampp:
```
and it appeared in the console with the TAB key... however after i tryed
```
$sudo lampp start
```
i have received an error 
```
$sudo: lampp: command not found
```

Any sugestions?

---

### Post by kamaji792 on 2011-04-15
Will I be quick enough?

You have added it to the path for your current user.

Not 'root'.

When you use **sudo** you are running as the **root** user.

Sadly I am not entirely sure how you cure this problem :P

K

---

### Post by spirit.986 on 2011-04-15
Ohh... i got it... so i have to add the path into the
**/etc/profile**

Thanks kamaji792 for the answer :)

I was just lazy every time i start XAMPP i had to type /opt/lampp/lampp start

---

