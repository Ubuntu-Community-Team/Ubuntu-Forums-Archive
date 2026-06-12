---
title: "Themes Wiped Out"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by AAllInFlynn on 2012-10-02
Ran my morning update on 02Oct12 and the default theme was gone (black title bar on windows with exit, minimize, and maximize buttons on the right[Edit: should have said left]).  I know I am running a testing release, so these things are to be expected.  However, when the new themes are pushed during an update will they automatically appear or am I going to have to figure out how change the themes to get back the default appearance?

---

### Post by philinux on 2012-10-02
> **AAllInFlynn said:**
> Ran my morning update on 02Oct12 and the default theme was gone (black title bar on windows with exit, minimize, and maximize buttons on the right) were wiped out.  I know I am running a testing release, so these things are to be expected.  However, when the new themes are pushed during an update will they automatically appear or am I going to have to figure out how change the themes to get back the default appearance?

First off right click desktop > change background option then try changing themes to something else then back to ambiance.

[edit] if that doesnt work run this to reset unity 

```
dconf reset -f /org/compiz/
```

---

### Post by AAllInFlynn on 2012-10-02
> **philinux said:**
> First off right click desktop > change background option then try changing themes to something else then back to ambiance.

[edit] if that doesnt work run this to reset unity 

```
dconf reset -f /org/compiz/
```

Phil,

Thanks for the quick response.  I tried both steps:

1.  Right clicked on the desktop, selected Change Desktop Background > Theme

The two options that appeared were:
  High Contrast
  High Contrast Inverse

2.  Executed the dconf reset - /org/compiz and that didn't work.  Assume that was superfluous since the correct theme doesn't appear to be installed.

---

### Post by philinux on 2012-10-02
Something odd if only those two themes. You should have ambiance and radiance too. Run this.

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by AAllInFlynn on 2012-10-02
> **philinux said:**
> Something odd if only those two themes. You should have ambiance and radiance too. Run this.

```
sudo apt-get install --reinstall ubuntu-desktop
```

Ran the command, then the theme appeared in the drop-down menu.  Selected ambiance and that changed the color scheme back to the settings that I had prior, however the exit, maximize, and minimize controls were on the right vs. the left.  A quick logout and login corrected those issues.

Phil, thank you so much for your help, I know this may have just been an minor thing, but your assistance was invaluable.

---

### Post by philinux on 2012-10-02
> **AAllInFlynn said:**
> Ran the command, then the theme appeared in the drop-down menu.  Selected ambiance and that changed the color scheme back to the settings that I had prior, however the exit, maximize, and minimize controls were on the right vs. the left.  A quick logout and login corrected those issues.

Phil, thank you so much for your help, I know this may have just been an minor thing, but your assistance was invaluable.

Glad it's sorted. I'm guessing you may have done a partial upgrade which is not recommended during a development release and this removed some packages.

See this sticky [http://ubuntuforums.org/showthread.php?t=1966935](http://ubuntuforums.org/showthread.php?t=1966935)

---

### Post by AAllInFlynn on 2012-10-02
> **philinux said:**
> Glad it's sorted. I'm guessing you may have done a partial upgrade which is not recommended during a development release and this removed some packages.

See this sticky [http://ubuntuforums.org/showthread.php?t=1966935](http://ubuntuforums.org/showthread.php?t=1966935)

You are correct, that is what I did, I actually ran:

```
sudo apt-get dist-upgrade
```

from the command line.  I will no longer run that (as recommended in the how to) and instead run the following command for future updates:

```
sudo apt-get upgrade
```

---

### Post by nilarimogard on 2012-10-02
Running just "upgrade" will hold back packages that need new dependencies. You can continue to use "dist-upgrade" but make sure you check out the output so it doesn't remove any important packages.

---

### Post by philinux on 2012-10-02
You do need dist-upgrade and in fact it's essential for say a new kernel,but you need to look carefully what it's doing and choose "n" if it wants to remove al lot of stuff, until the repo's settle down again. Occasionally dependencies are in a state of flux.

---

### Post by AAllInFlynn on 2012-10-02
> **philinux said:**
> You do need dist-upgrade and in fact it's essential for say a new kernel,but you need to look carefully what it's doing and choose "n" if it wants to remove al lot of stuff, until the repo's settle down again. Occasionally dependencies are in a state of flux.

Thanks.  I went through the log file

```
/var/log/apt/history.log
```

and was able to figure out what was un-installed this morning and re-installed them.  I will be more diligent when I do the "dist-upgrade" and make sure I have had my second cup of coffee before doing so...

---

### Post by philinux on 2012-10-02
> **AAllInFlynn said:**
> Thanks.  I went through the log file

```
/var/log/apt/history.log
```

and was able to figure out what was un-installed this morning and re-installed them.  I will be more diligent when I do the "dist-upgrade" and make sure I have had my second cup of coffee before doing so...

Just be aware that sometimes it is necessary for the system to remove obsolete packages so that it can install new ones.

---

