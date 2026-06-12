---
title: "[WINE] Not following through on opening certain programs"
date: 2010-11-04
forum: Wine
---

### Post by TheFlyingTangler on 2010-11-04
Hi, if this question has been asked and answered, apologies. I searched a lot for an answer but didn't seem to find a problem that matched mine.

Anways, on to the meat of this.

I recently updated to 10.10, and then updated all my video card drivers (I'm using an ATI RV630 HD 2600XT). I then updated Wine to version 1.3 and when I would try to run WoW, it would pop up on the taskbar "Opening World of Warcraft" sit there for a moment, then just go away. If I click on the launcher, it will bring up the launcher as per usual, however upon clicking "Play" the window closes and nothing happens.

I tried opening it from Terminal, and I got this respone


err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"H:\\.wine\\dosdevices\\c:\\Program Files\\World Of Warcraft\\WoW.exe" failed, status c0000005


Any help would be most appreciated,

---

### Post by Hairy_Palms on 2010-11-04
could ya post the output of
```
glxinfo | grep render
```

---

### Post by cwwilson721 on 2010-11-04
> **TheFlyingTangler said:**
> 

I recently [COLOR="Blue"]updated[/COLOR] to 10.10, and then [COLOR="Green"]updated[/COLOR] all my video card drivers (I'm using an ATI RV630 HD 2600XT). I then [COLOR="DarkOrange"] updated Wine to version 1.3[/COLOR] and when I would ... With those 3 'updates', were they 'updates'? or did you do a fresh install of 10.10? (If fresh, drivers and wine1.3 are installs, not updates).

If 'updated' the ATi driver, was it through Additional Drivers?
Because:> **TheFlyingTangler said:**
> 
err:module:[COLOR="Red"]attach_process_dlls "opengl32.dll" failed to initialize,[/COLOR] aborting...the driver didn't load opengl. Either wine missed it, or ATi driver, or could be Xorg.

If all was 'updated', then something went south during all that flurry of activity during 'updating'

---

### Post by TheFlyingTangler on 2010-11-04
Sorry for the unclear language, here's a better breakdown

I upgraded from 10.0 to 10.4, rebooted, then straight to 10.10. During the upgrade it removed my the open source ATI driver I was using, so I had to open in Recovery Mode. I then downloaded and installed the proprietary driver from ATI, rebooted, and Ubuntu opened perfectly fine. I tried running WoW, got the same error I posted, so I began searching the internet for answers. The most common one seemed to be updating Wine to 1.3.x, so I uninstalled 1.2 and installed 1.3 via Synaptic. As you can see, nothing changed.

Also, I ran that command line and nothing happened. It just drops me down a line.

Thanks again for the help so far!

*EDIT* When I run the command "glxinfo" it returns the following:

name of display: :0.0
Segmentation fault

I'm guessing something isn't installed or isn't installed correctly, but I'm new to all this so I could be way off

---

### Post by marl30 on 2010-11-04
Try ```
wineboot --update
``` to see if it repairs whatever error had developed. It's also better to stick with the stable versions of Wine. I upgraded from 1.2.1 to 1.3.6, and while most of my other programs continued to work ok, I noticed that one of my game stop working. I ran ```
sudo apt-get install wine1.2
``` in terminal. After I downgraded wine, everything worked fine after that.

---

### Post by TheFlyingTangler on 2010-11-04
Neither of those helped at all :/

I guess I'll just partition and do a small windows 7 install. It hurts to do it, but I've pretty much given up on it.

Thanks for all the suggestions, they've been very much appreciated!

---

