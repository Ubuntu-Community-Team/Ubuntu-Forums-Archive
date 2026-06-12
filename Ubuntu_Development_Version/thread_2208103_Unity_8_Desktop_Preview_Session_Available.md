---
title: "Unity 8 Desktop Preview Session Available*"
date: 2014-02-26
forum: Ubuntu Development Version
---

### Post by philinux on 2014-02-26
[http://www.omgubuntu.co.uk/2014/02/unity-8-desktop-preview-session-14-04?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2014/02/unity-8-desktop-preview-session-14-04?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

The emphasis is very much on Preview.

---

### Post by Mateusz Stachowski on 2014-02-26
I was trying to use it on a daily live image of Trusty. I ended up with black screen and in the top right corner "_".

There is also a PPA which has newer packages than the one in proposed. Also there are instructions in that PPA about updating the default EGL driver.

> NOTE: You may need to undo the damage done when libhybris was installed by running the command

  sudo update-alternatives --config x86_64-linux-gnu_egl_conf


and choosing the non-libhybris alternative. The symptom that you need to do this is an error in /var/log/lightdm/unity-system-compositor.log that says something like this:


undefined symbol: _glapi_tls_Dispatch

[https://launchpad.net/~unity8-desktop-session-team/+archive/custom](https://launchpad.net/~unity8-desktop-session-team/+archive/custom)

---

### Post by ventrical on 2014-02-26
Installed it from proposed. Now ,  same as above ... blackspace and "_".

---

### Post by Mateusz Stachowski on 2014-03-01
I've tried again today and Unity8 on Mir worked. 

I used a daily live of Trusty with enabled proposed and the PPA that I mentioned in my previous post. There was no mouse cursor but the mouse input worked. I had to use it in blind mode but managed to open webbrowser-app and system settings in sidestage. I had no internet because installing unity8-desktop-session-mir removes modemmanager so no content loaded in video lens and other online sources. 

If you want to mess with this yourself then I really recommend running from live session not your regular install.

---

