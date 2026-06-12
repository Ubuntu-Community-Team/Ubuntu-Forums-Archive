---
title: "Debian category at applications menu, what goes there?"
date: 2009-07-21
forum: The Cafe
---

### Post by chriskin on 2009-07-21
what applications go to the Debian category at the applications menu? i can find that it exists via the right click / edit menu feature, but i have never seen any application going there

---

### Post by wojox on 2009-07-21
I would guess a Debian Linux Package?

---

### Post by chriskin on 2009-07-21
if you mean .debs, they go to the category they belong to

a .deb with a music app for example would go to "sound and video", not "debian"

---

### Post by wojox on 2009-07-21
Right, but it's a deb package for Ubuntu. There are all types of package's.

---

### Post by chriskin on 2009-07-21
can you give me a link to a package that would not go to its respective place and choose to go to "debian" instead? cause i have even installed from the debian repositories before and it still went to the right place

---

### Post by wojox on 2009-07-21
Never done it. I always stayed with the ubuntu repo's. That why I said I guess?

---

### Post by RedSquirrel on 2009-07-21
> **chriskin said:**
> what applications go to the Debian category at the applications menu? i can find that it exists via the right click / edit menu feature, but i have never seen any application going there

The Debian Menu is used by window managers to generate an applications menu. For example, if you use the fluxbox window manager, there is a script to generate the right-click fluxbox menu under /etc/menu-methods and some other helper files under /etc/X11/fluxbox.

I haven't used GNOME in a long time, so I don't really know what would go under the Debian Menu when you're running GNOME. I thought there used to be some applications under there the last time I used GNOME, but maybe it doesn't do that anymore.

You could try running:

```
sudo update-menus
```to see if anything is generated for the Debian Menu in GNOME.

See:

[http://www.debian.org/doc/packaging-manuals/menu.html/](http://www.debian.org/doc/packaging-manuals/menu.html/)


**Edit:**

By the way, you need the **menu** package installed to use the Debian menu. If you don't already have it:

```
sudo apt-get install menu
```

---

### Post by chriskin on 2009-07-22
i did everything (checked the link, sudo update-menus - already had the menu package) but nothing helped to answer the question. probably i don't have any app that would go there. Since i have many apps installed though, i was thinking of the possibility that it is there only for backwards compatibility, and that it has in fact stopped putting apps there.

thanks for your time anyway :)

---

### Post by SunnyRabbiera on 2009-07-22
The debian menu layout is different then Ubuntu's, I remember navigating in debian etch with its menus looking kinda crazy.
I think lenny eliminated that though as lenny's menu layout is simular to ubuntu

---

### Post by RedSquirrel on 2009-07-22
> **chriskin said:**
> i did everything (checked the link, sudo update-menus - already had the menu package) but nothing helped to answer the question. 

The menu package is used by window managers to generate an applications menu. If you are running GNOME, your applications are found elsewhere in the GNOME menus.

There is likely no need to put anything in the Debian Menu under GNOME since almost everything in there would only duplicate the contents of your GNOME menus.

To be clear, **there isn't some special type of application that ends up in the Debian Menu**. The Debian Menu is an applications menu, just like your GNOME menus, only with a slightly different arrangement.

You can see this for yourself by installing a window manager and running it on its own.

```
sudo apt-get install fluxbox
```Then logout, go back to the login screen, choose Fluxbox from the Sessions menu at the login screen, and login. Once fluxbox has started, right-click on the desktop. That menu is created with the help of the Debian Menu system. Go into the Applications portion of the menu, and you will see all (or close to all) of the applications you have installed.



> **chriskin said:**
> probably i don't have any app that would go there.
You have plenty of applications that would appear in the Debian Menu if you were using a window manager on its own (fluxbox, openbox, icewm, etc.). The Debian Menu system is the tool that automatically generates menus when you use a window manager on its own.




> **chriskin said:**
> Since i have many apps installed though, i was thinking of the possibility that it is there only for backwards compatibility, and that it has in fact stopped putting apps there.
Perhaps under GNOME, it no longer puts anything in the Debian Menu category since, as I said, all of your applications are accessible elsewhere in the GNOME menus.

---

### Post by chriskin on 2009-07-22
thank you, i understand now :D

:popcorn:

---

