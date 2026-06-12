---
title: "Default guest account allowing unlock gufw firewall"
date: 2013-06-09
forum: Security
---

### Post by WhiteHatGuy on 2013-06-09
Hi everyone.

I went to the default guest account, made for security and protected with apparmor, and that does not allow sudo on terminal.

Thing is, when I open gufw firewall, it allow me to put my administrative login operating system password, and allow me to make changes and unlock it, I can turn on or off.

Should I worry about this in terms of security? I think this guest account should not allow to acces the firewall. I think even on xp in a low privilage account it does not allow to do changes or access the firewall. Why on linux is allowing this?

Is there I way I can configure this guest account, so does not allow using the firewall.

Thanks guys.

---

### Post by cariboo on 2013-06-09
If it asks for the Administrators password, what's the problem? Unless of course you make all users on your system administrators, which of course you shouldn't do.

---

### Post by WhiteHatGuy on 2013-06-09
> **cariboo907 said:**
> If it asks for the Administrators password, what's the problem? Unless of course you make all users on your system administrators, which of course you shouldn't do.




Well, I just like the fact that in the terminal does not allow sudo, and I thought that this rule it was going to apply to all parts of the guest account including firewall, updates, etc. Just in order to make a more restricted account, so if a hacker get the administrator password by guessing or using brute force, social enginering, etc. Is not going to be able to make administrator changes to the system, for example turning off the firewall.


I actually saw that if I turn off gufw firewall in the guest account, it apply the changes also to the administrator account.


Also this is suppose to be a guest account, made for guests, and for an extra layer of security, so the idea is that if someone is using it, he or she should not be able to make critical or important security changes to the system. Its suppose to be a limited account with less privilages. 


Dont get me wrong, I like linux a lot (Lubuntu and Ubuntu), Ive been using it for years and its a great OS. I like very much the idea that the guest account is lock down with apparmor. But this guest account can be improved. Like not allowing to turn off firewall and so on.


Or maybe some one can provide me with a link of how to make changes to the default guest account, like the ones I am refering to, or how to create restrictive guest accounts

Thanks, and sorry if I am being a pain in the a**.

---

### Post by paperplate9 on 2013-06-09
I've never used gufw, but if the elevation mechanism is the typical process used in Ubuntu, I believe that happens via dbus. Maybe the guest AppArmor profile does not lock down dbus (if that's even possible, don't know much about AppArmor). Find out how to block specific dbus messaging for authorization  & I believe that will get you what you want. And if you block dbus altogether, the UI  & other things will probably suffer (Network Manager makes heavy use of dbus).

---

