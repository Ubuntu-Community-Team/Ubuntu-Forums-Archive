---
title: "Forgotten Sudo Password"
date: 2012-01-24
forum: Security
---

### Post by Black_Sirrah239 on 2012-01-24
I inhereted my brothers computer and he installed ubuntu on it. He doesn't have a login password but I cant use sudo or install programs through the software center because it asks for a password and he doesn't know it. Is there a way to reset it?

---

### Post by cariboo on 2012-01-25
Start in recovery mode, you should be able to select from the grub menu, then once at the menu select drop to root prompt. Once at the prompt type:

```
password <username>
```

Where <username> is the user name you use.

---

### Post by gsgleason on 2012-01-25
Isn't it 'passwd' ?

---

### Post by haqking on 2012-01-25
> **cariboo907 said:**
> Start in recovery mode, you should be able to select from the grub menu, then once at the menu select drop to root prompt. Once at the prompt type:

```
[s]password[/s] <username>
```

.

> **gsgleason said:**
> Isn't it 'passwd' ?

yes it is.

see here for recovery console instructions

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

and it is

> passwd <username>

Peace

---

### Post by cariboo on 2012-01-25
I shouldn't type commands before I've had my first cup of coffee in the morning. :)

---

### Post by haqking on 2012-01-26
> **cariboo907 said:**
> I shouldn't type commands before I've had my first cup of coffee in the morning. :)

I do it all the time, infact i had a lay in today and havent had mine yet so best stop typing and go grab me some ;-)

Peace

---

