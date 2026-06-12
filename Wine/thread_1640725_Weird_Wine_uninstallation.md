---
title: "Weird Wine uninstallation"
date: 2010-12-08
forum: Wine
---

### Post by Godspell on 2010-12-08
Hi all,

I've been trying to completely remove Wine using various ways.
The first thing I did was
> rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
Everything went well except the Wine entry was still in the Main Menu which I thought wasn't a problem (cause I could always use Alacarte) BUT when I click "Configure Wine" 
the msg window comes up saying "Configuring Wine..."
After that Wine actually comes up and everything seems to work well.

I've also shift-deleted the /home/.wine folder but it doesn't make any difference.

So, I'm really puzzled. Why is it still there after being deleted for couple of times?

Please let me know.

Many thanks and regards,
GS

---

### Post by qamelian on 2010-12-08
Basically, all you've done is to remove your personal wine configuration. To actually uninstall wine, open a terminal and type:

```
sudo apt-get remove --purge wine
```

and press enter. This will actually uninstall the wine application.

---

### Post by Godspell on 2010-12-08
It doesn't work, mate. It keeps saying
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
and wine is very much still there, and working good lol

Are you sure what I was doing previously was ONLY removing personalisations??
I even SHIFT-DELETED the folder home/.wine and saw it disappeared but wine was still working.

So any bright ideas?

Thanks for replying btw.

Regards,
GS

---

### Post by Soulcage on 2010-12-09
```
sudo apt-get purge wine1.3
```
```
sudo apt-get purge wine1.2
```
```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
```

---

### Post by Godspell on 2010-12-09
> **Soulcage said:**
> ```
sudo apt-get purge wine1.3
``````
sudo apt-get purge wine1.2
``````
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
```

Nicely done, mate. Worked like a charm :) so thank you.

Can I ask what does purge mean?

And d'you have any clue why it wasn't unwised even though I deleted /home/.wine folder before??

Anyway, thanks for your help.

Regards,
GS

---

