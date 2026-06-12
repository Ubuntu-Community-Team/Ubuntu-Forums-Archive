---
title: "Ubuntuone. Website error messages when adding machine. No icon either."
date: 2010-03-15
forum: Ubuntu One (CLOSED)
---

### Post by philinux on 2010-03-15
What happened to the cloud icon. Also using sys>prefs>ubuntuone takes me to the login page. It offers to add the machine but then this page pops up with these errors. It adds the machine but then this process gets repeated.

---

### Post by philinux on 2010-03-17
Ok error gone and machine added but not syncing. Still no cloud icon in notification area.

---

### Post by tekstr1der on 2010-03-17
> **philinux said:**
> Still no cloud icon in notification area.

> The Ubuntu One applet in the panel has been removed. You can access the preferences from System -> Preferences -> Ubuntu One. You can use the Nautilus plug-in to Connect. You can find it by opening your Ubuntu One directory (Places -> Ubuntu One). Also, the u1sdtool is very handy. The following commands are run in Applications -> Accesories -> Terminal:

u1sdtool -c to connect
u1sdtool -s to check status
u1sdtool -q to quit syncdaemon

You will notice Ubuntu One is listed in the 'Me Menu'. That is the menu in the panel labeled with your user name. I believe they are working on a new GUI that will be accessed from there.

thank you,
duanedesign

Original thread:
[http://ubuntuforums.org/showthread.php?t=1416912](http://ubuntuforums.org/showthread.php?t=1416912)

---

### Post by philinux on 2010-03-18
> **tekstr1der said:**
> Original thread:
[http://ubuntuforums.org/showthread.php?t=1416912](http://ubuntuforums.org/showthread.php?t=1416912)

Cheers. It started syncing out the blue about half an hour after I'd been logged in to lucid. Must have been their server having a paddy.

---

### Post by joshuahoover on 2010-03-19
I'm happy it's working for you now! It likely was a hiccup on the server side but I wasn't aware of any issues during that time. If this happens again, please report the error as a bug to [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)

---

### Post by joshuahoover on 2010-03-25
> **aion4217 said:**
> Still no cloud icon in notification area.

We removed this as part of the latest releases (Lucid and our beta PPA). We'll be showing the status of syncing overall via Ubuntu One Preferences and on individual files/folders via the file emblems.

Thank you,

Joshua

---

