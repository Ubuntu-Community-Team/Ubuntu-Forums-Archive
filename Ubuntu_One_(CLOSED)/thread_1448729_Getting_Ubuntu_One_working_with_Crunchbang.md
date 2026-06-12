---
title: "Getting Ubuntu One working with Crunchbang"
date: 2010-04-07
forum: Ubuntu One (CLOSED)
---

### Post by HPD2 on 2010-04-07
Hey I was wondering if there is a way to install and get ubuntu one working on crunchbang. 
I tried following the instructions at
[http://crunchbanglinux.org/forums/topic/3333/how-to-setup-ubuntu-one-under-90401/](http://crunchbanglinux.org/forums/topic/3333/how-to-setup-ubuntu-one-under-90401/)
but when i try to launch it nothing happens and it just spits back errors like 
```
bash: ubuntuone-client-applet: command not found
```Any help would be much appreciated.

---

### Post by duanedesign on 2010-04-07
The ubuntuone-client-applet has been replaced by ubuntuone-preferences. Try entering ubuntuone-preferences in the commandline.

Let us know how it goes.

best of luck,
duanedesign

---

### Post by HPD2 on 2010-04-07
Thanks that helped, the good news is that it does some thing new, the bad news is its still not working, yet.  Now it gives me a popup error message.
"Authorization Error Expired timestamp: given 1270656738... greater difference than threshold 900"
Also there are no errors in the terminal window I launched it from just the popup that is in the screen shot

---

### Post by joshuahoover on 2010-04-08
> **HPD2 said:**
> Thanks that helped, the good news is that it does some thing new, the bad news is its still not working, yet.  Now it gives me a popup error message.
"Authorization Error Expired timestamp: given 1270656738... greater difference than threshold 900"
Also there are no errors in the terminal window I launched it from just the popup that is in the screen shot

This may mean your system time is wrong. Can you check the time on your computer and make sure it is correct? If the time is right, try this at a terminal session:

killall ubuntuone-login ubuntuone-syncdaemon ubuntuone-preferences
ubuntuone-preferences

This should kill all running ubuntuone related processes and then open the Ubuntu One Preferences. The Preferences should display for several seconds and then Firefox will open to an Ubuntu One web page prompting you to add your computer to your account. (NOTE: You may get prompted to login to the Ubuntu One web site first before you see the add your computer page.)

Thank you,

Joshua

---

### Post by HPD2 on 2010-04-08
Thanks for the help so far guys, my system time was way off. I didn't notice it till you suggested it. I don't use the computer that I'm trying to set it up on very often, its mostly just a server for what ever. Any way changing the time did the trick, and I can now get the preferences window open, but nothing shows up in the task bar at the bottom of the screen. It does look like it is syncing files for the time being so I'm just gonna let it go for now.

---

