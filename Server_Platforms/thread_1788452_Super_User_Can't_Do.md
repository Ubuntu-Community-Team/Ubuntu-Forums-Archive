---
title: "Super User Can't Do"
date: 2011-06-22
forum: Server Platforms
---

### Post by faraz.yashar on 2011-06-22
I'm running Ubuntu Server 11.04. It came time to add User to the sudoers file: so I decided to simple add User to the admin group: usermod -a -G admin user

Then I used visudo to check if admin users had been set to receive sudo privileges. I uncommented the line admin ALL=(ALL) ALL. And viola!

Nothing happened. I've even tried to add user directly into the sudoers file as user ALL=(ALL:ALL) ALL, but that failed too.

Ideas?

---

### Post by sisco311 on 2011-06-22
Hi,

Please post the content of /etc/sudoers and the output of **id user** (where **user** is the login name of the user).

---

### Post by faraz.yashar on 2011-06-22
Error was resolved by adding an @ sign before the admin line specific admin as a group.

---

### Post by sisco311 on 2011-06-22
> **faraz.yashar said:**
> Error was resolved by adding an @ sign before the admin line specific admin as a group.

You mean a percent sign, right? Groups have the `%' symbol prefixed against their name.

---

