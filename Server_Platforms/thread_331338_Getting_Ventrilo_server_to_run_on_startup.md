---
title: "Getting Ventrilo server to run on startup?"
date: 2007-01-04
forum: Server Platforms
---

### Post by Mikey7047 on 2007-01-04
I have Ventrilo installed and running correctly, but only when I activate it from the command line.  It is installed in /usr/bin/ventrilo
and the executable is /usr/bin/ventrilo/ventrilo_srv

I made a script using this guide to get the vent server to run on bootup:
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

which is /etc/init.d/vent.sh

The contents of vent.sh look like this right now:

```
su mvarrieur -c "/usr/bin/ventrilo/ventrilo_srv -f/usr/bin/ventrilo/3784 -d"
```

I have also tried a couple other ways of getting it to run on startup such as:

```
/usr/bin/ventrilo/ventrilo_srv -d
```
and:
```
/usr/bin/ventrilo/ventrilo_srv -d &
```

None of these methods have ran the script on startup.  Any advice or am I just completely missing something here?

---

### Post by ajgreeny on 2007-01-04
Assuming you usually start it as user and not root, I think you can simply add the link you use in terminal to the startup programs, which I think are in Administration>Start up Programs in your gnome menu.  I use KDE so can't remember the detail, but I'm sure you'll find it easily.

Should you be using KDE put the link into your ~/.kde/Autostart folder.

---

### Post by Mikey7047 on 2007-01-04
I believe it has to be started as root, though I will try running it as user and see what happens.

---

### Post by Mikey7047 on 2007-01-04
I chmod'd it 777 and ran it as user, so it's working now, thanks =)

EDIT: Working in terminal, still not working on startup

---

### Post by TSMJ on 2007-01-05
So the script is in /etc/init.d?

cd there and:
[INDENT]update-rc.d <scriptname> defaults[/INDENT]

You can use
[INDENT]update-rc.d -f <scriptname> remove[/INDENT]
to remove it from startup.

Does that help at all?! Did you do that before?

---

