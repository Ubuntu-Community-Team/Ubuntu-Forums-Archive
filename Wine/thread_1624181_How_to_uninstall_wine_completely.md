---
title: "How to uninstall wine completely?"
date: 2010-11-17
forum: Wine
---

### Post by jotto! on 2010-11-17
I installed a version of wine using the Ubuntu Software Centre and have uninstalled it using the same method.

I have also tried 

```

rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.{xpm,png}
rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png}

```But, wine is still listed in my application menu and if I click on Configure wine, it runs the configuration application. How can this be if Wine has been removed?

EDIT, I think I may have tried to also install the Beta version by adding a line of code to my software sources [I]
ppa:ubuntu-wine/ppa
[/I]Could it be that I have files from 2 different installations?

---

### Post by Soulcage on 2010-11-18
sudo apt-get purge wine1.3

---

### Post by jotto! on 2010-11-18
> **Soulcage said:**
> sudo apt-get purge wine1.3

Ok that certainly removed some files, thanks!

Is it safe for me to delete any rogue wine files I come across? Would any wine files be installed by default in an Ubuntu install?

I have just looked in the.local > share > applications folder and have found several references to wine. OK to simply delete?

Thanks.

---

### Post by doctorzeus on 2010-11-18
> **jotto! said:**
> Ok that certainly removed some files, thanks!

Is it safe for me to delete any rogue wine files I come across? Would any wine files be installed by default in an Ubuntu install?

I have just looked in the.local > share > applications folder and have found several references to wine. OK to simply delete?

Thanks.

It doesn't delete your ".wine" directory in /home/(usr)/
you have to delete this yourself if you want a clean windows slate.

If something goes wrong you can usually just delete the ".wine" directory and Wine will create a new one for you when you load winecfg...easier than purging and re-installing wine.

Should be fine to delete the share stuff although should have been removed during the purge

Hope this helps!

Doctorzeus

P.S

you may want to also delete your /home/(usr)/.cache/winetricks/ directory as well if your having issues..

---

### Post by matt_symes on 2010-11-18
Hi

> Is it safe for me to delete any rogue wine files I come across? 

Yes

> 
Would  any wine files be installed by default in an Ubuntu install?

No

> I have just looked in the.local > share > applications folder and  have found several references to wine. OK to simply delete?

Yes. 

Kind regards

---

### Post by jotto! on 2010-11-18
Thanks for the replies! will start deleting some files and see if we cant get this thing up and running again!

---

### Post by Soulcage on 2010-11-19
If you want to delete all the files wine makes then run this command in a terminal ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
```

---

