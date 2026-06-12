---
title: "Wine 1.2 leaving entries in."
date: 2011-01-27
forum: Wine
---

### Post by Brad55 on 2011-01-27
I'm having a little bit of a problem with Wine leaving entries in. I install Wine 1.2 on Ubuntu 10.04 64bit and because it would not run the program I want I un-installed it, and the program I wanted Wine to run was Dreamweaver 8. Now I know that Dreamweaver 8 will run under Wine because I have had it but not under Ubuntu.
Wine is leaving entries in some type of file that has to do with the file type. I can not file this file or how to remove these entries. See screen shots.

Can any one tell how to get these out I have tried deleting the Wine folder after I un-installed wine but that did not help and rebooting did not help. I want to reinstall wine at some other time but I don't want about 10 entries for IE or Notepad.

---

### Post by cogadh on 2011-01-31
One of the packages Wine depends on does that, but I can't remember which one and I don't have access to my Linux box at the moment. If you do a "--purge" of Wine instead of a simple uninstall it might make it go away. Additionally, if the package is marked as no longer needed after a Wine uninstall, you might be able to get rid of it by running "sudo apt-get autoremove".

---

### Post by Soulcage on 2011-02-02
If you want to remove the files that wine creates then run this command: ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*

``` You can use it even if wine is still installed, run winecfg after.

---

### Post by Brad55 on 2011-02-02
@cogadh I did the apt-get autoremove and it did not work.

@Soulcage I will have to try this.

Well I did find out how to do it the hard way. That is to go into your System>Preferences>Main Menu and delete all the entries dealing with wine.

Now on the other hand after I did that and re-installed wine I had to put them back in, but I had another computer sitting by.

---

