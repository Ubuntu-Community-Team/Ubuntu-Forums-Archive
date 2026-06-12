---
title: "New User Quriks"
date: 2009-02-14
forum: Server Platforms
---

### Post by psilokan on 2009-02-14
Alright, I've noticed this across many different Ubuntu installs.  Whenever I create a user via command line they end up quite different than the one created by the installer. 

I am creating them with this line:
useradd -d /home/newuser -m newuser

Then I set a password and add them to the sudoers file.  Now the problem is this new user acts very odd.  For example, instead of the prompt being newuser@myserver it is just a #

The next issue is there's no tab completion.  Nor is there any history available when I press the up button.

I copied over the .bashrc and .profile for my main user but still no luck.  Any idea on how to configure these options?

Thanks!

---

### Post by brian_p on 2009-02-17
> **psilokan said:**
> 

I am creating them with this line:
useradd -d /home/newuser -m newuser

You might be happier with the adduser command.

---

