---
title: "(noob) How to nuke C drive and start over?"
date: 2010-12-03
forum: Wine
---

### Post by Psyael on 2010-12-03
I installed something that contains Windows spyware to my WINE drive (coupons.com printer) and it's uninstall wasn't very successful (I got an error message followed by a notification of a successful uninstall).

I have hardly anything on my Wine drive at all that can't be easily replaced, so how can I wipe it and then set it up again so to be sure this garbageware is gone? Thanks.

---

### Post by ajgreeny on 2010-12-03
Show hidden files and folders in nautilus with Ctrl+H and remove the **.wine** folder in your home.

It may also be worth purging wine with synaptic, and then re-installing, but I think removing your hidden .wine folder should be enough.  There should certainly be no need to wipe the drive and reinstall the whole ubuntu OS.

---

### Post by CharlesA on 2010-12-03
+1 to purge, deleting ~/.wine and reinstalling.

---

### Post by cwwilson721 on 2010-12-03
> **CharlesA said:**
> +1 to purge, deleting ~/.wine and reinstalling.
This is the best way, but needs a bit of "translation" (the OP calls himself a 'noob', so...):

Open your file manager so you see your home folder, make sure that you can see 'hidden' files and folders ```
Places > Home Folder
View > Show Hidden Files

``` 
Now you can right click the .wine folder (note the "." before the name), and send to trash.

To 'reinstall' wine, go to ```
Applications > Wine > Configure Wine
```
This will create a new wine folder, and reset it to defaults.

If you have programs in the Wine programs list you don't want anymore, edit the Applications menu to remove the entries. (All this does is remove the 'shortcuts' to the programs. )

Hope this helps.

---

### Post by Soulcage on 2010-12-04
If you want wine to be like you just installed run this whole command in a terminal ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
```

---

