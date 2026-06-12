---
title: "Some simple security advice"
date: 2011-03-02
forum: Security
---

### Post by jon.mithe on 2011-03-02
Hi,

I want to lock down what a user can do when they ssh into my box.  Pretty much so they can not do or see anything, but su to another user.

I'm allowing myself remote access to the box.  I have 1 ssh user I use (sshd_config AllowUsers) and I log on using this user then su to my actual users I manage the box with.

I read about git shell creating a more secure shell where only git commands could be exec'd, is there something like that where I can lock down to just su?

Thanks,
Jon.

---

### Post by bodhi.zazen on 2011-03-02
> **jon.mithe said:**
> Hi,

I want to lock down what a user can do when they ssh into my box.  Pretty much so they can not do or see anything, but su to another user.

I'm allowing myself remote access to the box.  I have 1 ssh user I use (sshd_config AllowUsers) and I log on using this user then su to my actual users I manage the box with.

I read about git shell creating a more secure shell where only git commands could be exec'd, is there something like that where I can lock down to just su?

Thanks,
Jon.

Use apparmor or grsecurity.

---

### Post by jon.mithe on 2011-03-03
Ooo apparmor looks the ticket, thanks for your help :)

---

### Post by bodhi.zazen on 2011-03-03
> **jon.mithe said:**
> Ooo apparmor looks the ticket, thanks for your help :)

In that case, see if this post can get you started :

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

