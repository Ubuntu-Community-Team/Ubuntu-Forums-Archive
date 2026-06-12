---
title: "Changing login screen wallpaper?"
date: 2010-08-21
forum: Ubuntu Christian Edition
---

### Post by Deer Hunter on 2010-08-21
Hello all,

My question is really quite simple.  Is there a way for me to change the login screen wallpaper on my Ubuntu CE?  If it makes any difference, I clean-installed Ubuntu CE 9.10 from CD, and then upgraded to 10.04 when it was being released, as I wanted to have 10.04 but still keep e-Sword and other things.  Any help would be greatly appreciated.

Davis

---

### Post by sisco311 on 2010-08-21
Add gnome-appearance-properties to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The appearance properties window should show up on the GDM screen. 

Configure GDM how you want, then close the window and log back in. 

When you're done and want the window to stop opening with GDM, run:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by Deer Hunter on 2010-08-21
> **sisco311 said:**
> Add gnome-appearance-properties to gdm's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Then logout, the appearance properties windows will show up in the GDM screen for you to configure. 

When Finish, login normally and delete what you just add:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Thank you very much sir, that worked beautifully!!

Problem solved.

---

### Post by sisco311 on 2010-08-21
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks!

---

### Post by kc600 on 2010-09-12
thx

---

