---
title: "after uninstall wine"
date: 2011-04-04
forum: Wine
---

### Post by Sina_RJ on 2011-04-04
i uninstall wine from terminal,3 weeks ago,cos my software center didn't work
now every time i go to applications i see wine menu,and every .exe file is shown in wine format
I'm tired of this and wanna move on :(
what should i do?
how can i remove it totally from my laptop.
i remove it with this
```
sudo apt-get remove win
```
please tell me what should i do :(

---

### Post by dino99 on 2011-04-05
open synaptic, search for "wine" and completly delete (right click) all related wine packages. This will remove entries menu and symlinks. Then into nautilus, the hidden .wine folder should be gone, if not, manually delete it.

---

### Post by Soulcage on 2011-04-05
```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension* && rm -r $HOME/.cache/winetricks
```

---

### Post by Sina_RJ on 2011-04-05
> **dino99 said:**
> open synaptic, search for "wine" and completly delete (right click) all related wine packages. This will remove entries menu and symlinks. Then into nautilus, the hidden .wine folder should be gone, if not, manually delete it.


the only package which is installed is the one in screenshot,should i remove it?

---

### Post by Sina_RJ on 2011-04-05
> **Soulcage said:**
> ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension* && rm -r $HOME/.cache/winetricks
```

this is what i get after copy paste exactly what you said
```
rm: cannot remove `/home/moeen/.cache/winetricks': No such file or directory

```
should i change something?

---

### Post by rsnow on 2011-04-05
I recently had a similar situation. My solution was to use Places/search for files to locate all wine files and then to manually change ownership from root to myself and finally to remove the file. 

I used sudo chown myname: filename
and rm filename.

---

### Post by Soulcage on 2011-04-08
Sina_RJ you only got that message because you didn't use winetricks, you can just ignore it.

---

