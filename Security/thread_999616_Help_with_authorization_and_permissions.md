---
title: "Help with authorization and permissions"
date: 2008-12-02
forum: Security
---

### Post by gackt on 2008-12-02
Hi guys, 

I'm new with this ubuntu and currently there is two accounts in my laptop. Superadmin and me. I uses my user account to do daily activity, the problem is there so much restrictions with this account such can not add start up program, cann't access some folders etc. But if i login with superadmin none of this would happen. So how do i assign all the privileges and permissions from superadmin account into my account? 

Thanks guys.

---

### Post by Masuran on 2008-12-02
Hello,

First of all, my current system is in Dutch so it's possible I messed up the translation ;-)

When you go the Users and Groups tools with the superadmin, select your other user and get the properties. There is a tab called 'user permissions', check the option 'Can administer the system'.
Now that user can perform tasks using the sudo command.

---

### Post by gTinker on 2008-12-02
[QUOTE=gackt]
I'm new with this ubuntu ...[/QUOTE]

Well, you are currently using Ubuntu in the most secure and intelligent way, in my opinion, I would think that you should continue to use it that way. It seems a bit cumbersome at first but after you have configured everything the way you want it, it shouldn't be as necessary to switch users as often for things that can only be done with root permissions. As the regular user you can access all the files and folders that a regular user should have access to and you can't make a mistake that will trash the whole system. 

If you still choose to change permissions, poster Masuran has given you the method.

---

### Post by gackt on 2008-12-04
Thanks guys! I'll try it.

---

