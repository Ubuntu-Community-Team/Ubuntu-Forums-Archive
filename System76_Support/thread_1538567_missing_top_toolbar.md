---
title: "missing top toolbar"
date: 2010-07-25
forum: System76 Support
---

### Post by dscotese@hotmail.com on 2010-07-25
My system 76 linxus is new.  While downloading my first set of updates, the update got stuck.  After a few hours I restarted the system since I could not close the update window.  Now, the top toolbar is missing.  The only icon I have is the trash can. Any suggestions?

---

### Post by mhgsys on 2010-07-25
open a terminal (press alt+f2, ..in the box type; gnome-terminal)
 
then type in terminal;


```
gconftool-2 --recursive-unset /apps/panel
```

and restart gdm after that

switch to console ( press Ctrl+Alt+f1 ,f2, f3, etc) type

```
sudo /etc/init.d/gdm stop
```


```
sudo /etc/init.d/gdm start
```

Panels should be back to original.

---

### Post by dscotese@hotmail.com on 2010-07-25
> **dscotese@hotmail.com said:**
> My system 76 linxus is new.  While downloading my first set of updates, the update got stuck.  After a few hours I restarted the system since I could not close the update window.  Now, the top toolbar is missing.  The only icon I have is the trash can. Any suggestions?




thank you

---

### Post by mhgsys on 2010-07-25
Erh. You're welcome 

I guess you did not mean to quote your own text.. lol.

Anyway; 

If it's solved with the commands I gave you.. please mark this thread as solved. 
Go to tread tools > mark this thread as solved.

---

### Post by dscotese@hotmail.com on 2010-07-25
I got stuck at the restart gdm.  There was no restart command in the terminal window.  I did restart the computer( i do not know what gdm is).  I then went to control alt f1, f2 and it wanted me to log in but I was unable.

---

### Post by mhgsys on 2010-07-26
As long if you managed to type in the

[COLOR="DarkBlue"]gconftool-2 --recursive-unset /apps/panel[/COLOR]

in a terminal, rebooting instead of restarting gdm will do the same trick.
and panels should be back to original.

Anyway; Just to explain a little;

when switching to console ( with Ctrl+Alt+f1 ,f2, f3, etc) (Ctrl+Alt_f7 should be x again)
 your suppose to l[COLOR="DarkBlue"]ogin with your username and press enter, then type your password and press enter[/COLOR]. (you wont see the password when typing..)

Also;

[COLOR="DarkBlue"]sudo /etc/init.d/gdm stop is the command to stop gdm

sudo /etc/init.d/gdm start is the command to start gdm[/COLOR]

*You can also use sudo service gdm start/stop/restart*
(I never use restart because it won't always work correctly)

And finally

[COLOR="DarkBlue"]GDM - The GNOME Display Manager.[/COLOR]

---

### Post by dscotese@hotmail.com on 2010-08-03
Thank you thank you thank you.

---

