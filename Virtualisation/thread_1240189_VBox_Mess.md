---
title: "VBox Mess"
date: 2009-08-14
forum: Virtualisation
---

### Post by Mnew2Linux on 2009-08-14
Hello, I am running VBox 3.02 r49928 on my Windows XP SP2 host (sys specs: Lenovo T61 Intel Centrino Core 2 Duo T7700, 2.4ghz, 2gb RAM).  A problem recently arose on my client Ubuntu 9.04 where the login screen was truncated after installing desktop effects (though not Compiz).  I just recently got the Internet connection up and running on Ubuntu (client) and so I had 191 updates pushed to me...this is where I ran into more problems.   I have attached 2 screenshots.

Here is the login screen.  Now, this has looked like this for some time now but I figured because I can still login, a fix will come and everything will be fine...
[ATTACH]124833[/ATTACH]
...until today.  I finally updated and now the screen looks like this.  I had guest additions hooked up but that no longer works and I have to right-ctrl to capture/uncapture my pointer.  
[ATTACH]124834[/ATTACH]

Any tips?  If I need more information, please let me know.  I'm still new to Linux and haven't taken the time to understand any easy fixes.  Thanks...

-Lee

---

### Post by jocampo on 2009-08-14
It looks like your X server is #$%^&5 (edited for minors ;-) )

X, is the part which controls the GUI in Ubuntu. In my opinion, there is a wrong parameter, maybe screen resolution or refresh, that is broken. Boot into live CD and edit your X file. Maybe that's the easier way to fix it.

---

### Post by jaqrah on 2009-08-14
I have the same problem running 9.10 in vbox, although it has nothing to do with compiz effects.  I don't have them enabled.  Although, it didn't start happening until I enabled guest additions

I listen for the sound cues. I type in Username, tab, and then password.  Loads as normal and works perfectly with guest additions executing normally.

I just figured it was a 9.10 alpha issue but maybe it is something else, like a guest additions issue??

---

### Post by Mnew2Linux on 2009-08-20
> **jocampo said:**
> It looks like your X server is #$%^&5 (edited for minors ;-) )

X, is the part which controls the GUI in Ubuntu. In my opinion, there is a wrong parameter, maybe screen resolution or refresh, that is broken. Boot into live CD and edit your X file. Maybe that's the easier way to fix it.

Cheers mate!  Thanks for the heads up on that one.  When I get time I will definitely look into how to access X...I'm sure there are links here to do that?  If so please post some; as my UID says, I'm new to Linux (relatively speaking of course).  Thx again!

-Lee

---

