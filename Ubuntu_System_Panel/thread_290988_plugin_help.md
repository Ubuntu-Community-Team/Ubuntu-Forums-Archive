---
title: "plugin help"
date: 2006-11-01
forum: Ubuntu System Panel
---

### Post by zman3 on 2006-11-01
ok ive tried to install terminal plugin the calc plugin and the user plugin and i always get plugin not found any idea?

I have them in /home/zman3/.usp/plugins

they are listed in gconf   under key  /apps/usp/plugins



thanks

---

### Post by Malac on 2006-11-02
Unfortunately the "not found" message is a little misleading.
It actually pops up even if the plugin is where it should be but there is a problem with the module, i.e. one of the required python or gnome packages aren't loaded or there is an errror in the plugin code. This last one shouldn't be the case as I try to make sure any plugin posted works without code errors but it is possible.
Please forgive if this sounds dumb but if I could just check the basics.

Try these steps, testing USP each time.
1/.Make sure you have extracted both files in the tar.gz file to ~/.usp/plugins not just the .py file.

2/.Check the name of the plugin is correct it should be (all without the quotes)
"USPterm" for terminal,
"USPcalc" for calculator
and
"USPuser" for user plugin, names are case sensitive.

3/. Make sure you are running 0.41.1.deb file.

4/. Check that you have the python-vte package installed for terminal to work.

5/. Remove USP from the Panel and open a terminal and run :```
usp run-in-window
```and post any output that gives you.

---

### Post by zman3 on 2006-11-02
ok had them named wrong or somthing thank you so much :)

---

### Post by Malac on 2006-11-03
> **zman3 said:**
> ok had them named wrong or somthing thank you so much :)
You're Welcome :)

---

