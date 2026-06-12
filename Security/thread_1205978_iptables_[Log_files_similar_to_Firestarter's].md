---
title: "iptables [Log files similar to Firestarter's]"
date: 2009-07-06
forum: Security
---

### Post by XCan on 2009-07-06
I have recently decided to check out the various iptables configuration tools available in Ubuntu. From what I gather, if one is interested in GUI tools then one should nowadays avoid Firestarter in favor of gufw (at least in Ubuntu). However, I'm really confused after googling and searching regarding how to discover 'blocked' attempts. The thing I liked about Firestarter is the intuitive logging feature, does anyone know where or how to obtain such log files?

---

### Post by lovinglinux on 2009-07-06
You can run this on a terminal:

```
tail -f /var/log/kern.log | grep **[color=#FF0000]eth0[/color]**
```

Where **[color=#FF0000]eth0[/color]** is your network interface.

To monitor other connections (sent, established, timeout...) you can install [iptstate](apt:iptstate) [apt-get], which also allow to close connections manually.

If you use screenlets, conky or whatever other application that allows you to put a terminal on your desktop, then you have a nice monitor, easily accessible.

I use the [terminal screenlet ](http://www.screenlets.org/index.php/Terminal) on the widget layer of Compiz, so whenever I want to check blocked connections, I just hit the widget layer shortcut and the connection monitor terminal pops up on the screen. Besides the terminal screenlet allows to specify a startup command, so I don't have to enter the command every time or create a script/launcher.

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by XCan on 2009-07-06
Cool, thanks lovinglinux, it does more or less what I want! Took a while to figure out what all those fields meant though. :p Do you or anyone else also happen to know of any app (cli or gui) that could interpret the output of the log files in a little more elegant way? Again as an example I take the log window of Firestarter. :)

---

