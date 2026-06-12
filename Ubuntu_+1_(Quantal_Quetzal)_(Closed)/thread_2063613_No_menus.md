---
title: "No menus?"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by as2000 on 2012-09-27
I don't seem to have any menus in any of my application in 12.10, ie: File Edit View.. Even maximized the do not appear in the dash. Is there a setting I missed?

---

### Post by cariboo on 2012-09-27
Do you mean the ones in the screenshot?

---

### Post by philinux on 2012-09-27
> **as2000 said:**
> I don't seem to have any menus in any of my application in 12.10, ie: File Edit View.. Even maximized the do not appear in the dash. Is there a setting I missed?

Have you moved your mouse to the top left to reveal the global menu?

---

### Post by as2000 on 2012-09-27
> **cariboo907 said:**
> Do you mean the ones in the screenshot?

Yes. I have no menus in any applications or even maximized. I want to make sure this is a bug before I file it or is it something else

---

### Post by as2000 on 2012-09-27
> **philinux said:**
> Have you moved your mouse to the top left to reveal the global menu?

No menu. Nada. Zip

---

### Post by philinux on 2012-09-27
> **as2000 said:**
> No menu. Nada. Zip

Try this before resetting unity:-

from a terminal
```
sudo apt-get install --reinstall appmenu-gtk appmenu-gtk3 appmenu-qt 
```

Log out then in if no change.

If that doesn't work try a unity reset which will lose you any customisations you have made.

Open a terminal.

```
unity --reset
```

[edit] unity reset replaced by dconf reset -f /org/compiz/

---

### Post by as2000 on 2012-09-27
I will try that when I get home. Thanks!

---

### Post by mc4man on 2012-09-27
The unity --reset command is no longer used, see
[http://ubuntuforums.org/showpost.php?p=12222839&postcount=9](http://ubuntuforums.org/showpost.php?p=12222839&postcount=9)

---

### Post by arpanaut on 2012-09-27
@philinux  I thought that 'unity --reset' had been removed from Unity 6.6?

nevermind...  too slow

---

### Post by philinux on 2012-09-27
> **mc4man said:**
> The unity --reset command is no longer used, see
[http://ubuntuforums.org/showpost.php?p=12222839&postcount=9](http://ubuntuforums.org/showpost.php?p=12222839&postcount=9)

Sheesh I missed that thread. Reminder for me >```
dconf reset -f /org/compiz/
``` :p

Full instructions [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html?m=1](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html?m=1)

---

### Post by as2000 on 2012-09-27
@philinux Tried the re-install of the appmenu files and restarted. Nothing. 

Then, tried the:  dconf reset -f /org/compiz/ and got an error. (see terminal screenshot) Other screenshots show no menus...

Maybe I will try to re-install.

---

### Post by mc4man on 2012-09-28
!st. -  don't use root (sudo), these are user settings
2nd -  you didn't leave a space between  -f &  /org/compiz/ 

A fresh beta 2 install wouldn't be the worst thing, updates don't always get it 

If you wish - create a new user, login & see. If that user is good then the problem is local & something in your user's configs & probably can be  fixed

---

### Post by grahammechanical on 2012-09-28
In the second image you should see the words "Firefox web browser" and then when you move your mouse over that corner of the top panel you should see the File Edit View etc., menu options.

The third image should show something similar but with "Chromium web browser" instead of Firefox. This should also be the case with applications like Libreoffice.

The File Edit View etc., menus have now gone into the top panel. so you should be seeing something with a mouse over.

Regards.

---

### Post by philinux on 2012-09-28
"Firefox web browser" should always be visible when FF has focus. In the OP's second image it is not there.

---

### Post by as2000 on 2012-09-28
I did a complete re-install of 12.10 last night after trying all the suggestions. All of the menus are now visible and work as they should. To date, I have never seen this happen in any alpha, beta or release install. Chalk it up as one for the books. I do thank all that has given suggestions. As always, you were all very helpful.

---

