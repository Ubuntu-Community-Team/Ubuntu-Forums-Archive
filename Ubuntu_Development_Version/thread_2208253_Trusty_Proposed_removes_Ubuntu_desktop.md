---
title: "Trusty Proposed removes Ubuntu desktop"
date: 2014-02-27
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-02-27
In preparation for installing Unity 8 preview session I enabled the trusty-proposed repository and ran update/upgrade. I rebooted and although I could enter the password the system never loaded to the Unity desktop.

I tried again to see if I could load to Gnome Flashback and noticed that the Ubuntu option was not in the list. I have not yet got as far as installing unity8-desktop-session-mir.

Regards.

---

### Post by ventrical on 2014-02-27
> **grahammechanical said:**
> In preparation for installing Unity 8 preview session I enabled the trusty-proposed repository and ran update/upgrade. I rebooted and although I could enter the password the system never loaded to the Unity desktop.

I tried again to see if I could load to Gnome Flashback and noticed that the Ubuntu option was not in the list. I have not yet got as far as installing unity8-desktop-session-mir.

Regards.

 graham,

What I do is enable Trusty proposed. Then update. After that I do:

```

sudo apt-get install unity8-desktop-session-xmir  or x11


```

Then disable the trusty-proposed repo.

If I understand you message correctly, I think you upgraded all the proposed files. That will certainly cause breakage., nas pa?

You are a braver man than I :) lol

 Regards..

---

### Post by grahammechanical on 2014-02-27
I certainly did upgrade all the proposed. And then begun to regret my actions. Silly me for trying to be clever.

Synaptic showed ubuntu-desktop ready for an upgrade. So, mark all upgrades + apply and a ton more stuff came down and I now have Ubuntu (default) back as a menu option.

Now to see what happens when I install unity8 preview. I think the code is

```
sudo apt-get install unity8-desktop-session-mir
```

I got it from here

[http://www.omgubuntu.co.uk/2014/02/unity-8-desktop-preview-session-14-04](http://www.omgubuntu.co.uk/2014/02/unity-8-desktop-preview-session-14-04)

I also now see unity8-desktop-session-mir in the software centre.

Regards.

---

### Post by anca-emanuel on 2014-02-27
^ that software is not ready. I just reinstalled.

---

### Post by ventrical on 2014-02-27
> **anca-emanuel said:**
> ^ that software is not ready. I just reinstalled.

+1 ... will not work here either .. although you can install the x11 version .. but after restart the little mobile unity thingy will come up, however, you have to hard reboot, and, after that you loose unity desktop plus a few other things (like cannot use CTrl+Alt+F1 to get into terminal) [have to use terminal from recovery mode root].

Good luck :)

[URL="http://ubuntuforums.org/showthread.php?t=2208236"]http://ubuntuforums.org/showthread.php?t=2208236


[/URL][http://ubuntuforums.org/showthread.php?t=2208141&p=12940982#post12940982](http://ubuntuforums.org/showthread.php?t=2208141&p=12940982#post12940982)

---

