---
title: "ubuntu one"
date: 2010-11-11
forum: Ubuntu One (CLOSED)
---

### Post by Amy_1990 on 2010-11-11
I installed ppa:ubuntuone/stable ppa and now when i go to ubuntu one from the me-menu or from preferences i can only open it one time unless i reboot then i can open it 1 more time can someone help me with this i am running 10.04.Thanks

---

### Post by Sven6210 on 2010-11-12
> **Amy_1990 said:**
> I installed ppa:ubuntuone/stable ppa and now when i go to ubuntu one from the me-menu or from preferences i can only open it one time unless i reboot then i can open it 1 more time can someone help me with this i am running 10.04.Thanks

What do you mean with "I can open it one time"? Do you refer to a log-on on the website? Or the synchronisation tool? And if you are referring to the synchronisation tool, are you sure your computer is properly registered and linked with your UbuntuOne account?

---

### Post by Amy_1990 on 2010-11-12
Thank you, 

I can only open ubuntu one preferences one time if i start to upload a file and i want to slow the upload speed i can't reopen it again for some reason.

---

### Post by duanedesign on 2010-11-12
Could you try starting the preferences from the Terminal (Applications > Accesories > Terminal) with the command:

```
ubuntuone-preferences
```

This might result to some clues being printed to the Terminal.

Another thing you might check. If Ubuntu One Preferences is not opening check to make sure the ubuntuone-preferences process is not still running. You can do that with this command:

```
ps aux | grep ubu
```

look for - **/usr/bin/python /usr/bin/ubuntuone-preferences**

if you find it still running you can try and kill it with this command:

```
killall ubuntuone-preferences
```

run **ps aux | grep ubu** again to see if it quit. If it still is not dead you can try:

```
killall -9 ubuntuone-preferences
```

Lastly, we can take a look at the log file for Ubutnu One Preferences. If you post it please enclose the log text in the **CODE** tags (select the text and click the # in the Post Editor Toolbar). You can find this file at:

~/.cache/ubuntuone/log/u1-prefs.log

**NOTE:** To see the .cache directory you may need to View > Hidden Files (Ctrl + h)

---

