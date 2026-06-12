---
title: "GRUB Entries Password Protection"
date: 2020-08-02
forum: Security
---

### Post by mbztn on 2020-08-02
Hi, i wanna protect "Advanced Options for Ubuntu" as well as pressing "e" and "c" with a password. How can i achieve that without having to be prompted for the password when booting in my OS.

Thanks.

---

### Post by ecophobia on 2020-08-07
**I guess you can check Grub man page, look for [COLOR=#ff8c00][FONT=arial][B]lockalternative**[/FONT][FONT=arial]=[/FONT][FONT=arial]**true **[/FONT][/COLOR][COLOR=#5F6368][FONT=arial]** Alternatively, use HDD encryption.**[/FONT][/COLOR][/B]

---

### Post by EuclideanCoffee on 2020-08-20
Check out the security section in the man page. To set your menu entries.

[https://gnu.org/software/grub/manual/grub/grub.html#Security](https://gnu.org/software/grub/manual/grub/grub.html#Security)

Then follow this tutorial to set a password.

[https://askubuntu.com/questions/656206/how-to-password-proect-grub-menu](https://askubuntu.com/questions/656206/how-to-password-proect-grub-menu)

Take the output of [COLOR=#242729][FONT=Consolas]grub-mkpasswd-pbkdf2
Create a new file called: [/FONT][/COLOR][COLOR=#242729][FONT=Consolas]etc/grub.d/40_custom
Contents should look like this:
[/FONT][/COLOR]
set superusers="username" 
  [COLOR=#242729][FONT=Consolas] password_pbkdf2 username hash  [/FONT][/COLOR][COLOR=#242729][FONT=Consolas] 

Update. [/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sudo update-grub
Add menu specific commands here:

[/FONT][/COLOR]menuentry "May be run by user1 or a superuser" --users user1 {
	set root=(hd0,2)
	chainloader +1
}


[B]Any non-restrictive menus can be set like this
[/B]
**--unrestricted  ${CLASS}**

---

