---
title: "Firestarter won't start"
date: 2004-10-31
forum: Server Platforms
---

### Post by zevoneer on 2004-10-31
I've installed Firestarter from Synaptic but when I try to run it I get an error message.
"Failed to run /usr/sbin/firestarter as user root: Child termintated with 1 status"

Anyone any ideas?

---

### Post by diabolo on 2004-10-31
did you run it like this: **sudo firestarter**

If you're running it from a launcher, you might need to do this:

in Nautilus, File -> Open Location...
type applications:///
Now find the Firestarter icon and right-click it.
click on Properties in the contextual menu.
In the Properties panel click on the "Lancher" tab.
In the "Command:" textfield it should be **gksudo /usr/local/bin/firestarter**

---

### Post by zevoneer on 2004-11-01
Right, sudo firestarter works ok, does this "stick" or do I have to run it at each log on?
The change to Properties doesn't stick. I can change it then leave and click on the icon but I get the same message I did before. If I go back to Properties, the command has reverted to gksu /user/sbin/firestarter

---

### Post by diabolo on 2004-11-01
I may have given you the wrong path to firestarter. Do **which firestarter** in the terminal to get the correct path on your machine.

---

### Post by zevoneer on 2004-11-02
[QUOTE=][/QUOTE]
 Thanks Diablo.

Here's an odd one though. If I follow your instruction and keep the window open and launch the app from the icon it works fine. If I close the window then pick Firestarter from Applications on the tool bar it doesn't. However by right clicking on this icon I can get Properties and edit the command. Seems the icons in the two locations both need editing.

---

### Post by HungSquirrel on 2004-11-04
The problem is there is a bug in the package that makes the launcher point to 

gksu /usr/sbin/firestarter

Rather than

gksu***_do_*** /usr/sbin/firestarter

The simple solution is to open applications:/// in Nautilus, go to System Tools, right-click on the Firestarter launcher, choose Properties..., click the Launcher tab, and edit the appropriate value.

If the developers want to fix the problem, they just need to repackage firestarter with the correct launcher.

---

### Post by FLeiXiuS on 2004-11-04
sudo /etc/init.d/firestarter start
sudo /etc/init.d/firestarter stop
sudo /etc/init.d/firestarter status
sudo /etc/init.d/firestarter restart

---

### Post by zevoneer on 2004-11-06
[QUOTE=][/QUOTE]
 Not sure what these commands are supposed to do but I ran them anyway. However I still had to go to properties for the Firestarter icon and change the command "gksu /usr/sbin/firestarter" to"gksudo /usr/sbin/firestarter" Not a big deal, the firewall is running and it's not something that needs attention all the time.

---

