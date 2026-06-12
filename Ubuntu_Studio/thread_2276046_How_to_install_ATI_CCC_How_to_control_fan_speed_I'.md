---
title: "How to install ATI CCC? How to control fan speed? I'm using ATI HD4850"
date: 2015-04-30
forum: Ubuntu Studio
---

### Post by jaspa on 2015-04-30
Hi

Ysterday I tried to install ATI xorg from ubuntu software center but it made the whole system really sluggish and extremely slow.
Fortunately it was a clean install so I could just reinstall it to make it work again.

Now I need in how to install ATI CCC or something else to control fan speed either GUI or commandline?
I already found some commands but they don't work e.g. fglrx isn't installed and command isn't found or some can't be installed which would include this command.

I'm using latest Ubuntu Studio 15.04.

---

### Post by jaspa on 2015-04-30
So, I just decided to try again and now it actually installed fglrx. However, results was the same: slooow, sluggish, 2 FPS.

And now I also managed to remove it to gain normal performance. But before removal/uninstalling I tried to **startx **which did start a new desktop env or whatever the naming would be.
And of course, there isn't any corresponding **stopx **like one could think.

Since then I've had a xfce and ubuntu studio sessions(? correct me if I'm wrong) and when I'm trying to login it just flashes few screens and returns back to login. Seems like it can't decided what to use and won't allow to login.

Hmm, this really didn't go like planned. **CTRL+ALT+F1** takes me to terminal so what can I do there? Login works so I can sudo.

---

### Post by jaspa on 2015-04-30
Few retries showed that it states following after hitting login:
[B]starting version 219
[OK] Started Light Display Manager[/B]

Then back to login screen.

**EDIT:** Xorg version 1.17 (arch documentation states that it does not support catalyst;  and later catalyst > 12.x does not support such old ATI as mine)
So I need to forget whole display card?

---

