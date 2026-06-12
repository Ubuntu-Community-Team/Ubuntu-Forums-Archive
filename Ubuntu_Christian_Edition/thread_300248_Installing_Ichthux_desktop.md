---
title: "Installing Ichthux desktop?"
date: 2006-11-15
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2006-11-15
When I try and install the Ichthux desktop, it doesn't work.  There error in the xterm window is: ```
WARNING: The following packages cannot be authenticated!  ichthux-artwork-usplash ichthux-emoticons superkaramba-themem-losungen ichthux-default-settings language-selector-qt sword-text-tr ichthux-desktop
E: There are problems and -y was used without --force-yes

```
??  Just wanted to let you know.

Shane

---

### Post by mhancoc7 on 2006-11-15
> **shane2peru said:**
> When I try and install the Ichthux desktop, it doesn't work.  There error in the xterm window is: ```
WARNING: The following packages cannot be authenticated!  ichthux-artwork-usplash ichthux-emoticons superkaramba-themem-losungen ichthux-default-settings language-selector-qt sword-text-tr ichthux-desktop
E: There are problems and -y was used without --force-yes

```??  Just wanted to let you know.

Shane

Thanks, did you upgrade to v1.5? I assume you are using the Ubuntu CE Installer to install ichthux.
God Bless, Jereme

---

### Post by mhancoc7 on 2006-11-15
You know it sounds like you may not have the Ichthux key. The script should have added it, that is assuming you used the upgrade_me script. Could you try the following for me and let me know if it worked.

```
 wget http://archive.ichthux.com/ichthux.asc # This downloads the key to identify the Ichthux repository
sudo apt-key add ichthux.asc
sudo apt-get update
```

Then run the Ubuntu CE Installer and try to install it again.

God Bless, Jereme

---

### Post by shane2peru on 2006-11-16
Jereme,

    Thanks for the help, that fixed it.  Yes, I used the upgrade_me Script.  Seemed to work fine.  Thanks.

Shane

---

### Post by mhancoc7 on 2006-11-16
> **shane2peru said:**
> Jereme,

    Thanks for the help, that fixed it.  Yes, I used the upgrade_me Script.  Seemed to work fine.  Thanks.

Shane

Awesome, thanks for letting me know. I will retest the upgrade_me script to be sure it is working. Hopefully nothing is wrong with it and it was just one of those things. :-k :)
God Bless, Jereme

---

### Post by shane2peru on 2006-11-16
Right, no problem.  Thanks for the distro!  I do enjoy using it.

Shane

---

