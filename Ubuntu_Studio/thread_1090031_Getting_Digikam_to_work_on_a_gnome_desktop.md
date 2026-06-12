---
title: "Getting Digikam to work on a gnome desktop"
date: 2009-03-07
forum: Ubuntu Studio
---

### Post by maxclimber1w on 2009-03-07
Hello all. I am having problems getting Digikam to work on my gnome desktop.

Yes, I have tried F-spot and Picasa. Digikam is more useful to me as a photography student.

When I try to run Digikam, I get:
[I]
"There was an error setting up inter-process communications for KDE. The message returned by the system was:

could not read network connection list. 
/home/max/.DCOPserver_dell-desktop__0
please check that the "dcopserver" program is running!
[/I]
I click ok, and then get another error saying:

[I]"Will not save configuration. Configuration file "/home/max/.kde/share/config/digikamrc" not writable.
Configuration file "/home/max/.kde/share/config/kdeglobals" not writable.
Please contact your system administrator."[/I]

Then a dialog pops up prompting me to set the default album folder. I am unable to change this, and when I click ok the program fails to load.

Any ideas? I am desperate for some help!

---

### Post by cotcot on 2009-03-08
I guess you got digikam from the repos ?
A work around the error 'not writable' might be to run digikam as root. (sudo digikam in terminal). Maybe you get better error messages starting digikam from terminal as user.
I compiled digikam myself. It was not that easy. I got through it with the help of the digikam forum. It is running well on hardy and 64 bit.

---

### Post by maxclimber1w on 2009-03-08
hmmm... that worked!

Is there any way I can automate this so I don't have to open a terminal every time?

---

### Post by cubeist on 2009-03-08
> **maxclimber1w said:**
> 

[I]"Will not save configuration. Configuration file "/home/max/.kde/share/config/digikamrc" not writable.
Configuration file "/home/max/.kde/share/config/kdeglobals" not writable.
Please contact your system administrator."[/I]


Rather than run the program as root, just go to your .kde folder and change the permissions so the program can write to it...

If you are new to linux permissions, here is a brief primer
[http://www.tuxfiles.org/linuxhelp/filepermissions.html]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")

Or post back if you have more problems...

---

### Post by maxclimber1w on 2009-03-08
hmmm... I changed the permissions in a sudo nautilus session but, the same error messages pop up saying I don't have the right permissions, and that dcopserver is not running.

---

### Post by cubeist on 2009-03-08
can you post the output of 
```
ls -al ~/ | grep .kde
```

---

### Post by maxclimber1w on 2009-03-08
Sure. And thanks for the help!

max@dell-desktop:~$ ls -al ~/ | grep .kde
drwx------  6 root root   4096 2009-03-08 12:25 .kde

---

### Post by cotcot on 2009-03-09
Owner and group are 'root'. That is not normal. You should see here your user name. You need to change the owner fromm root to your username.

```
sudo chown -R yourusername /home/yourusername/.kde
``` to change the first root (user)
```
sudo chown -R :yourusername /home/yourusername/.kde
``` to change the second root (group)

---

### Post by cubeist on 2009-03-09
Thanks for beating me to the punch cotcot!

I like to change ownership with one command:
```
sudo chown -R yourusername:yourusername /home/yourusername/.kde
```

I should mention this will fix the permission problem, but I have no idea how to fix the first error message about the .DCOP server

---

### Post by maxclimber1w on 2009-03-09
That did it! Thanks so much for the help guys!

---

### Post by kayosiii on 2009-03-09
A much better solution would be to see if the folders in question do exist and make them writable... If they are not already
.kde if you could let me know if the folders in question do exist
and who owns them...

---

### Post by nilsnh on 2011-01-18
> **cubeist said:**
> Thanks for beating me to the punch cotcot!

I like to change ownership with one command:
```
sudo chown -R yourusername:yourusername /home/yourusername/.kde
```

I should mention this will fix the permission problem, but I have no idea how to fix the first error message about the .DCOP server

It worked for me as well. Yay! :KS

---

