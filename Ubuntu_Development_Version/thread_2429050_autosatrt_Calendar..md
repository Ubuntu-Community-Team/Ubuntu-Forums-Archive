---
title: "autosatrt Calendar."
date: 2019-10-12
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2019-10-12
Need some help.  I simply wanted to setup calendar to autostart at bootup/restart.  All I believe I had to do was run startup app, add,and then name it Calendar.  Also added the file path asusr/bin/Calendar then save.  But on bootup/restart, nothing happens.


What Am I doing wrong?


Gort

---

### Post by Skaperen on 2019-10-12
if you want to do this from a command line, you can put a [COLOR=#a52a2a][FONT=courier new]**.desktop**[/FONT][/COLOR] file in [COLOR=#0000cd][FONT=courier new]**~/.config/autostart**[/FONT][/COLOR] to have it launched at login.  make that directory if it does not exist, yet.  that's how i get my command line terminals to start up at login.

---

### Post by PaulW2U on 2019-10-13
In GNOME Tweaks go to Startup Applications, click the '+' button,  scroll down to Calendar and click 'Add'.
Log out and back in again.
You should find Calendar already started when the desktop appears.
No need to enter any application paths or filenames.

---

### Post by Hewjr100 on 2019-10-13
Will give both a try.  BTW thanks and sorry for the delayed response, for some reason I did not get the email notification.

Henry

---

